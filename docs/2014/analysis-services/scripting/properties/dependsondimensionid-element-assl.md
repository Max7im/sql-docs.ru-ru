---
title: Элемент DependsOnDimensionID (ASSL) | Документация Майкрософт
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
- DependsOnDimensionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DependsOnDimensionID
helpviewer_keywords:
- DependsOnDimensionID element
ms.assetid: 66ec20dd-b475-4895-a92c-7ac0e7e1c675
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8bda178f067cb8bf1a3cfe4bf7341c6916659a65
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171405"
---
# <a name="dependsondimensionid-element-assl"></a>Элемент DependsOnDimensionID (ASSL)
  Содержит идентификатор другого измерения, от которого зависит родительское измерение.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension>  
      ...  
   <DependsOnDimensionID>...</DependsOnDimensionID>  
   ...  
</Dimension>  
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
|Родительские элементы|[Dimension](../objects/dimension-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `DependsOnDimensionID` позволяет зависимому измерению определить измерение, от которого оно зависит.  
  
 Элемент, соответствующий родителю параметра `DependsOnDimensionID` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
