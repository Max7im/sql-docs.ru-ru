---
title: Репликация в базу данных SQL | Документация Майкрософт
ms.custom: ''
ms.date: 04/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Database replication
- replication, SQL Database
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1cc27917de59f10ccb41ef7b8254ac6b2e5c020e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43074703"
---
# <a name="replication-to-sql-database"></a>Репликация в базу данных SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Репликацию[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно настроить в [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
 
 ### <a name="supported-configurations"></a>**Поддерживаемые конфигурации:**  
 -  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может быть экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенным локально, или экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенным на виртуальной машине Azure в облаке. Дополнительные сведения см. в статье [Обзор SQL Server на виртуальных машинах Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).  
 - База[!INCLUDE[ssSDS](../../includes/sssds-md.md)] должна быть подписчиком с принудительной подпиской издателя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
 -  База данных распространителя и агенты репликации не могут размещаться в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
 - Поддерживается односторонняя репликация транзакций и создание моментальных снимков. Одноранговая репликация транзакций и репликация слиянием не поддерживаются.
 - Управляемый экземпляр Базы данных SQL (предварительная версия) поддерживает базы данных издателя и распространителя. См. дополнительные сведения о [репликации с использованием Управляемого экземпляра Базы данных SQL](replication-with-sql-database-managed-instance.md).
 
 ## <a name="versions"></a>Версии  
 - Минимальные требования к версиям издателя и распространителя:  
   
 -   [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)]  
 
 -   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
   
 -   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с пакетом обновления 1 (SP1) CU3  
   
 -   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] RTM CU10  
   
 -   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 2 (SP2) CU8  
   
 -   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , ожидаемая в версии с пакетом обновления 3 (SP3)  
   
 - Если вы попытаетесь настроить репликацию с помощью более старой версии, может возникнуть ошибка MSSQL_REPL20084 ("Процесс не может подключиться к подписчику") или MSSQL_REPL40532 (Не удается открыть сервер \<имя_сервера>, запрошенный в имени входа. Ошибка входа").  
 
 - Версия подписчика [!INCLUDE[ssSDS](../../includes/sssds-md.md)] должна быть не ниже 12; сам подписчик может находиться в любом регионе.  
   
 - Чтобы использовать все возможности [!INCLUDE[ssSDS](../../includes/sssds-md.md)], должны быть установлены последние версии [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx) и [SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx).  
   
 ## <a name="remarks"></a>Remarks  
 - Репликацию можно настроить с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или путем выполнения инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] на издателе. Настроить репликацию с помощью портала [!INCLUDE[ssSDS](../../includes/sssds-md.md)] нельзя.  
   
 - Для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в репликации можно использовать только учетные данные для входа [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
   
 - Реплицируемая таблица должна иметь первичный ключ.  
   
 - Вам понадобится существующая подписка Azure и [!INCLUDE[ssSDS](../../includes/sssds-md.md)] версии 12.  
   
 - В одной публикации на сервере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются подписчики [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (локальная версия и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на виртуальной машине Azure).  
   
 - Управление репликацией, мониторинг и устранение неполадок должны выполняться из локальной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
   
 - Поддерживаются только принудительные подписки на [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
   
 - В подписке `@subscriber_type = 0` для базы данных SQL поддерживается только **@subscriber_type = 0** .  
   
 - [!INCLUDE[ssSDS](../../includes/sssds-md.md)] не поддерживает двустороннюю, немедленную, обновляемую и одноранговую репликацию.      
   
 ## <a name="replication-architecture"></a>Архитектура репликации  
 ![Репликация в базу данных SQL](../../relational-databases/replication/media/replication-to-sql-database.png "Репликация в базу данных SQL")  
   
 ## <a name="scenarios"></a>Сценарии  
   
 ### <a name="typical-replication-scenario"></a>Сценарий стандартной репликации  
   
 1.  Создание публикации репликации транзакций в локальной базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
   
 2.  В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенном локально, используйте **мастер создания подписки** или инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] для создания принудительной подписки в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
   
 3.  В качестве исходного набора данных обычно используется моментальный снимок, созданный агентом моментальных снимков, который распространяется и применяется агентом распространителя. Исходный набор данных может также предоставляться через резервную копию или другие средства, например [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
   
 #### <a name="data-migration-scenario"></a>Сценарии переноса данных  
   
 1.  Использование репликации транзакций для репликации данных из локальной базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
   
 2.  Перенаправление клиента или приложения среднего уровня для обновления копии [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
   
 3.  Остановка обновления версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы и удаление публикации.  
   
 ## <a name="limitations"></a>Ограничения  
  В подписках [!INCLUDE[ssSDS](../../includes/sssds-md.md)] не поддерживаются следующие функции:  
   
 -   Копирование сопоставления групп файлов  
   
 -   Копирование схем секционирования таблиц  
   
 -   Копирование схем секционирования индексов  
   
 -   Копирование определяемой пользователем статистики  
   
 -   Копирование привязок по умолчанию  
   
 -   Копирование привязок правил  
   
 -   Копирование полнотекстовых индексов  
   
 -   Копирование XML XSD  
   
 -   Копирование XML-индексов  
   
 -   Копирование разрешений  
   
 -   Копирование пространственных индексов  
   
 -   Копирование отфильтрованных индексов  
   
 -   Копирование атрибутов сжатия данных  
   
 -   Копирование атрибутов разреженных столбцов  
   
 -   Преобразование типа filestream в типы данных MAX  
   
 -   Преобразование типа hierarchyId в типы данных MAX  
   
 -   Преобразование пространственных типов в типы данных MAX  
   
 -   Копирование расширенных свойств  
   
 -   Копирование разрешений  
   
### <a name="limitations-to-be-determined"></a>Ограничения, подлежащие определению 
 
 -   Копирование параметров сортировки  
   
 -   Выполнение в сериализованной транзакции хранимой процедуры  
   
 ## <a name="examples"></a>Примеры  
  Создание публикации и принудительной подписки. Дополнительные сведения см. в разделе:  
   
 -   [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)  
   
 -   [Создайте принудительную подписку](../../relational-databases/replication/create-a-push-subscription.md), указав имя логического сервера [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] в качестве подписчика (например, **N'azuresqldbdns.database.windows.net'**) и имя [!INCLUDE[ssSDS](../../includes/sssds-md.md)] в качестве целевой базы данных (например, **AdventureWorks**).  
   
 ## <a name="see-also"></a>См. также:  
 - [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 - [Создание принудительной подписки](../../relational-databases/replication/create-a-push-subscription.md)   
 - [Типы репликации](../../relational-databases/replication/types-of-replication.md)   
 - [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication.md)   
 - [Инициализация подписки](../../relational-databases/replication/initialize-a-subscription.md)  
