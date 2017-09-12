---
title: "Управление источниками данных отчета | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reports [Reporting Services], data
- published reports [Reporting Services], data source connections
- shared data sources [Reporting Services]
- data sources [Reporting Services], managing
ms.assetid: 0475aded-c8fe-4337-a2b5-4df0ec4c46af
caps.latest.revision: 52
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9791cd34a321173e30bf2016956f02e54e62112c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="manage-report-data-sources"></a>Управление источниками данных отчета
  В службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] отчеты, модели отчетов и управляемые данными подписки получают данные из внешних источников данных. Чтобы подключиться к внешнему источнику данных, сервер отчетов использует сведения соединения с источником данных, которые определены в отчете, модели или подписке или на которые они ссылаются. Свойства соединения с источником данных всегда определяются при создании отчета или модели, но управление ими может выполняться отдельно после публикации отчета или модели на сервере отчетов.  
  
 Управление источниками данных отчета производится при помощи диспетчера отчетов для сервера отчетов, работающего в собственном режиме, либо страницы приложения на сайте SharePoint, если сервер отчетов развернут в режиме интеграции с SharePoint.  
  
 Управление соединениями с источниками данных связано с выполнением следующих задач, описываемых в этом разделе.  
  
-   Изменение строк соединений.  
  
-   Изменение учетных данных.  
  
-   Создание и использование общих источников данных на сервере отчетов, в том числе переключение внедренного источника данных для общего источника данных.  
  
-   Управление доступом к свойствам источников данных заданием разрешений для отчета, модели или используемых общих источников данных.  
  
 Обратите внимание, что изменение запросов в задачи управления соединениями с источниками данных не входит. Изменение запроса для отчета или модели необходимо производить при помощи средств разработки, а затем вносить изменения в определение отчета или модели.  
  
## <a name="managed-properties-data-source-type-connection-strings-and-credentials"></a>Управляемые свойства: тип источника данных, строки подключения и учетные данные  
 Свойства источника данных, доступные для управления на сервере отчетов:  
  
