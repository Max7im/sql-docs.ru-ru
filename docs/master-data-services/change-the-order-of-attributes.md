---
title: "Изменение порядка атрибутов | Документы Microsoft"
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
ms.assetid: 835a032c-e37c-4f35-8ab0-5e4ae25c2e9b
caps.latest.revision: 5
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 403b8824c09993b79f82422ba9136db73b2f7eb7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="change-the-order-of-attributes"></a>Изменение порядка атрибутов
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]вы можете изменять порядок атрибутов.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-change-the-order-of-an-attribute"></a>Изменение порядка атрибутов  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Управление сущностью** выберите строку сущности, для которой необходимо создать атрибут.  
  
4.  Нажмите **Атрибуты**.  
  
5.  На странице **Управление атрибутами** выполните одно из следующих действий:  
  
    -   Если атрибут предназначен для конечных элементов, в списке **Типы членов** выберите **Конечный элемент** .  
  
    -   Если атрибут предназначен для консолидированных элементов, в списке **Типы членов** выберите **Консолидированный элемент** .  
  
    -   Если атрибут предназначен для коллекций, в списке **Типы членов** выберите **Коллекция** .  
  
6.  Выберите строку для атрибута, порядок которого необходимо изменить.  
  
    > [!NOTE]  
    >  Изменить порядок атрибутов "Имя" и "Код" нельзя.  
  
7.  Щелкните **Вверх** или **Вниз**.  
  
## <a name="see-also"></a>См. также:  
 [Атрибуты &#40; Службы Master Data Services &#41;](../master-data-services/attributes-master-data-services.md)  
  
  