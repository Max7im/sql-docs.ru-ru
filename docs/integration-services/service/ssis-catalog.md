---
title: "Каталог служб SSIS | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.ssms.iscreatecatalog.f1
- sql13.ssis.ssms.iscatalogprop.general.f1
- sql13.ssis.dbupgradewizard.f1
ms.assetid: 24bd987e-164a-48fd-b4f2-cbe16a3cd95e
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 0bcdf5c7eec91bccabc4b7b54f6121bec4d6c7f2
ms.openlocfilehash: 82784542c0f6c21bf803590aa4af0ea7942516cf
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---

# <a name="ssis-catalog"></a>Каталог служб SSIS
  Каталог **SSISDB** служит центральным пунктом для работы с проектами служб [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] (SSIS), развернутыми на сервере служб [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)]. Например, можно задавать параметры проектов и пакетов, настраивать среды для указания значений времени выполнения для пакетов, выполнять пакеты и проводить устранение неполадок, а также управлять операциями на сервере служб [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] .  
  
 Объекты, которые хранятся в каталоге **SSISDB** , включают проекты, пакеты, параметры, среды и журнал операций.  
  
 Для просмотра объектов, параметров и рабочих данных, которые хранятся в каталоге **SSISDB** , создайте запрос к представлениям в базе данных **SSISDB** . Для управления объектами вызывайте хранимые процедуры в базе данных **SSISDB** или используйте пользовательский интерфейс каталога **SSISDB** . Во многих случаях одну и ту же задачу можно выполнить и в пользовательском интерфейсе, и путем вызова хранимой процедуры.  
  
 Чтобы обеспечить поддержку базы данных **SSISDB** , рекомендуется применять предопределенные политики предприятия для управления пользовательскими базами данных. Дополнительные сведения о создании планов обслуживания см. в разделе [Maintenance Plans](../../relational-databases/maintenance-plans/maintenance-plans.md).  
  
 Каталог базы данных **SSISDB** и база данных **SSISDB** поддерживают Windows PowerShell. Дополнительные сведения об использовании SQL Server с Windows PowerShell см. в разделе [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md). Примеры использования Windows PowerShell для выполнения задач, например таких как развертывание проекта, см. в записи блога [SSIS и Powershell в SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=242539)на сайте blogs.msdn.com.  
  
 Дополнительные сведения о просмотре данных операций см. в разделе [Наблюдение за выполнением пакетов и других операций](../../integration-services/performance/monitor-running-packages-and-other-operations.md).  
  
 Для доступа к каталогу **SSISDB** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] соединитесь с ядром СУБД [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а затем разверните узел **Каталоги служб Integration Services** в обозревателе объектов. Для доступа к базе данных **SSISDB** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] разверните узел «Базы данных» в обозревателе объектов.  
  
> [!NOTE]
> Невозможно переименовать базу данных **SSISDB** .  
  
> [!NOTE]
> Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , к которому присоединена база данных **SSISDB** , остановлен или не отвечает, процесс ISServerExec.exe завершается. Сообщение записывается в журнал событий Windows.  
>   
>  Если ресурсы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] переходят на другой ресурс в процессе отработки отказа кластера, выполняемые пакеты не перезапускаются. Перезапуск пакетов вы можете выполнять с помощью контрольных точек. Дополнительные сведения см. в разделе [Restart Packages by Using Checkpoints](../../integration-services/packages/restart-packages-by-using-checkpoints.md).  
  
## <a name="features-and-capabilities"></a>Функции и возможности  
  
