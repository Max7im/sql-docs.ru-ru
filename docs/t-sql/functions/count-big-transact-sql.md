---
title: "Функция COUNT_BIG (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COUNT_BIG_TSQL
- COUNT_BIG
dev_langs:
- TSQL
helpviewer_keywords:
- totals [SQL Server], COUNT_BIG function
- counting items in group
- groups [SQL Server], number of items in
- number of group items
- COUNT_BIG function
ms.assetid: f2e3601f-487e-4917-bb01-47b1047908cd
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8ce3046c36b7d224f6294948029cef6cf5afd43c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="countbig-transact-sql"></a>COUNT_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает количество элементов в группе. Функция COUNT_BIG работает подобно функции COUNT. Единственное различие между двумя функциями — возвращаемые значения. Функция COUNT_BIG всегда возвращает **bigint** значение типа данных. Функция COUNT всегда возвращает **int** значение типа данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Syntax for SQL Server and Azure SQL Database  
  
COUNT_BIG ( { [ ALL | DISTINCT ] expression } | * )  
   [ OVER ( [ partition_by_clause ] [ order_by_clause ] ) ]  
```  
  
```sql
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

-- Aggregation Function Syntax  
COUNT_BIG ( { [ [ ALL | DISTINCT ] expression ] | * } )  
  
-- Analytic Function Syntax  
COUNT_BIG ( { expression | * } ) OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Аргументы  
ALL  
Применяет агрегатную функцию ко всем значениям. ALL является параметром по умолчанию.
  
DISTINCT  
Указывает, что функция COUNT_BIG возвращает количество уникальных значений, не равных NULL.
  
*expression*  
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа. Агрегатные функции и вложенные запросы не допускаются.
  
*\**  
Указывает, что все строки должны быть подсчитаны для возврата общего числа строк в таблице. Функция COUNT_BIG (*\**) не принимает никаких параметров и не может использоваться с ключевым словом DISTINCT. Функция COUNT_BIG (*\**) не требует *выражение* параметр так, как по определению не использует сведения о любого столбца. Функция COUNT_BIG (*\**) возвращает количество строк в указанной таблице, не отбрасывая дубликаты. Она подсчитывает каждую строку отдельно. При этом учитываются и строки, содержащие значения NULL.
  
ALL  
Применяет агрегатную функцию ко всем значениям. ALL является параметром по умолчанию.
  
DISTINCT  
Указывает на то, что функция AVG будет выполнена только для одного экземпляра каждого уникального значения, независимо от того, сколько раз встречается это значение.
  
*expression*  
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) точных числовых или приблизительных числовых типа данных, за исключением **бит** тип данных. Агрегатные функции и вложенные запросы не допускаются.
  
НАД **(** [ *partition_by_clause* ] [ *order_by_clause* ] **)**  
*partition_by_clause* Делит результирующий набор, полученный с помощью предложения FROM, на секции, к которым применяется функция. Если этот параметр не указан, функция обрабатывает все строки результирующего набора запроса как отдельные группы. *order_by_clause* , определяет логический порядок, в котором выполняется операция. Дополнительные сведения см. в разделе [предложение OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).
  
## <a name="return-types"></a>Возвращаемые типы
**bigint**
  
## <a name="remarks"></a>Замечания  
Функция COUNT_BIG(*) возвращает количество элементов в группе. Сюда входят значения NULL и повторяющиеся значения.
  
Функция COUNT_BIG (все *выражение*) вычисляет *выражение* для каждой строки в группе и возвращает количество значений, отличных от NULL.
  
Функция COUNT_BIG (DISTINCT *выражение*) вычисляет *выражение* для каждой строки в группе и возвращает количество уникальных ненулевых значений,.
  
COUNT_BIG — это детерминированная функция, если она используется без предложений OVER и ORDER BY. Она не детерминирована при использовании с предложениями OVER и ORDER BY. Дополнительные сведения см. в разделе [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="examples"></a>Примеры  
Примеры см. в разделе [число &#40; Transact-SQL &#41; ](../../t-sql/functions/count-transact-sql.md).
  
## <a name="see-also"></a>См. также:
[Агрегатные функции &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[Число &#40; Transact-SQL &#41;](../../t-sql/functions/count-transact-sql.md)  
[int, bigint, smallint и tinyint &#40; Transact-SQL &#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
[ЧЕРЕЗ предложение &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
