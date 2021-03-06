---
title: КАК предиката Escape-символ | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38fa73fb069f7b7a037a61af711474b277cfa0d7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911869"
---
# <a name="like-predicate-escape-character"></a>КАК предиката Escape-символ
В **как** предиката, знак процента (%) соответствует ноль или несколько любых символов, и символ подчеркивания (_) соответствует любому символу. В соответствии с фактический процент или символ подчеркивания в **как** предиката, escape-символ должен указываться до знак процента или знака подчеркивания. Escape-последовательность, которая определяет **как** предиката escape-символ —:  
  
 **{escape "** *escape символ* **"}**  
  
 где *escape символ* — это любой символ, который поддерживается источником данных.  
  
 Дополнительные сведения о LIKE escape-последовательности, см. в разделе [как управляющая последовательность](../../../odbc/reference/appendixes/like-escape-sequence.md) в грамматику SQL приложение C:.  
  
 Например следующие инструкции SQL создать один и тот же результирующий набор клиенту, имена которых начинаются с символов «% AAA». В первом операторе используется синтаксис escape последовательность. Вторая инструкция использует собственный синтаксис для Microsoft® Access и не поддерживает взаимодействие. Обратите внимание, что второй процентов символов в каждом **как** предикат является подстановочный знак, который заменяет ноль или несколько любых символов.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Чтобы определить, является ли **как** предиката escape-символ поддерживается источником данных, приложение вызывает **SQLGetInfo** с параметром SQL_LIKE_ESCAPE_CLAUSE.
