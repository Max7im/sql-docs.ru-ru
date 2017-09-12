---
title: "DELETE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DELETE
- DELETE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- row removal [SQL Server]
- DELETE statement [SQL Server], about DELETE statement
- views [SQL Server], deleting rows
- removing rows
- tables [SQL Server], deleting rows
- DELETE statement [SQL Server]
- deleting rows
- row removal [SQL Server], DELETE statement
- deleting data
ms.assetid: ed6b2105-0f35-408f-ba51-e36ade7ad5b2
caps.latest.revision: 78
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b4238aeb45bd18a5b868640af235985f33ccb4c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="delete-transact-sql"></a>DELETE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Удаляет одну или несколько строк из таблицы или представления в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
[ WITH <common_table_expression> [ ,...n ] ]  
DELETE   
    [ TOP ( expression ) [ PERCENT ] ]   
    [ FROM ]   
    { { table_alias  
      | <object>   
      | rowset_function_limited   
      [ WITH ( table_hint_limited [ ...n ] ) ] }   
      | @table_variable  
    }  
    [ <OUTPUT Clause> ]  
    [ FROM table_source [ ,...n ] ]   
    [ WHERE { <search_condition>   
            | { [ CURRENT OF   
                   { { [ GLOBAL ] cursor_name }   
                       | cursor_variable_name   
                   }   
                ]  
              }  
            }   
    ]   
    [ OPTION ( <Query Hint> [ ,...n ] ) ]   
[; ]  
  
<object> ::=  
{   
    [ server_name.database_name.schema_name.   
      | database_name. [ schema_name ] .   
      | schema_name.  
    ]  
    table_or_view_name   
}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DELETE FROM [database_name . [ schema ] . | schema. ] table_name    
    [ WHERE <search_condition> ]   
    [ OPTION ( <query_options> [ ,...n ]  ) ]  
[; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 С \<общее_табличное_выражение >  
 Задает временный именованный результирующий набор, также называемый обобщенным табличным выражением, который определяется в области действия инструкции DELETE. Результирующий набор получается из инструкции SELECT.  
  
 Обобщенные табличные выражения также можно использовать в инструкциях SELECT, INSERT, UPDATE и CREATE VIEW. Дополнительные сведения см. в разделе [с общее_табличное_выражение &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 Начало **(***выражение***)** [%]  
 Задает количество или процент удаляемых случайных строк. *expression* может быть либо числом, либо процентом от числа строк. Строки, на которые ссылается выражение TOP, используемое с инструкциями INSERT, UPDATE и DELETE, не упорядочиваются. Дополнительные сведения см. в разделе [в начало &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
 FROM  
 Необязательное ключевое слово, которое можно использовать между ключевым словом DELETE и целевым *table_or_view_name*, или *rowset_function_limited*.  
  
 *table_alias*  
 Псевдоним, заданный в предложении *table_source* предложение, представляющем таблицу или представление, из которого должны быть удалены строки.  
  
 *имя_сервера*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Имя сервера (с использованием имени связанного сервера или [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md) работать в качестве имени сервера) на котором расположена таблица или представление. Если *имя_сервера* указано, *имя_базы_данных* и *schema_name* являются обязательными.  
  
 *database_name*  
 Имя базы данных.  
  
 *schema_name*  
 Имя схемы, которой принадлежит таблица или представление.  
  
 *table_or view_name*  
 Имя таблицы или представления, откуда удаляются строки.  
  
 Табличную переменную в пределах ее области действия также можно использовать в качестве источника таблицы в инструкции DELETE.  
  
 Представление ссылается *table_or_view_name* должно быть обновляемым и ссылаться ровно одну базовую таблицу в предложении FROM определения представления. Дополнительные сведения об обновляемых представлениях см. в разделе [CREATE VIEW &#40; Transact-SQL &#41; ](../../t-sql/statements/create-view-transact-sql.md).  
  
 *rowset_function_limited*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Либо [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md) или [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) функции, в зависимости от возможностей поставщика.  
  
 С **(** \<table_hint_limited > [... *n*] **)**  
 Задает одно или несколько табличных указаний, разрешенных для целевой таблицы. Ключевое слово WITH и круглые скобки обязательны. Использование ключевых слов NOLOCK и READUNCOMMITTED запрещено. Дополнительные сведения о табличных подсказках см. в разделе [табличные подсказки &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-table.md).  
  
 \<OUTPUT_Clause >  
 Возвращает удаленные строки или выражения, основанные на них, как часть операции DELETE. Предложение OUTPUT не поддерживается ни в каких инструкциях DML, направленных на представления и удаленные таблицы. Дополнительные сведения см. в разделе [предложение OUTPUT &#40; Transact-SQL &#41; ](../../t-sql/queries/output-clause-transact-sql.md).  
  
 ИЗ *table_source*  
 Задает дополнительное предложение FROM. Это [!INCLUDE[tsql](../../includes/tsql-md.md)] расширение DELETE позволяет задавать данные из \<table_source > и удалять соответствующие строки из таблицы в первом предложении.  
  
 Это расширение, в котором задается соединение, может быть использовано вместо вложенного запроса в предложении WHERE для указания удаляемых строк.  
  
 Дополнительные сведения см. в разделе [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md).  
  
 WHERE  
 Указывает условия, используемые для ограничения числа удаляемых строк. Если предложение WHERE не указывается, инструкция DELETE удаляет все строки из таблицы.  
  
 Предусмотрено два вида операций удаления в соответствии с тем, что указывается в предложении WHERE.  
  
-   Операции удаления с поиском указывают условие поиска для уточнения строк, которые будут удалены. Например, ГДЕ *column_name* = *значение*.  
  
-   Операции удаления по позиции используют предложение CURRENT OF для указания курсора. Удаление осуществляется в текущей позиции курсора. Это может быть более точной, чем инструкция DELETE по найденному, использующая предложение WHERE *search_condition* предложение для определения удаляемых строк. Инструкция DELETE по найденному удаляет несколько строк, если условие поиска не определяет уникально одну строку.  
  
\<search_condition >  
 Указывает ограничивающие условия для удаляемых строк. Количество предикатов, которое может содержать условие поиска, не ограничено. Дополнительные сведения см. в разделе [условие поиска &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
 CURRENT OF  
 Указывает выполнение инструкции DELETE в текущей позиции указанного курсора.  
  
 GLOBAL  
 Указывает, что *cursor_name* ссылается на глобальный курсор.  
  
 *cursor_name*  
 Имя открытого курсора, из которого производится выборка. Если как глобальный, так и локальный курсор с именем *cursor_name* существует, этот аргумент ссылается на глобальный курсор, если GLOBAL указанного; в противном случае, он ссылается на локальный курсор. Курсор должен позволять производить обновления.  
  
 *cursor_variable_name*  
 Имя переменной курсора. Переменная курсора должна содержать ссылку на курсор, обновления которого разрешены.  
  
 ПАРАМЕТР **(** \<query_hint > [ **,**... *n*] **)**  
 Ключевые слова, указывающие, какие указания оптимизатора применяются при настройке способа [!INCLUDE[ssDE](../../includes/ssde-md.md)] обработки инструкции. Дополнительные сведения см. в разделе [Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md).  
  
## <a name="best-practices"></a>Рекомендации  
 Для удаления всех строк в таблице воспользуйтесь инструкцией TRUNCATE TABLE. Инструкция TRUNCATE TABLE выполняется быстрее, чем инструкция DELETE, и использует меньше системных ресурсов и ресурсов журнала транзакций. Инструкция TRUNCATE TABLE имеет ограничения, например, таблица не может участвовать в репликации. Дополнительные сведения см. в разделе [TRUNCATE TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/truncate-table-transact-sql.md)  
  
 Используйте @@ROWCOUNT функцию для возврата количества удаленных строк в клиентское приложение. Дополнительные сведения см. в разделе [@@ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/functions/rowcount-transact-sql.md).  
  
## <a name="error-handling"></a>Обработка ошибок  
 Для инструкции DELETE можно реализовать обработку ошибок, заключив ее в конструкцию TRY…CATCH.  
  
 При выполнении инструкции DELETE может произойти ошибка, если она нарушает триггер или пытается удалить строку, на которую ссылаются данные в другой таблице с помощью ограничения FOREIGN KEY. Если инструкция DELETE удаляет несколько строк и одна из удаленных строк нарушает триггер или ограничение, то эта инструкция отменяется, т.е. возвращается ошибка и строки не удаляются.  
  
 В случае арифметической ошибки (переполнение, деление на ноль или выход за пределы допустимых значений), возникающей в ходе вычисления выражения при выполнении инструкции DELETE, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] будет обрабатывать эти ошибки, как если бы параметр SET ARITHABORT имел значение ON. Оставшаяся часть пакетной операции отменяется и возвращается сообщение об ошибке.  
  
## <a name="interoperability"></a>Совместимость  
 Инструкцию DELETE можно использовать в тексте определяемой пользователем функции, если изменяемым объектом является табличная переменная.  
  
 При удалении строки, содержащей столбец FILESTREAM, также удаляются и связанные с ней файлы файловой системы. Базовые файлы удаляются сборщиком мусора FILESTREAM. Дополнительные сведения см. в разделе [доступ к данным FILESTREAM с помощью Transact-SQL](../../relational-databases/blob/access-filestream-data-with-transact-sql.md).  
  
 Предложение FROM нельзя указывать в инструкции DELETE, ссылающейся (прямо или косвенно) на представление, в котором указан триггер INSTEAD OF. Дополнительные сведения о триггеры INSTEAD OF см. в разделе [CREATE TRIGGER &#40; Transact-SQL &#41; ](../../t-sql/statements/create-trigger-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 При использовании выражения TOP в инструкции DELETE строки, на которые имеются ссылки, не упорядочиваются, а предложение ORDER BY не может быть прямо указано в этой инструкции. Если необходимо с помощью предложения TOP удалять строки в значимом хронологическом порядке, то вместе с ним в инструкции вложенного запроса выборки следует использовать ORDER BY. См. подраздел «Примеры» далее в этом разделе.  
  
 Предложение TOP не может быть использовано вместе с инструкцией DELETE для секционированных представлений.  
  
## <a name="locking-behavior"></a>Режим блокировки  
 По умолчанию инструкция DELETE всегда получает монопольную блокировку (X) на таблицу, которую она изменяет, и держит блокировку до тех пор, пока транзакция не завершится. Если ресурс удерживается монопольной (X) блокировкой, то другие транзакции не могут изменять данные. Операции считывания будут допускаться только при наличии подсказки NOLOCK или уровня изоляции незафиксированной операции чтения. Можно переопределить поведение оптимизатора запросов по умолчанию с помощью табличных подсказок на время выполнения инструкции DELETE указанием другого способа блокировки, но использовать подсказки рекомендуется только опытным разработчикам и администраторам баз данных и только при крайней необходимости. Дополнительные сведения см. в разделе [Табличные указания (Transact-SQL)](../../t-sql/queries/hints-transact-sql-table.md).  
  
 Когда строки удаляются из кучи, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] может использовать строку или страницу блокировки для операции. В результате пустые страницы, в которых выполняются операции удаления, остаются размещенными для кучи. Если их не освободить, занимаемое ими место не может быть использовано под другие объекты базы данных.  
  
 Чтобы удалить из кучи строки и освободить страницы, воспользуйтесь одним из следующих методов.  
  
-   Задайте указания TABLOCK в инструкции DELETE. Использование TABLOCK приведет к тому, что при выполнении операции удаления будет установлена монопольная блокировка таблицы, а не блокировка строки или страницы, что позволит освободить страницы. Дополнительные сведения о подсказке TABLOCK см. в разделе [табличные подсказки &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-table.md).  
  
-   Если из таблицы удаляются все строки, пользуйтесь инструкцией TRUNCATE TABLE.  
  
-   Перед удалением строк создайте в куче кластеризованный индекс. Потом его можно будет удалить. Этот метод потребует больше времени и потребляет больше временных ресурсов.  
  
> [!NOTE]  
>  Пустые страницы можно удалить из кучи в любое время с помощью `ALTER TABLE <table_name> REBUILD` инструкции.  
  
## <a name="logging-behavior"></a>Режим ведения журнала  
 Инструкция DELETE всегда полностью регистрируется в журнале.  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Разрешения DELETE необходимы для целевой таблицы. Разрешения SELECT также необходимы, если инструкция содержит предложение WHERE.  
  
 УДАЛЕНИЕ разрешений по умолчанию предоставляются членам **sysadmin** предопределенной роли сервера **db_owner** и **db_datawriter** фиксированной роли базы данных, а также владельцу таблицы. Члены **sysadmin**, **db_owner**и **db_securityadmin** ролей, а также владелец таблицы могут передавать разрешения другим пользователям.  
  
## <a name="examples"></a>Примеры  
  
|Категория|Используемые элементы синтаксиса|  
|--------------|------------------------------|  
|[Базовый синтаксис](#BasicSyntax)|DELETE|  
|[Ограничение удаляемых строк](#LimitRows)|WHERE • FROM • курсор •|  
|[Удаление строк из удаленной таблицы](#RemoteTables)|Связанный сервер • OPENQUERY, функция набора строк • OPENDATASOURCE, функция набора строк|  
|[Сбор результатов инструкции DELETE](#CaptureResults)|OUTPUT, предложение|  
  
###  <a name="BasicSyntax"></a>Базовый синтаксис  
 В примерах в этом разделе описывается базовая функциональность инструкции DELETE с помощью минимального необходимого синтаксиса.  
  
#### <a name="a-using-delete-with-no-where-clause"></a>А. Использование инструкции DELETE без предложения WHERE  
 Следующий пример удаляет все строки из таблицы `SalesPersonQuotaHistory` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], поскольку не указано предложение WHERE, ограничивающее количество удаляемых строк.  
  
```  
DELETE FROM Sales.SalesPersonQuotaHistory;  
GO  
```  
  
###  <a name="LimitRows"></a>Ограничение удаляемых строк  
 В примерах в этом разделе описываются способы ограничения количества удаляемых строк.  
  
#### <a name="b-using-the-where-clause-to-delete-a-set-of-rows"></a>Б. Использование предложения WHERE для удаления набора строк  
 Следующий пример удаляет все строки из `ProductCostHistory` в таблицу [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных, в котором значения в `StandardCost` столбец является более `1000.00`.  
  
```    
DELETE FROM Production.ProductCostHistory  
WHERE StandardCost > 1000.00;  
GO  
```  
  
 В следующем примере показано использование более сложного предложения WHERE. Предложение WHERE определяет два условия, которые должны быть выполнены для определения удаляемых строк. Значение в столбце `StandardCost` должно быть в диапазоне от `12.00` до `14.00` , а значение в столбце `SellEndDate` должно быть равно NULL. В примере также выводится значение из **@@ROWCOUNT**  функцию для возврата количества удаленных строк.  
  
```  
DELETE Production.ProductCostHistory  
WHERE StandardCost BETWEEN 12.00 AND 14.00  
      AND EndDate IS NULL;  
PRINT 'Number of rows deleted is ' + CAST(@@ROWCOUNT as char(3));  
```  
  
#### <a name="c-using-a-cursor-to-determine-the-row-to-delete"></a>В. Использование курсора для определения удаляемой строки  
 Следующий пример удаляет одну строку из `EmployeePayHistory` в таблицу [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных с помощью курсора `my`_`cursor`. Операция удаления затрагивает только одну строку, выбранную в данный момент курсором.  
  
```  
DECLARE complex_cursor CURSOR FOR  
    SELECT a.BusinessEntityID  
    FROM HumanResources.EmployeePayHistory AS a  
    WHERE RateChangeDate <>   
         (SELECT MAX(RateChangeDate)  
          FROM HumanResources.EmployeePayHistory AS b  
          WHERE a.BusinessEntityID = b.BusinessEntityID) ;  
OPEN complex_cursor;  
FETCH FROM complex_cursor;  
DELETE FROM HumanResources.EmployeePayHistory  
WHERE CURRENT OF complex_cursor;  
CLOSE complex_cursor;  
DEALLOCATE complex_cursor;  
GO  
```  
  
#### <a name="d-using-joins-and-subqueries-to-data-in-one-table-to-delete-rows-in-another-table"></a>Г. Использование операторов объединения и вложенных запросов к данным в одной таблице для удаления строк в другой таблице  
 В следующих примерах показано два способа удаления строк в одной таблице на основании данных в другой таблице. В обоих примерах строк от `SalesPersonQuotaHistory` в таблицу [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] удалить базу данных на основе продаж с начала года, хранящиеся в `SalesPerson` таблицы. Первый `DELETE` инструкции показано решение ISO-совместимой вложенный запрос, а второй `DELETE` показывает инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] из расширения для соединения двух таблиц.  
  
```  
-- SQL-2003 Standard subquery  
  
DELETE FROM Sales.SalesPersonQuotaHistory   
WHERE BusinessEntityID IN   
    (SELECT BusinessEntityID   
     FROM Sales.SalesPerson   
     WHERE SalesYTD > 2500000.00);  
GO  
```  
  
```  
-- Transact-SQL extension  
  
DELETE FROM Sales.SalesPersonQuotaHistory   
FROM Sales.SalesPersonQuotaHistory AS spqh  
INNER JOIN Sales.SalesPerson AS sp  
ON spqh.BusinessEntityID = sp.BusinessEntityID  
WHERE sp.SalesYTD > 2500000.00;  
GO  
```  
  
```  
-- No need to mention target table more than once.  
  
DELETE spqh  
  FROM  
        Sales.SalesPersonQuotaHistory AS spqh  
    INNER JOIN Sales.SalesPerson AS sp  
        ON spqh.BusinessEntityID = sp.BusinessEntityID  
  WHERE  sp.SalesYTD > 2500000.00;  
```  
  
#### <a name="e-using-top-to-limit-the-number-of-rows-deleted"></a>Д. Ограничение числа удаляемых строк с помощью ключевого слова TOP  
 Когда TOP (*n*) DELETE применяется предложение, операция удаления производится над произвольным подмножеством  *n*  строк. В следующем примере удаляется `20` случайных строк из `PurchaseOrderDetail` в таблицу [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных, имеющих дату ранее 1 июля 2006 г.  
  
```  
DELETE TOP (20)   
FROM Purchasing.PurchaseOrderDetail  
WHERE DueDate < '20020701';  
GO  
```  
  
 Если необходимо с помощью предложения TOP удалять строки в значимом хронологическом порядке, то вместе с ним в инструкции вложенного запроса выборки следует использовать ORDER BY. Следующий запрос удаляет из таблицы `PurchaseOrderDetail` 10 строк, имеющих самую раннюю дату. Чтобы гарантировать удаление только 10 строк, столбец, указанный в инструкции подзапроса выборки (`PurchaseOrderID`) должен являться первичным ключом таблицы. Использование неключевого столбца в инструкции подзапроса выборки может привести к удалению более чем 10 строк, если указанный столбец содержит повторяющиеся значения.  
  
```  
DELETE FROM Purchasing.PurchaseOrderDetail  
WHERE PurchaseOrderDetailID IN  
   (SELECT TOP 10 PurchaseOrderDetailID   
    FROM Purchasing.PurchaseOrderDetail   
    ORDER BY DueDate ASC);  
GO  
```  
  
###  <a name="RemoteTables"></a>Удаление строк из удаленной таблицы  
 Примеры в этом разделе демонстрируют, как удаление строк из удаленной таблицы с помощью [связанного сервера](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) или [функцию набора строк](../../t-sql/functions/rowset-functions-transact-sql.md) для ссылки на удаленную таблицу. Удаленная таблица существует на другом сервере или экземпляре SQL Server.  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
#### <a name="f-deleting-data-from-a-remote-table-by-using-a-linked-server"></a>Е. Удаление данных из удаленной таблицы с помощью связанного сервера  
 В следующем примере будет удалена строка из удаленной таблицы. Пример начинается с создания ссылки на удаленный источник данных с помощью [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md). Имя связанного сервера, `MyLinkServer`, задается в качестве части имени объекта, состоящее из четырех частей в форме *сервер.каталог.схема.объект*.  
  
```  
USE master;  
GO  
-- Create a link to the remote data source.   
-- Specify a valid server name for @datasrc as 'server_name' or 'server_name\instance_name'.  
  
EXEC sp_addlinkedserver @server = N'MyLinkServer',  
    @srvproduct = N' ',  
    @provider = N'SQLNCLI',   
    @datasrc = N'server_name',  
    @catalog = N'AdventureWorks2012';  
GO  
```  
  
```  
-- Specify the remote data source using a four-part name   
-- in the form linked_server.catalog.schema.object.  
  
DELETE MyLinkServer.AdventureWorks2012.HumanResources.Department 
WHERE DepartmentID > 16;  
GO  
```  
  
#### <a name="g-deleting-data-from-a-remote-table-by-using-the-openquery-function"></a>Ж. Удаление данных из удаленной таблицы с помощью функции OPENQUERY  
 Следующий пример удаляет строки из удаленной таблицы, указав [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md) функцию набора строк. В этом примере используется имя связанного сервера, созданного в предыдущем примере.  
  
```  
DELETE OPENQUERY (MyLinkServer, 'SELECT Name, GroupName 
FROM AdventureWorks2012.HumanResources.Department  
WHERE DepartmentID = 18');  
GO  
```  
  
#### <a name="h-deleting-data-from-a-remote-table-by-using-the-opendatasource-function"></a>З. Удаление данных из удаленной таблицы с помощью функции OPENDATASOURCE  
 Следующий пример удаляет строки из удаленной таблицы, указав [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md) функцию набора строк. Укажите допустимое имя сервера для источника данных, используя формат *имя_сервера* или *имя_сервера\имя_экземпляра*.  
  
```  
DELETE FROM OPENDATASOURCE('SQLNCLI',  
    'Data Source= <server_name>; Integrated Security=SSPI')  
    .AdventureWorks2012.HumanResources.Department   
WHERE DepartmentID = 17;'  
```  
  
###  <a name="CaptureResults"></a>Сбор результатов инструкции DELETE  
  
#### <a name="i-using-delete-with-the-output-clause"></a>И. Использование инструкции DELETE с предложением OUTPUT  
 В следующем примере показано, как сохранить результаты `DELETE` инструкции в табличную переменную в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных.  
  
```  
DELETE Sales.ShoppingCartItem  
OUTPUT DELETED.*   
WHERE ShoppingCartID = 20621;  
  
--Verify the rows in the table matching the WHERE clause have been deleted.  
SELECT COUNT(*) AS [Rows in Table] 
FROM Sales.ShoppingCartItem 
WHERE ShoppingCartID = 20621;  
GO  
```  
  
#### <a name="j-using-output-with-fromtablename-in-a-delete-statement"></a>К. Использование предложения OUTPUT с аргументом <from_table_name> в инструкции DELETE  
 Следующий пример удаляет строки в `ProductProductPhoto` в таблицу [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных на основе критерия поиска определенных в `FROM` предложения `DELETE` инструкции. Предложение `OUTPUT` возвращает столбцы из таблицы, в которой проводится удаление, `DELETED.ProductID`, `DELETED.ProductPhotoID`и столбцы из таблицы `Product` . Оно используется в предложении `FROM` для указания удаляемых строк.  
  
```  
DECLARE @MyTableVar table (  
    ProductID int NOT NULL,   
    ProductName nvarchar(50)NOT NULL,  
    ProductModelID int NOT NULL,   
    PhotoID int NOT NULL);  
  
DELETE Production.ProductProductPhoto  
OUTPUT DELETED.ProductID,  
       p.Name,  
       p.ProductModelID,  
       DELETED.ProductPhotoID  
    INTO @MyTableVar  
FROM Production.ProductProductPhoto AS ph  
JOIN Production.Product as p   
    ON ph.ProductID = p.ProductID   
    WHERE p.ProductModelID BETWEEN 120 and 130;  
  
--Display the results of the table variable.  
SELECT ProductID, ProductName, ProductModelID, PhotoID   
FROM @MyTableVar  
ORDER BY ProductModelID;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="k-delete-all-rows-from-a-table"></a>Л. Удалите все строки из таблицы  
 Следующий пример удаляет все строки из таблицы `Table1`, поскольку не указано предложение WHERE, ограничивающее количество удаляемых строк.  
  
```  
DELETE FROM Table1;  
```  
  
### <a name="l-delete-a-set-of-rows-from-a-table"></a>М. Удаление набора строк из таблицы  
 Следующий пример удаляет все строки из `Table1` таблицы, которая имеет значение больше 1000,00 в `StandardCost` столбца.  
  
```  
DELETE FROM Table1  
WHERE StandardCost > 1000.00;  
```  
  
### <a name="m-using-label-with-a-delete-statement"></a>Н. С помощью МЕТКИ с инструкцией DELETE  
 В следующем примере метку с помощью инструкции DELETE.  
  
```  
DELETE FROM Table1  
OPTION ( LABEL = N'label1' );  
  
```  
  
### <a name="n-using-a-label-and-a-query-hint-with-the-delete-statement"></a>О. С помощью метки и подсказки в запросе с помощью инструкции DELETE  
 Этот запрос показан основной синтаксис для использования подсказки в запросе соединения с помощью инструкции DELETE. Дополнительные сведения о указания соединения и как использовать предложение OPTION. в разделе [параметр (SQL Server PDW)](http://msdn.microsoft.com/en-us/72bbce98-305b-42fa-a19f-d89620621ecc).  
  
```  
-- Uses AdventureWorks  
  
DELETE FROM dbo.FactInternetSales  
WHERE ProductKey IN (   
    SELECT T1.ProductKey FROM dbo.DimProduct T1   
    JOIN dbo.DimProductSubcategory T2  
    ON T1.ProductSubcategoryKey = T2.ProductSubcategoryKey  
    WHERE T2.EnglishProductSubcategoryName = 'Road Bikes' )  
OPTION ( LABEL = N'CustomJoin', HASH JOIN ) ;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [После УСЕЧЕНИЯ таблицы &#40; Transact-SQL &#41;](../../t-sql/statements/truncate-table-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)   
 [С общее_табличное_выражение &#40; Transact-SQL &#41;](../../t-sql/queries/with-common-table-expression-transact-sql.md)   
 [@@ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/rowcount-transact-sql.md)  
  
  