-   [Идентификаторы объектов каталога](../../integration-services/service/ssis-catalog.md#CatalogObjectIdentifiers)  
  
-   [Конфигурация каталога](../../integration-services/service/ssis-catalog.md#Configuration)  
  
-   [Разрешения](../../integration-services/service/ssis-catalog.md#Permissions)  
  
-   [Папки](../../integration-services/service/ssis-catalog.md#Folders)  
  
-   [Проекты и пакеты](../../integration-services/service/ssis-catalog.md#ProjectsAndPackages)  
  
-   [Параметры](../../integration-services/service/ssis-catalog.md#Parameters)  
  
-   [Серверные среды, переменные сервера и ссылки на серверные среды](../../integration-services/service/ssis-catalog.md#ServerEnvironments)  
  
-   [Выполнение и проверки](../../integration-services/service/ssis-catalog.md#Executions)  

##  <a name="CatalogObjectIdentifiers"></a> Идентификаторы объектов каталога  
 При создании нового объекта в каталоге необходимо назначить имя объекта. Идентификатором объекта является его имя. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет правила, указывающие, какие символы могут использоваться в идентификаторе. Имена следующих объектов должны соответствовать правилам для идентификаторов.  
  
-   Папка  
  
-   Проект  
  
-   Среда  
  
-   Параметр  
  
-   Переменная среды  
  
###  <a name="Folder"></a> Папка, проект, среда  
 Учитывайте следующие правила при переименовании папки, проекта или среды.  
  
-   Недопустимые символы включают символы ASCII/Юникода с кодами от 1 до 31, кавычки ("«), меньше (\<), больше (>), вертикальная черта (|), backspace (\b), значение null (\0) и табуляции (\t).  
  
-   Имя не должно содержать начальных и конечных пробелов.  
  
-   @ не допускается в качестве первого символа, но в последующих символах может использоваться @.  
  
-   Длина имени должна быть больше 0 и меньше или равна 128.  
  
###  <a name="Parameter"></a> Параметр  
 Принимайте во внимание следующие правила при именовании параметра.  
  
-   Первым символом имени должна быть буква, по определению стандарта Юникод 2.0, или символ подчеркивания (_).  
  
-   Далее могут следовать буквы или цифры, по определению стандарта Юникод 2.0, или символы подчеркивания (_).  
  
###  <a name="EnvironmentVariable"></a> Переменная среды  
 Учитывайте следующие правила при наименовании переменной среды  
  
-   Недопустимые символы включают символы ASCII/Юникода с кодами от 1 до 31, кавычки ("«), меньше (\<), больше (>), вертикальная черта (|), backspace (\b), значение null (\0) и табуляции (\t).  
  
-   Имя не должно содержать начальных и конечных пробелов.  
  
-   @ не допускается в качестве первого символа, но в последующих символах может использоваться @.  
  
-   Длина имени должна быть больше 0 и меньше или равна 128.  
  
-   Первым символом имени должна быть буква, по определению стандарта Юникод 2.0, или символ подчеркивания (_).  
  
-   Далее могут следовать буквы или цифры, по определению стандарта Юникод 2.0, или символы подчеркивания (_).  
  
##  <a name="Configuration"></a> Конфигурация каталога  
 Для точной настройки поведения каталога измените свойства каталога. Свойства каталога определяют методы шифрования конфиденциальных данных и способы хранения данных об управлении версиями операций и проектов. Задать свойства каталога можно в диалоговом окне **Свойства каталога** или с помощью хранимой процедуры [catalog.configure_catalog (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md). Просмотреть свойства можно в диалоговом окне или с помощью запроса [catalog.catalog_properties (база данных SSISDB)](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md). Диалоговое окно можно открыть, щелкнув **SSISDB** правой кнопкой мыши в обозревателе объектов.  
  
###  <a name="Cleanup"></a> Очистка версий операций и проектов  
 Данные о состоянии для многих из этих операций в каталоге хранятся во внутренних таблицах базы данных. Например, каталог отслеживает состояние выполнения пакета и развертывания проекта. Чтобы поддерживался размер данных операций, для удаления старых данных используется **задание по обслуживанию служб SSIS** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Это задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается при установке служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Вы можете обновить или повторно развернуть проект [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с тем же именем в той же папке в каталоге. По умолчанию при каждом повторном развертывании проекта в каталоге **SSISDB** сохраняется предыдущая версия проекта. Чтобы поддерживался размер данных операций, для удаления старых версий проектов используется **задание обслуживания сервера служб SSIS** .  
 
Для запуска **задания обслуживания сервера служб SSIS**службы SSIS создают имя для входа SQL Server **##MS_SSISServerCleanupJobLogin##**. Это имя входа предназначено только для внутреннего использования службами SSIS.
  
 Следующие два свойства каталога **SSISDB** определяют поведение этого задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Просмотреть и изменить свойства вы можете в диалоговом окне **Свойства каталога** или с помощью процедур [catalog.catalog_properties (база данных SSISDB)](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) и [catalog.configure_catalog (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md).  
  
 **Периодическая очистка журналов**  
 Шаг задания для очистки операций запускается в том случае, если это свойство имеет значение **True**.  
  
 **Срок хранения (в днях)**  
 Определяет максимальный срок хранения данных о допустимых операциях (в днях). Более старые данные удаляются.  
  
 Минимальное значение срока хранения — 1 день. Максимальное значение ограничено только максимальным значением данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **int**. Сведения об этом типе данных см. в разделе [int, bigint, smallint, and tinyint (Transact-SQL)](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).  
  
 **Периодическое удаление старых версий**  
 Шаг задания для очистки версий проекта запускается в том случае, если это свойство имеет значение **True**.  
  
 **Максимальное количество версий в проекте**  
 Определяет, сколько версий проекта будет храниться в каталоге. Более старые версии проектов удаляются.  
  
###  <a name="Encryption"></a> Алгоритм шифрования  
 Свойство **Алгоритм шифрования** указывает тип шифрования, который используется при шифровании значений конфиденциальных параметров. Вы можете выбрать из следующих типов шифрования.  
  
-   AES_256 (по умолчанию)  
  
-   AES_192  
  
-   AES_128  
  
-   DESX  
  
-   TRIPLE_DES_3KEY  
  
-   TRIPLE_DES  
  
-   DES  
  
 При развертывании проекта [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]каталог автоматически шифрует данные пакета и конфиденциальные значения. Каталог также автоматически расшифровывает данные после их получения. Каталог SSISDB использует уровень защиты **ServerStorage** . Дополнительные сведения см. в разделе [Access Control for Sensitive Data in Packages](../../integration-services/security/access-control-for-sensitive-data-in-packages.md).  
  
 Изменение алгоритма шифрования занимает длительное время. Сначала сервер использует указанный ранее алгоритм для расшифровки всех значений конфигурации. Затем сервер использует новый алгоритм для повторного шифрования значений. При выполнении этого процесса на сервере не могут выполняться другие операции служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Таким образом, чтобы обеспечить непрерывное выполнение операций служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , для алгоритма шифрования задается значение только для чтения в диалоговом окне в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 Чтобы изменить настройку свойства **алгоритма шифрования** , переведите базу данных **SSISDB** в однопользовательский режим и вызовите хранимую процедуру catalog.configure_catalog. Используйте ENCRYPTION_ALGORITHM для аргумента *property_name*. Список поддерживаемых значений свойств см. в разделе [catalog.catalog_properties (база данных SSISDB)](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md). Дополнительные сведения о хранимой процедуре см. в разделе [catalog.configure_catalog (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md).  
  
 Дополнительные сведения об однопользовательском режиме см. в разделе [Установка однопользовательского режима базы данных](../../relational-databases/databases/set-a-database-to-single-user-mode.md). Дополнительные сведения о шифровании и алгоритмах шифрования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]см. в подразделах раздела [Шифрование SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md).  
  
 Для шифрования используется главный ключ базы данных. Ключ создается при создании каталога.  
  
 В следующей таблице приведены имена свойств, показанных в диалоговом окне **Свойства каталога** , а также соответствующие свойства в представлении базы данных.  
  
|Имя свойства (диалоговое окно**Свойства каталога** )|Имя свойства (представление базы данных)|  
|---------------------------------------------------------|-------------------------------------|  
|Имя алгоритма шифрования|ENCRYPTION_ALGORITHM|  
|Периодическая очистка журналов|OPERATION_CLEANUP_ENABLED|  
|Срок хранения (в днях)|RETENTION_WINDOW|  
|Периодическое удаление старых версий|VERSION_CLEANUP_ENABLED|  
|Максимальное количество версий в проекте|MAX_PROJECT_VERSIONS|  
|Серверное значение уровня ведения журнала по умолчанию|SERVER_LOGGING_LEVEL|  
  
##  <a name="Permissions"></a> Разрешения  
 Проекты, среды и пакеты содержатся в папках, которые являются защищаемыми объектами. Вы можете предоставить разрешения для папки, включая разрешение MANAGE_OBJECT_PERMISSIONS. Разрешение MANAGE_OBJECT_PERMISSIONS позволяет делегировать пользователю разрешения на администрирование содержимого папки, не предоставляя ему членства в роли ssis_admin. Вы можете также предоставлять разрешения проектам, средам и операциям. К операциям относятся инициализация [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], развертывание проектов, создание и запуск выполнений, проверка проектов и пакетов, а также настройка каталога **SSISDB** .  
  
 Дополнительные сведения о ролях баз данных см. в разделе [Роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
 В каталоге SSISDB используется триггер DDL ddl_cleanup_object_permissions для принудительного обеспечения целостности сведений о разрешениях для защищаемых объектов служб SSIS. Триггер срабатывает, когда участник базы данных, например пользователь базы данных, роль базы данных или роль приложения базы данных, удаляется из базы данных SSISDB.  
  
 Если участник предоставлял или запрещал права доступа другим участникам, их необходимо отменить, прежде чем можно будет удалить этого участника. В противном случае возвращается сообщение об ошибке, если система пытается удалить участника. Триггер удаляет все записи разрешений, в которых участник базы данных является получателем разрешений.  
  
 Рекомендуется не отключать триггер, так как он гарантирует отсутствие потерянных записей разрешений после удаления участника базы данных из базы данных **SSISDB** .  
  
### <a name="managing-permissions"></a>Управление разрешениями  
 Вы можете управлять разрешениями на основе пользовательского интерфейса [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , хранимых процедур и пространства имен <xref:Microsoft.SqlServer.Management.IntegrationServices> .  
  
 Для управления разрешениями с помощью пользовательского интерфейса [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] используются следующие диалоговые окна.  
  
-   Для папки пользуйтесь страницей **Разрешения** в диалоговом окне [Folder Properties Dialog Box](../../integration-services/service/folder-properties-dialog-box.md)  
  
-   Для проекта пользуйтесь страницей **Разрешения** в диалоговом окне [Project Properties Dialog Box](../../integration-services/service/project-properties-dialog-box.md).  
  
-   Для среды пользуйтесь страницей **Разрешения** в диалоговом окне [NIB: свойства среды](http://msdn.microsoft.com/en-us/6a91a8d4-0006-4cfd-9759-3e4295ae452b).  
  
 Для управления разрешениями с помощью Transact-SQL вызовите процедуру [catalog.grant_permission (SSISDB Database)](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md), [catalog.deny_permission (SSISDB Database)](../../integration-services/system-stored-procedures/catalog-deny-permission-ssisdb-database.md) или [catalog.revoke_permission (SSISDB Database)](../../integration-services/system-stored-procedures/catalog-revoke-permission-ssisdb-database.md). Чтобы просмотреть действующие разрешения текущего участника для всех объектов, выполните запрос [catalog.effective_object_permissions (база данных SSISDB)](../../integration-services/system-views/catalog-effective-object-permissions-ssisdb-database.md). В этом разделе содержатся описания различных типов разрешений. Для просмотра разрешений, явным образом назначенных пользователю, выполните запрос [catalog.explicit_object_permissions (база данных SSISDB)](../../integration-services/system-views/catalog-explicit-object-permissions-ssisdb-database.md).  
  
##  <a name="Folders"></a> Папки  
 Папка содержит один или несколько проектов и сред в каталоге **SSISDB** . Вы можете использовать представление [catalog.folders (база данных SSISDB)](../../integration-services/system-views/catalog-folders-ssisdb-database.md) для получения доступа к сведениям о папках в каталоге. Для управления папками вы можете использовать следующие хранимые процедуры.  
  
-   [catalog.create_folder (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-create-folder-ssisdb-database.md)  
  
-   [catalog.delete_folder (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-delete-folder-ssisdb-database.md)  
  
-   [catalog.rename_folder (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-rename-folder-ssisdb-database.md)  
  
-   [catalog.set_folder_description (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-folder-description-ssisdb-database.md)  
  
##  <a name="ProjectsAndPackages"></a> Проекты и пакеты  
 Каждый проект может содержать несколько пакетов. Как проекты, так и пакеты могут содержать параметры и ссылки на среды. Доступ к параметрам и ссылкам на среды возможен с использованием [Configure Dialog Box](../../integration-services/service/configure-dialog-box.md).  
  
 Вы можете выполнять другие задачи администрирования проекта, вызывая следующие хранимые процедуры.  
  
-   [catalog.delete_project (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-delete-project-ssisdb-database.md)  
  
-   [catalog.deploy_project (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database.md)  
  
-   [catalog.get_project (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-get-project-ssisdb-database.md)  
  
-   [catalog.move_project (база данных SSISDB)](../Topic/catalog.move_project%20\(\(SSISDB%20Database\).md)  
  
-   [catalog.restore_project (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database.md)  
  
 Эти представления содержат сведения о пакетах, проектах и версиях проектов.  
  
-   [catalog.projects (база данных SSISDB)](../../integration-services/system-views/catalog-projects-ssisdb-database.md)  
  
-   [catalog.packages (база данных SSISDB)](../../integration-services/system-views/catalog-packages-ssisdb-database.md)  
  
-   [catalog.object_versions (база данных SSISDB)](../../integration-services/system-views/catalog-object-versions-ssisdb-database.md)  
  
##  <a name="Parameters"></a> Параметры  
 Параметры используются для присвоения значений свойствам пакета во время выполнения пакета. Для задания значения параметра проекта или пакета и очистки этого значения следует вызвать процедуру [catalog.set_object_parameter_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database.md) или [catalog.clear_object_parameter_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database.md). Чтобы задать значение параметра для экземпляра выполнения, следует вызвать [catalog.set_execution_parameter_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md). Значения параметров по умолчанию можно получить, вызвав процедуру [catalog.get_parameter_values (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database.md).  
  
 Эти представления показывают параметры для всех пакетов и проектов, а также значения параметров, используемые для экземпляра выполнения.  
  
-   [catalog.object_parameters (база данных SSISDB)](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md)  
  
-   [catalog.execution_parameter_values (база данных SSISDB)](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)  
  
##  <a name="ServerEnvironments"></a> Серверные среды, переменные сервера и ссылки на серверные среды  
 Серверные среды содержат переменные сервера. Значения переменных могут использоваться при выполнении или проверке пакета на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Следующие хранимые процедуры позволяют выполнять многие другие задачи управления для сред и переменных.  
  
-   [catalog.create_environment (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-create-environment-ssisdb-database.md)  
  
-   [catalog.delete_environment (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-delete-environment-ssisdb-database.md)  
  
-   [catalog.move_environment (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-move-environment-ssisdb-database.md)  
  
-   [catalog.rename_environment (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-rename-environment-ssisdb-database.md)  
  
-   [catalog.set_environment_property (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-environment-property-ssisdb-database.md)  
  
-   [catalog.create_environment_variable (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-create-environment-variable-ssisdb-database.md)  
  
-   [catalog.delete_environment_variable (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-delete-environment-variable-ssisdb-database.md)  
  
-   [catalog.set_environment_variable_property (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-environment-variable-property-ssisdb-database.md)  
  
-   [catalog.set_environment_variable_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-environment-variable-value-ssisdb-database.md)  
  
 Вызов хранимой процедуры [catalog.set_environment_variable_protection (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-environment-variable-protection-ssisdb-database.md) позволит установить бит конфиденциальности для переменной.  
  
 Для использования значения серверной переменной необходимо указать ссылку между проектом и серверной средой. Вы можете использовать следующие хранимые процедуры создания и удаления ссылок. Вы можете также указать, может ли среда находиться в той же папке, что и проект, или в другой папке.  
  
-   [catalog.create_environment_reference (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-create-environment-reference-ssisdb-database.md)  
  
-   [catalog.delete_environment_reference (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-delete-environment-reference-ssisdb-database.md)  
  
-   [catalog.set_environment_reference_type (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-environment-reference-type-ssisdb-database.md)  
  
 Чтобы получить дополнительные сведения о средах и переменных, выполните запрос к этим представлениям.  
  
-   [catalog.environments (база данных SSISDB)](../../integration-services/system-views/catalog-environments-ssisdb-database.md)  
  
-   [catalog.environment_variables (база данных SSISDB)](../../integration-services/system-views/catalog-environment-variables-ssisdb-database.md)  
  
-   [catalog.environment_references (база данных SSISDB)](../../integration-services/system-views/catalog-environment-references-ssisdb-database.md)  
  
##  <a name="Executions"></a> Выполнение и проверки  
 Выполнение — это экземпляр выполнения пакета. Процедуры [catalog.create_execution (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md) и [catalog.start_execution (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md) позволяют настроить и запустить выполнение пакета. Чтобы остановить выполнение или проверку пакета или проекта, вызовите [catalog.stop_operation (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database.md).  
  
 Для приостановки выполняемого пакета и создания файла дампа вызовите хранимую процедуру catalog.create_execution_dump. Файл дампа предоставляет сведения о выполнении пакета, которые могут быть полезны при диагностике неполадок в ходе выполнения. Дополнительные сведения о создании и настройке файлов дампа см. в разделе [Generating Dump Files for Package Execution](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md).  
  
 Выполняйте запросы к этим представлениям для получения сведений о выполнениях, проверках и сообщениях, регистрируемых в ходе операций, а также контекстных сведений, связанных с ошибками.  
  
-   [catalog.executions (база данных SSISDB)](../../integration-services/system-views/catalog-executions-ssisdb-database.md)  
  
-   [catalog.operations (база данных SSISDB)](../../integration-services/system-views/catalog-operations-ssisdb-database.md)  
  
-   [catalog.operation_messages (база данных SSISDB)](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md)  
  
-   [catalog.extended_operation_info (база данных SSISDB)](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md)  
  
-   [catalog.event_messages](../../integration-services/system-views/catalog-event-messages.md)  
  
-   [catalog.event_message_context](../../integration-services/system-views/catalog-event-message-context.md)  
  
 Для проверки проектов и пакетов можно вызвать хранимые процедуры [catalog.validate_project (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-validate-project-ssisdb-database.md) и [catalog.validate_package (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-validate-package-ssisdb-database.md). Представление [catalog.validations (база данных SSISDB)](../../integration-services/system-views/catalog-validations-ssisdb-database.md) содержит сведения о таких проверках, как ссылки серверной среды, учитываемые при проверке, имеет ли место проверка зависимостей или полная проверка и используется ли при запуске пакета 32-разрядная или 64-разрядная среда выполнения.  

## <a name="create-the-ssis-catalog"></a>Создание каталога служб SSIS
  После разработки и тестирования пакетов в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]можно выполнить развертывание проектов, содержащих пакеты, на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Прежде чем развертывать проекты на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , необходимо создать каталог **SSISDB** на этом сервере. Программа установки [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] не создает этот каталог автоматически. Его необходимо создать вручную, следуя приведенным ниже инструкциям.  
  
 Вы можете создать каталог SSISDB в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Можно также создать каталог программным способом с помощью Windows PowerShell.  
  
### <a name="to-create-the-ssisdb-catalog-in-sql-server-management-studio"></a>Создание каталога SSISDB в SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
2.  Соединитесь с ядром СУБД [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
3.  В обозревателе объектов разверните узел сервера, щелкните правой кнопкой мыши узел **Каталоги служб Integration Services** и выберите пункт **Создать каталог**.  
  
4.  Установите флажок **Включить интеграцию со средой CLR**.  
  
     Каталог использует хранимые процедуры CLR.  
  
5.  Щелкните **Включить автоматическое выполнение хранимой процедуры служб Integration Services при запуске SQL Server** , чтобы хранимая процедура [catalog.startup](../../integration-services/system-stored-procedures/catalog-startup.md) выполнялась каждый раз при перезапуске экземпляра сервера служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
     Хранимая процедура осуществляет обслуживание состояния операций для каталога SSISDB. Она исправляет состояние любых пакетов, выполнявшихся в момент отключения экземпляра сервера служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
6.  Введите пароль и нажмите кнопку **ОК**.  
  
     Этот пароль защищает главный ключ базы данных, используемый для шифрования данных каталога. Сохраните пароль в надежном месте. Рекомендуется также создать резервную копию главного ключа базы данных. Дополнительные сведения см. в статье [Back Up a Database Master Key](../../relational-databases/security/encryption/back-up-a-database-master-key.md).  
  
### <a name="to-create-the-ssisdb-catalog-programmatically"></a>Создание каталога SSISDB программным способом  
  
1.  Выполните следующий скрипт PowerShell.  
  
    ```  
    # Load the IntegrationServices Assembly  
    [Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices")  
  
    # Store the IntegrationServices Assembly namespace to avoid typing it every time  
    $ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"  
  
    Write-Host "Connecting to server ..."  
  
    # Create a connection to the server  
    $sqlConnectionString = "Data Source=localhost;Initial Catalog=master;Integrated Security=SSPI;"  
    $sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString  
  
    # Create the Integration Services object  
    $integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection  
  
    # Provision a new SSIS Catalog  
    $catalog = New-Object $ISNamespace".Catalog" ($integrationServices, "SSISDB", "P@assword1")  
    $catalog.Create()  
  
    ```  
  
     Дополнительные примеры использования Windows PowerShell и <xref:Microsoft.SqlServer.Management.IntegrationServices> пространства имен, см. в записи блога [SSIS и PowerShell в SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=242539), на сайте blogs.msdn.com. Общие сведения о пространстве имен и примеры кода см. в записи блога [Обзор модели управляемых объектов каталога служб SSIS](http://go.microsoft.com/fwlink/?LinkId=254267)на сайте blogs.msdn.com.  

## <a name="catalog-properties-dialog-box"></a>Диалоговое окно свойств каталога
  Диалоговое окно свойств каталога служит для настройки каталога SSISDB. Свойства каталога определяют методы шифрования конфиденциальных данных, параметры хранения данных о версиях операций и проектов, а также время ожидания операций проверки. Каталог служб SSISDB представляет собой центральную точку хранения и администрирования проектов, пакетов, параметров и сред служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Свойства каталога можно также просмотреть в представлении catalog.catalog_property и задать эти свойства с помощью хранимой процедуры catalog.configure_catalog. Дополнительные сведения см. в разделах [catalog.catalog_properties (база данных SSISDB)](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) и [catalog.configure_catalog (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md).  
  
 **Выбор действия**  
  
-   [Открытие диалогового окна свойств каталога](#open_dialog)  
  
-   [Настройка параметров](#options)  
  
###  <a name="open_dialog"></a> Открытие диалогового окна свойств каталога  
  
1.  Откройте среду [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Создайте соединение с компонентом Microsoft SQL Server Database Engine.  
  
3.  В обозревателе объектов разверните узел **Службы Integration Services** , щелкните правой кнопкой мыши элемент **SSISDB**и выберите пункт **Свойства**.  
  
###  <a name="options"></a> Настройка параметров  
  
#### <a name="options"></a>Параметры  
 В следующей таблице описаны некоторые свойства, определенные в диалоговом окне, а также соответствующие свойства в представлении catalog.catalog_property.  
  
|Имя свойства (диалоговое окно свойств каталога)|Имя свойства (представление catalog.catalog_property)|Description|  
|-----------------------------------------------------|------------------------------------------------------|-----------------|  
|Имя алгоритма шифрования|ENCRYPTION_CLEANUP_ENABLED|Указывает тип шифрования, который используется при шифровании значений конфиденциальных параметров каталога. Допустимы следующие значения:<br /><br /> DES<br /><br /> TRIPLE_DES<br /><br /> TRIPLE_DES_3KEY<br /><br /> DESPX<br /><br /> AES_128<br /><br /> AES_192<br /><br /> AES_256 (по умолчанию)|  
|Время ожидания проверки (в секундах)|VALIDATION_TIMEOUT|Задайте максимальное время в секундах, в течение которого может выполняться операция проверки проекта или пакета до того, как будет остановлена. Значение по умолчанию — 300 секунд.<br /><br /> Выполнение проверки является асинхронной операцией. Чем больше проект или пакет, тем больше времени необходимо для проверки.<br /><br /> Дополнительные сведения о проверке проектов и пакетов см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).|  
|Периодическая очистка журналов|OPERATION_CLEANUP_ENABLED|Установите это свойство в значение True, чтобы указать, что задание агента SQL Server по очистке операций выполняется. В противном случае установите свойство в значение False.|  
|Срок хранения (в днях)|RETENTION_WINDOW|Задайте максимальный срок хранения данных о допустимых операциях (в днях). Данные, которые хранятся дольше указанного числа дней, удаляются заданием агента SQL Server по очистке операций.|  
|Максимальное количество версий в проекте|MAX_PROJECT_VERSIONS|Укажите, сколько версий проекта будет храниться в каталоге. Когда общее количество версий превышает максимальное значение, более ранние версии проектов удаляются при выполнении задания по очистке версий проекта.|  

## <a name="back-up-restore-and-move-the-ssis-catalog"></a>Резервное копирование, восстановление и перемещение каталога служб SSIS
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]включает в себя базу данных SSISDB. Создайте запрос представления в базе данных SSISDB для просмотра объектов, настроек и рабочих данных, которые хранятся в каталоге **SSISDB** . Этот раздел содержит инструкции для выполнения резервного копирования и восстановления базы данных.  
  
 В каталоге **SSISDB** хранятся пакеты, которые развернуты на сервере службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Дополнительные сведения о каталоге см. в разделе [Каталог служб SSIS](../../integration-services/service/ssis-catalog.md).  
  
###  <a name="backup"></a> Создание резервной копии базы данных служб SSIS  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Создайте резервную копию главного ключа для базы данных SSISDB с помощью инструкции BACKUP MASTER KEY Transact-SQL. Ключ хранится в указанном файле. Используйте пароль для шифрования главного ключа базы данных в файле.  
  
     Дополнительные сведения об инструкции см. в разделе [BACKUP MASTER KEY (Transact-SQL)](../../t-sql/statements/backup-master-key-transact-sql.md).  
  
     В следующем примере главный ключ экспортируется в файл `c:\temp directory\RCTestInstKey` . Пароль `LS2Setup!` используется для шифрования главного ключа.  
  
    ```  
    backup master key to file = 'c:\temp\RCTestInstKey'  
           encryption by password = 'LS2Setup!'  
  
    ```  
  
3.  Выполните резервное копирование базы данных SSISDB с помощью диалогового окна **Создание резервной копии базы данных** в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Как создать резервную копию базы данных (среда SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=231812).  
  
4.  Создайте скрипт CREATE LOGIN для ## MS_SSISServerCleanupJobLogin ##, выполнив следующие действия. Дополнительные сведения см. в разделе [CREATE LOGIN (Transact-SQL)](../../t-sql/statements/create-login-transact-sql.md).  
  
    1.  В обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]разверните узел **Безопасность** , а затем узел **Имена входа** .  
  
    2.  Щелкните правой кнопкой мыши **##MS_SSISServerCleanupJobLogin##**и выберите **Внести в скрипт имена входа как** > **СОЗДАТЬ в** > **В новом окне редактора запросов**.  
  
5.  Если планируется восстановление базы данных SSISDB из копии на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], где каталог SSISDB еще не создан, создайте скрипт CREATE PROCEDURE для sp_ssis_startup следующим образом. Дополнительные сведения см. в статье [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md).  
  
    1.  В обозревателе объектов разверните узел **Базы данных**, а затем узел **master** > **Программирование** > **Хранимые процедуры**.  
  
    2.  Щелкните правой кнопкой мыши **dbo.sp_ssis_startup**и выберите **Внести в скрипт хранимые процедуры как** > **СОЗДАТЬ в** > **В новом окне редактора запросов**.  
  
6.  Убедитесь, что агент SQL Server запущен.  
  
7.  Если планируется восстановление базы данных SSISDB из копии на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , где каталог SSISDB еще не создан, создайте скрипт для задания обслуживания сервера SSIS следующим образом. Скрипт создается в агенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически при создании каталога SSISDB. Задание помогает очистить журналы операции с вышедшим сроком сохранения и удалить старые версии проектов.  
  
    1.  В обозревателе объектов разверните узел **Агент SQL Server** , а затем узел **Задания** .  
  
    2.  Щелкните правой кнопкой мыши задание по обслуживанию служб SSIS и выберите **Внести в скрипт задание как** > **СОЗДАТЬ в** > **В новом окне редактора запросов**.  
  
### <a name="to-restore-the-ssis-database"></a>Восстановление базы данных служб SSIS  
  
1.  Если база данных SSISDB восстанавливается из копии в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], где каталог SSISDB никогда не создавался, включите среду CLR с помощью хранимой процедуры sp_configure. Дополнительные сведения см. в разделах [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) и [Параметр clr enabled](http://go.microsoft.com/fwlink/?LinkId=231855).  
  
    ```  
    use master   
           sp_configure 'clr enabled', 1  
           reconfigure  
  
    ```  
  
2.  Если база данных SSISDB восстанавливается из копии на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , где каталог SSISDB никогда не создавался, создайте асимметричный ключ и имя входа из асимметричного ключа и предоставьте разрешение UNSAFE для имени входа.  
  
    ```  
    Create Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey  
           FROM Executable File = 'C:\Program Files\Microsoft SQL Server\110\DTS\Binn\Microsoft.SqlServer.IntegrationServices.Server.dll'  
  
    ```  
  
     Хранимые процедуры CLR [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] требуют предоставления разрешения UNSAFE для имени входа, поскольку имени входа необходим дополнительный доступ к ресурсам, на которые существуют ограничения, например API-интерфейс Microsoft Win32. Дополнительные сведения о коде разрешения UNSAFE см. в разделе [Creating an Assembly](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md).  
  
    ```  
    Create Login MS_SQLEnableSystemAssemblyLoadingUser  
           FROM Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey   
  
           Grant unsafe Assembly to MS_SQLEnableSystemAssemblyLoadingUser  
  
    ```  
  
3.  Восстановите базу данных SSISDB из резервной копии с помощью диалогового окна **Восстановление базы данных** в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в следующих разделах:  
  
    -   [Восстановление базы данных (страница "Общие")](../../relational-databases/backup-restore/restore-database-general-page.md)  
  
    -   [Восстановление базы данных (страница "Файлы")](../../relational-databases/backup-restore/restore-database-files-page.md)  
  
    -   [Восстановление базы данных (страница "Параметры")](../../relational-databases/backup-restore/restore-database-options-page.md)  
  
4.  Выполните скрипт, созданный в разделе [Создание резервной копии базы данных служб SSIS](#backup) для ##MS_SSISServerCleanupJobLogin##, sp_ssis_startup и заданий по обслуживанию служб SSIS. Убедитесь, что агент SQL Server запущен.  
  
5.  Выполните следующую инструкцию для установки автоматического выполнения процедуры sp_ssis_startup. Дополнительные сведения см. в разделе [sp_procoption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-procoption-transact-sql.md).  
  
    ```  
    EXEC sp_procoption N'sp_ssis_startup','startup','on'  
    ```  
  
6.  Сопоставьте пользователя SSISDB ##MS_SSISServerCleanupJobUser## (база данных SSISDB) с ##MS_SSISServerCleanupJobLogin## с помощью диалогового окна **Свойства имени входа** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
7.  Восстановите главный ключ с помощью одного из следующих методов. Дополнительные сведения о шифровании см. в разделе [Encryption Hierarchy](../../relational-databases/security/encryption/encryption-hierarchy.md).  
  
    -   **Метод 1**  
  
         Используйте этот метод при наличии резервной копии главного ключа базы данных и пароля, используемого для шифрования этого ключа.  
  
        ```  
               Restore master key from file = 'c:\temp\RCTestInstKey'  
               Decryption by password = 'LS2Setup!' -- 'Password used to encrypt the master key during SSISDB backup'  
               Encryption by password = 'LS3Setup!' -- 'New Password'  
               Force  
  
        ```  
  
        > [!NOTE]  
        >  Убедитесь, что учетная запись службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет разрешения на чтение файла резервной копии ключа.  
  
        > [!NOTE]  
        >  Если главный ключ базы данных еще не зашифрован главным ключом сервера, то в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] отобразится следующее предупреждающее сообщение. Пропустите это предупреждающее сообщение.  
        >   
        >  **Не удается расшифровать текущий главный ключ. Ошибка пропущена, так как был указан параметр FORCE.**  
        >   
        >  Аргумент FORCE указывает, что следует продолжить процесс восстановления, даже если текущий главный ключ базы данных закрыт. Для каталога SSISDB это сообщение будет отображаться, поскольку главный ключ базы данных не является открытым в экземпляре, где осуществляется восстановление базы данных.  
  
    -   **Метод 2.**  
  
         Этот метод следует использовать при наличии исходного пароля, который использовался для создания SSISDB.  
  
        ```  
        open master key decryption by password = 'LS1Setup!' --'Password used when creating SSISDB'  
               Alter Master Key Add encryption by Service Master Key  
        ```  
  
8.  Определите, совместимы ли схема каталога SSISDB и двоичные файлы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (сборка ISServerExec и SQLCLR), запустив [catalog.check_schema_version](../../integration-services/system-stored-procedures/catalog-check-schema-version.md).  
  
9. Для подтверждения того, что база данных SSISDB успешно восстановлена, выполните такие операции с каталогом SSISDB, как запуск пакетов, развернутых на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Дополнительные сведения см. в разделе [пакетов выполнения Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md).  
  
### <a name="to-move-the-ssis-database"></a>Перемещение базы данных служб SSIS  
  
-   Следуйте инструкциям по перемещению пользовательских баз данных. Дополнительные сведения см. в статье [Move User Databases](../../relational-databases/databases/move-user-databases.md).  
  
     Обязательно создайте резервную копию главного ключа базы данных SSISDB и защитите файл резервной копии. Дополнительные сведения см. в статье [Создание резервной копии каталога SSISDB](#backup).  
  
     Убедитесь, что соответствующие объекты служб Integration Services (SSIS) созданы в новом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , где каталог SSISDB еще не был создан.  

## <a name="upgrade-the-ssis-catalog-ssisdb"></a>Обновление каталога служб SSIS (SSISDB)
  Используйте мастер обновления SSISDB, чтобы обновить базу данных для каталога служб SSIS (SSISDB), если эта база данных старше текущей версии экземпляра SQL Server. Это случается, если верно любое из следующих условий:  
  
-   База данных восстановлена из более старой версии SQL Server.  
  
-   База данных не была удалена из группы доступности AlwaysOn перед обновлением экземпляра SQL Server. Это препятствует автоматическому обновлению базы данных. Дополнительные сведения см. в разделе [Upgrading SSISDB in an availability group](#Upgrade).  
  
 Мастер может обновить только базу данных на экземпляре локального сервера.  
  
### <a name="upgrade-the-ssis-catalog-ssisdb-by-running-the-ssisdb-upgrade-wizard"></a>Обновление каталога служб SSIS (SSISDB) посредством запуска мастера обновления SSISDB  
  
1.  Выполните архивацию базы данных каталога служб SSIS (SSISDB).  
  
2.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]разверните локальный сервер, а затем — **Каталоги служб Integration Services**.  
  
3.  Щелкните правой кнопкой мыши **SSISDB**, а затем выберите **Обновление базы данных** , чтобы запустить мастер обновления SSISDB.  
  
     ![Запустите мастер обновления SSISDB](../../integration-services/service/media/ssisdb-upgrade-wizard-1.png "запуска мастера обновления SSISDB")  
  
4.  На странице **Выбор экземпляра** выберите экземпляр SQL Server на локальном сервере.  
  
    > [!IMPORTANT]  
    >  Мастер может обновить только базу данных на экземпляре локального сервера.  
  
     Установите флажок, чтобы указать, что вы выполнили архивацию базы данных SSISDB перед запуском мастера.  
  
     ![Выберите сервер в мастере обновления SSISDB](../../integration-services/service/media/ssisdb-upgrade-wizard-2.png "выберите сервер в мастере обновления SSISDB")  
  
5.  Выберите **Обновить** , чтобы обновить базу данных каталога служб SSIS.  
  
6.  Просмотрите результаты на странице **Результаты** .  
  
     ![Просмотрите результаты в мастере обновления SSISDB](../../integration-services/service/media/ssisdb-upgrade-wizard-3.png "просмотрите результаты в мастере обновления SSISDB")  

## <a name="always-on-for-ssis-catalog-ssisdb"></a>Always On для каталога служб SSIS (SSISDB)
  Группы доступности AlwaysOn — это решение для высокой доступности и аварийного восстановления, являющееся альтернативой зеркальному отображению баз данных на уровне предприятия. Группа доступности поддерживает среду отработки отказа для дискретного набора пользовательских баз данных, известных как базы данных доступности, которые совместно выполняют переход на другой ресурс. Дополнительные сведения см. в разделе [Группы доступности AlwaysOn](https://msdn.microsoft.com/library/hh510230.aspx).  
  
 Для обеспечения высокого уровня доступности для каталога служб SSIS (SSISDB) и его содержимого (проектов, пакетов, журналов выполнения и т. д.) можно добавить базу данных SSISDB (практически так же, как и любую другую базу данных) в группу доступности AlwaysOn. В случае сбоя один из вторичных узлов автоматически становится новым основным узлом.  
 
 > [!IMPORTANT]
 > В случае сбоя выполнявшиеся пакеты не перезапускаются и не возобновляются. 
 
 **В этом разделе:**  
  
1.  [Предварительные требования](#prereq)  
  
2.  [Настройка поддержки служб SSIS для AlwaysOn](#Firsttime)  
  
3.  [Обновление SSISDB в группе доступности](#Upgrade)  
  
###  <a name="prereq"></a> Предварительные требования  
 Перед включением поддержки AlwaysOn для базы данных SSISDB необходимо выполнить указанные далее предварительные действия.  
  
1.  Настроить отказоустойчивый кластер Windows. Инструкции см. в записи блога [Установка компонентов и средств отказоустойчивого кластера для Windows Server 2012)](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) (Installing the Failover Cluster Feature and Tools for Windows Server 2012). Компоненты и средства необходимо установить на всех узлах кластера.  
  
2.  Установить SQL Server 2016 с компонентом Integration Services (SSIS) на каждом узле кластера.  
  
3.  Включение групп доступности AlwaysOn для каждого экземпляра SQL Server. Более подробные сведения см. в разделе [Включение групп доступности AlwaysOn](https://msdn.microsoft.com/library/ff878259.aspx) .  
  
###  <a name="Firsttime"></a> Настройка поддержки служб SSIS для AlwaysOn  
  
-   [Шаг 1. Создание каталога служб Integration Services](#Step1)  
  
-   [Шаг 2. Добавление SSISDB в группу доступности AlwaysOn](#Step2)  
  
-   [Шаг 3. Включение поддержки служб SSIS для AlwaysOn](#Step3)  
  
> [!IMPORTANT]  
> -   Эти действия необходимо выполнить на **основном узле** группы доступности.
> -   Необходимо включить **поддержку SSIS для AlwaysOn** *после* добавления SSISDB в группы доступности AlwaysOn.  
  
####  <a name="Step1"></a> Шаг 1. Создание каталога служб Integration Services  
  
1.  Запустите **SQL Server Management Studio** и подключитесь к экземпляру SQL Server в кластере, который нужно задать в качестве **основного узла** группы высокой доступности AlwaysOn для SSISDB.  
  
2.  В обозревателе объектов разверните узел сервера, щелкните правой кнопкой мыши узел **Каталоги служб Integration Services** и выберите пункт **Создать каталог**.  
  
3.  Установите флажок **Включить интеграцию со средой CLR**. Каталог использует хранимые процедуры CLR.  
  
4.  Щелкните **Включить автоматическое выполнение хранимой процедуры служб Integration Services при запуске SQL Server** , чтобы хранимая процедура [catalog.startup](https://msdn.microsoft.com/library/hh230984.aspx) выполнялась каждый раз при перезапуске экземпляра сервера служб SSIS. Хранимая процедура осуществляет обслуживание состояния операций для каталога SSISDB. Она исправляет состояние любых пакетов, выполнявшихся в момент отключения экземпляра сервера служб SSIS.  
  
5.  Введите **пароль**и нажмите кнопку **ОК**. Этот пароль защищает главный ключ базы данных, используемый для шифрования данных каталога. Сохраните пароль в надежном месте. Рекомендуется также создать резервную копию главного ключа базы данных. Дополнительные сведения см. в статье [Back Up a Database Master Key](https://msdn.microsoft.com/library/aa337546.aspx).  
  
####  <a name="Step2"></a> Шаг 2. Добавление SSISDB в группу доступности AlwaysOn  
 Процедура добавления базы данных SSISDB в группу доступности AlwaysOn практически не отличается от добавления другой базы данных пользователей в группу доступности. См. раздел [Использование мастера групп доступности](https://msdn.microsoft.com/library/hh403415.aspx).  
  
 Необходимо ввести пароль, указанный при создании каталога служб SSIS на странице **Выбор баз данных** мастера **создания групп доступности** .  
  
 ![создания групп доступности](../../integration-services/service/media/ssis-newavailabilitygroup.png "создания групп доступности")  
  
####  <a name="Step3"></a> Шаг 3. Включение поддержки служб SSIS для AlwaysOn  
 После создания каталога служб Integration Service щелкните правой кнопкой мыши узел **Каталоги служб Integration Service** и выберите команду **Включить поддержку AlwaysOn**. Вы должны увидеть следующие диалоговое окно **Включение поддержки AlwaysOn** . Если этот пункт меню неактивен, убедитесь, что установлены все необходимые компоненты, и нажмите кнопку **Обновить**.  
  
 ![Включите поддержку для всегда на](../../integration-services/service/media/ssis-enablesupportforalwayson.png)  
  
> [!WARNING]  
>  Автоматическая отработка отказа базы данных SSISDB поддерживается только после включения поддержки служб SSIS для AlwaysOn.  
  
 В таблице отображается вторичной реплики, добавленные из группы доступности Always On. Установите флажок **Подключить** для каждой реплики в списке и введите учетные данные для подключения к реплике. Учетная запись пользователя должна быть членом группы sysadmin на каждой реплике для включения поддержки служб SSIS для AlwaysOn. После успешного подключения к каждой реплике нажмите кнопку **ОК** , чтобы включить поддержку служб SSIS для AlwaysOn.  
 
Если **включить поддержка AlwaysOn** параметр в контекстном меню появляется отключается после завершения других условиях, попробуйте выполнить следующие действия:
1.  Обновить в контекстном меню, нажав **обновление** параметр.
2.  Убедитесь, что вы подключаетесь к основным узлом. Необходимо включить поддержку Always On на основном узле.
3.  Убедитесь, что версия SQL Server 13.0 или более поздней версии. Службы SSIS поддерживают Always On только на SQL Server 2016 и более поздних версиях.

###  <a name="Upgrade"></a> Обновление SSISDB в группе доступности  
 Если вы обновляете SQL Server с предыдущей версии и SSISDB находится в группе доступности AlwaysOn, обновление может блокироваться правилом "Проверка SSISDB в группе доступности AlwaysOn". Эта блокировка связана с тем, что обновление выполняется в однопользовательском режиме, а база данных доступности должна быть многопользовательской. Таким образом, во время обновления или применения исправлений все базы данных доступности, включая SSISDB, переводятся в автономный режим и не обновляются или исправляются. Чтобы продолжить обновление, необходимо сначала удалить SSISDB из группы доступности, затем обновить каждый узел или применить к нему исправление, а после этого добавить SSISDB обратно в группу доступности.  
  
 Если обновление заблокировано правилом "Проверка SSISDB в группе доступности AlwaysOn", нужно выполнить следующие действия, чтобы обновить SQL Server.  
  
1.  Удалите базу данных SSISDB из группы доступности. Дополнительные сведения см. в разделах [Удаление базы данных-получателя из группы доступности (SQL Server)](../../database-engine/availability-groups/windows/remove-a-secondary-database-from-an-availability-group-sql-server.md) и [Удаление базы данных-источника из группы доступности (SQL Server)](../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md).  
  
2.  В мастере обновления щелкните **Выполнить повторно**. Правило "Проверка SSISDB в группе доступности AlwaysOn" будет соблюдено.  
  
3.  Нажмите кнопку **Далее** , чтобы продолжить обновление.  
  
4.  После обновления всех узлов добавьте базу данных SSISDB обратно в группу доступности AlwaysOn. Дополнительные сведения см. в разделе [Добавление базы данных в группу доступности (SQL Server)](../../database-engine/availability-groups/windows/availability-group-add-a-database.md).  
  
 Если при обновлении SQL Server блокировка применена не была и SSISDB находится в группе доступности AlwaysOn, необходимо отдельно обновить SSISDB после обновления компонента SQL Server Database Engine. Используйте мастер обновления служб SSIS для обновления SSISDB, как описано в следующей процедуре.  
  
1.  Переместите базу данных SSISDB из группы доступности или удалите группу доступности, если SSISDB является единственной базой данных в группе доступности. Для выполнения этой задачи необходимо запустить **SQL Server Management Studio** на **основном узле** группы доступности.  
  
2.  Удалите базу данных SSISDB со всех **узлов реплики**.  
  
3.  Обновите базу данных SSISDB на **основном узле**. В**обозревателе объектов** в SQL Server Management Studio разверните **Каталоги служб Integration Services**, щелкните правой кнопкой мыши **SSISDB**, а затем выберите команду **Обновить базу данных**. Следуйте инструкциям в **мастере обновления SSISDB** по обновлению базы данных. **Мастер обновления SSIDB** необходимо запустить локально на **основном узле**.  
  
4.  Следуйте инструкциям по добавлению SSISDB обратно в группу доступности, приведенным в пункте [Шаг 2. Добавление SSISDB в группу доступности AlwaysOn](#Step2) .  
  
5.  Следуйте инструкциям в пункте [Шаг 3. Включение поддержки служб SSIS для AlwaysOn](#Step3).  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   Запись в блоге [Службы SSIS и Powershell в SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=242539)на сайте blogs.msdn.com.  
  
-   Запись в блоге [Советы по управлению доступом к каталогу служб SSIS](http://go.microsoft.com/fwlink/?LinkId=246669)на сайте blogs.msdn.com.  
  
-   Запись [Обзор модели управляемых объектов каталога служб SSIS](http://go.microsoft.com/fwlink/?LinkId=254267)в блоге blogs.msdn.com.  
