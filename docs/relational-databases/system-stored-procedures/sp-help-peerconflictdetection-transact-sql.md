---
title: процедура sp_help_peerconflictdetection (Transact-SQL) | Документация Майкрософт
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
- sp_help_peerconflictdetection
- sp_help_peerconflictdetection_TSQL
helpviewer_keywords:
- sp_help_peerconflictdetection
ms.assetid: 59e04107-5eaa-44a1-beb6-ac4f2dbbcb28
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 01ab569de510b115e0c2643192254366d5b41ebb
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021065"
---
# <a name="sphelppeerconflictdetection-transact-sql"></a>sp_help_peerconflictdetection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о настройках обнаружения конфликта для публикации, участвующей в топологии одноранговой репликации транзакций.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_peerconflictdetection [ @publication = ] 'publication'  
    [ ,[ @timeout = ] timeout ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @publication=] '*публикации*"  
 Имя публикации, для которой возвращаются данные. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ @timeout=] *время ожидания*  
 Указывает время (в секундах), в течение которого процедура ожидает ответа от каждого из узлов топологии. Если в топологии имеется подписчик, доступный только для чтения, указание значения времени ожидания недопустимо. Подписчик, доступный только для чтения, никогда не ответит на вызов из этой процедуры. *время ожидания* — **int**, значение по умолчанию 60.  
  
## <a name="result-sets"></a>Результирующие наборы  
 Процедура sp_help_peerconflictdetection возвращает три результирующих набора. Все они описаны в следующих разделах:  
  
-   [MSpeer_conflictdetectionconfigrequest](../../relational-databases/system-tables/mspeer-conflictdetectionconfigrequest-transact-sql.md)  
  
-   [MSpeer_conflictdetectionconfigresponse](../../relational-databases/system-tables/mspeer-conflictdetectionconfigresponse-transact-sql.md)  
  
-   [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md)  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_help_peerconflictdetection применяется в одноранговой репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также  
 [Обнаружение конфликтов в одноранговой репликации](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
