---
title: SET ANSI_NULLS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SET_ANSI_NULLS_TSQL
- ANSI_NULLS
- SET ANSI_NULLS
- ANSI_NULLS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET ANSI_NULLS statement
- not equal to operator (<>)
- ANSI_NULLS option
- equals operator (=)
- null values [SQL Server], comparison operators
- comparison operators [SQL Server], null values
ms.assetid: aae263ef-a3c7-4dae-80c2-cc901e48c755
caps.latest.revision: 43
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2c26c23cfca578a7d729aac4dd3817f6dc24f954
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43083233"
---
# <a name="set-ansinulls-transact-sql"></a>SET ANSI_NULLS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Задает совместимое со стандартом ISO поведение операторов сравнения «равно» (=) и «не равно» (<>) при их использовании со значениями NULL в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> [!IMPORTANT]  
>  В будущей версии параметр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ANSI_NULLS будет иметь значение ON, а приложения, явно присваивающие ему значение OFF, будут вызывать ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>Синтаксис

```
-- Syntax for SQL Server

SET ANSI_NULLS { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ANSI_NULLS ON
```

## <a name="remarks"></a>Remarks  
 Если параметру SET ANSI_NULLS установлено значение ON, любая инструкция SELECT, использующая предложение WHERE *column_name* = **NULL**, не вернет ни одной строки, даже если в столбце *column_name* есть значения NULL. Инструкция SELECT, использующая предложение WHERE *column_name* <> **NULL**, не вернет ни одной строки, даже если в столбце *column_name* есть значения, отличные от NULL.  
  
 Если SET ANSI_NULLS установлено в OFF, операторы «равно» (=) и «не равно» (<>) не следуют стандарту ISO. Инструкция SELECT, использующая предложение WHERE *column_name* = **NULL**, вернет строки, имеющие значения NULL, в столбце *column_name*. Инструкция SELECT, использующая предложение WHERE *column_name* <> **NULL**, вернет строки, имеющие значения, отличные от NULL, в столбце. Также любая инструкция SELECT, использующая предложение WHERE *column_name* <> *XYZ_value*, возвращает все строки со значениями, не равными *XYZ_value* и не равными NULL.  
  
 Если SET ANSI_NULLS равняется ON, все сравнения со значением NULL возвращают значение UNKNOWN. Когда SET ANSI_NULLS равняется OFF, сравнение любых значений с NULL вернет TRUE только в том случае, если сравниваемое значение тоже NULL. Если параметр SET ANSI_NULLS не указан, применяется значение параметра ANSI_NULLS текущей базы данных. Дополнительные сведения о параметре базы данных ANSI_NULLS см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).  

 В следующей таблице показано влияние значения параметра ANSI_NULLS на результаты нескольких логических выражений с использованием значений NULL и значений, отличных от NULL.  
  
|Логическое выражение|SET ANSI_NULLS ON|SET ANSI_NULLS OFF|  
|---------------|---------------|------------|  
|NULL = NULL|UNKNOWN|TRUE|  
|1 = NULL|UNKNOWN|FALSE|  
|NULL <> NULL|UNKNOWN|FALSE|  
|1 <> NULL|UNKNOWN|TRUE|  
|NULL > NULL|UNKNOWN|UNKNOWN|  
|1 > NULL|UNKNOWN|UNKNOWN|  
|NULL IS NULL|TRUE|TRUE|  
|1 IS NULL|FALSE|FALSE|  
|NULL IS NOT NULL|FALSE|FALSE|  
|1 IS NOT NULL|TRUE|TRUE|  

 Директива SET ANSI_NULLS ON влияет только на сравнения, в которых в качестве одного из операндов используется NULL в виде переменной или литеральной константы. Если оба операнда представляют собой столбцы или составные выражения, эта настройка не влияет на результат сравнения.  
  
 Чтобы скрипт работал в соответствии с первоначальным замыслом, вне зависимости от параметра базы данных ANSI NULLS или настроек SET ANSI_NULLS, в сравнениях, которые могут содержать значения NULL, следует использовать выражения IS NULL и IS NOT NULL.  
  
 Значение SET ANSI_NULLS должно быть равно ON при выполнении распределенных запросов.  
  
 Значение SET ANSI_NULLS также должно быть ON при создании или изменении индексов вычисляемых столбцов или индексированных представлений. Если SET ANSI_NULLS равно OFF, то при работе с таблицами, содержащими индексы вычисляемых столбцов, а также при работе с индексированными представлениями инструкции CREATE, UPDATE, INSERT и DELETE завершатся неудачно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сообщение об ошибке с перечислением всех недопустимых аргументов инструкции SET. Также при вызове инструкции SELECT в случае, если значение SET ANSI_NULLS равно OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не обрабатывает значения индексов вычисляемых столбцов или представлений и произведет выборку, словно этих индексов не существовало.  
  
