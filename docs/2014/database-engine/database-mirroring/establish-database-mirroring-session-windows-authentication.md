---
title: Создание базы данных с использованием проверки подлинности Windows (SQL Server Management Studio) сеанса зеркального отображения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], sessions
ms.assetid: 7cb418d6-dce1-4a0d-830e-9c5ccfe3bd72
caps.latest.revision: 57
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d212f5f1dda7ebe0e596808d56fb2060af467a04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235664"
---
# <a name="establish-a-database-mirroring-session-using-windows-authentication-sql-server-management-studio"></a>Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
 Чтобы установить сеанс зеркального отображения базы данных и изменить свойства зеркального отображения для базы данных, воспользуйтесь страницей **Зеркальное отображение** диалогового окна **Свойства базы данных** . Перед переходом на страницу **Зеркальное отображение** для настройки зеркального отображения базы данных убедитесь, что выполнены следующие требования.  
  
-   Экземпляры основного и зеркального сервера должны работать под управлением одного и того же выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]— либо Standard, либо Enterprise. Кроме того, настоятельно рекомендуется размещать серверы в системах со сравнимой производительностью, которые могут справляться с одинаковой рабочей нагрузкой.  
  
    > [!NOTE]  
    >  Экземпляр следящего сервера доступен не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
-   Зеркальная база данных должна существовать и находиться в актуальном состоянии.  
  
     Создание зеркальной базы данных требует восстановления последней резервной копии основной базы данных (с ключевым словом WITH NORECOVERY) на экземпляре зеркального сервера. Необходимо также после полного резервного копирования выполнить резервное копирование одного или нескольких журналов и последовательно восстановить их в зеркальной базе данных (с ключевым словом WITH NORECOVERY). Дополнительные сведения см. в разделе [Подготовка зеркальной базы данных к зеркальному отображению (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
-   Если экземпляры сервера выполняются под разными учетными записями пользователей домена, каждому из них необходимо имя входа в базу данных **master** . Если оно отсутствует, необходимо создать его перед настройкой зеркального отображения. Дополнительные сведения см. в разделе [Разрешение сетевого доступа к конечной точке зеркального отображения базы данных с использованием проверки подлинности Windows (SQL Server)](../database-mirroring-allow-network-access-windows-authentication.md).  
  
### <a name="to-configure-database-mirroring"></a>Настройка зеркального отображения базы данных  
  
1.  После подключения к экземпляру основного сервера в обозревателе объектов щелкните имя сервера, чтобы развернуть дерево сервера.  
  
2.  Раскройте узел **Базы данных**и выберите базу данных для зеркального отображения.  
  
3.  Щелкните базу данных правой кнопкой мыши, выберите **Задачи**, а затем **Зеркальное отображение**. Откроется страница **Зеркальное отображение** диалогового окна **Свойства базы данных** .  
  
4.  Чтобы начать настройку зеркального отображения, нажмите кнопку **Настройка безопасности** для запуска мастера настройки безопасности зеркального отображения баз данных.  
  
    > [!NOTE]  
    >  Во время сеанса зеркального отображения базы данных этим мастером можно пользоваться только для добавления или изменения экземпляра следящего сервера.  
  
5.  Мастер настройки безопасности зеркального отображения баз данных автоматически создает конечную точку зеркального отображения (если она не существует) на каждом экземпляре сервера и вводит сетевые адреса серверов в поле, соответствующее роли экземпляра сервера (**Основной**, **Зеркальный**или **Следящий**).  
  
    > [!IMPORTANT]  
    >  При создании конечной точки мастер настройки безопасности зеркального отображения баз данных всегда использует проверку подлинности Windows. Прежде чем использовать мастер совместно с проверкой подлинности на основе сертификатов, конечные точки на каждом экземпляре сервера должны быть настроены на их использование. Кроме этого, все поля диалогового окна **Учетные записи служб** мастера должны остаться пустыми. Дополнительные сведения о создании конечных точек, настроенных на использование сертификатов, см. в разделе [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
6.  При необходимости можно изменить режим работы. Доступность определенных режимов работы зависит от того, был ли указан TCP-адрес для свидетеля. Существуют следующие варианты выбора.  
  
    |Параметр|Следящий сервер|Объяснение|  
    |------------|--------------|-----------------|  
    |**Высокая производительность (асинхронный)**|NULL (при наличии не используется, но сеансу требуется кворум)|Чтобы добиться максимальной производительности, зеркальная база данных всегда отражает прошедшее состояние основной базы данных, никогда полностью не совпадая с ней. Однако разрыв между базами данных, как правило, очень мал. Потеря участника приведет к следующим последствиям.<br /><br /> Если экземпляр зеркального сервера становится недоступным, основной сервер продолжает работу.<br /><br /> если экземпляр основного сервера становится недоступным, зеркальное отображение останавливается, но если сеанс не имеет следящего сервера (как рекомендовано) или следящий сервер подключен к зеркальному, то последний доступен в режиме «горячего» резервирования. Владелец базы данных может принудительно запустить службу на экземпляре зеркального сервера (с возможной потерей данных).<br /><br /> <br /><br /> Дополнительные сведения см. в статье [Переключение ролей во время сеанса зеркального отображения базы данных (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md).|  
    |**Высокий уровень безопасности без автоматического перехода на другой ресурс (синхронного)**|Нет|Гарантируется запись всех фиксированных транзакций на диск зеркального сервера.<br /><br /> Отработка отказа вручную возможна, если участники соединены друг с другом. Потеря участника приведет к следующим последствиям.<br /><br /> Если экземпляр зеркального сервера становится недоступным, основной сервер продолжает работу.<br /><br /> если экземпляр основного сервера становится недоступным, зеркальный сервер останавливается, но остается доступным в качестве «горячего» резерва. Владелец базы данных может включить службу на экземпляре зеркального сервера (с возможной потерей данных).<br /><br /> Дополнительные сведения см. в статье [Переключение ролей во время сеанса зеркального отображения базы данных (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md).|  
    |**Высокий уровень безопасности с автоматическим переходом на другой ресурс (синхронным)**|Да (требуется)|Гарантируется запись всех фиксированных транзакций на диск зеркального сервера. Доступность доводится до максимума, поскольку экземпляр следящего сервера начинает поддерживать автоматическую отработку отказа. Обратите внимание, что параметр **Высокая безопасность с автоматической отработкой отказа (синхронный)** можно выбрать только после того, как будет задан адрес следящего сервера. Отработка отказа вручную возможна, если участники соединены друг с другом.<br /><br /> При наличии следящего сервера потеря участника повлечет следующие последствия:<br /><br /> — Если на экземпляре основного сервера становится недоступным, происходит автоматическая отработка отказа. Экземпляр зеркального сервера начинает выполнять функции основного сервера и предлагает свою базу данных как основную.<br /><br /> — Если на экземпляре зеркального сервера становится недоступным, основной сервер продолжает работу.<br /><br /> Дополнительные сведения см. в статье [Переключение ролей во время сеанса зеркального отображения базы данных (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md).<br /><br /> **\*\* Важно! \*\*** Если следящий сервер отключается, для обеспечения доступности базы данных участники должны быть соединены друг с другом. Дополнительные сведения см. в разделе [Кворум: как следящий сервер влияет на доступность базы данных (зеркальное отображение базы данных)](quorum-how-a-witness-affects-database-availability-database-mirroring.md).|  
  
7.  Если выполняются все перечисленные ниже условия, то для запуска процесса зеркального отображения нажмите кнопку **Начать отображение** .  
  
    -   Установлено соединение с экземпляром основного сервера.  
  
    -   Настройки безопасности заданы верно.  
  
    -   Полностью определенные TCP-адреса экземпляров основного и зеркального серверов уже указаны (в разделе **Сетевые адреса серверов** ).  
  
    -   Если установлен режим работы **Высокая безопасность с автоматической отработкой отказа (синхронный)**, то также указывается полный TCP-адрес экземпляра следящего сервера.  
  
8.  После начала зеркального отображения можно изменить рабочий режим и сохранить изменения, нажав кнопку **ОК**. Обратите внимание, что переключение на режим высокой безопасности с автоматической отработкой отказа возможно, только если сначала был указан адрес следящего сервера.  
  
    > [!NOTE]  
    >  Чтобы удалить следящий сервер, удалите его сетевой адрес из поля **Следящий** . При переключении из режима высокого уровня безопасности с автоматической отработкой отказа в высокопроизводительный режим поле **Следящий** автоматически очищается.  
  
## <a name="see-also"></a>См. также  
 [Переключение ролей во время сеанса зеркального отображения базы данных (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md)   
 [Подготовка зеркальной базы данных к зеркальному отображению (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)   
 [Свойства базы данных (страница "Зеркальное отображение")](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Приостановка или возобновление сеанса зеркального отображения базы данных (SQL Server)](pause-or-resume-a-database-mirroring-session-sql-server.md)   
 [Настройка зеркальной базы данных на использование свойства TRUSTWORTHY (Transact-SQL)](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)   
 [Удаление зеркального отображения базы данных (SQL Server)](database-mirroring-sql-server.md)   
 [Управление именами входа и заданиями после переключения ролей (SQL Server)](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)   
 [Настройка зеркального отображения базы данных (SQL Server)](setting-up-database-mirroring-sql-server.md)   
 [Управление метаданными при обеспечении доступности базы данных на другом экземпляре сервера (SQL Server)](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [Добавление или замена следящего сервера зеркального отображения базы данных (среда SQL Server Management Studio)](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
  
