---
title: 'Устранение неполадок: превышение RTO в группе доступности (SQL Server) | Документы Майкрософт'
ms.custom: ag-guide
ms.date: 06/13/2017
ms.prod: sql-server-2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e83e4ef8-92f0-406f-bd0b-dc48dc210517
caps.latest.revision: 7
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: a70d141800d9d8d43d47f0703d64e03505015aa4
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2018
---
# <a name="troubleshoot-availability-group-exceeded-rto"></a>Устранение неполадок: превышение RTO в группе доступности
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  После автоматического перехода на другой ресурс или планового перехода на другой ресурс вручную без потери данных в группе доступности можно обнаружить, что время перехода на другой ресурс превышает цель времени восстановления (RTO). Или при оценке времени перехода на другой ресурс для вторичной реплики с синхронной фиксацией (например, партнера по обеспечению автоматической отработки отказа) с использованием метода, описанного в разделе [Мониторинг производительности для групп доступности AlwaysOn](monitor-performance-for-always-on-availability-groups.md), вы обнаруживаете, что оно превышает RTO.  
  
 Если автоматический переход на другой ресурс все еще не завершен, см. раздел [Устранение неполадок автоматического перехода на другой ресурс в средах AlwaysOn SQL Server 2012](http://support.microsoft.com/kb/2833707).  
  
 Следующие разделы описывают распространенные причины того, что время перехода на другой ресурс превышает RTO.  
  
1.  [Рабочая нагрузка отчетов блокирует запуск потока повтора](#BKMK_REDOBLOCK)  
  
2.  [Поток повтора запаздывает из-за состязания ресурсов](#BKMK_CONTENTION)  
  
##  <a name="BKMK_REDOBLOCK"></a> Рабочая нагрузка отчетов блокирует запуск потока повтора  
 Поток повтора на вторичной реплике не может вносить изменения на языке описания данных DDL из-за блокировки со стороны длительного запроса только для чтения.  
  
### <a name="explanation"></a>Объяснение  
 Во вторичной реплике запросы только для чтения получают блокировки стабилизации схемы (`Sch-S`). Эти блокировки `Sch-S` могут мешать потоку повтора получать блокировки изменения схемы (`Sch-M`) для внесения изменений DDL. Заблокированный поток повтора не может применять записи журнала до разблокировки. После разблокировки он может продолжить работу с конца журнала, позволяя выполнить последующий процесс отмены и перехода на другой ресурс.  
  
### <a name="diagnosis-and-resolution"></a>Диагностика и способ устранения  
 Когда поток повтора заблокирован, создается расширенное событие `sqlserver.lock_redo_blocked`. Кроме того, можно запросить динамическое административное представление sys.dm_exec_request во вторичной реплике, чтобы узнать, какой сеанс блокирует поток повтора, чтобы затем предпринять корректирующее действие. Приведенный ниже запрос возвращает идентификатор сеанса запроса только для чтения, блокирующего поток повтора.  
  
```sql  
select session_id, command, blocking_session_id, wait_time, wait_type, wait_resource   
from sys.dm_exec_requests where command = 'DB STARTUP'  
```  
  
 Вы можете дождаться окончания рабочей нагрузки отчетов, после чего поток повтора разблокируется, или сразу же разблокировать этот поток, выполнив команду [KILL (Transact-SQL)](~/t-sql/language-elements/kill-transact-sql.md) по идентификатору сеанса блокировки.  
  
##  <a name="BKMK_CONTENTION"></a> Поток повтора запаздывает из-за состязания ресурсов  
 Большая рабочая нагрузка отчетов на вторичной реплике замедлила работу вторичной реплики, и поток повтора запаздывает.  
  
### <a name="explanation"></a>Объяснение  
 При применении записей журнала на вторичной реплике поток повтора считывает записи журнала с диска журнала, а затем для каждой записи журнала он обращается к страницам данных, чтобы применить эту запись. Обращение к странице может быть привязано к вводу-выводу (доступ к физическому диску), если данная страница еще не находится в буферном пуле. Если имеется рабочая нагрузка отчетов, привязанная к вводу-выводу, она конкурирует за ресурсы ввода-вывода с потоком повтора и может замедлить его работу.  
  
### <a name="diagnosis-and-resolution"></a>Диагностика и способ устранения  
 Вы можете использовать приведенный ниже запрос динамического административного представления, чтобы узнать, насколько сильно отстает поток повтора, измерив разницу между `last_redone_lsn` и `last_received_lsn`.  
  
```sql  
select recovery_lsn, truncation_lsn, last_hardened_lsn, last_received_lsn,   
   last_redone_lsn, last_redone_time  
from sys.dm_hadr_database_replica_states  
  
```  
  
 Если поток повтора на самом деле запаздывает, нужно исследовать первопричину снижения производительности на вторичной реплике. Если присутствует состязание ввода-вывода с рабочей нагрузкой отчетов, можно использовать [Resource Governor](~/relational-databases/resource-governor/resource-governor.md) для управления циклами ЦП, которые рабочая нагрузка отчетов использует для косвенного управления использованными циклами ввода-вывода. Например, если рабочая нагрузка отчетов использует 10 процентов ресурсов ЦП, но она привязана к вводу-выводу, можно с помощью Resource Governor ограничить использование ресурсов ЦП на 5 процентов для регулирования рабочей нагрузки чтения, что минимизирует влияние на операции ввода-вывода.  
  
## <a name="next-steps"></a>Следующие шаги  
 [Устранение проблем с производительностью в SQL Server (применяется к SQL Server 2012)](http://msdn.microsoft.com/library/dd672789(v=SQL.100).aspx)  
  
  