---
title: sp_scriptpublicationcustomprocs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_scriptpublicationcustomprocs
- sp_scriptpublicationcustomprocs_TSQL
helpviewer_keywords:
- sp_scriptpublicationcustomprocs
ms.assetid: b06102d5-4284-4834-b126-bc0baea49be5
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 15c841becf856af68e37273349cdb7b3fe578fdf
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43026863"
---
# <a name="spscriptpublicationcustomprocs-transact-sql"></a>sp_scriptpublicationcustomprocs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Записывает в скрипт пользовательские процедуры INSERT, UPDATE и DELETE для всех статей таблиц из публикации, в которой включен параметр автоматического создания схемы пользовательской процедуры. **sp_scriptpublicationcustomprocs** особенно полезна для настройки подписок, для которых моментальный снимок применяется вручную.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_scriptpublicationcustomprocs [ @publication = ] 'publication_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publication**=] **"***publication_name***"**  
 Имя публикации. *publication_name* — **sysname** не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор, состоящий из одного **nvarchar(4000)** столбца. Результирующий набор формирует полную инструкцию CREATE PROCEDURE, необходимую для создания пользовательской хранимой процедуры.  
  
## <a name="remarks"></a>Примечания  
 Пользовательские процедуры не вносятся в сценарии для статей, для которых не задан параметр автоматического создания схемы пользовательской процедуры (0x2).  
  
 Следующие процедуры используются **sp_scriptpublicationcustomprocs** создавать процедуры на подписчике и не следует выполнять вручную:  
  
 **sp_script_reconciliation_delproc**  
  
 **sp_script_reconciliation_insproc**  
  
 **sp_script_reconciliation_vdelproc**  
  
 **sp_script_reconciliation_xdelproc**  
  
 **sp_scriptdelproc**  
  
 **sp_scriptinsproc**  
  
 **sp_scriptmappedupdproc**  
  
 **sp_scriptupdproc**  
  
 **sp_scriptvdelproc**  
  
 **sp_scriptvupdproc**  
  
 **sp_scriptxdelproc**  
  
 **sp_scriptxupdproc**  
  
## <a name="permissions"></a>Разрешения  
 Выполните разрешение предоставляется **открытый**; проверка безопасности выполняется внутри этой хранимой процедуры, чтобы ограничить доступ к членам **sysadmin** предопределенной роли сервера и **db_ владелец** предопределенной роли базы данных в текущей базе данных.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
