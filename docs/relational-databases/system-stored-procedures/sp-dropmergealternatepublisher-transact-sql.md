---
title: Хранимая процедура sp_dropmergealternatepublisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
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
- sp_dropmergealternatepublisher
- sp_dropmergealternatepublisher_TSQL
helpviewer_keywords:
- sp_dropmergealternatepublisher
ms.assetid: a7dee4e2-2a60-41da-9d1d-6f991d7e2c5e
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c259f83b37577425764d2d0ea2325c5cc275dec2
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036857"
---
# <a name="spdropmergealternatepublisher-transact-sql"></a>Хранимая процедура sp_dropmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет альтернативный издатель из публикации слиянием. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropmergealaternatepublisher [ @publisher = ] 'publisher'    , [ @publisher_db = ] 'publisher_db'    , [ @publication = ] 'publication'    , [ @alternate_publisher = ] 'alternate_publisher'    , [ @alternate_publisher_db = ] 'alternate_publisher_db'    , [ @alternate_publication = ] 'alternate_publication'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=**] **"***издателя***"**  
 Имя текущего издателя. *издатель*— **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher_db=**] **"***publisher_db***"**  
 Имя текущей базы данных публикации. *publisher_db*— **sysname**, не имеет значения по умолчанию.  
  
 [  **@publication =**] **"***публикации***"**  
 Имя текущей публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@alternate_publisher=**] **"***alternate_publisher***"**  
 Имя альтернативного издателя, который будет удален как альтернативный участник синхронизации. *alternate_publisher*— **sysname**, не имеет значения по умолчанию.  
  
 [  **@alternate_publisher_db=**] **"***alternate_publisher_db***"**  
 Имя базы данных публикации, которая будет удалена как база данных публикации альтернативного участника синхронизации. *alternate_publisher_db*— **sysname**, не имеет значения по умолчанию.  
  
 [  **@alternate_publication=**] **"***alternate_publication***"**  
 Имя публикации, которая будет удалена как публикация альтернативного участника синхронизации. *alternate_publication*— **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **Хранимая процедура sp_dropmergealternatepublisher** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_dropmergelternatepublisher**.  
  
## <a name="see-also"></a>См. также  
 [sp_addmergealternatepublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergealternatepublisher-transact-sql.md)  
  
  
