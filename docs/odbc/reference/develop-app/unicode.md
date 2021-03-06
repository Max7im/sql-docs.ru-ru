---
title: Юникод | Документы Microsoft
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
- Unicode [ODBC]
- Unicode [ODBC], about Unicode
ms.assetid: 113e1c9a-8333-4805-86f2-e4b57ab816a5
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 61195f58629f1eb3cdbcb7ee66b5b2ace87b4558
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915089"
---
# <a name="unicode"></a>Юникод
Юникод определяет кодировку для символов на различных языках.  
  
 Дополнительные сведения о стандарте Юникод см. в разделе [Unicode Consortium](http://www.unicode.org).  
  
 В Юникоде определяются универсального набора знаков. Кодовая страница Windows ANSI определяет набор символов, обычно содержащий знаков для одного языка. Он может быть труднее написать приложение, которое требуется использовать разные кодовые страницы.  
  
 Юникод не требуется кодовая страница. Каждая точка кода сопоставляется с одного символа в какой-либо язык.  
  
 В настоящее время только Юникод, кодировка, ODBC поддерживает — UCS-2, который использует 16-разрядное целое (фиксированной длины) для представления символа. Юникод позволяет приложениям работать на разных языках.  
  
 Диспетчер драйверов ODBC 3.5 (или более поздней версии) поддерживает Юникод. Это влияет на две основные области: вызовами функции и строковые типы данных. Диспетчер драйверов maps строка аргументы функций и строковые данные, требуемые для приложений и драйверов, из которых может быть поддержкой ANSI или Юникод. Эти две области подробно описываются в разделах, [аргументы функции Юникода](../../../odbc/reference/develop-app/unicode-function-arguments.md) и [данных в Юникоде](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Диспетчер драйверов ODBC 3.5 (или более поздней версии) поддерживает использование драйвера Юникода с помощью приложения с поддержкой Юникода и приложение ANSI. Оно также поддерживает использование драйвера ANSI с приложением ANSI. Диспетчер драйверов предоставляет ограниченный сопоставление Unicode-ANSI для приложения с поддержкой Юникода, работе с драйвером ANSI.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Аргументы функции Юникода](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Данные в Юникоде](../../../odbc/reference/develop-app/unicode-data.md)
