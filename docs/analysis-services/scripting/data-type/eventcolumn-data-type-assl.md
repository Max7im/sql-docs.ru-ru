---
title: "Тип данных EventColumn (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- EventColumn Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- EventColumn
helpviewer_keywords:
- EventColumn data type
ms.assetid: c0009f1d-d136-4155-9a1b-7baacda4b552
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1fd43ebfcea516a6d5560818efe0b7814deb8fde
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="eventcolumn-data-type-assl"></a>Тип данных EventColumn (ASSL)
  Определяет примитивный тип данных, представляющий столбец с данными, которые будут захвачены для [событий](../../../analysis-services/scripting/objects/event-element-assl.md) как часть [трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[ColumnID](../../../analysis-services/scripting/properties/columnid-element-eventcolumn-assl.md)|  
|Производные элементы|[Столбец](../../../analysis-services/scripting/objects/column-element-assl.md) ([столбцы](../../../analysis-services/scripting/collections/columns-element-assl.md) коллекцию [трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md))|  
  
## <a name="see-also"></a>См. также:  
 [Элемент Events &#40; ASSL &#41;](../../../analysis-services/scripting/collections/events-element-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  