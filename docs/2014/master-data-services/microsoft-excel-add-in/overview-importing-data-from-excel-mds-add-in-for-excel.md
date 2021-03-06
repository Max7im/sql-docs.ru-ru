---
title: Публикация данных (надстройка MDS для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f9fbee4ad70222c81f8f2fc40c460974f6f5ac05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155065"
---
# <a name="publishing-data-mds-add-in-for-excel"></a>Публикация данных (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]можно опубликовать данные в репозитории MDS, если их необходимо передать другим пользователям. После публикации они станут доступными для загрузки другим пользователям надстройки.  
  
 Все добавленные и обновившиеся при публикации данные публикуются в репозитории MDS. Удаленные данные не публикуются, их необходимо удалить отдельно. Дополнительные сведения см. в разделе [Delete a Row &#40;MDS Add-in for Excel&#41;](delete-a-row-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  Публикация не может быть использована для создания новой сущности. Дополнительные сведения о создании сущностей см. в разделе [Создание сущности (надстройка MDS для Excel)](create-an-entity-mds-add-in-for-excel.md).  
  
## <a name="when-multiple-users-publish-at-the-same-time"></a>Одновременная публикация несколькими пользователями  
 Несколько пользователей могут публиковать обновления одних и тех же данных одновременно. В результате каждой публикации в базу данных записывается обновление. Это означает, что пользователь, не имеющий самых последних обновленных данных, может изменять значения во время публикации.  
  
 В базе данных публикуются только внесенные вами изменения. Устаревшие данные на листе не публикуются.  
  
## <a name="transactions-and-annotations"></a>Транзакции и заметки  
 Каждое опубликованное изменение сохраняется в виде транзакции. По вашему выбору в транзакцию можно добавить заметки (комментарии), объясняющие причины внесения изменений.  
  
-   Заметки к операциям удаления не добавляются, хотя они сохраняются в виде транзакций, которые могут использоваться для выполнения обратной операции администратором.  
  
-   При изменении **код** значение для элемента, он не регистрируется как транзакции, а все предыдущие транзакции для элемента будут недоступны.  
  
-   Можно просмотреть транзакции для элемента, сделанные другими пользователями. Можно также просмотреть все свои транзакции для элемента, даже если вы больше не имеете разрешений на определенные атрибуты.  
  
 Можно просмотреть все транзакции, выполненные для элемента. Дополнительные сведения см. в разделе [View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md).  
  
> [!IMPORTANT]  
>  Если введена заметка длиной более 500 символов, то она автоматически усекается.  
  
## <a name="business-rule-and-other-validation"></a>Проверка бизнес-правил и другие проверки  
 При публикации данных выполняется проверка, чтобы обеспечить точность данных перед их добавлением в репозиторий MDS. Если данные не соответствуют заданным условиям, то они не будут опубликованы. Дополнительные сведения см. в разделе [Проверка данных (надстройка MDS для Excel)](validating-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Публикация данных из активного листа в репозитории MDS.|[Публикация данных из Excel в MDS &#40;надстройка MDS для Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Одновременное удаление строки из репозитория MDS и с листа.|[Удалить строку &#40;надстройка MDS для Excel&#41;](delete-a-row-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Обновление данных (надстройка MDS для Excel)](refreshing-data-mds-add-in-for-excel.md)  
  
-   [Надстройка служб Master Data Services для Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
  
