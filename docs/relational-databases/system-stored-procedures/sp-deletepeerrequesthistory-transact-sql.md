---
title: sp_deletepeerrequesthistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
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
- sp_deletepeerrequesthistory
- sp_deletepeerrequesthistory_TSQL
helpviewer_keywords:
- sp_deletepeerrequesthistory
ms.assetid: 63a4ec6e-ce79-4bf1-9d37-5ac88f8d6beb
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f10334205614bc0fae541a80bb00d9fa3a58f27c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021412"
---
# <a name="spdeletepeerrequesthistory-transact-sql"></a>sp_deletepeerrequesthistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет журнал, связанный с запросом состояния публикации, который включает журнал запросов ([MSpeer_request &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mspeer-request-transact-sql.md)) и историю ответа ([MSpeer_response &#40; Transact-SQL&#41;](../../relational-databases/system-tables/mspeer-response-transact-sql.md)). Эта хранимая процедура выполняется на базе данных публикации на издателе, являющемся Peer-to-Peer топологии репликации. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_deletepeerrequesthistory [ @publication = ] 'publication'  
    [ , [ @request_id = ] request_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации, запрос состояния которой был создан. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@request_id=** ] *request_id*  
 Указывает отдельный запрос состояния, так что все ответы на этот запрос будут удалены. *Идентификатор request_id* — **int**, со значением по умолчанию NULL.  
  
 [  **@cutoff_date=** ] *cutoff_date*  
 Указывает начальную дату, до которой все более ранние записи ответов удаляются. *cutoff_date* — **datetime**, со значением по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_deletepeerrequesthistory** используется в топологии репликации транзакций Peer-to-Peer. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 При выполнении **sp_deletepeerrequesthistory**, либо *request_id* или *cutoff_date* должен быть указан.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_deletepeerrequesthistory**.  
  
## <a name="see-also"></a>См. также  
 [sp_helppeerrequests &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)   
 [sp_helppeerresponses &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)   
 [sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)  
  
  
