---
title: "sp_fulltext_semantic_register_language_statistics_db (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_register_language_statistics_db
- sp_fulltext_semantic_register_language_statistics_db_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_fulltext_semantic_register_language_statistics_db
ms.assetid: bef1b104-5a44-4327-9ae4-45eae3000f7e
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0d1a0820d6cafd6930eb4446267840b52aa24fd3
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spfulltextsemanticregisterlanguagestatisticsdb-transact-sql"></a>sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Регистрирует предварительно заполненную базу данных семантической статистики языка в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Семантическое извлечения возможно только после присоединения этой базы данных статистики языка и ее регистрации с помощью этой хранимой процедуры. Это действие выполняется только один раз для каждого из экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```tsql  
EXEC sp_fulltext_semantic_register_language_statistics_db  
    [ @dbname = ] ‘database_name’;  
GO  
```  
  
##  <a name="Arguments"></a> Аргументы  
 [ @dbname =] '*имя_базы_данных*"  
 Имя базы данных семантической статистики языка, регистрируемой в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. База данных должна быть уже присоединена. *database_name* — **sysname**, и не может иметь значение NULL.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-set"></a>Результирующий набор  
 Нет.  
  
## <a name="general-remarks"></a>Общие замечания  
 База данных семантической статистики языка содержит статистическую информацию, связанную с языком и необходимую для семантической обработки текстового содержимого.  
  
 **sp_fulltext_semantic_register_language_statistics_db** выполняет следующие действия:  
  
1.  Проверяет, является ли экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версией, которая поддерживает семантическую обработку.  
  
2.  Проверяет, определена ли уже база данных семантической статистики языка в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Проверяет, является ли база данных допустимой базой данных семантической статистики языка.  
  
4.  Устанавливает разрешения для базы данных семантической статистики языка, ограничивая доступ пользователей к этой базе данных.  
  
5.  Вставляет метаданные, определяющие имя базы данных семантической статистики языка для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
6.  Вставляет метаданные, определяющие соответствие между установленной базой данных семантической статистики языка и внутренними таблицами языковой модели.  
  
7.  Проверяет, готова ли база данных к использованию.  
  
 Дополнительные сведения см. в разделе [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Метаданные  
 Сведения о базе данных статистики семантики языка, установленной на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запрос к представлению каталога [sys.fulltext_semantic_language_statistics_database &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Требуются разрешения CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как зарегистрировать базу данных семантической статистики языка путем вызова **sp_fulltext_semantic_register_language_statistics_db**.  
  
```tsql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = 'semanticsDb';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  