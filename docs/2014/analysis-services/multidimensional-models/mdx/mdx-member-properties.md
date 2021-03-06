---
title: Использование свойств элементов (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c2918188146fd84761bd23340ec5b76b48685eab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37259540"
---
# <a name="using-member-properties-mdx"></a>Использование свойств элементов (многомерные выражения)
  Свойства элементов включают основные сведения о каждом элементе каждого кортежа. К таким основным сведениям относятся имя элемента, родительский уровень, число потомков и т. д. Свойства элемента доступны всем элементам данного уровня. С точки зрения организации свойства элемента рассматриваются как организованные по измерениям данные, хранимые в одном измерении.  
  
> [!NOTE]  
>  В [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]свойства элемента рассматриваются как связь атрибутов. Дополнительные сведения см. в разделе [Связи атрибутов](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
 Существуют *внутренние* и *пользовательские*свойства:  
  
 Внутренние свойства элементов  
 Все элементы поддерживают внутренние свойства элементов, такие как форматированное значение элемента, а измерения и уровни обеспечивают еще и дополнительные внутренние свойства измерения и уровня элементов, например идентификатор элемента.  
  
 Дополнительные сведения см. в разделе [Внутренние свойства элементов (многомерные выражения)](mdx-member-properties-intrinsic-member-properties.md).  
  
 Пользовательские свойства элементов  
 С элементами часто связаны дополнительные свойства. Например, каждому товару уровня «Продукты» могут быть присвоены свойства SKU, SRP, Weight и Volume. Эти свойства не являются элементами, они содержат дополнительные сведения об элементах на уровне «Продукты».  
  
 Дополнительные сведения см. в разделе [Пользовательские свойства элементов (многомерные выражения)](mdx-member-properties-user-defined-member-properties.md).  
  
 Оба свойства встроенных и определяемых пользователем элементов можно извлечь воспользоваться `PROPERTIES` ключевое слово или [свойства](/sql/mdx/properties-mdx) функции.  
  
## <a name="using-the-properties-keyword"></a>Использование ключевого слова PROPERTIES  
 `PROPERTIES` Ключевое слово указывает свойства элементов, которые будут использоваться для данной оси измерения. `PROPERTIES` Ключевое слово запрятано в `<axis specification>` предложение многомерных выражений [ВЫБЕРИТЕ](/sql/mdx/mdx-data-manipulation-select) инструкции:  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 Предложение `<axis_specification>` содержит необязательное предложение `<dim_props>` , как видно в следующем синтаксисе:  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  Дополнительные сведения о значениях `<set>` и `<axis_name>` см. в разделе [Определение содержимого оси запроса (многомерные выражения)](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
 `<dim_props>` Предложение позволяет запроса измерения, уровня и свойств элементов используется `PROPERTIES` ключевое слово. Следующий синтаксис показывает формат предложения `<dim_props>` :  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 Синтаксическая конструкция `<property>` изменяется в зависимости от свойства, к которому обращен запрос.  
  
-   Чувствительным к контексту внутренним свойствам элементов должно предшествовать имя измерения или уровня. Однако нечувствительные к контексту внутренние свойства элементов не могут быть определены именем измерения или уровня. Дополнительные сведения об использовании `PROPERTIES` ключевое слово с внутренними свойствами элементов см. в разделе [внутренние свойства элементов &#40;многомерных Выражений&#41;](mdx-member-properties-intrinsic-member-properties.md).  
  
-   Заданным пользователем внутренним свойствам элемента должно предшествовать имя уровня, на котором они располагаются. Дополнительные сведения об использовании `PROPERTIES` ключевого слова with свойства элементов, определяемых пользователем, см. в разделе [пользовательские свойства элементов &#40;многомерных Выражений&#41;](mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="see-also"></a>См. также  
 [Создание и использование значений свойств &#40;многомерных Выражений&#41;](../../creating-and-using-property-values-mdx.md)  
  
  
