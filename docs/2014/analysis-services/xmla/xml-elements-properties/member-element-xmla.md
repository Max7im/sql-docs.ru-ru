---
title: Элемент Member (XMLA) | Документация Майкрософт
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
- Member Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Member
- microsoft.xml.analysis.member
- http://schemas.microsoft.com/analysisservices/2003/engine#Member
helpviewer_keywords:
- Member element
ms.assetid: 5cc33a1f-192e-4821-a4ef-9a5f2bb7a9f0
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 318a54528ed5f9d22f0925ff10e0596413e47043
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37217934"
---
# <a name="member-element-xmla"></a>Элемент Member (XML для аналитики)
  Представляет собой отдельный элемент родительского элемента [Members](members-element-xmla.md) или [Tuple](tuple-element-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Members>  
   ...  
   <Member>  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Members>  
<!-- or -->  
<Tuple>  
   ...  
   <Member Hierarchy="string">  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Tuple>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Members](members-element-xmla.md), [Tuple](tuple-element-xmla.md)|  
|Дочерние элементы|[Caption](caption-element-xmla.md), [DisplayInfo](displayinfo-element-xmla.md), [LName](name-element-xmla.md), [LNum](lnum-element-xmla.md), [UName](uname-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|Иерархия|Обязательный атрибут типа `String` (только для родительских элементов `Tuple`). Имя иерархии, которой принадлежат члены, представленные элементом `Member`.|  
  
## <a name="remarks"></a>Примечания  
 Элемент `Member` содержит сведения, необходимые для определения и отображения элементов в рамках заданной иерархии. Для родительских элементов `Members` иерархия уже задана атрибутом `Hierarchy` родительского элемента. Для родительских элементов `Tuple` иерархия задается при помощи атрибута `Hierarchy` элемента `Member`.   
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
