---
title: Получение сведений о триггерах DDL | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- status information [SQL Server], DDL triggers
- DDL triggers, metadata
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1f7af76abbae4408a177961636a3decd94b61ea6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408124"
---
# <a name="get-information-about-ddl-triggers"></a>Получение сведений о триггерах DDL
  Представления каталога, приведенные в этом разделе, можно использовать для получения сведений о триггерах DDL.  
  
 **Получение сведений о событиях или группах событий, при возникновении которых может сработать триггер DDL.**  
  
-   [sys.trigger_event_types (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql)  
  
 **Просмотр зависимостей триггера**  
  
-   [Представление каталога sys.sql_expression_dependencies (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [Функция динамического управления sys.dm_sql_referenced_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [sys.dm_sql_referencing_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="database-scoped-ddl-triggers"></a>Триггеры DDL уровня базы данных  
 **Сведения о триггерах с областью действия на уровне базы данных**  
  
-   [sys.triggers (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)  
  
 **Сведения о событиях базы данных, вызывающих срабатывание триггеров**  
  
-   [sys.trigger_events (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)  
  
 **Определения триггеров уровня базы данных**  
  
-   [sys.sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
 **Сведения о триггерах среды CLR уровня базы данных**  
  
-   [sys.assembly_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
## <a name="server-scoped-ddl-triggers"></a>Триггеры DDL уровня сервера  
 **Сведения о триггерах с областью действия на уровне сервера**  
  
-   [sys.server_triggers (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)  
  
 **Сведения о событиях сервера, вызывающих срабатывание триггеров**  
  
-   [sys.server_trigger_events (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)  
  
 **Определения триггеров с областью действия на уровне сервера**  
  
-   [sys.server_sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)  
  
 **Сведения о триггерах CLR с областью действия на уровне сервера**  
  
-   [sys.server_assembly_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
## <a name="see-also"></a>См. также  
 [Триггеры DDL](../triggers/ddl-triggers.md)  
  
  
