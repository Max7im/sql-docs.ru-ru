---
title: Элемент DefaultScript (ASSL) | Документация Майкрософт
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
- DefaultScript Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultScript
helpviewer_keywords:
- DefaultScript element
ms.assetid: 60716e63-2d64-4774-9ac9-253efe612fa5
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5de4eca3e226e6eddbe811af5dc089b1965cbd08
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200064"
---
# <a name="defaultscript-element-assl"></a>Элемент DefaultScript (ASSL)
  Определяет значение по умолчанию [MdxScript](../objects/mdxscript-element-assl.md) элемент в [MdxScripts](../collections/mdxscripts-element-assl.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MdxScript>  
   ...  
   <DefaultScript>...</DefaultScript>  
   ...  
</MdxScript>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|`True`|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[MdxScript](../objects/mdxscript-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Присвоение элементу `DefaultScript` значения `True` для одного скрипта приводит к присвоению элементу `DefaultScript` значения `False` для всех остальных элементов `MdxScript` в коллекции `MdxScripts`.  
  
 Элемент, соответствующий родителю параметра `DefaultScript` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.MdxScript>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
