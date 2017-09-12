---
title: "STR (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STR
- STR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- converting numbers to characters
- characters [SQL Server], converting
- character data [SQL Server]
- STR function
ms.assetid: de03531b-d9e7-4c3c-9604-14e582ac20c6
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 27af210aca06130818fd00fea9d53eebcc8aa016
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="str-transact-sql"></a>STR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает символьные данные, преобразованные из числовых данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
STR ( float_expression [ , length [ , decimal ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *float_expression*  
 Выражение приближенного числового (**float**) типа данных с десятичной запятой.  
  
 *length*  
 Общая длина. Она включает десятичную запятую, знак, цифры и пробелы. Значение по умолчанию равно 10.  
  
 *decimal*  
 Количество знаков справа от десятичной запятой. *десятичное число* должно быть меньше или равен 16. Если *десятичное* больше 16, то результат усекается до 16 знаков справа от десятичной запятой.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varchar**  
  
## <a name="remarks"></a>Замечания  
 Если указано, то значения для *длина* и *десятичное* параметров в функции STR должны быть положительными. Число округляется до целого или по умолчанию, или если десятичный параметр равен 0. Указанная длина должна быть больше или равна части числа до запятой плюс знак числа (если имеется). Короткие *float_expression* — по правому краю в указанной длины, а длинное *float_expression* усекается до заданного числа десятичных знаков. Например, STR (12**,**10) дает значение 12. Выравнивается в результирующем наборе вправо. Однако STR (1223**,**2) усекает результирующий набор до **. Строковые функции могут быть вложенными.  
  
> [!NOTE]  
>  Чтобы преобразовать данные в кодировке Юникод, используйте STR внутри преобразование или [ПРИВЕДЕНИЯ](../../t-sql/functions/cast-and-convert-transact-sql.md) функции преобразования.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выражение, состоящее из пяти знаков и десятичной запятой, преобразуется в шестизначную символьную строку. Дробная часть числа округляется до одного десятичного знака.  
  
```  
SELECT STR(123.45, 6, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------  
 123.5  
  
(1 row(s) affected)  
```  
  
 Когда выражение превышает заданную длину, строка возвращает `**` для указанной длины.  
  
```  
SELECT STR(123.45, 2, 2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--  
**  
  
(1 row(s) affected)  
```  
  
 Даже когда в `STR` вложены числовые данные, результатом являются символьные данные с указанным форматом.  
  
```  
SELECT STR (FLOOR (123.45), 8, 3;)  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
 123.000  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере выражение, состоящее из пяти знаков и десятичной запятой, преобразуется в шестизначную символьную строку. Дробная часть числа округляется до одного десятичного знака.  
  
```  
SELECT STR(123.45, 6, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------  
 123.5  
  
(1 row(s) affected)  
```  
  
 Когда выражение превышает заданную длину, строка возвращает `**` для указанной длины.  
  
```  
SELECT STR(123.45, 2, 2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--  
**  
  
(1 row(s) affected)  
```  
  
 Даже когда в `STR` вложены числовые данные, результатом являются символьные данные с указанным форматом.  
  
```  
SELECT STR (FLOOR (123.45), 8, 3);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
 123.000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

