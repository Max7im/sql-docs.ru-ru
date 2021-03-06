---
title: Сравнение ролей и задач служб Reporting Services с группами и разрешениями SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- security [Reporting Services], tasks
- roles [Reporting Services], predefined
- SharePoint integration [Reporting Services], permissions
- permissions [Reporting Services], native mode
- security [Reporting Services], predefined roles
- security [Reporting Services], SharePoint integrated mode
ms.assetid: 429f1dbb-183a-4097-bd1b-693da9fe7a36
caps.latest.revision: 18
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 01e24a3aaa994a5e186634221fc4b64f396a8a2d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204904"
---
# <a name="compare-roles-and-tasks-in-reporting-services-to-sharepoint-groups-and-permissions"></a>Сравнение ролей и задач служб Reporting Services с группами и разрешениями SharePoint
  В этом разделе приводится сравнение функции авторизации на основе ролей и задач служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , работающих в собственном режиме, со средствами безопасности из продуктов SharePoint. В нем сравнивается терминология и характеристики ролей, задач, групп SharePoint, уровней разрешений и самих разрешений.  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)]<br /><br /> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint &#124; SharePoint 2010 и SharePoint 2013<br /><br /> Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в собственном режиме|  
  
 **В этом разделе:**  
  
-   [Сравнение средств и терминологии, связанных с разрешениями](#bkmk_compare_tools_terms)  
  
-   [Сравнение ролей в собственном режиме и групп SharePoint](#bkmk_compare_roles_groups)  
  
-   [Сравнение задач в собственном режиме и разрешений SharePoint](#bkmk_compare_tasks_permissions)  
  
##  <a name="bkmk_compare_tools_terms"></a> Сравнение средств и терминологии, связанных с разрешениями  
 **Основной режим.** Объекты разрешений служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в основном режиме (роли и задачи) создаются в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и настраиваются для отдельных пользователей в диспетчере отчетов.  
  
 **Режим интеграции с SharePoint:** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] режим интеграции с SharePoint использует функции разрешений SharePoint. Управление группами и разрешениями SharePoint осуществляется из следующей страницы **Параметры сайта** .  
  
 В следующей таблице сравниваются объекты и основные понятия, связанные с разрешением, между службами [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в собственном режиме и в режиме интеграции с SharePoint.  
  
|Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в собственном режиме|SharePoint|  
|---------------------------------------------|----------------|  
|**Роль.** Например, «Диспетчер содержимого».|**Группа.** Например, группа «Средства просмотра» по умолчанию.|  
|---|**Группа уровня разрешений.** Например, «Только просмотр» для группы «Средства просмотра».|  
|**Задачи.** Например, "Управление отчетами".|**Разрешения.** Например, в группе «Только просмотр» есть список разрешений, связанных с элементами представления, версиями представления и страницами представления приложения.|  
  
 Дополнительные сведения о разрешениях SharePoint см. в разделах [Уровни разрешений и разрешения](http://office.microsoft.com/windows-sharepoint-services-help/permission-levels-and-permissions-HA010100149.aspx) и [Определение уровня разрешений и групп в SharePoint 2013](http://technet.microsoft.com/library/cc262690.aspx).  
  
##  <a name="bkmk_compare_roles_groups"></a> Сравнение ролей в собственном режиме и групп SharePoint  
 В следующей таблице сравниваются стандартные определения ролей служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в собственном режиме со стандартными группами SharePoint. Если группы SharePoint не соответствуют определенной необходимой роли, можно создать пользовательскую группу и назначить для нее уровни разрешений в SharePoint.  
  
 **Примечание**. Группы по умолчанию SharePoint доступны в зависимости от шаблона сайта, который использовался при создании сайта SharePoint.  
  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Роли|Группы SharePoint|  
|--------------------------------------|-----------------------|  
|**Браузер**<br /><br /> Представление|Используйте группу **Посетители** для предоставления разрешений на просмотр отчетов. Группа **Посетители** имеет уровень разрешений «Чтение», который позволяет членам группы просматривать страницы, элементы списков и документы.|  
|**Диспетчер содержимого**<br /><br /> Полный набор разрешений на все элементы и операции на уровне элементов, включая разрешения на установку параметров безопасности|Используйте группу **Владельцы** для предоставления полного доступа к элементам сервера отчетов на сайте SharePoint. Группа **Владельцы** имеет разрешения «Полный доступ», позволяющие членам этой группы изменять содержимое, страницы и функциональность сайта. Уровень доступа «Полный доступ» должен предоставляться только администраторам сайта.|  
|**Мои отчеты**|Эквивалентной группы нет. Роль**Мои отчеты** не поддерживается на сервере отчетов, работающем в режиме интеграции с SharePoint. Если необходима эквивалентная функциональность, можно воспользоваться функциями «Мой сайт» служб [!INCLUDE[winSPServ](../includes/winspserv-md.md)] .|  
|**Издатель**<br /><br /> Добавление, обновление, просмотр и удаление отчетов, моделей отчетов, общих источников данных и ресурсов.|Используйте группу **Члены** для предоставления разрешений на добавление и изменение элементов, а также обновление ссылок на зависимые элементы на сайте SharePoint. Группа **Члены** имеет уровень разрешений «Участие», который позволяет членам группы просматривать страницы, добавлять и обновлять элементы и отправлять изменения на утверждение.|  
|**построитель отчетов**<br /><br /> Просмотр отчетов, самостоятельное управление индивидуальными подписками и открытие отчетов в построителе отчетов.|Стандартный уровень разрешений или группа SharePoint, эквивалентные определению «Построитель отчетов», отсутствуют. По умолчанию пользователи, принадлежащие к группам **Члены** или **Владельцы** , имеют разрешение на использование построителя отчетов. Если необходимо сделать построитель отчетов доступным для большего числа пользователей, необходимо создать пользовательские настройки безопасности, предоставляющие уровень разрешений, аналогичный обеспечиваемому ролью «Построитель отчетов». Дополнительные сведения см. в разделе [Установка разрешений для элементов сервера отчетов на сайте SharePoint &#40;служб Reporting Services в режиме интеграции с SharePoint&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md).|  
|-|Используйте группу **Наблюдатели** для предоставления разрешений на просмотр отчетов, готовых для просмотра. Группа **Наблюдатели** не может загружать или просматривать содержимое элементов отчетов.<br /><br /> **Примечание:** начиная с SQL Server 2012 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], **средств просмотра** группа не имеет разрешений для создания подписок.|  
|**Системный пользователь** и **Системный администратор**|Эти роли не обязательны для сервера отчетов, работающего в режиме интеграции с SharePoint. Роли**Системный пользователь** и **Системный администратор** соответствуют уровню разрешений фермы SharePoint или веб-приложения. Сервер отчетов не предоставляет никакой функциональности, требующей авторизации на этом уровне.|  
  
##  <a name="bkmk_compare_tasks_permissions"></a> Сравнение задач в собственном режиме и разрешений SharePoint  
 В следующей таблице приведено сравнение задач служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в собственном режиме и разрешений SharePoint. В столбце **Тип** указано, связана ли задача, выполняющаяся в собственном режиме, с системной ролью или стандартной ролью и элементами. Системные роли управляют разрешениями на уровне системы, например на общие расписания.  
  
|Задачи в собственном режиме|Тип роли|Эквивалентное разрешение SharePoint|  
|----------------------|---------------|--------------------------------------|  
|Использование отчетов|Элемент|Изменение элементов, просмотр элементов.|  
|Создание связанных отчетов|Элемент|Не поддерживается.|  
|Управление всеми подписками|Элемент|Управление предупреждениями.|  
|Управление источниками данных|Элемент|Добавление, изменение, удаление и просмотр элементов.|  
|Управление папками|Элемент|Добавление, изменение, удаление и просмотр элементов.|  
|Управление отдельными подписками|Элемент|Изменение элементов<br /><br /> До версии [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] требуемым уровнем разрешений было «Создание предупреждений».|  
|Управление моделями|Элемент|Добавление, изменение, удаление и просмотр элементов.|  
|Управление журналом отчета|Элемент|Изменение элементов, просмотр и удаление версий.|  
|Управление отчетами|Элемент|Добавление, изменение, удаление и просмотр элементов.|  
|Управление ресурсами|Элемент|Добавление, изменение, удаление и просмотр элементов.|  
|Установка безопасности для отдельных элементов|Элемент|Управление разрешениями|  
|Просмотр источников данных|Элемент|Просмотр элементов.|  
|Просмотр папок|Элемент|Просмотр элементов.|  
|Просмотр моделей|Элемент|Просмотр элементов.|  
|Просмотр отчетов|Элемент|Просмотр элементов.|  
|Просмотр ресурсов|Элемент|Просмотр элементов.|  
||||  
|Выполнение определений отчета|Система|Просмотр элементов.|  
|Создание событий|Система|Управление веб-сайтом.|  
|Управление заданиями|Система|Отсутствует (не поддерживается).|  
|Управление свойствами сервера отчетов|Система|Отсутствует (неприменимо). Сервер отчетов не проверяет, имеет ли пользователь разрешение на просмотр параметров интеграции в центре администрирования.|  
|Управление ролями|Система|Управление разрешениями.|  
|Управление общими расписаниями|Система|Управление веб-сайтом, открытие.|  
|Управление безопасностью сервера отчетов|Система|Отсутствует (неприменимо). Сервер отчетов не использует назначения ролей на системном уровне на сервере, работающем в режиме интеграции с SharePoint.|  
|Просмотр свойств сервера отчетов|Система|Отсутствует (неприменимо). Сервер отчетов не проверяет, имеет ли пользователь разрешение на просмотр параметров интеграции в центре администрирования.|  
|Просмотр общих расписаний|Система|Открытие элементов.|  
  
## <a name="see-also"></a>См. также  
 [Задать разрешения для элементов сервера отчетов на сайте SharePoint &#40;режим интеграции служб Reporting Services в SharePoint&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md)   
 [Задание разрешений для работы сервера отчетов в веб-приложении SharePoint](security/set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md)   
 [Предоставление разрешений для элементов сервера отчетов на сайте SharePoint](security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Определение ролей](security/role-definitions.md)   
 [Предопределенные роли](security/role-definitions-predefined-roles.md)  
  
  
