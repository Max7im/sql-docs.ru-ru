---
title: sp_testlinkedserver (Transact-SQL) | Документация Майкрософт
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
- sp_testlinkedserver
- sp_testlinkedserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_testlinkedserver
ms.assetid: e63ca7d4-47d6-455e-9aac-421f9683dadc
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b03253014b198a83d2c9516fd7fa3e09ce16fbab
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032804"
---
# <a name="sptestlinkedserver-transact-sql"></a>sp_testlinkedserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Проверяет соединение со связанным сервером. Если проверка завершилась неуспешно, то процедура вызывает исключение с указанием причины сбоя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_testlinkedserver [ @servername ] = servername  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@servername =** ]*servername*  
 Имя связанного сервера. *ServerName* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Разрешения не проверяются, однако у вызывающего объекта должно быть соответствующее сопоставление имени входа.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается связанный сервер с именем `SEATTLESales` и тестируется соединение.  
  
```  
USE master;  
GO  
EXEC sp_addlinkedserver   
    'SEATTLESales',  
    N'SQL Server';  
GO  
sp_testlinkedserver SEATTLESales;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addlinkedsrvlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)  
  
  
