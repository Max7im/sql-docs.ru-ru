---
title: "Установка служб R SQL Server 2016 (в базе данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "установка служб R SQL Server"
- "Установка служб SQL Server машины обучения"
- "Установка служб R Services"
- "установить SQL машинного обучения"
ms.assetid: 
caps.latest.revision: 
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Active
ms.openlocfilehash: 0012b48101085b7ccb18695fbda1f25c10a6b90b
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2018
---
# <a name="install-sql-server-2016-r-services-in-database"></a>Установка служб SQL Server 2016 R Services (в базе данных) 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье объясняется, как установить и настроить **служб R SQL Server 2016 (в базе данных)**. Если SQL Server 2016, установите этот компонент позволяет выполнение кода R в SQL Server.

## <a name="bkmk_prereqs"> </a> Контрольный список действий перед установкой

+ SQL Server 2016 является обязательным. Если SQL Server 2016, установите [обучения машины службы (в базе данных) для SQL Server 2017 г](sql-machine-learning-services-windows-install.md) вместо него.

+ Требуется экземпляр ядра СУБД. Не удается установить R так же, хотя постепенно добавить его к существующему экземпляру.

+ Не устанавливайте службы R в отказоустойчивом кластере. Механизм безопасности, используемый для изоляции процессов R не совместим с среде отказоустойчивого кластера Windows Server.

+ Не устанавливайте службы R на контроллере домена. Часть процесса установки служб R завершится ошибкой.

+ Не устанавливайте **общие компоненты** > **R Server (изолированный)** на том же компьютере, где запущен экземпляр в базе данных. 

+ Параллельную установку с другими версиями R и Python возможны, так как экземпляр SQL Server использует своими собственными копиями с открытым исходным кодом R и Anaconda распределений. Однако выполнение кода, который использует Python и R на компьютере SQL Server за пределами SQL Server может привести к различным проблемам:
    
  + Можно использовать различные библиотеки и другой исполняемый файл и получить разные результаты, чем при выполнении в SQL Server.
  + SQL Server, что приведет к конфликтам ресурсов не может управляться Python и R-скриптов, запускаемых во внешних библиотеках.
  
Если вы использовали все предыдущие версии среды разработки Revolution Analytics или пакеты RevoScaleR или если вы установили все предварительные версии SQL Server 2016, их необходимо удалить. Под управлением более старых и новых версий RevoScaleR и других собственных пакетов не поддерживается. Для помощи в удалении предыдущих версий, в разделе [обновление и часто задаваемые вопросы установки служб SQL Server Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md).

> [!IMPORTANT]
> После завершения установки убедитесь, что для выполнения дополнительных действий после конфигурации, описанной в этой статье. Эти действия включают Включение SQL Server для использования внешних скриптов и добавление учетных записей, требуемых для SQL Server для выполнения заданий R от вашего имени. Изменения конфигурации обычно требуют перезапуска экземпляра или перезапуск службы панели запуска.

## <a name="get-the-installation-media"></a>Получение установочного носителя

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> Требование для установки исправления 

Корпорация Майкрософт выявила проблему с определенной версией двоичных файлов среды выполнения Microsoft VC++ 2013, которые SQL Server устанавливает в качестве необходимого компонента. Если это обновление двоичных файлов среды выполнения VC не установлено, в SQL Server могут возникать проблемы с надежностью в определенных сценариях. Перед установкой SQL Server выполните инструкции, приведенные в [заметках о выпуске SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch), чтобы узнать, требуется ли на вашем компьютере исправление для двоичных файлов среды выполнения VC.  

## <a name="bkmk2016top"></a>Запустите программу установки

Для локальных установок необходимо запускать программу установки с правами администратора. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленной общей папки необходимо использовать учетную запись домена с разрешениями на чтение и выполнение для удаленной общей папки.

1. Запустите мастер установки SQL Server 2016.

2. На **установки** выберите **автономная установка нового SQL Server или добавление компонентов к существующей установке**.
    
   ![Установка служб R (в базе данных)](media/2016-setup-installation-rsvcs.png "запуск установки компонента database engine со службами R Services")
   
3. На **Выбор компонентов** выберите следующие параметры:

   - Выберите **службы компонента Database Engine**. Компонент database engine требуется в каждом экземпляре, с применением машинного обучения.
   - Выберите **служб R (в базе данных)**. Устанавливает поддержку для использования в базе данных R.
    
     ![Выбор компонентов служб R](media/2016setup-rsvcs-features.png "выберите эти компоненты для R службы в базе данных")

    > [!IMPORTANT]
    > Не устанавливайте R Server и служб R в то же время. Обычно следует установить R Server (изолированный), чтобы создать среду, специалист по анализу данных или разработчик использует для подключения к SQL Server и развертывать решения R. Поэтому вы можете установить только R Server.

