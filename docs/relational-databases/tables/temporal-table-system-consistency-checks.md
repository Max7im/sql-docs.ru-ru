---
title: Проверка согласованности системной темпоральной таблицы | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ec081d42-57e4-43c7-9e1c-317ba8f23437
caps.latest.revision: 10
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cdcbfb679266ae91aa39bca271085acc3d541ddf
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43083437"
---
# <a name="temporal-table-system-consistency-checks"></a>Проверка согласованности системной темпоральной таблицы
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  При использовании темпоральных таблиц система выполняет ряд проверок согласованности. Они необходимы для обеспечения соответствия схемы требованиям, чтобы данные в таблице были и оставались согласованными. Кроме того, проверки темпоральных таблиц были добавлены в инструкцию **DBCC CHECKCONSTRAINTS** .  
  
## <a name="system-consistency-checks"></a>Системные проверки согласованности  
 Прежде чем **SYSTEM_VERSIONING** примет значение **ON**, выполняется ряд проверок таблицы журнала и текущей таблицы. Эти проверки подразделяются на проверки схемы и проверки данных (если таблица журнала содержит данные). Кроме того, система выполняет проверку согласованности среды выполнения.  
  
### <a name="schema-check"></a>Проверка схемы  
 При создании или изменении таблицы, которая становится темпоральной, система проверяет соблюдение следующих требований.  
  
1.  Имена и количество столбцов в текущей таблице и таблице журнала совпадают.  
  
2.  Типы данных для каждого столбца в текущей таблице и таблице журнала совпадают.  
  
3.  Значения в столбцах периода равны **NOT NULL**.  
  
4.  Текущая таблица содержит ограничение первичного ключа, а таблица журнала не имеет первичного ключа.  
  
5.  В таблице журнала не определены столбцы **IDENTITY** .  
  
6.  В таблице журнала не определены триггеры.  
  
7.  В таблице журнала не определены внешние ключи.  
  
8.  В таблице журнала не определены ограничения для таблицы или столбцов. Тем не менее в таблице журнала допускается наличие значений столбцов по умолчанию.  
  
9. Таблица журнала не размещена в файловой группе, доступной только для чтения.  
  
10. Таблица журнала не настроена на отслеживание изменений или запись измененных данных.  
  
### <a name="data-consistency-check"></a>Проверка согласованности данных  
 Прежде чем **SYSTEM_VERSIONING** примет значение **ON** , в рамках операции DML система выполнит следующую проверку: **SysEndTime** ≥**SysStartTime**  
  
 При создании ссылки на существующую таблицу журнала вы можете указать необходимость проверки согласованности данных. Проверка согласованности данных гарантирует, что существующие записи не будут перекрываться и что для каждой записи будут выполняться временные требования. Проверка согласованности данных является проверкой по умолчанию. Как правило, выполнение проверки согласованности данных рекомендуется, когда данные текущей таблицы и таблицы журнала могут оказаться несинхронизированными. Например, такая ситуация может возникнуть при внедрении существующей таблицы журнала, заполненной данными журнала.  
  
> [!WARNING]  
>  Ручное внесение изменений в системные часы приведет к неожиданному сбою системы, так как текущие проверки согласованности данных в среде выполнения не допускают перекрытия данных (т.е. время окончания записи не может быть меньше времени начала).  
  
## <a name="dbcc-checkconstraints"></a>DBCC CHECKCONSTRAINTS  
 Команда **DBCC CHECKCONSTRAINTS** включает проверки согласованности темпоральных данных. Дополнительные сведения см. в разделе [DBCC CHECKCONSTRAINTS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkconstraints-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)   
 [Приступая к работе c темпоральными таблицами с системным управлением версиями](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Секционирование с помощью темпоральных таблиц](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [Рекомендации и ограничения для темпоральной таблицы](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [Безопасность темпоральных таблиц](../../relational-databases/tables/temporal-table-security.md)   
 [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Представления и функции метаданных для временной таблицы](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
