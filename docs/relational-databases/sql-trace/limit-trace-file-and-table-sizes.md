---
title: "Ограничение размеров файла и таблицы трассировки | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum file size for traces
- traces [SQL Server], file size
- size [SQL Server], tables
- file rollover option [SQL Server]
- size [SQL Server], files
ms.assetid: 88c31b02-f44c-4a14-be8b-437f2097de12
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 88ac44b6c82349c1c0294a512a24ffacd6002ad3
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="limit-trace-file-and-table-sizes"></a>Ограничение размеров файла и таблицы трассировки
  Результаты трассировки SQL могут иметь различный размер в зависимости от того, какие классы событий включены в трассировку и каким образом был использован компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Если производится трассировка часто происходящих классов событий, объем собираемых данных может быть уменьшен путем установки максимального размера файла или максимального числа строк. Указывая максимальный размер файла или максимальное число строк, можно гарантировать, что файл или таблица трассировки не превысят указанные размеры.  
  
> [!NOTE]  
>  Если данные трассировки сохраняются в уже существующем файле, можно добавить данные в файл или перезаписать файл. Если данные добавляются в файл, а файл трассировки уже имеет или превышает заданный максимальный размер, будет показано уведомление и будет предложено либо увеличить максимальный размер файла, либо выбрать новый файл. Это верно и для таблиц трассировки.  
  
## <a name="maximum-file-size"></a>Максимальный размер файла  
 Трассировка, для которой указан максимальный размер файла, прекращает сохранять трассировочные сведения после того, как максимальный размер файла достигнут. Этот параметр позволяет группировать события в меньшие, более удобные для управления файлы. Кроме того, ограничение размера файла делает более безопасным запуск автоматических трассировок, так как трассировка прекращается по достижении максимального размера файла. Максимальный размер файла может быть установлен для трассировок, созданных как посредством хранимых процедур языка Transact-SQL, так и при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 Существует верхняя граница для параметра максимального размера файла, равная 1 гигабайт (ГБ). По умолчанию максимальный размер файла равен 5 мегабайт (МБ).  
  
### <a name="enabling-file-rollover"></a>Включение операции переключение на файл продолжения  
 Если выбран параметр «операция переключения на файл продолжения», то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] закрывает текущий файл, как только он достигнет максимального размера, а затем создает новый файл. Новый файл имеет такое же имя, что и предыдущий файл, но к нему добавляется целое число для указания последовательности. Например, если оригинальный файл трассировки имел имя «filename_1.trc», следующий файл трассировки будет иметь имя «filename_2.trc» и т.д. Если имя, присвоенное новому файлу продолжения, уже используется существующим файлом, существующий файл будет перезаписан, если не является файлом только для чтения. Параметр «операция переключения на файл продолжения» устанавливается автоматически при сохранении данных трассировки в файл.  
  
> [!NOTE]  
>  Если параметр «операция переключения на файл продолжения» включен, то трассировка будет продолжаться до тех пор, пока не будет остановлена другими средствами. Чтобы трассировка останавливалась по достижении максимального размера файла, отключите параметр «операция переключения на файл продолжения».  
  
 **Указание максимального размера файла трассировки**  
  
 [Установить максимальный размер для файла трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
## <a name="maximum-number-of-rows"></a>Максимальное число строк  
 Трассировка с заданным максимальным числом строк прекращает сохранять трассировочные сведения по достижении таблицей максимального числа строк. Каждое событие создает одну строку, поэтому этот параметр устанавливает границу числа собранных событий. Установка максимального числа строк упрощает выполнение автоматических трассировок. Например, если необходимо запустить трассировку, которая сохраняет данные трассировки в таблицу, но желательно прекратить трассировку, когда таблица становится слишком большой, это может быть сделано автоматически.  
  
 Если указано максимальное число строк и таблица содержит количество строк, равное максимальному числу строк, трассировка продолжает выполняться, пока выполняется приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , но сведения трассировки больше не записываются. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] результаты трассировки продолжают отображаться до завершения трассировки.  
  
 **Установка максимального числа строк для трассировки**  
  
 [Установить максимальный размер для таблицы трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_create (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)  
  
  