---
title: Просмотр сохраненной трассировки (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: sql-trace
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
caps.latest.revision: 22
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e65a80b3ec4b344cbd20e249c7184bfc6926b07b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38061692"
---
# <a name="view-a-saved-trace-transact-sql"></a>просмотреть сохраненную трассировку (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе разъясняется, как использовать встроенные функции для просмотра сохраненных трассировок.  
  
### <a name="to-view-a-specific-trace"></a>Просмотр конкретной трассировки  
  
1.  Выполните функцию **fn_trace_getinfo** , указав идентификатор трассировки, сведения о котором необходимо получить. Данная функция возвращает таблицу, в которой перечислены трассировка, свойство трассировки и сведения об этом свойстве.  
  
     Запустите функцию следующим способом:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### <a name="to-view-all-existing-traces"></a>Просмотр всех существующих трассировок  
  
1.  Выполните функцию **fn_trace_getinfo** , указав значения `0` или `default`. Данная функция возвращает таблицу, в которой перечислены все трассировки, свойства трассировок и сведения об этих свойствах.  
  
     Функция вызывается следующим образом:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## <a name="net-framework-security"></a>Безопасность .NET Framework  
 Для выполнения встроенной функции **fn_trace_getinfo**пользователю требуются следующие разрешения:  
  
 ALTER TRACE на сервере.  
  
## <a name="see-also"></a>См. также:  
 [sys.fn_trace_getinfo (Transact-SQL)](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Просмотр и анализ трассировок с помощью приложения SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  
