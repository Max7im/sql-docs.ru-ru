---
title: "Агрегатные функции (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], aggregate
- aggregate functions [SQL Server], about aggregate functions
- summarizing functions
- aggregate functions [SQL Server]
ms.assetid: 0c06ae42-eb0a-4d77-9d74-aa1e7f344009
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5a97d68c641d2a3deb1d3fd3a674f65cafc3854c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="aggregate-functions-transact-sql"></a>Агрегатные функции (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Агрегатные функции выполняют вычисление на наборе значений и возвращают одиночное значение. Агрегатные функции, за исключением COUNT, не учитывают значения NULL. Агрегатные функции часто используются в выражении GROUP BY инструкции SELECT.
  
Все агрегатные функции являются детерминированными. Это означает, что агрегатные функции возвращают одну и ту же величину при каждом их вызове на одном и том же наборе входных значений. Дополнительные сведения о детерминизме функций см. в разделе [функций](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md). [Предложение OVER](../../t-sql/queries/select-over-clause-transact-sql.md) может следовать за всеми агрегатными функциями, кроме GROUPING или GROUPING_ID.
  
Агрегатные функции могут быть использованы в качестве выражений только в следующих случаях.
-   Список выбора инструкции SELECT (вложенный или внешний запрос).  
-   Предложение HAVING.  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] предоставляет следующие агрегатные функции.
  
|||  
|-|-|  
|[СР.](../../t-sql/functions/avg-transact-sql.md)|[МИН.](../../t-sql/functions/min-transact-sql.md)|  
|[CHECKSUM_AGG](../../t-sql/functions/checksum-agg-transact-sql.md)|[СУММА](../../t-sql/functions/sum-transact-sql.md)|  
|[СЧЕТЧИК](../../t-sql/functions/count-transact-sql.md)|[STDEV](../../t-sql/functions/stdev-transact-sql.md)|  
|[ФУНКЦИЯ COUNT_BIG](../../t-sql/functions/count-big-transact-sql.md)|[STDEVP](../../t-sql/functions/stdevp-transact-sql.md)|  
|[ГРУППИРОВАНИЕ](../../t-sql/functions/grouping-transact-sql.md)|[VAR](../../t-sql/functions/var-transact-sql.md)|  
|[ФУНКЦИЯ GROUPING_ID](../../t-sql/functions/grouping-id-transact-sql.md)|[ФУНКЦИЯ VARP](../../t-sql/functions/varp-transact-sql.md)|  
|[MAX](../../t-sql/functions/max-transact-sql.md)||  
  
## <a name="see-also"></a>См. также:
[Встроенные функции (Transact-SQL)](../../t-sql/functions/functions.md)  
[ЧЕРЕЗ предложение &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
