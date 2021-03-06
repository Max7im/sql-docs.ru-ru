---
title: Создание и публикация бизнес-правила (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], creating
- creating business rules [Master Data Services]
ms.assetid: 6961d636-4d69-468e-81f7-8d0be6a4a039
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 5cdcdb6edb146393a9daee7221d0a0d979989046
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37322385"
---
# <a name="create-and-publish-a-business-rule-master-data-services"></a>Создание и публикация бизнес-правила (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]бизнес-правило создается для гарантии точности основных данных. Чтобы применить к данным созданное правило, его необходимо опубликовать.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-and-publish-a-business-rule"></a>Создание и публикация бизнес-правила  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Обслуживание бизнес-правил** выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  В списке **Тип элемента** выберите тип элемента, к которому будет применяться бизнес-правило.  
  
6.  Выберите из списка **Атрибут** атрибут или оставьте **Все**по умолчанию.  
  
7.  Нажмите **Добавить бизнес-правило**.  
  
8.  Нажмите **Изменить выбранное бизнес-правило**.  
  
9. На панели **Компоненты** разверните узел **Условия** .  
  
10. Выберите условие и перетащите его на значок **IF** области **условия** метки.  
  
    > [!TIP]  
    >  Можно удалить элементы из бизнес-правила, щелкнув правой кнопкой мыши и выбрав **удалить**.  
  
11. В **атрибуты** панели, щелкните атрибут и перетащите его на значок **Изменение условия** области **выбора атрибута** метки.  
  
12. В **Изменение условия** области, заполните все необходимые поля.  
  
13. На панели **Изменение условия** нажмите кнопку **Сохранить элемент**.  
  
14. На панели **Компоненты** разверните узел **Действия** .  
  
15. Перетащите действие на значок **Действие** панели **THEN** .  
  
16. На панели **Атрибуты** щелкните атрибут и перетащите его на значок **Выбор атрибута** панели **Изменение действия** .  
  
17. На панели **Изменение действия** заполните все необходимые поля.  
  
18. На панели **Изменение действия** нажмите кнопку **Сохранить элемент**.  
  
19. В правило также можно добавлять по несколько условий. Дополнительные сведения см. в статье [Добавление нескольких условий к бизнес-правилу &#40службы Master Data Services&#41](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md).  
  
20. Нажмите кнопку **Назад**.  
  
21. По желанию на странице **Обслуживание бизнес-правил** дважды щелкните ячейку столбца **Имя**, **Описание**или **Уведомление** , чтобы обновить значение.  
  
    > [!NOTE]  
    >  Уведомления отправляются только для правил, включающих действие по проверке.  
  
22. Нажмите кнопку **Опубликовать бизнес-правила**.  
  
23. В диалоговом окне подтверждения нажмите кнопку **ОК**. Состояние правила изменится на **Активно**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   Примените бизнес-правила к данным с помощью одной из следующих процедур:  
  
    -   [Проверка конкретных членов, соответствие бизнес-правилам &#40;службы Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Проверка версии на соответствие бизнес-правила &#40;службы Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>См. также  
 [Настройка бизнес-правилах отправки уведомлений &#40;службы Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)   
 [Изменение имени бизнес-правила (службы Master Data Services)](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Добавление нескольких условий к бизнес-правилу (службы Master Data Services)](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)  
  
  
