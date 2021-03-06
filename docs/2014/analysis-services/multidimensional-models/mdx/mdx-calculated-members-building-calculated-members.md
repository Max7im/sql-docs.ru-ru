---
title: Создание вычисляемых элементов в многомерных Выражениях (многомерные Выражения) | Документация Майкрософт
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
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5f01746c6bb0c73705451db8f236c75c1b8935bf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312654"
---
# <a name="building-calculated-members-in-mdx-mdx"></a>Создание вычисляемых элементов в многомерных выражениях (многомерные выражения)
  В многомерных выражениях вычисляемым называется элемент, разрешаемый путем вычисления многомерного выражения, возвращающего значение. В этом определении кроется огромный потенциал. Возможность создания и использования вычисляемых элементов в многомерных запросах дает широкие возможности для манипулирования данными.  
  
 Вычисляемый элемент можно создать в любом месте иерархии. Кроме того, вычисляемые элементы могут зависеть не только от существующих элементов куба, но и от других вычисляемых элементов, определенных в том же многомерном выражении.  
  
 При определении вычисляемого элемента для него можно задать один из следующих контекстов.  
  
-   **Область запроса.** Для создания вычисляемого элемента, определяемого как часть многомерного запроса, область которого, следовательно, ограничена этим запросом, применяется ключевое слово WITH. После создания вычисляемый элемент можно использовать в инструкции многомерных выражений SELECT. Этот подход позволяет изменять вычисляемый элемент, созданный при помощи ключевого слова WITH, не изменяя инструкцию SELECT.  
  
     Дополнительные сведения о создании вычисляемых элементов с помощью ключевого слова WITH см. в разделе [Создание вычисляемых элементов с областью действия запроса (многомерные выражения)](mdx-calculated-members-query-scoped-calculated-members.md).  
  
-   **Область сеанса.** Для создания вычисляемого элемента, область которого шире контекста запроса и распространяется на весь сеанс многомерных выражений, применяется инструкция CREATE MEMBER. Вычисляемый элемент, определенный при помощи инструкции CREATE MEMBER, доступен для всех многомерных запросов текущего сеанса. Например, инструкцию CREATE MEMBER имеет смысл использовать в клиентском приложении, которое постоянно использует один и тот же набор в различных запросах.  
  
     Дополнительные сведения о создании вычисляемых элементов в сеансе с помощью инструкции CREATE MEMBER см. в разделе [Создание вычисляемых элементов с областью действия сеанса (многомерные выражения)](mdx-calculated-members-session-scoped-calculated-members.md).  
  
## <a name="see-also"></a>См. также  
 [Инструкция CREATE MEMBER &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-definition-create-member)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](/sql/mdx/mdx-function-reference-mdx)   
 [Инструкция SELECT &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-manipulation-select)  
  
  
