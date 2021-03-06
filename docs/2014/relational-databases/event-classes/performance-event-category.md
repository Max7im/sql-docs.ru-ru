---
title: Категория событий Performance | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6fc0cc35e44386189a3692133b5c31e2b47098bb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37195386"
---
# <a name="performance-event-category"></a>Категория событий Performance
  Категория событий **Performance** используется для контроля классов событий **Showplan** и классов событий, формируемых при выполнении операторов SQL языка DML.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий Auto Stats](auto-stats-event-class.md)|Указывает, что произошло автоматическое обновление статистики индекса и столбца.|  
|[Класс событий Degree of Parallelism (используется с версией 7.0)](degree-of-parallelism-7-0-insert-event-class.md)|Указывает, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкции SELECT, INSERT, UPDATE или DELETE были выполнены с использованием последовательного или параллельного плана. В отчет также включается количество ЦП, использованных для выполнения операции.|  
|[Класс событий Performance Statistics](performance-statistics-event-class.md)|Наблюдает за производительностью выполняемых запросов.|  
|[Класс событий Showplan All](showplan-all-event-class.md)|Идентифицирует операторы **Showplan** в инструкции SQL.|  
|[Класс событий Showplan All for Query Compile](showplan-all-for-query-compile-event-class.md)|Отображает данные компиляции для операторов **Showplan** .|  
|[Класс событий Showplan Statistics Profile](showplan-statistics-profile-event-class.md)|Отображает предполагаемую стоимость запроса.|  
|[Класс событий Showplan XML](showplan-xml-event-class.md)|Идентифицирует операторы **Showplan** в инструкции SQL. Класс событий хранит описание каждого события как правильный XML-документ.|  
|[Класс событий Showplan XML for Query Compile](showplan-xml-for-query-compile-event-class.md)|Отображает данные компиляции для операторов **Showplan** в формате XML.|  
|[Класс событий Showplan XML Statistics Profile](showplan-xml-statistics-profile-event-class.md)|Идентифицирует операторы **Showplan** , связанные с инструкцией SQL. Выходом является XML-документ.|  
|[Класс событий SQL:FullTextQuery](sql-fulltextquery-event-class.md)|Указывает на то, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершил выполнение полнотекстового запроса.|  
|[Класс событий Plan Guide Successful](plan-guide-successful-event-class.md)|Указывает, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] успешно создан план выполнения для запроса или пакета, в котором содержится структура плана.|  
|[Класс событий Plan Guide Unsuccessful](plan-guide-unsuccessful-event-class.md)|Указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось создать план выполнения для запроса или пакета, в котором содержится структура плана.|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)  
  
  
