---
title: Тип данных PerspectiveAction (ASSL) | Документация Майкрософт
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
- PerspectiveAction Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PerspectiveAction
helpviewer_keywords:
- PerspectiveAction data type
ms.assetid: a0e4a545-688c-4d4e-b05f-0008d3503349
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8886962d5b2014d3cdaa466861d4693319d21d34
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316914"
---
# <a name="perspectiveaction-data-type-assl"></a>Тип данных PerspectiveAction (ASSL)
  Определяет тип-примитив, представляющий сведения о действии в [перспективы](../objects/perspective-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<PerspectiveAction>  
   <ActionID>...</ActionID>  
   <Annotations>...</Annotations>  
</PerspectiveAction>  
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
|Дочерние элементы|[ActionID](../properties/id-element-assl.md), [заметок](../collections/annotations-element-assl.md)|  
|Производные элементы|[Действие](../objects/action-element-assl.md) ([действия](../collections/actions-element-assl.md) коллекцию [перспективы](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.PerspectiveAction>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
