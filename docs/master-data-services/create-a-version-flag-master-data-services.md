---
title: "Создание флага версии (Master Data Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: be3585a40a7ce8312e4e31b13118f6b128e2be13
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-version-flag-master-data-services"></a>Создание флага версии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]флаг версии создается, чтобы назначить версию. Флаг может указывать на то, какую версию следует использовать пользователям или системам-подписчикам.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Необходимо иметь разрешение на доступ к функциональной области "Управление версиями". Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-create-a-version-flag"></a>Создание флага версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На панели меню страницы **Управление версиями** наведите курсор на **Управление** и выберите **Флаги**.  
  
3.  На странице **Управление флагами версий** выберите модель в поле **Модель** , для которой нужно создать флаг.  
  
4.  Нажмите кнопку **Добавить**.  
  
5.  В поле **Имя** введите имя.  
  
6.  В поле **Описание** введите описание.  
  
7.  В поле **Только зафиксированные версии** выберите **True** , чтобы указать, что флаг может назначаться только версиям со статусом **Зафиксированная** . Выберите **False** , чтобы указать, что флаг может назначаться версиям с любым состоянием.  
  
8.  Нажмите кнопку **Сохранить**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Назначение флага версии &#40; Службы Master Data Services &#41;](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Версии &#40; Службы Master Data Services &#41;](../master-data-services/versions-master-data-services.md)   
 [Изменение имени флага версии &#40; Службы Master Data Services &#41;](../master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  