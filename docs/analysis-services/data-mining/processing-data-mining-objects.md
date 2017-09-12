---
title: "Обработка объектов интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing objects [Analysis Services]
- mining structures [Analysis Services]
- process [Analysis Services]
- mining structures [Analysis Services], creating
- mining structures [Analysis Services], how-to topics
- mining structures [Analysis Services], processing
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c05c204eab305b42ddce4a3114cd9162a921c7b2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="processing-data-mining-objects"></a>Обработка объектов интеллектуального анализа данных
  До обработки объект интеллектуального анализа данных представляет собой просто пустой контейнер. *Обработка* модели интеллектуального анализа данных также называется *обучением*.  
  
 **Обработка структур интеллектуального анализа данных.** Структура интеллектуального анализа данных получает данные из внешнего источника, определенного в привязках столбцов и метаданных использования, и считывает данные. Эти данные считываются полностью и затем подвергаются анализу, чтобы получить различную статистику. Службы Analysis Services сохраняют в локальном кэше компактное представление данных, которое удобно для анализа, проводимого алгоритмами интеллектуального анализа данных. После обработки моделей этот кэш можно сохранить или удалить. По умолчанию кэш сохраняется. Дополнительные сведения см. в разделе [Обработка структуры интеллектуального анализа данных](../../analysis-services/data-mining/process-a-mining-structure.md).  
  
 **Обработка моделей интеллектуального анализа данных:** до обработки модель интеллектуального анализа данных пуста и содержит только определения. Чтобы обработать модель интеллектуального анализа данных, необходимо обработать структуру интеллектуального анализа данных, на которой основана модель. Модель интеллектуального анализа данных получает данные из кэша структуры интеллектуального анализа данных, применяет все фильтры, созданные для модели, а затем передает набор данных алгоритму, чтобы выявить закономерности. После обработки модели сохраняются только результаты обработки, но не сами данные. Дополнительные сведения см. в статье [Обработка модели интеллектуального анализа данных](../../analysis-services/data-mining/process-a-mining-model.md).  
  
 На следующей диаграмме показан поток данных во время обработки структуры интеллектуального анализа данных и во время обработки модели интеллектуального анализа данных.  
  
 ![Обработка данных: источник моделируемой структуры](../../analysis-services/data-mining/media/dmcon-modelarch.gif "обработка данных: источник моделируемой структуры")  
  
## <a name="viewing-the-results-of-processing"></a>Просмотр результатов обработки  
 После обработки структура интеллектуального анализа данных содержит компактное представление данных для использования в статистическом анализе. Если кэш не очищен, доступ к хранящимся в нем данным можно получить следующими способами.  
  
-   Создание запроса DMX-запроса к модели и детализация до уровня структуры. Дополнительные сведения см. в разделе [SELECT FROM &#60;модель&#62;.CASES (расширения интеллектуального анализа данных)](../../dmx/select-from-model-cases-dmx.md).  
  
-   Просмотр модели, основанной на структуре, и использование одного из параметров пользовательского интерфейса для детализации до вариантов структуры. Дополнительные сведения см. в разделе [Средства просмотра моделей интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-model-viewers.md)или [Детализация по данным вариантов из модели интеллектуального анализа данных](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md).  
  
-   Создание DMX-запроса к вариантам структуры. Дополнительные сведения см. в разделе [SELECT FROM &#60;структура&#62;.CASES](../../dmx/select-from-structure-cases.md).  
  
 Модель интеллектуального анализа данных после обработки содержит только закономерности, полученные во время анализа, и сопоставления результатов модели с обучающими данными в кэше. Можно просмотреть или запросить результаты модели, называемые *содержимым модели*, или запросить варианты модели и структуры, если они помещены в кэш.  
  
 Содержимое каждой модели интеллектуального анализа данных зависит от алгоритма, использованного для ее создания. Например, если одна модель является моделью кластеризации, а другая — моделью дерева принятия решений, содержимое моделей будет сильно различаться, несмотря на то, что модели используют совершенно идентичный набор данных. Дополнительные сведения см. в разделе [Содержимое модели интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
## <a name="processing-requirements"></a>Требования к обработке  
 Требования к обработке могут отличаться в зависимости от того, основана модель интеллектуального анализа данных только на реляционных данных или на источнике многомерных данных.  
  
 Для обработки источника реляционных данных требуется только создание данных для обучения и выполнения алгоритма интеллектуального анализа относительно этих данных. Но для моделей интеллектуального анализа, основанных на объектах OLAP, например для измерений и мер, базовые данные должны быть представлены в обработанном виде. Для этого может потребоваться обработка многомерных объектов для заполнения модели интеллектуального анализа данных.  
  
 Дополнительные сведения см. в разделе [Требования к обработке и связанные замечания (интеллектуальный анализ данных)](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
## <a name="see-also"></a>См. также:  
 [Запросы детализации (интеллектуальный анализ данных)](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [Структуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Модели интеллектуального анализа данных &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41;](../../analysis-services/data-mining/mining-models-analysis-services-data-mining.md)   
 [Логическая архитектура (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/logical-architecture-analysis-services-data-mining.md)  
  
  