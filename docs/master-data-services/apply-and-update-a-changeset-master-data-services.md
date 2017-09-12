---
title: "Применение и обновление набора изменений (Master Data Services) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a6a3cf2-1e77-43d3-a64a-855ae51258e7
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8bd1f16bf28951aa128d1ab218ef12e8affbe1aa
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="apply-and-update-a-changeset-master-data-services"></a>Применение и обновление набора изменений (Master Data Services)
  Набор изменений — это совокупность ожидающих изменений основных данных. Набор изменений можно применить локально, чтобы просмотреть, добавить, обновить и удалить ожидающие изменения в этом наборе.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** . Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Необходимо иметь по крайней мере доступ на обновление сущности или одного из ее атрибутов.  
  
-   Можно просмотреть только набор изменений, которым вы владеете или который отправлен вам на утверждение, если вы являетесь администратором сущности.  
  
-   Вы можете изменить только набор изменений, владельцем которого вы являетесь, и если он находится в открытом или отклоненном состоянии.  
  
## <a name="to-apply-and-update-a-changeset"></a>Применение и обновление набора изменений  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель и версию, а затем щелкните **Обозреватель**.  
  
2.  Щелкните сущность в меню **Сущности** .  
  
3.  В области справа выберите **Наборы изменений** и дважды щелкните набор изменений, который хотите просмотреть и изменить.  
  
4.  Нажмите кнопку **Применить**.  
  
     Ожидающие изменения применяются к элементу сущности в сетке. Ожидающие изменения выделены.  
  
     Создание, удаление и обновление элементов приводит к изменениям в наборе изменений.  
  
5.  Чтобы обратить ожидающие изменения, в области **Наборы изменений** щелкните правой кнопкой мыши в сетке и выберите пункт **Обратить**.  
  
## <a name="next-steps"></a>Следующие шаги  
 [Фиксация или отправка набора изменений (Master Data Services)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Создание набора изменений (Master Data Services)](../master-data-services/create-a-changeset-master-data-services.md)   
 [Утверждение или отклонение набора изменений (Master Data Services)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  