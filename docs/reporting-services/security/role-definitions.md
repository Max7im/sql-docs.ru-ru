---
title: Определения ролей | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: security
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- roles [Reporting Services], security
- security [Reporting Services], role definitions
- role-based security [Reporting Services], role definitions
ms.assetid: d1b8dbf0-4462-402e-92dd-0e4835002b6e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 006d109559a8232664c4f83f651048a3077212f1
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43279864"
---
# <a name="role-definitions"></a>Определение ролей
  В службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] *определение**роли* — это именованная коллекция задач, которая включает операции, доступные на сервере отчетов. Определение ролей содержит правила, которые сервер отчетов использует для обеспечения безопасности. Когда пользователь пытается выполнить задачу, например опубликовать отчет, сервер отчетов, сверяясь с назначением ролей этого пользователя, определяет, включена ли данная задача в определение роли пользователя. Запрос выполняется только в том случае, если задача включена в определение роли.  
  
## <a name="using-roles-to-authorize-access-to-a-report-server"></a>Использование ролей для санкционирования доступа к серверу отчетов  
 Роль становится действительной только тогда, когда она включена в назначение ролей. Дополнительные сведения об обеспечении безопасности с помощью ролей см. в разделе [Назначения ролей](../../reporting-services/security/role-assignments.md).  
  
## <a name="types-of-role-definitions"></a>Типы определения ролей  
 Определения ролей бывают определениями на уровне элемента или на уровне системы. В *определении роли на уровне элемента* описываются задачи, относящиеся к элементам, которые хранятся и управляются на сервере отчетов, например, к отчетам, папкам и моделям. Управление отчетами, просмотр папок и управление индивидуальными подписками являются примерами задач, которые можно включить в определения роли на уровне элемента. *Определение системной роли* включает в себя задачи, относящиеся к сайту как к целому. Просмотр свойств сервера отчетов — пример задачи, которую можно включить в системную роль.  
  
## <a name="predefined-roles"></a>Стандартные роли  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают стандартные роли, соответствующие различным уровням взаимодействия пользователей. Следующий список содержит стандартные роли, которые можно использовать.  
  
-   «Диспетчер содержимого», «Издатель», «Браузер», «Построитель отчетов» и «Мои отчеты» — это определения ролей на уровне элемента, которые можно использовать при создании назначения ролей для доступа к содержимому сервера отчетов.  
  
-   «Системный администратор» и «Системный пользователь» — примеры определения ролей на уровне системы, которые можно использовать для санкционирования доступа к операциям на сайте.  
  
 Дополнительные сведения см. в статье [Стандартные роли](../../reporting-services/security/role-definitions-predefined-roles.md).  
  
## <a name="creating-a-role-definition"></a>Создание определения роли  
 Чтобы создать роль, нужно указать ее имя и содержащиеся в ней задачи в среде Management Studio. Следует создавать отдельные определения роли для задач на уровне элемента и для системных задач. Роли могут включать задачи уровня элемента и задачи системного уровня, но не те и другие одновременно. Для создания определения роли необходимо задать имя и выбрать набор задач для данного определения. Также необходимо иметь разрешение на создание определения роли. Эти разрешения предоставляет задача «Установка безопасности для отдельных элементов». По умолчанию эту задачу могут выполнять администраторы и пользователи, которым назначена стандартная роль **Диспетчер содержимого** .  
  
 Роли следует присвоить уникальное имя. В определении правильной роли должна содержаться хотя бы одна задача. Дополнительные сведения см. в статье [Tasks and Permissions](../../reporting-services/security/tasks-and-permissions.md).  
  
 Чтобы создать определение роли, воспользуйтесь средой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Дополнительные сведения см. в статье [Создание, удаление и изменение ролей (среда Management Studio)](../../reporting-services/security/role-definitions-create-delete-or-modify.md).  
  
 Созданное определение роли можно использовать, выбрав его в назначении ролей. Дополнительные сведения см. в статье [Предоставление пользователям доступа к серверу отчетов (диспетчер отчетов)](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md).  
  
## <a name="customize-or-delete-a-role-definition"></a>Настройка или удаление определения роли  
 Стандартные роли можно модифицировать или заменять пользовательскими ролями. Для изменения роли следует добавлять или удалять задачи из ее определения. Переименовать роль нельзя. Любые внесенные изменения немедленно применяются ко всем назначениям ролей, содержащим это определение роли.  
  
 Можно удалить определение роли, если оно больше не нужно. Нельзя удалить определение роли, выбранное для функции «Мои отчеты», если эта функция включена. Перед тем как удалить определение роли, используемое для функции «Мои отчеты», сначала отключите ее или выберите другое определение роли.  
  
## <a name="see-also"></a>См. также:  
 [Tasks and Permissions](../../reporting-services/security/tasks-and-permissions.md)   
 [Предоставление разрешений на сервер отчетов в собственном режиме](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Создание, удаление и изменение ролей (среда Management Studio)](../../reporting-services/security/role-definitions-create-delete-or-modify.md)   
 [Предоставление пользователям доступа к серверу отчетов (диспетчер отчетов)](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)   
 [Изменение или удаление назначения ролей (диспетчер отчетов)](../../reporting-services/security/role-assignments-modify-or-delete.md)   
 [Задание разрешений для элементов сервера отчетов на сайте SharePoint (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/security/set-permissions-for-report-server-items-on-a-sharepoint-site.md)  
  
  
