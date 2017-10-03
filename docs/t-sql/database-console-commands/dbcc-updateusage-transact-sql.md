---
title: "DBCC UPDATEUSAGE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATEUSAGE
- UPDATEUSAGE_TSQL
- DBCC_UPDATEUSAGE_TSQL
- DBCC UPDATEUSAGE
dev_langs:
- TSQL
helpviewer_keywords:
- inaccurate page or row counts [SQL Server]
- space [SQL Server], usage reports
- updating space usage information
- updating row counts
- disk space [SQL Server], inaccurate counts
- counting pages
- reporting count inaccuracies
- updating page counts
- synchronization [SQL Server], inaccurate counts
- incorrect space usage reports [SQL Server]
- DBCC UPDATEUSAGE statement
- integrity [SQL Server], database objects
- counting rows
- row count accuracy [SQL Server]
- page count accuracy [SQL Server]
ms.assetid: b8752ecc-db45-4e23-aee7-13b8bc3cbae2
caps.latest.revision: 56
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0e99240896bb1192a742ad2b614080e5325acc1f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-updateusage-transact-sql"></a>DBCC UPDATEUSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Описывает и исправляет неточности в подсчете страниц и строк в представлениях каталога. Эти неточности могут стать причиной неверных отчетов об использовании пространства, возвращаемых системной хранимой процедурой sp_spaceused.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC UPDATEUSAGE   
(   { database_name | database_id | 0 }   
    [ , { table_name | table_id | view_name | view_id }   
    [ , { index_name | index_id } ] ]   
) [ WITH [ NO_INFOMSGS ] [ , ] [ COUNT_ROWS ] ]   
```  
  
## <a name="arguments"></a>Аргументы  
*database_name* | *database_id* | 0  
Имя или идентификатор базы данных, для которой нужно составить отчет и исправить статистику использования дискового пространства. Если указано значение 0, используется текущая база данных. Имена баз данных должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
*имя_таблицы* | *table_id* | *view_name* | *view_id*  
Имя или идентификатор таблицы или индексированного представления, для которой нужно составить отчет и исправить статистику использования дискового пространства. Имена таблиц и представлений должны соответствовать требованиям, предъявляемым к идентификаторам.  
  
*index_id* | *index_name*  
Имя или идентификатор используемого индекса. Если этот аргумент не указан, инструкция обрабатывает все индексы для указанной таблицы или представления.  
  
на  
Позволяет указывать параметры.  
  
NO_INFOMSGS  
Подавляет вывод всех информационных сообщений.  
  
COUNT_ROWS  
Указывает, что столбец row count обновляется текущим значением количества строк в таблице или представлении.  
  
## <a name="remarks"></a>Замечания  
Инструкция DBCC UPDATEUSAGE исправляет результаты подсчета строк, использованных страниц, зарезервированных страниц, конечных страниц и страниц данных для каждой секции в таблице или индексе. Если в системных таблицах нет неточностей, инструкция DBCC UPDATEUSAGE не возвращает никаких данных. Если неточности обнаружены и исправлены, а параметр WITH NO_INFOMSGS не использовался, инструкция DBCC UPDATEUSAGE возвращает строки и столбцы, обновляемые в системных таблицах.
  
Инструкция DBCC CHECKDB была улучшена для обнаружения неправильных результатов подсчета страниц и строк. При их обнаружении выходные данные инструкции DBCC CHECKDB будут содержать предупреждение и рекомендацию выполнить инструкцию DBCC UPDATEUSAGE, чтобы решить эту проблему.
  
## <a name="best-practices"></a>Рекомендации  
Рекомендуется следующее:
-   Не следует регулярно выполнять инструкцию DBCC UPDATEUSAGE. Поскольку выполнение инструкции DBCC UPDATEUSAGE для больших таблиц или баз данных занимает много времени, ее следует запускать, только если есть подозрения, что хранимая процедура sp_spaceused возвращает неверные значения.
-   Регулярно (например, еженедельно) инструкцию DBCC UPDATEUSAGE стоит выполнять, только если в базе данных часто производятся изменения на языке описания данных DDL, например выполняются инструкции CREATE, ALTER или DROP.  
  
## <a name="result-sets"></a>Результирующие наборы  
Сообщение инструкции DBCC UPDATEUSAGE (значения могут меняться).
  
`DBCC execution completed. If DBCC printed error messages, contact your system administrator.`
  
## <a name="permissions"></a>Permissions  
Необходимо быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** .
  
## <a name="examples"></a>Примеры  
  
### <a name="a-updating-page-or-row-counts-or-both-for-all-objects-in-the-current-database"></a>A. Обновление результатов подсчета страниц, строк или того и другого одновременно для всех объектов в текущей базе данных  
В следующем примере в качестве имени базы данных указывается значение `0`, и инструкция `DBCC UPDATEUSAGE` выдает обновленные сведения о подсчете страниц или строк для текущей базы данных.
  
```sql
DBCC UPDATEUSAGE (0);  
GO  
```  
  
### <a name="b-updating-page-or-row-counts-or-both-for-adventureworks-and-suppressing-informational-messages"></a>Б. Обновление результатов подсчета страниц, строк или того и другого одновременно для базы данных AdventureWorks с подавлением информационных сообщений  
В следующем примере в качестве имени базы данных указано [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], а все информационные сообщения подавлены.
  
```sql
DBCC UPDATEUSAGE (AdventureWorks2012) WITH NO_INFOMSGS;   
GO  
```  
  
### <a name="c-updating-page-or-row-counts-or-both-for-the-employee-table"></a>В. Обновление результатов подсчета страниц, строк или того и другого одновременно в таблице Employee  
В следующем примере выдаются обновленные страниц или строк сведений о счетчика для `Employee` в таблицу [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] базы данных.
  
```sql
DBCC UPDATEUSAGE (AdventureWorks2012,'HumanResources.Employee');  
GO  
```  
  
### <a name="d-updating-page-or-row-counts-or-both-for-a-specific-index-in-a-table"></a>Г. Обновление результатов подсчета страниц, строк или того и другого одновременно для указанного индекса в таблице  
 В следующем примере указано имя индекса `IX_Employee_ManagerID`.  
  
```sql
DBCC UPDATEUSAGE (AdventureWorks2012, 'HumanResources.Employee', IX_Employee_OrganizationLevel_OrganizationNode);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sp_spaceused &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)  
[UPDATE STATISTICS (Transact-SQL)](../../t-sql/statements/update-statistics-transact-sql.md)
  
  
