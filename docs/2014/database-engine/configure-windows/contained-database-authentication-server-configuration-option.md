---
title: Параметр конфигурации сервера "проверка подлинности автономной базы данных" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- contained_database_authentication_TSQL
- contained database authentication
helpviewer_keywords:
- contained database, enabling
- contained database authentication option
ms.assetid: b80768d2-ac20-4035-a335-d9adb74b3f6e
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b39c50ae71206f923cb2e8a86ae570da010c7d40
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153055"
---
# <a name="contained-database-authentication-server-configuration-option"></a>Параметр конфигурации сервера «проверка подлинности автономной базы данных»
  Параметр **проверка подлинности автономной базы данных** позволяет включить автономные базы данных на экземпляре [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Данный параметр сервера позволяет управлять **проверкой подлинности автономной базы данных**.  
  
-   Если **проверка подлинности автономной базы данных** в экземпляре выключена (0), автономные базы нельзя создавать или присоединять к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   Если **проверка подлинности автономной базы данных** в экземпляре включена (1), автономные базы можно создавать или присоединять к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Автономная база данных содержит все параметры базы данных и метаданные, необходимые для определения базы данных, и не зависит от экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , где установлена базы данных. Пользователи могут соединяться с базой данных без проверки подлинности имени входа на уровне компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Если изолировать базу данных от компонента Database Engine, будет легко переместить эту базу данных на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Помещение всех параметров базы данных внутрь базы данных позволяет ее владельцу управлять всеми параметрами для этой базы данных. Дополнительные сведения об автономных базах данных см. в разделе [Автономные базы данных](../../relational-databases/databases/contained-databases.md).  
  
 Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит автономные базы данных, можно установить параметр **contained database authentication** в значение 0 с помощью инструкции **RECONFIGURE WITH OVERRIDE** . Значение параметра **contained database authentication** , равное 0, отключает проверку подлинности автономной базы данных для автономных баз данных.  
  
> [!IMPORTANT]  
>  При включении автономных баз данных базы данных пользователи с разрешением ALTER ANY USER, такие как члены роли базы данных db_owner или db_accessadmin, могут предоставлять доступ к базам данных и таким образом предоставлять доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это означает, что управление доступом к серверу больше не принадлежит только членам предопределенной роли сервера sysadmin и securityadmin и входам с разрешениями CONTROL SERVER и ALTER ANY LOGIN на уровне сервера. С использованием автономных баз данных связаны определенные риски. Дополнительные сведения см. в разделе [Security Best Practices with Contained Databases](../../relational-databases/databases/security-best-practices-with-contained-databases.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере в экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]создаются автономные базы данных.  
  
```tsql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)  
  
  