|Свойство|Description|Способ управления свойством|  
|--------------|-----------------|----------------------|  
|Тип источника данных|Определяет, какие модули обработки данных сервера отчетов должны использоваться для внешних данных. В качестве примеров процессоров данных могут быть указаны SQL Server, службы Analysis Services или база данных Oracle.|Тип источника данных является управляемым свойством, поскольку оно может быть настроено. Однако настраивать тип источника данных следует только при создании нового общего источника данных.<br /><br /> Изменять тип источника данных на страницах свойств опубликованного отчета или опубликованной модели не следует, так как это почти наверняка нарушит работоспособность соединения. Маловероятно, что на новой платформе данных структуры данных, необходимые отчету или модели, совпадут со старыми.|  
|Строка соединения|Устанавливает начальное соединение с внешним источником данных. Отчет может использовать статические или динамические строки соединения.<br /><br /> *Статическая строка соединения* представляет собой набор значений, которые отчет всегда использует для соединения с одним и тем же источником данных при каждом запуске отчета.<br /><br /> *Динамическая строка соединения* представляет собой выражение, встроенное в отчет, которое дает пользователю возможность выбрать источник данных, который следует использовать во время выполнения. Выражение и список выбора источников данных встраиваются в отчет во время его создания в конструкторе отчетов.|Изменение строки соединения может оказаться полезным при переносе источника данных на другой компьютер либо если отчет создается с использованием тестовых данных, но затем отчеты должны развертываться при помощи производственной базы данных.<br /><br /> Управление статическими строками соединения производится только путем их замены.<br /><br /> Возможности управления динамическими строками соединения в диспетчере отчетов или на сайте SharePoint ограничены заменой этой строки на статическую. Нельзя изменять ни само выражение, ни список выбора источников данных. Чтобы изменить выражение или список допустимых значений, необходимо изменить определение отчета и повторно опубликовать отчет на сервере отчетов. Дополнительные сведения см. в разделе [Подключения к данным, источники данных и строки подключения (построитель отчетов и службы SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).|  
|Учетные данные|Предоставляют имя и пароль пользователя, имеющего разрешение на чтение данных из источника данных.<br /><br /> Если источник данных не поддерживает проверку подлинности (например, если источником данных является XML-файл или файловая система), то можно настроить учетную запись автоматического выполнения, чтобы сервер отчетов мог соединиться с источником внешних данных без передачи учетных данных.|Управление учетными данными позволяет обновить учетную запись или пароль пользователя при истечении срока его действия.<br /><br /> Можно также изменить способ получения учетных данных (например, предложив пользователю ввести учетные данные во время выполнения).<br /><br /> Если необходимо предоставить пользователям возможность подписки на отчет, то необходимо настроить отчет на использование сохраненных учетных данных.|  
  
## <a name="creating-and-using-shared-data-sources"></a>Создание и использование общих источников данных  
 Если публикация отчета производится с внедренными свойствами источника данных, необходимо рассмотреть вопрос перехода на свойства общего источника данных. Общими источниками данных легче управлять, поскольку они позволяют обновлять учетные данные и строки соединения на одной странице. Изменения мгновенно отразятся на всех отчетах, моделях и управляемых данных подписки, использующих этот источник данных. Работать с общим источником данных можно также в режиме «вне сети», эффективно приостановив отчет или подписку, чтобы предотвратить их выполнение во время устранения неполадок или исследования возникших проблем.  
  
## <a name="controlling-access-data-source-properties"></a>Управление доступом к свойствам источника данных  
 По умолчанию любой пользователь, имеющий разрешения на управление отчетами, может задавать для отчета любые свойства, в том числе определяющие тип источника данных, строку соединения, учетные данные, а также получение отчетом сведений о соединении из внедренного или общего источника данных. Дополнительные сведения о том, какие задачи и разрешения управляют доступом к свойствам источников данных на сервере отчетов, работающем в собственном режиме, см. в разделах [Защита элементов общего набора данных](../../reporting-services/security/secure-shared-data-source-items.md) и [Защищенные отчеты и ресурсы](../../reporting-services/security/secure-reports-and-resources.md).  
  
 Разрешения на просмотр и изменение свойств элементов в библиотеке SharePoint определяются администратором сайта. Дополнительные сведения о том, какие разрешения управляют доступом к свойствам подключения к источнику данных, см. в разделе [Справочная таблица по разрешениям на сайты SharePoint и списки для элементов сервера отчетов](../../reporting-services/security/sharepoint-site-and-list-permission-reference-for-report-server-items.md).  
  
## <a name="how-to-work-with-data-source-properties-on-a-report-server"></a>Работа со свойствами источника данных на сервере отчетов  
 Создание и изменение свойств источника данных может быть выполнено различными средствами. В следующей таблице приведено краткое описание подходов и средств со ссылками на дополнительные инструкции.  
  
|Задача|Инструмент|Ссылка|  
|----------|----------|----------|  
|Просмотр примеров строк соединения.||[Подключения к данным, источники данных и строки подключения (построитель отчетов и службы SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)|  
|Выбор подхода для получения учетных данных для соединения с источником данных.||[Укажите учетные данные и сведения о соединении для источников данных отчета](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)|  
|Добавление свойств соединения с источником данных в файл определения отчета (RDL).|конструктор отчетов|[Создать внедренный или общий источник данных &#40; Службы SSRS &#41;](http://msdn.microsoft.com/library/b111a8d0-a60d-4c8b-b00a-51644b19c34b)|  
|Добавление и создание ссылки на файл общего источника данных (RDS) в проекте отчета.|конструктор отчетов|[Создание, изменение и удаление общих источников данных &#40; Службы SSRS &#41;](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)|  
|Создание стандартного списка, из которого пользователь выбирает источник данных во время выполнения. Когда пользователь запрашивает отчет, то список источников данных берется из отчета. Пользователь должен выбрать источник данных, который следует использовать при выполнении отчета. Для добавления в отчет списка выбора источников данных используется выражение.<br /><br /> Это называется динамическим соединением с источником данных.|конструктор отчетов|[Подключения к данным, источники данных и строки подключения (построитель отчетов и службы SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)|  
|Создание на сервере отчетов совместно используемого элемента источника данных.|Диспетчер отчетов|[Создать, удалить или изменить общий источник данных &#40; Диспетчер отчетов &#41;](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)|  
|Сохранение учетных данных, необходимых для создания подписок или моментальных снимков отчетов.|Диспетчер отчетов|[Хранить учетные данные в источнике данных Reporting Services](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md)|  
|Изменение свойств соединения с источником данных для опубликованного отчета.|Диспетчер отчетов|[Настройка свойств источника данных для отчета &#40; Диспетчер отчетов &#41;](../../reporting-services/report-data/configure-data-source-properties-for-a-report-report-manager.md)|  
|Создание на сервере отчетов совместно используемого элемента источника данных.|Сайт SharePoint|[Создание общих источников данных и управление ими &#40;службы Reporting Services в режиме интеграции с SharePoint&#41;](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76)|  
|Использование с отчетом существующего ODC-файла, содержащего сведения о соединении.|Сайт SharePoint|[Используйте подключения к данным Office &#40;. ODC &#41; с отчеты &#40; Службы Reporting Services в SharePoint интегрированная режим &#41;](../../reporting-services/report-data/use-an-office-data-connection-odc-with-reports.md)|  
  
> [!NOTE]  
>  Управление соединениями источников данных с источниками данных отчета отличается от управления соединением сервера отчетов с базой данных сервера отчетов. Дополнительные сведения о подключении сервера отчетов к внутреннему хранилищу данных см. в разделе [Настройка подключения к базе данных сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
## <a name="see-also"></a>См. также:  
 [Привязка отчета или модели к общему источнику данных &#40; Службы SSRS &#41;](../../reporting-services/report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md)   
 [Создать, удалить или изменить общий источник данных &#40; Диспетчер отчетов &#41;](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [Хранить учетные данные в источнике данных Reporting Services](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md)   
 [Подключения к данным, источники данных и строки подключения &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Источники данных, поддерживаемые службами Reporting Services &#40; Службы SSRS &#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)   
 [Управление содержимым сервера отчетов &#40; Собственный режим служб SSRS &#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)  
  
  