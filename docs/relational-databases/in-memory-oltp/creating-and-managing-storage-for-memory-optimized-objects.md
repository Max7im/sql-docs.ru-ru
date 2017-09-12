---
title: "Создание и управление хранилищем для оптимизированных для памяти объектов | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 622aabe6-95c7-42cc-8768-ac2e679c5089
caps.latest.revision: 64
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2b955ffcf895f5356b77e0d772b3f1ac0cd9780e
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="creating-and-managing-storage-for-memory-optimized-objects"></a>Создание и управление хранилищем для оптимизированных для памяти объектов
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Механизм [!INCLUDE[hek_2](../../includes/hek-2-md.md)] интегрирован в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], что позволяет использовать оптимизированные для памяти таблицы и (традиционные) таблицы на диске в одной базе данных. Тем не менее структуры хранилища оптимизированных для памяти таблиц и таблиц на диске отличаются.  
  
 Хранилище для таблиц на диске имеет следующие ключевые атрибуты:  
  
-   Оно сопоставляется с файловой группой, которая содержит один или несколько файлов.  
  
-   Каждый файл делится на экстенты по 8 страниц, а каждая страница имеет размер 8 КБ.  
  
-   Экстент может совместно использоваться несколькими таблицами. Однако между выделенной страницей и таблицей или индексом устанавливается сопоставление "один к одному". Иными словами, страница не может содержать строки из двух или более таблиц или индексов.  
  
-   Данные перемещаются в память (буферный пул) по мере необходимости. Измененные или созданные страницы асинхронно записываются на диск, создавая произвольные операции ввода-вывода.  
  
 Хранилище оптимизированных для памяти таблиц имеет следующие ключевые атрибуты:  
  
-   Все оптимизированные для памяти таблицы сопоставляются с оптимизированной для памяти файловой группой данных. Эта файловая группа использует синтаксис и семантику, аналогичную файловому потоку.  
  
-   Страницы отсутствуют, а данные сохраняются в виде строки.  
  
-   Все изменения в оптимизированных для памяти таблицах сохраняются путем добавления в активные файлы. Операции чтения и записи в файлах выполняются последовательно.  
  
-   Обновление реализуется как операция удаления с последующей вставкой. Удаленные строки не удаляются из хранилища немедленно. Они удаляются фоновым процессом с именем MERGE на основе политики, как описано в статье [Устойчивость таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/durability-for-memory-optimized-tables.md).  
  
-   В отличие от таблиц на дисках, хранилище для оптимизированных для памяти таблиц не сжимается. При переносе сжатой таблицы на диске (ROW или PAGE) в оптимизированную для памяти таблицу необходимо учитывать изменение размера.  
  
-   Оптимизированные для памяти таблицы могут быть постоянными или временными. Хранилище нужно настраивать только для постоянных оптимизированных для памяти таблиц.  
  
 В этом разделе рассматриваются пары файлов контрольных точек и другие вопросы хранения оптимизированных для памяти таблиц.  
  
 Подразделы в этом разделе:  
  
-   [Настройка хранилища оптимизированных для памяти таблиц](../../relational-databases/in-memory-oltp/configuring-storage-for-memory-optimized-tables.md)  
  
-   [Оптимизированная для памяти файловая группа](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md)  
  
-   [Устойчивость таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/durability-for-memory-optimized-tables.md)  
  
-   [Работа контрольной точки для оптимизированных для памяти таблиц](../../relational-databases/in-memory-oltp/checkpoint-operation-for-memory-optimized-tables.md)  
  
-   [Определение устойчивости для оптимизированных для памяти объектов](../../relational-databases/in-memory-oltp/defining-durability-for-memory-optimized-objects.md)  
  
-   [Сравнение хранилища таблиц на диске с хранилищем таблиц оптимизированным для памяти](../../relational-databases/in-memory-oltp/comparing-disk-based-table-storage-to-memory-optimized-table-storage.md)  
  
## <a name="see-also"></a>См. также:  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  