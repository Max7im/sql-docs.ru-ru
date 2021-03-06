---
title: Тип данных CubeDimension (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CubeDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeDimension
helpviewer_keywords:
- CubeDimension data type
ms.assetid: 128ac790-65a1-4e35-b909-8dba2a61b24c
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a02ef89f5dac200450faf8151a71aeae703e8b35
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220327"
---
# <a name="cubedimension-data-type-assl"></a>Тип данных CubeDimension (ASSL)
  Определяет примитивный тип данных, представляющий связь между измерением и кубом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeDimension>  
      <ID>...</ID>  
   <Name>...</Name>  
   <Translations>...</Translations>  
   <DimensionID>...</DimensionID>  
   <Visible>...</Visible>  
   <AllMemberAggregationUsage>...</AllMemberAggregationUsage>  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
      <Attributes>...</Attributes>  
   <Hierarchies>...</Hierarchies>  
      <Annotations>...</Annotation>  
</CubeDimension>  
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
|Дочерние элементы|[AllMemberAggregationUsage](../properties/aggregationusage-element-assl.md), [заметки](../collections/annotations-element-assl.md), [атрибуты](../collections/attributes-element-assl.md), [DimensionID](../properties/id-element-assl.md), [иерархий](../collections/hierarchies-element-assl.md), [HierarchyUniqueNameStyle](../properties/hierarchyuniquenamestyle-element-assl.md), [идентификатор](../properties/id-element-assl.md), [MemberUniqueNameStyle](../properties/memberuniquenamestyle-element-assl.md), [имя](../properties/name-element-assl.md), [видимым](../properties/visible-element-assl.md), [Переводы](../collections/translations-element-assl.md)|  
|Производные элементы|[Измерение](../objects/dimension-element-assl.md) ([измерения](../collections/dimensions-element-assl.md) коллекцию [куба](../objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Предусмотрено по одному измерению `CubeDimension` для каждой связи измерений в кубе `Cube`. Объект `CubeDimension` охватывает все группы мер `MeasureGroups` куба.  
  
 Объект `CubeDimension` должен включать [CubeHierarchy](hierarchy-data-type-assl.md) Если измерение содержит какие-то конкретные сказать об иерархии, в том числе предусматривающие иерархии (и тем самым допускающие выбор иерархий, относящихся к конкретному Использование измерения), или невидимую иерархии.  
  
 Аналогичным образом `CubeDimension` должен включать [CubeAttribute](cubeattribute-data-type-assl.md) только в том случае, если измерение содержит какие-то конкретные, чтобы сказать об атрибуте. (Какой-либо способ, позволяющий выбирать атрибуты, относящиеся к конкретному назначению измерения, не предусмотрен, однако атрибуты можно преобразовать в невидимые.)  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
