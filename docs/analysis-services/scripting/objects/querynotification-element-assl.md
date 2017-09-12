---
title: "Элемент QueryNotification (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- QueryNotification Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- QueryNotification element
ms.assetid: 0ee06730-81ff-4913-96e6-f39b6f181650
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 610b18f6c9c02f2ce6cfa8dd33d9eaca53abecd3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="querynotification-element-assl"></a>Элемент QueryNotification (ASSL)
  Содержит сведения для элемента [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) о запросе, который необходимо выполнить, чтобы определить, был ли изменен источник данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<QueryNotifications>  
   <QueryNotification>  
      <Query>...</Query>  
...</QueryNotification>  
</QueryNotifications>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[QueryNotifications](../../../analysis-services/scripting/collections/querynotifications-element-assl.md)|  
|Дочерние элементы|[Запрос](../../../analysis-services/scripting/properties/query-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.QueryNotification>.  
  
## <a name="see-also"></a>См. также:  
 [Тип данных ProactiveCachingQueryBinding &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  