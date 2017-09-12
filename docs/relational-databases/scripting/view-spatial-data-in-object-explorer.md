---
title: "Просмотр пространственных данных в обозревателе объектов | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c5757bcb84f441e81f3da7b91e6acf449696cc30
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="view-spatial-data-in-object-explorer"></a>Просмотр пространственных данных в обозревателе объектов
  Окно **Пространственные результаты** в редакторе запросов содержит визуальные средства сопоставления для просмотра результатов запроса к пространственным данным в дополнение к данным, отображаемых в формате сетки в окне **Результаты** . Чтобы пространственные данные отображались в окне **Пространственные результаты** , результаты запроса должны содержать по крайней мере один столбец пространственных данных с данными геометрического или географического типа.  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a>Просмотр пространственных данных в окне «Пространственные результаты»  
  
1.  Перейдите на вкладку **Пространственные результаты** в редакторе запросов.  
  
    > [!NOTE]  
    >  Это окно будет недоступно, если в результаты запроса не входят пространственные данные или если задано возвращение результатов в виде текста.  
  
2.  Выберите в списке **Выберите пространственный столбец** столбец для просмотра. Если в таблице присутствует только один пространственный столбец, он будет выбираться в списке по умолчанию.  
  
3.  В списке **Выберите столбцы меток** выберите непространственный столбец для использования в качестве меток данных.  
  
4.  В списке **Выберите проекцию** выберите проекцию для географических данных. По умолчанию используется проекция Equirectangular. Также доступны проекции Mercator, Robinson и Bonne.  
  
    > [!NOTE]  
    >  Список**Выберите проекцию** недоступен, если пространственный столбец содержит геометрические данные.  
  
5.  Чтобы увеличить отображаемый размер сопоставленных элементов, передвиньте ползунок **Масштаб** . Для фигур-многоугольников метка будет видима только в случае, если фигура достаточно велика, чтобы вместить текст метки.  
  
## <a name="see-also"></a>См. также:  
 [Окно «Пространственные результаты»](../../relational-databases/scripting/spatial-results-window.md)   
 [Редактор запросов компонента Database Engine (среда SQL Server Management Studio)](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Редакторы запросов и текста (SQL Server Management Studio)](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  