---
title: sp_cycle_agent_errorlog (Transact-SQL) | Документы Microsoft
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
- sp_cycle_agent_errorlog
- sp_cycle_agent_errorlog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cycle_agent_errorlog
ms.assetid: 8aa96182-60b7-4d7b-b2a7-ccce70378c6e
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 74b0bc568dfa883b6b2eb4c6b19fcf3a38512e9e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33238015"
---
# <a name="spcycleagenterrorlog-transact-sql"></a>sp_cycle_agent_errorlog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Закрывает текущий файл журнала ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и циклически меняет номера расширений журнала ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], как при перезапуске системы. Новый журнал ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит строку, указывающую на создание нового журнала.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cycle_agent_errorlog  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Каждый раз [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент запускается, текущий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнала ошибок агента переименовывается в **SQLAgent.1**; **SQLAgent.1** становится **SQLAgent.2**, **SQLAgent.2** становится **SQLAgent.3**, и т. д. **sp_cycle_agent_errorlog** позволяет Зацикливать файлы журналов ошибок без остановки и запуска сервера.  
  
 Эта хранимая процедура должна запускаться из **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение **sp_cycle_agent_errorlog** , ограничены членами **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 На следующем примере показано, как производится циклическое переименование журнала ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_cycle_agent_errorlog ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_cycle_errorlog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql.md)  
  
  
