---
title: Использование функций четкими | Документы Microsoft
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
- concise functions [ODBC]
- functions [ODBC], concise functions
- descriptors [ODBC], concise functions
ms.assetid: 31ac070f-8c59-4fd5-bd5a-466bb27dbca0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c53a628eaaa3ca8348ce8917ace36da35c33f653
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915579"
---
# <a name="using-concise-functions"></a>С помощью краткого функций
Некоторые функции ODBC получают неявный доступ к дескрипторам. Авторы приложений может оказаться более удобным, чем вызов **SQLSetDescField** или **SQLGetDescField**. Эти функции вызываются *четкими* функции, так как они выполняют ряд функций, включая задания или получения поля дескриптора. Некоторые функции четкими позволяют приложению задавать или извлекать несколько связанных дескриптора полей в одном вызове функции.  
  
 Краткие функции могут вызываться не извлекая дескриптора для использования в качестве аргумента. Эти функции работают с поля дескриптора, связанные с дескриптором инструкции, их вызове.  
  
 Краткие функции **SQLBindCol** и **SQLBindParameter** связать столбец или параметр, указав поля дескриптора, которые соответствуют их аргументы. Каждая из этих функций выполняет дополнительные задачи, чем просто задание дескрипторов. **SQLBindCol** и **SQLBindParameter** обеспечивают полную спецификацию привязки данных столбца или динамических параметров. Приложение может Однако изменять индивидуальные сведения привязки путем вызова **SQLSetDescField** или **SQLSetDescRec** и полностью может привязать столбец или параметр посредством серии подходящий вызовов Эти функции.  
  
 Краткие функции **SQLColAttribute**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLNumParams**, и  **SQLNumResultCols** получать значения в поля дескриптора.  
  
 **SQLSetDescRec** и **SQLGetDescRec** — это краткие функции, устанавливающие или получающие несколько поля дескриптора, которые влияют на тип данных и хранения данных столбца или параметра с помощью одного вызова. **SQLSetDescRec** — это эффективный способ, чтобы изменить привязку данных столбца или параметра в один шаг.  
  
 **SQLSetStmtAttr** и **SQLGetStmtAttr** служат в качестве краткого функции в некоторых случаях. (См. [поля дескриптора](../../../odbc/reference/develop-app/descriptor-fields.md).)
