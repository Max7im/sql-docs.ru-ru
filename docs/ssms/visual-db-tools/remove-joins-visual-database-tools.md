---
title: "Удаление соединений (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6c7c9503f8b2edd9dce534e2c7a4caed659add86
ms.contentlocale: ru-ru
ms.lasthandoff: 08/18/2017

---
# <a name="remove-joins-visual-database-tools"></a>Удаление соединений (визуальные инструменты для баз данных)
Если нежелательно, чтобы таблицы были соединены с помощью внутреннего или внешнего соединения, можно удалить это соединение между таблицами. Например, можно удалить соединение, автоматически созданное между двумя таблицами в [конструкторе запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) .  
  
> [!NOTE]  
> Удаление соединения из запроса не влияет на базовые связи, существующие в базе данных.  
  
Если две соединяемые таблицы являются частью запроса и все условия соединения между ними удаляются, то результирующий запрос становится пересечением этих таблиц, то есть перекрестным соединением (CROSS JOIN).  
  
### <a name="to-remove-a-join"></a>Удаление соединения  
  
-   На [панели диаграммы](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)выберите удаляемую линию соединения и нажмите клавишу DELETE. Можно одновременно выбрать и удалить несколько линий соединений.  
  
Конструктор запросов и представлений удаляет линию соединения и изменяет инструкцию на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>См. также:  
[Автоматическое соединение таблиц (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)  
[Соединение таблиц вручную (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md)  
[Запросы с соединениями (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
