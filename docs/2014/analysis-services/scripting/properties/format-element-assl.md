---
title: Форматировать элемент (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Format Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Format
helpviewer_keywords:
- Format element
ms.assetid: 881ea707-52a7-46f7-ba16-ac2ec44eca22
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b8b5fdae50b38c81ad29143887717b412084c2c2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169505"
---
# <a name="format-element-assl"></a>Элемент Format (ASSL)
  Содержит требуемый формат параметра [DataItem](../data-type/dataitem-data-type-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataItem>  
   ...  
   <Format>...</Format>  
      ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Допустимые значения для `Format` элемент являются форматы Microsoft Office Excel, а также строки *TrimRight*, *TrimLeft*, *TrimAll*, и  *TrimNone*. Для усечения значением по умолчанию является значение *TrimRight* .  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|Строка в любом формате Excel|Данные форматируются в соответствии с указанной именованной или пользовательской строкой форматирования. Любая строка форматирования, которую поддерживает Excel, может быть предоставлена.|  
|*TrimAll*|Данные усекаются слева и справа.|  
|*TrimLeft*|Данные усекаются слева.|  
|*TrimNone*|Данные не усекаются.|  
|*TrimRight*|Данные усекаются справа.|  
  
 Элемент, соответствующий родителю параметра `Format` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
