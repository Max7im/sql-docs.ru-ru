---
title: sysmergesubscriptions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysmergesubscriptions_TSQL
- sysmergesubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergesubscriptions system table
ms.assetid: 6adc78da-991d-4c08-98c3-ecb4762e0e99
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fcbe175a186b42c7bfb8e49290c7594e7b9e67d1
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102502"
---
# <a name="sysmergesubscriptions-transact-sql"></a>sysmergesubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица в базе данных издателя, которая содержит по одной строке на каждого известного подписчика. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|subscriber_server|**sysname**|Идентификатор сервера. Используется для сопоставления поля srvid с уникальным для сервера значением при размещении копии базы данных подписки на другом сервере.|  
|db_name|**sysname**|Имя подписывающейся базы данных.|  
|pubid|**uniqueidentifier**|Идентификатор публикации, на которую осуществляется подписка.|  
|datasource_type|**int**|Тип источника данных:<br /><br /> **0** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **2** = jet OLE DB.|  
|subid|**uniqueidentifier**|Уникальный идентификационный номер подписки.|  
|replnickname|**binary**|Сжатый псевдоним реплики.|  
|replicastate|**uniqueidentifier**|Уникальный идентификатор, используемый для определения того, была ли успешна предыдущая синхронизация путем сравнения значений на стороне издателя и подписчика.|  
|status|**tinyint**|Состояние подписки.<br /><br /> **0** = неактивно.<br /><br /> **1** = активно.<br /><br /> **2** = удалена.|  
|subscriber_type|**int**|Тип подписчика:<br /><br /> **1** = глобальный.<br /><br /> **2** = local.<br /><br /> **3** = анонимная.|  
|subscription_type|**int**|Тип подписки.<br /><br /> **0** = принудительно отправить.<br /><br /> **1** = по запросу.<br /><br /> **2** = анонимная.|  
|sync_type|**tinyint**|Тип синхронизации:<br /><br /> **1** = автоматическая.<br /><br /> **2** = нет синхронизации.|  
|description|**nvarchar(255)**|Краткое описание подписки.|  
|priority|**real**|Указывает приоритет подписки и позволяет реализовать разрешение связанных с ним конфликтов. Равняется **0,00** для всех локальных и анонимных подписок.|  
|recgen|**bigint**|Номер последнего полученного поколения данных.|  
|recguid|**uniqueidentifier**|Уникальный идентификатор полученного поколения данных.|  
|sentgen|**bigint**|Номер последнего отправленного поколения данных.|  
|sentguid|**uniqueidentifier**|Уникальный идентификатор последнего отправленного поколения данных.|  
|schemaversion|**int**|Номер последней полученной схемы.|  
|schemaguid|**uniqueidentifier**|Уникальный идентификатор последней полученной схемы.|  
|last_validated|**datetime**|**Datetime** последней успешной проверки данных подписчика.|  
|attempted_validate|**datetime**|Последний **datetime** что попытки проверки подписки.|  
|last_sync_date|**datetime**|**Datetime** синхронизации.|  
|last_sync_status|**int**|Состояние подписки:<br /><br /> **0** = все задания ожидают запуска.<br /><br /> **1** = одно или более заданий запускаются.<br /><br /> **2** = все задания выполнены успешно.<br /><br /> **3** = по крайней мере одно задание выполняется.<br /><br /> **4** = все задания запланированы и простоя.<br /><br /> **5** = по крайней мере одно задание производит попытку запуска после предыдущего сбоя.<br /><br /> **6** = по крайней мере одно задание завершилось неудачно.|  
|last_sync_summary|**sysname**|Описание результатов последней синхронизации.|  
|metadatacleanuptime|**datetime**|Последний **datetime** истекшим сроком действия метаданных был удален из системных таблиц репликации слиянием.|  
|partition_id|**int**|Идентифицирует предварительно вычисляемую секцию, которой принадлежит подписка.|  
|cleanedup_unsent_changes|**bit**|Указывает, что метаданные для неотправленных изменений были удалены на стороне подписчика.|  
|replica_version|**int**|Идентифицирует версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] владельца данной подписки и может принимать одно из следующих значений:<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|supportability_mode|**int**|Только для внутреннего применения.|  
|application_name|**nvarchar(128)**|Только для внутреннего применения.|  
|subscriber_number|**int**|Только для внутреннего применения.|  
|last_makegeneration_datetime|**datetime**|Последний **datetime** , процесс makegeneration запущен для издателя. Дополнительные сведения см. в разделе параметра - MakeGenerationInterval в [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
