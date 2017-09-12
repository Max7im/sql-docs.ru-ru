## <a name="pacemakerNotify"></a> Агент ресурсов SQL Server для Pacemaker

До выхода CTP 1.4 агент ресурсов Pacemaker для групп доступности не мог определять, действительно ли актуальна реплика, помеченная как `SYNCHRONOUS_COMMIT`. Синхронизация с первичной репликой могла быть прервана, но уведомления об этом не поступали. Это значит, что агент мог сделать первичной устаревшую реплику, что, в свою очередь, вызывало потерю данных. 

Чтобы устранить эту проблему, в SQL Server 2017 с CTP 1.4 к `sys.availability_groups` добавляется `sequence_number`. `sequence_number` — это монотонно возрастающий BIGINT, который показывает, насколько актуальна локальная реплика группы доступности относительно остальных реплик в этой группе доступности. Это число обновляется при отработках отказа, добавлении или удалении реплик, а также выполнении других операций в группах доступности. Сначала оно обновляется в первичной реплике, а затем во вторичных. Таким образом вторичная актуальная реплика и первичная реплика будут иметь одинаковый порядковый номер. 

Когда необходимо повысить реплику до первичной, Pacemaker отправляет уведомления во все реплики, чтобы извлечь порядковый номер и сохранить его (мы называем это предварительным уведомлением). Затем, когда Pacemaker пытается обновить реплику до первичной, она обновляется, только если ее порядковый номер выше номеров всех остальных реплик. В противном случае операция обновления реплики отклоняется. Таким образом, до первичной реплики может быть обновлена только реплика с наибольшим значением порядкового номера, что позволяет избежать потери данных. 

Стоит заметить, что это работает, только если порядковый номер хотя бы одной реплики, доступной для обновления, совпадает с номером прежней первичной реплики. Для этого агент ресурсов Pacemaker по умолчанию настраивает `REQUIRED_COPIES_TO_COMMIT` таким образом, чтобы хотя бы одна вторичная реплика синхронной фиксации была актуальна и доступна для целевого объекта автоматической отработки отказа. При каждом действии мониторинга значение `REQUIRED_COPIES_TO_COMMIT` вычисляется (и, если нужно, обновляется) как ("число реплик синхронной фиксации"/2). Затем, при отработке отказа, агент ресурсов требует, чтобы (реплики `total number of replicas` - `required_copies_to_commit`) отреагировали на предварительное уведомление — так он сможет сделать одну из этих реплик первичной. Реплика с самым высоким значением `sequence_number` станет первичной. 

Рассмотрим, например, вариант группы доступности с тремя синхронными репликами — одной первичной и двумя вторичными репликами синхронной фиксации.

- `REQUIRED_COPIES_TO_COMMIT` — это 3 / 2 = 1

- Количество реплик, которые должны отреагировать на предварительное действие: 3 – 1 = 2. Таким образом, для запуска отработки отказа актуальными должны быть 2 реплики. Это значит, что в случае, если первичная реплика выдаст сбой, а одна из вторичных реплик перестанет отвечать и только одна из вторичных реплик отреагирует на предварительное действие, агент ресурсов не сможет гарантировать, что отреагировавшая реплика будет иметь наибольший порядковый номер, и отработка отказа не запустится.

Пользователь может переопределить поведение по умолчанию, отказавшись от автоматической настройки `REQUIRED_COPIES_TO_COMMIT` для ресурсов группы доступности, описанной выше.

>[!IMPORTANT]
>Нулевое значение `REQUIRED_COPIES_TO_COMMIT` создает риск потери данных. В случае сбоя первичной реплики агент ресурсов не запустит отработку отказа автоматически. Пользователю придется либо дождаться восстановления первичной реплики, либо выполнить отработку отказа вручную.

Чтобы задать для `REQUIRED_COPIES_TO_COMMIT` значение 0, выполните следующую команду:

```bash
sudo pcs resource update <**ag_cluster**> required_copies_to_commit=0
```

Эквивалентная команда с использованием crm (в SLES):

```bash
sudo crm resource param <**ag_cluster**> set required_synchronized_secondaries_to_commit 0
```

Чтобы восстановить вычисляемое значение по умолчанию, выполните следующую команду:

```bash
sudo pcs resource update <**ag_cluster**> required_copies_to_commit=
```

>[!NOTE]
>При обновлении свойств ресурсов все реплики останавливаются и перезапускаются. Это означает, что первичная реплика будет временно понижена до вторичной, а затем снова повышена, что приведет к ее временной недоступности для записи. Новое значение REQUIRED_COPIES_TO_COMMIT будет задано только после перезапуска реплик, а не сразу после выполнения команды pcs.

## <a name="balancing-high-availability-and-data-protection"></a>Баланс высокого уровня доступности и защиты данных 

Описанное выше поведение по умолчанию проявляется также в случае, если синхронных реплик 2 (первичная + вторичная). Для максимальной защиты данных Pacemaker по умолчанию задаст `REQUIRED_COPIES_TO_COMMIT = 1`, чтобы вторичная реплика всегда была актуальна.  

>[!WARNING]
>При этом возникает высокий риск недоступности первичной реплики из-за плановых и внеплановых простоев вторичной реплики. Пользователь может изменить поведение агента ресурсов по умолчанию, задав для `REQUIRED_COPIES_TO_COMMIT` значение 0:

```bash
sudo pcs resource update <**ag1**> required_copies_to_commit=0
```

После переопределения агент ресурсов будет использовать для `REQUIRED_COPIES_TO_COMMIT` новое значение и перестанет его вычислять. Это означает, что пользователям придется обновлять это значение вручную (например, при увеличении количества реплик).

В представленных ниже таблицах описывается результат сбоя первичной или вторичной реплики в различных конфигурациях ресурсов группы доступности.

### <a name="availability-group---2-sync-replicas"></a>Группа доступности — 2 реплики с синхронизацией

| |Сбой первичной реплики |Сбой одной вторичной реплики
|:---|:--- |:--- |
|`REQUIRED_COPIES_TO_COMMIT=0`|Пользователю необходимо выполнить команду FAILOVER вручную. <br>Возможна потеря данных.<br> Новая первичная реплика доступна для чтения и записи |Первичная реплика доступна для чтения и записи и подвержена риску потери данных.
|`REQUIRED_COPIES_TO_COMMIT=1` * |Кластер автоматически запустит команду FAILOVER. <br>Потери данных нет. <br> Новая первичная реплика будет отклонять все подключения до тех пор, пока предыдущая первичная реплика не будет восстановлена и не присоединится к группе доступности как вторичная. |Первичная реплика будет отклонять все подключения до тех пор, пока вторичная реплика не будет восстановлена.

\* Поведение агента ресурсов SQL Server для Pacemaker по умолчанию.

### <a name="availability-group---3-sync-replicas"></a>Группа доступности — 3 реплики с синхронизацией

| |Сбой первичной реплики |Сбой одной вторичной реплики
|:---|:--- |:--- |
|`REQUIRED_COPIES_TO_COMMIT=0`|Пользователю необходимо выполнить команду FAILOVER вручную. <br>Возможна потеря данных. <br>Новая первичная реплика доступна для чтения и записи. |Первичная реплика доступна для чтения и записи.
|`REQUIRED_COPIES_TO_COMMIT=1` * |Кластер автоматически запустит команду FAILOVER. <br>Потери данных нет. <br>Новая первичная реплика доступна для чтения и записи. |Первичная реплика доступна для чтения и записи. 

\* Поведение агента ресурсов SQL Server для Pacemaker по умолчанию.