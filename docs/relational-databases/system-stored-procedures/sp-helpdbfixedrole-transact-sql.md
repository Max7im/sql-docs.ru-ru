---
title: sp_helpdbfixedrole (Transact-SQL) | Документация Майкрософт
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
- sp_helpdbfixedrole
- sp_helpdbfixedrole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdbfixedrole
ms.assetid: ad87e9a0-b901-4e37-9950-aa517d680fc3
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 387ea35ed6e2c6be10eb738e0c53f26bbbbf60da
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022096"
---
# <a name="sphelpdbfixedrole-transact-sql"></a>sp_helpdbfixedrole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список всех предопределенных ролей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdbfixedrole [ [ @rolename = ] 'role' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@rolename =** ] **"***роли***"**  
 Имя предопределенной роли базы данных. *роль* — **sysname**, значение по умолчанию NULL. Если *роли* будет указан, возвращаются только сведения об этой роли; в противном случае возвращается список и описание всех предопределенных ролей базы данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**DbFixedRole**|**sysname**|Имя предопределенной роли базы данных.|  
|**Описание**|**nvarchar(70)**|Описание **DbFixedRole.**|  
  
## <a name="remarks"></a>Примечания  
 Предопределенные роли базы данных, как показано в таблице, определены на уровне базы данных и обладают специальными разрешениями для выполнения определенных административных функций. Предопределенные роли базы данных не могут быть добавлены или удалены. Нельзя изменить разрешения, предоставленные предопределенной роли базы данных.  
  
|Предопределенная роль базы данных|Описание|  
|-------------------------|-----------------|  
|**db_owner**|Владельцы базы данных|  
|**db_accessadmin**|Администраторы доступа к базе данных|  
|**db_securityadmin**|Администраторы безопасности базы данных|  
|**db_ddladmin**|Администраторы DDL базы данных|  
|**db_backupoperator**|Операторы резервного копирования базы данных|  
|**db_datareader**|Модули чтения данных из базы данных|  
|**db_datawriter**|Модули записи данных в базу данных|  
|**db_denydatareader**|Модули чтения данных из базы данных, которым отказано в доступе|  
|**db_denydatawriter**|Модули записи данных в базу данных, которым отказано в доступе|  
  
 Следующая таблица показывает хранимые процедуры, которые используются для изменения ролей базы данных.  
  
|Хранимая процедура|Действие|  
|----------------------|------------|  
|**sp_addrolemember**|Добавляет пользователя базы данных к предопределенной роли базы данных.|  
|**sp_helprole**|Возвращает список всех членов предопределенной роли базы данных.|  
|**sp_droprolemember**|Удаляет член из предопределенной роли базы данных.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
 Полученные данные подлежат ограничениям на доступ к метаданным. Сущности, на которые участник не имеет разрешения, не показаны. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
 Следующий пример иллюстрирует получение списка всех предопределенных ролей базы данных.  
  
```  
EXEC sp_helpdbfixedrole;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Хранимая процедура sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_dbfixedrolepermission &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbfixedrolepermission-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
