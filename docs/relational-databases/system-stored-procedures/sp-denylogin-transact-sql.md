---
title: Хранимая процедура sp_denylogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_denylogin_TSQL
- sp_denylogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_denylogin
ms.assetid: db80f152-e8af-4303-95b6-3a3a7b664374
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 39a33d466b06b070bb3fcf1e47a99b8e296c2a87
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031412"
---
# <a name="spdenylogin-transact-sql"></a>sp_denylogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предотвращает подключение пользователя или группы Windows к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_denylogin [ @loginame = ] 'login'   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@loginame =** ] **"*** входа* **"**  
 Имя пользователя или группы Windows. *Имя входа* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_denylogin** запрещается разрешение CONNECT SQL участникам уровня сервера на сопоставляется с указанного пользователя Windows или группы Windows. Если сервер-участник не существует, он будет создан. Новый участник будет отображаться в [sys.server_principals &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) представления каталога.  
  
 **sp_denylogin** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как использовать **sp_denylogin** во избежание пользователя Windows `CORPORATE\GeorgeV` подключаться к серверу.  
  
```  
EXEC sp_denylogin 'CORPORATE\GeorgeV';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_grantlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN (Transact-SQL)](../../t-sql/statements/alter-login-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