> [!NOTE]  
>  ANSI_NULLS является одним из семи параметров директивы SET, которые должны быть установлены определенным образом при работе с вычисляемыми столбцами или индексированными представлениями. Параметры ANSI_PADDING, ANSI_WARNINGS, ARITHABORT, QUOTED_IDENTIFIER и CONCAT_NULL_YIELDS_NULL должны иметь значение ON, а параметр NUMERIC_ROUNDABORT — значение OFF.  
  
 При соединении с драйвером ODBC для Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или поставщика OLE DB для Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметру ANSI_NULLS автоматически задается значение ON. Этот параметр может быть настроен в источниках данных ODBC, в атрибутах соединения ODBC или свойствах соединения OLE DB, установленных в приложении перед подключением к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию значение SET ANSI_NULLS равно OFF.  
  
 Когда параметр SET ANSI_DEFAULTS имеет значение ON, режим SET ANSI_NULLS включен.  
  
 Установка значения SET ANSI_NULLS происходит во время запуска или выполнения, но не во время синтаксического анализа.  
  
 Чтобы просмотреть текущее значение для этого параметра, выполните следующий запрос:
  
```  
DECLARE @ANSI_NULLS VARCHAR(3) = 'OFF';  
IF ( (32 & @@OPTIONS) = 32 ) SET @ANSI_NULLS = 'ON';  
SELECT @ANSI_NULLS AS ANSI_NULLS;  
  
```  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 Следующий пример иллюстрирует использование операторов «равно» (`=`) и «не равно» (`<>`) для сравнения со значениями `NULL` и не NULL в таблице. Этот пример также демонстрирует, что использование конструкции `IS NULL` не зависит от значения параметра `SET ANSI_NULLS`.  
  
```  
-- Create table t1 and insert values.  
CREATE TABLE dbo.t1 (a INT NULL);  
INSERT INTO dbo.t1 values (NULL),(0),(1);  
GO  
  
-- Print message and perform SELECT statements.  
PRINT 'Testing default setting';  
DECLARE @varname int;   
SET @varname = NULL;  
  
SELECT a  
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to ON and test.  
PRINT 'Testing ANSI_NULLS ON';  
SET ANSI_NULLS ON;  
GO  
DECLARE @varname int;  
SET @varname = NULL  
  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to OFF and test.  
PRINT 'Testing SET ANSI_NULLS OFF';  
SET ANSI_NULLS OFF;  
GO  
DECLARE @varname int;  
SET @varname = NULL;  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- Drop table t1.  
DROP TABLE dbo.t1;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY (Transact-SQL)](../../t-sql/functions/sessionproperty-transact-sql.md)   
 [= (равно) (Transact-SQL)](../../t-sql/language-elements/equals-transact-sql.md)   
 [IF...ELSE (Transact-SQL)](../../t-sql/language-elements/if-else-transact-sql.md)   
 [<> (не равно) (Transact-SQL)](../../t-sql/language-elements/not-equal-to-transact-sql-traditional.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS (Transact-SQL)](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  
