---
title: "SQL Server, объект статистики пула ресурсов | Документация Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Reosurce Pool Stats object
- 'SQLServer: Resource Pool Stats object'
ms.assetid: bb46e029-fcf9-4aeb-a066-be41e7668fb9
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1ccd649e92cd416ff086758005f3b5df728dfe1d
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-resource-pool-stats-object"></a>SQL Server, объект Resource Pool Stats
  Объект SQLServer:Resource Pool Stats содержит счетчики производительности, сообщающие основные данные статистики пула ресурсов регулятора ресурсов.  
  
 Каждый активный пул ресурсов создает экземпляр объекта производительности SQLServer:Resource Pool Stats, при этом имя экземпляра совпадает с именем пула ресурсов в регуляторе ресурсов. В следующей таблице описываются счетчики, поддерживаемые этим экземпляром.  
  
|Имя счетчика|Description|  
|------------------|-----------------|  
|**Active memory grant amount (KB)**|Текущий суммарный объем предоставленной памяти, в килобайтах (КБ). Эта информация также доступна в представлении [sys.dm_exec_query_resource_semaphores](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql.md).| 
|**Active memory grants count**|Текущее общее количество операций по предоставлению памяти. Эта информация также доступна в представлении [sys.dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md).|  
|**Ср. вр. чт. с диска (мс)**|Среднее время (в миллисекундах) операции чтения с диска.|  
|**Средняя продолжительность операции чтения с диска, мс, базовая**|Только для внутреннего применения.|
|**Ср. вр. записи на диск (мс)**|Среднее время (мс) операции записи на диск.|  
|**Средняя продолжительность операции записи на диск, мс, базовая**|Только для внутреннего применения.|
|**Cache memory target (KB)**|Текущее значение целевого брокера памяти для кэширования, в килобайтах (КБ).|  
|**Compile memory target (KB)**|Текущее значение целевого брокера памяти для компиляции запросов, в килобайтах (КБ).|  
|**CPU control effect %**|Воздействие регулятора ресурсов на пул ресурсов. Рассчитывается по формуле: (Загрузка ЦП, %)/(Загрузка ЦП, %, без регулятора ресурсов).|  
|**Процент задержки ЦП**|Системные ЦП задерживаются для всех запросов в указанном экземпляре объекта производительности в процентах от общего времени активности.|
|**Базовый % задержки ЦП**|Только для внутреннего применения.|
|**Процент эффективной загрузки ЦП**|Загрузка системных ЦП всеми запросами в указанном экземпляре производительности в процентах от общего времени активности.|
|**База % эффективной загрузки ЦП**|Только для внутреннего применения.|
|**Загрузка ЦП, %**|Использование пропускной способности ЦП всеми группами рабочей нагрузки, принадлежащими данному пулу. Измеряется относительно рабочего компьютера и нормализуется по всем процессорам системы. Это значение будет изменено при изменении количества ЦП, доступных для процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Оно не нормализовано по отношению к значению, получаемому процессом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**Загрузка ЦП, база %**|Только для внутреннего применения.|
|**CPU usage target %**|Целевое значение параметра загрузки ЦП для пула ресурсов, рассчитанное на основании параметров конфигурации пула ресурсов и загрузки системы.|  
|**Процент нарушений ЦП**|Разница между резервированием ЦП и эффективным планированием в процентах.|
|**Байтов прочитано с диска/с**|Число байтов, прочитанных с диска в течение последней секунды.|  
|**Регулированных операций ввода-вывода чтения с диска/с**|Количество операций чтения, регулированных в течение последней секунды.|  
|**Операций чтения с диска/с**|Количество операций чтения с диска в течение последней секунды.| 
|**Скорость записи на диск (байт/сек)**|Число байтов, записанных на диск в течение последней секунды.|  
|**Регулированные операции ввода-вывода записи на диск/с**|Количество операций записи, регулированных в течение последней секунды.| 
|**Операции записи на диск/с**|Количество операций записи на диск в течение последней секунды.|
|**Max memory (KB)**|Максимальный объем памяти в килобайтах (КБ), которым может располагать пул ресурсов; рассчитывается на основе заданных параметров пула ресурсов и состояния сервера.| 
|**Memory grant timeouts/sec**|Количество операций предоставления памяти с истекшим временем ожидания за секунду.|
|**Memory grants/sec**|Число операций предоставления памяти, выполняемых в данном пуле ресурсов за одну секунду.| 
|**Pending memory grant count**|Число запросов на предоставление памяти, ожидающих в очереди. Эта информация также доступна в представлении [sys.dm_exec_query_resource_semaphores](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql.md).|
|**Query exec memory target (KB)**|Текущее значение целевого брокера памяти для предоставления памяти на выполнение запросов, в килобайтах (КБ). Эта информация также доступна в представлении [sys.dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md).|  
|**Target memory (KB)**|Целевой объем памяти, в килобайтах (КБ), который пул ресурсов пытается получить. Рассчитывается на основе заданных параметров пула ресурсов и состояния сервера.|   
|**Used memory (KB)**|Объем используемой памяти в пуле ресурсов, в килобайтах (КБ).|  

  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server, объект Workload Group Stats](../../relational-databases/performance-monitor/sql-server-workload-group-stats-object.md)   
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)  
  
  