4.  На **согласия для установки Microsoft R Open** щелкните **Accept**.
  
    Это лицензионное соглашение, необходимое для загрузки, Microsoft R Open, включая распространения базовых пакетов R с открытым исходным и средств, а также улучшенные пакеты R и поставщиков услуг подключения от команды разработчиков Microsoft R.
  
5. После принятия лицензионного соглашения имеется небольшой паузы, во время подготовки установщик. Нажмите кнопку **Далее** при кнопка стала доступной.

6. На **все готово для установки** убедитесь, что включены следующие элементы, а затем выберите **установить**.

   + Службы ядра СУБД
   + Службы R (в базе данных)

    Запишите расположение папки по пути `..\Setup Bootstrap\Log` хранения файлов конфигурации. После завершения установки можно просмотреть установленные компоненты в файл сводки.

7. После завершения установки перезагрузите компьютер.

##  <a name="bkmk_enableFeature"></a>Разрешить выполнение внешних скриптов

1. Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Можно загрузить и установить соответствующую версию на этой странице: [загрузить SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > Также можно попробовать предварительный выпуск [операций SQL Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is), который поддерживает административные задачи и запросы к SQL Server.
  
2. Подключитесь к экземпляру, в которой установлены службы обучения для компьютера, нажмите кнопку **новый запрос** откройте окно запроса и выполните следующую команду:

   ```SQL
   sp_configure
   ```
    На данном этапе значение для свойства `external scripts enabled` должно быть **0**. Это, так как функция отключена по умолчанию. Компонент должны явно включены администратором, прежде чем вы сможете выполнять сценарии R или Python.
     
3. Чтобы включить внешние средства написания сценариев, выполните следующую инструкцию:
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>Перезапустите службу.

По завершении установки перезапустите компонент database engine, прежде чем переходить к другому, Включение выполнения скрипта.

Я также автоматически при перезапуске связанный [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] службы.

Можно перезапустить службу при помощи правой кнопкой мыши **перезапустите** команды для экземпляра в среде SSMS или с помощью **службы** панели на панели управления или с помощью [диспетчер конфигурации SQL Server ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Проверка установки

Чтобы убедиться, что запущены все компоненты, используемые для запуска внешнего сценария, выполните следующие действия.

1. В SQL Server Management Studio откройте новое окно запроса и выполните следующую команду:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    Задайте для **run_value** значение 1.

2. Откройте **служб** панели или диспетчер конфигурации SQL Server и проверьте **службы панели запуска SQL Server** выполняется. Следует установить одну службу для каждого экземпляра ядра базы данных, имеющего R или Python. Если не запущена, перезапустите службу. Дополнительные сведения см. в разделе [компоненты для поддержки интеграции Python](../python/new-components-in-sql-server-to-support-python-integration.md).

7. Если панель запуска выполняется, следует выполнить простой R, чтобы убедиться, что внешних сред выполнения сценариев может обмениваться данными с SQL Server. 

    Откройте новый **запроса** окна в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем запустите скрипт примерно следующего вида:
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    Скрипт может занять несколько, для запуска в первый раз загружается среда выполнения внешнего сценария. Результаты должны выглядеть следующим образом:

    | hello |
    |----|
    | 1|

## <a name="bkmk_FollowUp"></a> Дополнительная настройка

При успешном выполнении шага проверки внешнего сценария Python команды запускаются из SQL Server Management Studio, Visual Studio Code или любым другим клиентом, можно отправить инструкции T-SQL на сервере.

Если при выполнении команды произошла ошибка, просмотрите дополнительные шаги настройки в этом разделе. Может потребоваться указать дополнительные соответствующие параметры конфигурации для службы или базы данных.

Наиболее распространенные сценарии, которые требуют дополнительных изменений:

* [Настройка брандмауэра Windows для входящих подключений](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [Включить дополнительные сетевые протоколы](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Разрешить удаленные подключения](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Расширить встроенные разрешения для удаленных пользователей](#bkmk_configureAccounts)
* [Предоставлены разрешения на выполнение внешних скриптов](#bkmk_AllowLogon)
* [Предоставление доступа к отдельным базам данных](#permissions-db)

> [!NOTE]
> Не все перечисленные изменения требуются и не могут быть необходимы. Требования зависят от схемы безопасности, где установлен SQL Server, и как пользователи для подключения к базе данных и выполнения внешних скриптов. Дополнительные советы по устранению неполадок можно найти здесь: [часто задаваемые вопросы по обновлению и установке](../r/upgrade-and-installation-faq-sql-server-r-services.md)

### <a name="bkmk_configureAccounts"></a>Включить неявной проверки подлинности для учетной записи группы панель запуска

Во время установки, некоторые учетные записи пользователей Windows создаются для выполнения задачи, связанные с маркером безопасности [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] службы. Когда пользователь отправляет сценарий R из внешнего клиента, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] активирует учетной записи свободных рабочих, сопоставляется удостоверения вызывающего пользователя и запускает скрипт R от имени пользователя. Эта новая служба компонента database engine поддерживает безопасное выполнение внешних скриптов, вызывается *неявной проверки подлинности*.

Можно просмотреть эти учетные записи в группу пользователей Windows **SQLRUserGroup**. По умолчанию создаются 20 рабочих учетных записей, которое обычно является более чем достаточно для выполнения R заданий.

Тем не менее, если требуется выполнять сценарии R из клиента обработки и анализа удаленных данных и используется проверка подлинности Windows, необходимо предоставить эти учетные записи работника разрешено выполнять вход систему [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр от вашего имени.

1. В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в обозревателе объектов разверните узел **Безопасность**, щелкните правой кнопкой мыши **Имена входа**и выберите пункт **Создать имя входа**.
2. В **Создание имени входа** выберите **поиска**.
3. Выберите **типы объектов** и **группы** флажки и снимите все флажки.
4. Нажмите кнопку **Дополнительно**, убедитесь, что расположение для поиска текущего компьютера и нажмите кнопку **найти**.
5. В списке учетных записей групп на сервере, пока не найдете начинающееся `SQLRUserGroup`.
    
    + Имя группы, связанной со службой запуска для _экземпляр по умолчанию_ всегда является просто **SQLRUserGroup**. Выберите эту учетную запись только для экземпляра по умолчанию.
    + Если вы используете _именованный экземпляр_, добавляется имя по умолчанию имя экземпляра `SQLRUserGroup`. Таким образом, если экземпляр имеет имя «MLTEST», имя группы пользователей по умолчанию для этого экземпляра будет **SQLRUserGroupMLTest**.
5. Нажмите кнопку **ОК** закрыть диалоговое окно расширенного поиска и убедитесь, что выделен ли учетная запись для экземпляра. Каждый экземпляр можно использовать только собственные службы для запуска и группа, созданная для этой службы.
6. Нажмите кнопку **ОК** еще раз, чтобы закрыть **Выбор пользователя или группы** диалоговое окно.
7. В **Создание имени входа** диалоговое окно, нажмите кнопку **ОК**. По умолчанию имя входа назначается **общедоступной** роли и имеет разрешение на подключение к ядру СУБД.

### <a name="bkmk_AllowLogon"></a>Предоставить пользователям разрешение на выполнение внешних скриптов

> [!NOTE]
> Если используется имя входа SQL для выполнения скриптов R в контексте вычислений SQL Server, этот шаг не требуется.

Если вы установили [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в экземпляре, обычно выполняются сценарии с правами администратора, или по крайней мере владелец базы данных, и поэтому имеют неявные разрешения для выполнения различных операций, все данные в базе данных, а также возможность установить новые пакеты При необходимости.

Однако в сценарии предприятия, большинство пользователей, включая пользователей, доступ к базе данных с помощью имен входа SQL, имеют такие разрешения более высокого уровня. Таким образом для каждого пользователя, который будет работать в сценарии R, необходимо предоставить разрешения пользователя для запуска скриптов в каждой базе данных, где будет использоваться внешних скриптов.

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> Нужно помочь в установке? Сомневаетесь, выполнили ли вы все действия? Эти пользовательские отчеты можно используйте для проверки состояния установки и выполнить дополнительные действия. 
> 
> [Отслеживать пользовательские отчеты с помощью службы обучения машины](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

### <a name="permissions-db"></a> Предоставьте вашей пользователям чтение, запись или DDL права доступа к базе

Учетная запись пользователя, который используется для выполнения R может необходимо считывать данные из других баз данных, создания новых таблиц для хранения результатов и записывать данные в таблицах. Поэтому для каждого пользователя, будут выполняться скрипты R, убедитесь, что у пользователя есть соответствующие разрешения в базе данных: *db_datareader*, *db_datawriter*, или *db_ddladmin*.

Например, приведенная ниже инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] предоставляет имени входа SQL *MySQLLogin* права на выполнение запросов T-SQL в базе данных *RSamples* . Для выполнения этой инструкции имя входа SQL уже должно существовать в контексте безопасности сервера.

```SQL
USE RSamples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Дополнительные сведения о разрешениях, которые включены в каждой роли см. в разделе [роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md).


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Создание источника данных ODBC для экземпляра в клиенте обработки и анализа данных

Если создать решение R на клиентском компьютере обработки и анализа данных, необходимо запустить код с помощью имени компьютера SQL Server в контексте можно использовать встроенную проверку подлинности Windows или имени входа SQL.

* Для имен входа SQL: имя входа должно иметь соответствующие разрешения на доступ к базе данных, из которой будут считываться данные. Это можно сделать, добавив *подключиться к* и *ВЫБЕРИТЕ* разрешения, либо путем добавления имени входа *db_datareader* роли. Для имен входа, которые необходимо создать объекты, добавить *DDL_admin* права. Для имен входа, которые необходимо сохранить данные в таблицах, добавьте имя входа для *db_datawriter* роли.

* Для проверки подлинности Windows: может потребоваться настроить источник данных ODBC на клиенте обработки и анализа данных, который указывает имя экземпляра и другие сведения. Дополнительные сведения см. в разделе [администратор источников данных ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="suggested-optimizations"></a>Предлагаемые оптимизации

Теперь, когда у вас есть все работает, может потребоваться оптимизировать сервер для поддержки машинного обучения или установки обученная моделей.

### <a name="add-more-worker-accounts"></a>Добавить больше рабочих учетных записей

Если вы считаете, что можно активно использовать R или если ожидается, что несколько пользователей одновременно быть выполнение скриптов, можно увеличить количество рабочих учетных записей, назначенных для службы панели запуска. Дополнительные сведения см. в разделе [изменение пула учетных записей пользователей для служб SQL Server Machine Learning](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="bkmk_optimize"></a>Оптимизировать сервер для выполнения внешних скриптов

Параметры по умолчанию для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установки предназначены для оптимизации баланса сервера для различных служб, поддерживаемые компонентом database engine, которая может включать извлечения, преобразования и загрузки (ETL) процессов, отчетов, аудите, и приложения, использующие [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных. Таким образом в конфигурации по умолчанию может оказаться ресурсы для машинного обучения иногда ограничен или регулировать, особенно в операции с интенсивным использованием памяти.

Чтобы обеспечить задач обучения машины приоритеты и соответствующим образом ресурсов, рекомендуется использовать для настройки внешнего пула ресурсов регулятора ресурсов SQL Server. Можно также изменить объем памяти, выделяемый для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компонент database engine, или увеличьте количество учетных записей, которые работают под [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] службы.

- Чтобы настроить пул ресурсов для управления внешними ресурсами, см. [создания пула внешних ресурсов](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Чтобы изменить объем памяти, зарезервированной для базы данных, в разделе [параметры конфигурации памяти сервера](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Чтобы изменить количество учетных записей R можно запустить, [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], в разделе [изменение пула учетных записей пользователей для машинного обучения](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

Если в выпуске Standard Edition и не имеют регулятора ресурсов, можно использовать динамические административные представления (DMV) и расширенных событий, а также события Windows, мониторинг, чтобы обеспечить управление ресурсами сервера, используемые R. Дополнительные сведения см. в разделе [мониторинг и управление службами R](../r/managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Установка дополнительных R-пакетов

Решения R, который создается для SQL Server может вызывать базовых функций R, функции из packes properietary, устанавливается вместе с SQL Server и пакетов сторонних R, совместимыми с версией открытым исходным кодом R, устанавливаемые с SQL Server.

Пакеты, которыми вы хотите пользоваться из SQL Server, должны быть установлены в библиотеке по умолчанию, используемой экземпляром. Если имеется отдельная Установка служб R на компьютере или установленных пакетов для библиотек пользователей, его нельзя будет использовать эти пакеты из T-SQL.

Процесс установки пакетов и управления ими R отличается в SQL Server 2016 и 2017 г. SQL Server. В SQL Server 2016 администратор базы данных необходимо установить пакеты R, которые нужны пользователю. В SQL Server 2017 г можно настроить группы пользователей для совместного использования пакетов на уровне каждой базы данных или настроить роли базы данных, чтобы пользователи могли установить собственные пакеты. Дополнительные сведения см. в разделе [пакета управления](../r/r-package-management-for-sql-server-r-services.md).


## <a name="get-help"></a>Получить справку

Нужна помощь с установку или обновление? Ответы на часто задаваемые вопросы и известные проблемы см. в следующей статье:

* [Обновление и установка часто задаваемые вопросы — Machine Services обучения](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Чтобы проверить состояние установки экземпляра и устранить распространенные проблемы, попробуйте следующие пользовательские отчеты.

* [Пользовательские отчеты для служб SQL Server R](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Следующие шаги

Разработчики R можно начать работу с несколько простых примеров и основные сведения о работе с SQL Server R. Следующий шаг см. по следующим ссылкам:

+ [Учебник: Запускать в T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Учебник: Анализ в базе данных для разработчиков R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Чтобы просмотреть примеры машинного обучения, основанные на реальных сценариев, в разделе [машинного обучения учебники](../tutorials/machine-learning-services-tutorials.md).

