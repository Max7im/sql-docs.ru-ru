---
title: Аргументов функций каталога | Документы Microsoft
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
- arguments in catalog functions [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], about arguments
- functions [ODBC], catalog functions
ms.assetid: f5e0abec-8f24-42e0-b94f-16dd1f2004fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1df1c7701b3e6c64e2acb103ad2b38fc4cbb99d6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911499"
---
# <a name="arguments-in-catalog-functions"></a>Аргументов в функции работы с каталогами
Все функции работы с каталогами аргументов, с которыми приложение можно ограничить область возвращаемых данных. Например, первая и вторая вызовы **SQLTables** в следующем коде возвращает результирующий набор, содержащий сведения обо всех таблицах, а третий вызов возвращает сведения о таблице Orders:  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Строковые аргументы функции каталога делятся на четыре различных типа: обычный аргумент (OA), значение аргумента pattern (PV), аргумента идентификатора (ID) и значение списка аргументов (корпоративного лицензирования). Большая часть строковых аргументов может быть одного из двух различных типов, в зависимости от значения атрибута SQL_ATTR_METADATA_ID инструкции. В следующей таблице приведены возможные аргументы для каждой функции каталога и описывает тип аргумента для значения SQL_TRUE или SQL_FALSE SQL_ATTR_METADATA_ID.  
  
|Функция|Аргумент|Время SQL_<br /><br /> ATTR_METADATA_<br /><br /> ИДЕНТИФИКАТОР = SQL_FALSE|Время SQL_<br /><br /> ATTR_METADATA_<br /><br /> ИДЕНТИФИКАТОР = SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA OA OA PV|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОРОМ ID|  
|**SQLColumns**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA PV PV PV|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОРОМ ID|  
|**SQLForeignKeys**|*PKCatalogName* *PKSchemaName* *PKTableName* *FKCatalogName* *FKSchemaName*  *FKTableName*|OA OA OA OA OA OA|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОРОМ ID|  
|**SQLPrimaryKeys**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ИДЕНТИФИКАТОР ИДЕНТИФИКАТОРОМ ID|  
|**SQLProcedureColumns**|*CatalogName* *SchemaName* *ProcName* *ColumnName*|OA PV PV PV|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОРОМ ID|  
|**SQLProcedures**|*CatalogName* *SchemaName* *ProcName*|OA PV PV|ИДЕНТИФИКАТОР ИДЕНТИФИКАТОРОМ ID|  
|**SQLSpecialColumns**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ИДЕНТИФИКАТОР ИДЕНТИФИКАТОРОМ ID|  
|**SQLStatistics**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ИДЕНТИФИКАТОР ИДЕНТИФИКАТОРОМ ID|  
|**SQLTablePrivileges**|*CatalogName* *SchemaName* *TableName*|OA PV PV|ИДЕНТИФИКАТОР ИДЕНТИФИКАТОРОМ ID|  
|**SQLTables**|*CatalogName* *SchemaName* *TableName* *TableType*|КОРПОРАТИВНАЯ ЛИЦЕНЗИЯ PV PV PV|КОРПОРАТИВНАЯ ЛИЦЕНЗИЯ ИДЕНТИФИКАТОР ИДЕНТИФИКАТОР ID|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обычные аргументы](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Аргументы значения шаблона](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Аргументы идентификатора](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Аргументы списка значений](../../../odbc/reference/develop-app/value-list-arguments.md)
