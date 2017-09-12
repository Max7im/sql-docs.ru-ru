---
title: "Создание группы атрибутов (Master Data Services) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cd89cee45f9f0973764a2b4f4dc32f32abc6d1c9
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="create-an-attribute-group-master-data-services"></a>Создание группы атрибутов (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]группы атрибутов создаются, когда нужно отобразить атрибуты на отдельных вкладках сетки **обозревателя** .  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Требуется хотя бы один атрибут. Дополнительные сведения см. в разделе [Создание текстового атрибута (службы Master Data Services)](../master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-create-an-attribute-group"></a>Создание группы атрибутов  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) выберите в сетке строку сущности, для которой необходимо создать группу атрибутов.  
  
4.  Щелкните **Группы атрибутов**.  
  
5.  На странице "Управление группами атрибутов" выполните одно из следующих действий, а затем нажмите кнопку **Добавить**.  
  
     Если группа атрибутов предназначена для конечных элементов, выберите пункт **Конечный** из раскрывающегося списка **Типы элементов** в верхней части страницы.  
  
     Если группа атрибутов предназначена для консолидированных элементов, из раскрывающегося списка **Типы элементов** выберите пункт **Консолидированный** .  
  
     Если группа атрибутов предназначена для коллекций, из раскрывающегося списка **Типы элементов** выберите **Коллекция** .  
  
6.  Выберите **Конечные группы**, **Консолидированные группы**или **Группы коллекций** , чтобы создать группу атрибутов для конечных элементов, объединенных элементов или коллекций соответственно.  
  
7.  Введите имя группы атрибутов в поле **Имя** . Это имя отображается на вкладке в **обозревателе**.  
  
8.  Чтобы добавить атрибут, щелкните атрибут в поле **Доступные атрибуты** , а затем щелкните стрелку **Добавить** . Чтобы добавить все атрибуты, щелкните стрелку **Добавить все** .  
  
9. Можно изменить порядок атрибутов слева направо, щелкая стрелки **Вверх** и **Вниз** .  
  
10. Выберите пользователей в поле **Доступные пользователи** , затем щелкните стрелку **Добавить** . Чтобы добавить всех пользователей, щелкните стрелку **Добавить все** .  
  
11. Выберите группы в поле **Доступные группы** , затем щелкните стрелку **Добавить** . Чтобы добавить все группы, щелкните стрелку **Добавить все** .  
  
12. Нажмите кнопку **Сохранить**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Превращение группы атрибутов в видимую для пользователей (службы Master Data Services)](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Группы атрибутов (службы Master Data Services)](../master-data-services/attribute-groups-master-data-services.md)   
 [Атрибуты &#40; Службы Master Data Services &#41;](../master-data-services/attributes-master-data-services.md)   
 [Изменение имени группы атрибутов &#40; Службы Master Data Services &#41;](../master-data-services/change-an-attribute-group-name-master-data-services.md)   
 [Удалить группу атрибутов &#40; Службы Master Data Services &#41;](../master-data-services/delete-an-attribute-group-master-data-services.md)   
 [Разрешения конечного элемента (службы основных данных)](../master-data-services/leaf-permissions-master-data-services.md)   
   
  
  
