---
title: Удаление таблиц из запросов (визуальные инструменты для базы данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0e0c7ef00a4ccd8a2c5299760b34ff348da689f3
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984006"
---
# <a name="remove-tables-from-queries-visual-database-tools"></a>Удаление таблиц из запросов (визуальные инструменты для базы данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Из запроса можно удалить таблицу или любой возвращающий табличное значение объект.  
  
> [!NOTE]  
> Удаление таблицы или возвращающего табличное значение объекта из текущего запроса не приводит к их удалению из базы данных. Дополнительные сведения об удалении таблицы из базы данных см. в разделе [Практическое руководство: удаление таблиц из базы данных (визуальные инструменты для баз данных)](http://msdn.microsoft.com/ca6aa3e9-9885-44c3-bafc-aec441fd97ec).  
  
### <a name="to-remove-a-table-or-table-structured-object"></a>Удаление таблицы или табличного объекта  
  
-   На **панели диаграммы**выберите таблицу, представление, определяемую пользователем функцию, синоним или запрос и нажмите клавишу DELETE, либо щелкните объект правой кнопкой мыши и в контекстном меню выберите команду **Удалить** . Можно выбрать и одновременно удалить несколько объектов.  
  
    –или–  
  
-   Удалите все ссылки на объект на **панели SQL**.  
  
При удалении таблицы или возвращающего табличное значение объекта конструктор запросов и представлений автоматически удаляет все включающие их соединения и ссылки на столбцы объектов на **панели SQL** и **панели критериев**. Однако если запрос содержит сложные выражения, включающие объект, то он может быть автоматически удален только после удаления всех ссылок на него.  
  
## <a name="see-also"></a>См. также:  
[Добавление таблиц в запросы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md)  
[Создание псевдонимов таблицы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-table-aliases-visual-database-tools.md)  
[Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
