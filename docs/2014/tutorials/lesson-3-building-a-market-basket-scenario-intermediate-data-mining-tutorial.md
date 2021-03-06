---
title: 'Занятие 3: Построение сценария потребительской корзины (учебник по интеллектуальному анализу интеллектуальному анализу данных) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- association algorithms [Analysis Services]
- nested tables
- tutorials [Data Mining]
ms.assetid: 651eef38-772e-4d97-af51-075b1b27fc5a
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0c03f8b54859a960479d78f1d0de7a0a30836347
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255126"
---
# <a name="lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial"></a>Занятие 3: Построение сценария потребительской корзины (учебник по интеллектуальному анализу интеллектуальному анализу данных)
  Отделу маркетинга [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] стремится к улучшениям веб-сайт компании для продвижения перекрестных продаж. После обновления сайт должен поддерживать создание модели интеллектуального анализа данных, которая позволит на основании текущего содержимого корзин заказов в сети прогнозировать, какие продукты клиенты хотели бы купить. Отделу маркетинга также требуется более глубокое понимание поведения клиента в процессе покупки, что позволит сгруппировать на веб-сайте те позиции, которые часто приобретаются вместе. Отдел маркетинга пришел к выводу, что интеллектуальный анализ данных может быть особенно полезен для этого типа *анализа потребительской корзины* , и попросил разработать соответствующую модель интеллектуального анализа данных.  
  
 После завершения задач этого занятия будет создана модель интеллектуального анализа данных, показывающая товары в группах по транзакциям клиентов за более ранние периоды. Кроме того, модель интеллектуального анализа данных можно использовать для прогнозирования дополнительных товаров, которые, возможно, захочет приобрести клиент.  
  
 Для выполнения задач этого занятия, следует использовать решение и источник данных, созданный на первом занятии [данных учебник по интеллектуальному анализу &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md). Решение будет изменено путем добавления представления источников данных с таблицами, касающимися заказчиков, в том числе с вложенной таблицей покупок заказчиков.  Затем будет построена модель интеллектуального анализа данных, использующая алгоритм правил взаимосвязей (Майкрософт), приспособленный для сценариев потребительских корзин.  
  
 Это занятие содержит следующие разделы:  
  
-   [Добавление данных источника представления с вложенными таблицами &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
-   [Создание структуры Market Basket и модели &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Изменение и обработка модели потребительской корзины &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
-   [Изучение модели Потребительская &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
-   [Фильтрование вложенной таблицы в модели интеллектуального анализа данных &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
-   [Прогноз взаимосвязей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Добавление данных источника представления с вложенными таблицами &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>Все занятия  
 [Урок 1: Создание промежуточного решения интеллектуального анализа &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Занятие 2: Построение сценария прогнозирования &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 Урок 3. Построение сценария покупательского поведения (учебник по интеллектуальному анализу данных — средний уровень)  
  
 [Занятие 4: Построение сценария кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [Занятие 5: Построение моделей логистической регрессии нейронной сети и &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Учебник интеллектуального анализа данных](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Занятие 2: Построение сценария прогнозирования &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)   
 [Занятие 4: Построение сценария кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
  
