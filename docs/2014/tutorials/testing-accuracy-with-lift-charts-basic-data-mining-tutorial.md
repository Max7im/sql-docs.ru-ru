---
title: Проверка точности при помощи диаграммы точности прогнозов (учебник интеллектуального анализа данных) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 822d414b-4a39-473f-80c3-53476e30655a
caps.latest.revision: 48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 864f255556063ea5011e3d3954294edcbdd9cb5b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37329006"
---
# <a name="testing-accuracy-with-lift-charts-basic-data-mining-tutorial"></a>Проверка точности при помощи диаграмм точности прогнозов (учебник интеллектуального анализа данных — начальный уровень)
  На **диаграмма точности интеллектуального анализа** вкладки конструктора интеллектуального анализа данных, можно вычислить, насколько хорошо каждой из моделей прогнозов и сравнить результаты каждой модели непосредственно с результатами других моделей. Этот метод сравнения называется *диаграмма точности прогнозов*. Обычно точность прогнозирования модели интеллектуального анализа данных определяется либо точностью предсказания, либо точностью классификации. В данном учебнике используются только диаграммы точности прогнозов.  
  
 В этом разделе будут выполнены следующие задачи:  
  
-   [Выберите входные данные](#BKMK_InputData)  
  
-   [Настройка параметров диаграммы точности](#BKMK_Selecting)  
  
##  <a name="BKMK_InputData"></a> Выбор входных данных  
 Первым шагом в проверке точности моделей интеллектуального анализа данных является выбор источника данных, который будет использоваться для проверки. Будет проверено, насколько хорошо работают модели на проверочных данных, а затем эти модели будут использованы с внешними данными.  
  
#### <a name="to-select-the-data-set"></a>Выбор набора данных  
  
1.  Переключиться в режим **диаграмма точности интеллектуального анализа** вкладку в конструкторе интеллектуального анализа данных в [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] и выберите **Выбор входа** вкладки.  
  
2.  В **Выбор набора данных для диаграммы точности** группы» — «select **использовать проверочные варианты структуры интеллектуального анализа данных**. Это проверочные данные которые резервировались при создании структуры интеллектуального анализа данных.  
  
     Дополнительные сведения о других параметрах см. в разделе [Выбор типа диаграммы точности и задание параметров диаграммы](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md).  
  
##  <a name="BKMK_Selecting"></a> Задание параметров диаграммы точности  
 Для создания диаграммы точности, необходимо определить три действия:  
  
-   Какие модели следует включить в диаграмму точности?  
  
-   Какие прогнозируемый атрибут будет измеряться? Некоторые модели могут иметь несколько целевых объектов, но каждая диаграмма можно оценить только один результат за раз.  
  
     Чтобы использовать столбец в качестве **Имя прогнозируемого столбца** в диаграмме точности, столбцы должны иметь тип использования `Predict` или `Predict Only`. Кроме того, тип содержимого целевой столбец должен быть либо `Discrete` или `Discretized`. Другими словами нельзя измерить точность для непрерывного числового выходов при помощи диаграммы точности прогнозов.  
  
-   Вы действительно хотите мер точности общие модели или определения точности прогноза определенное значение (например [Bike Buyer] = «Да»)  
  
#### <a name="to-generate-the-lift-chart"></a>Для создания диаграммы точности прогнозов.  
  
1.  На **Выбор входа** конструктора интеллектуального анализа данных в разделе **выбрать прогнозируемые столбцы интеллектуального анализа модели для отображения на диаграмме точности прогнозов**, установите флажок для **синхронизировать прогнозируемые столбцы и Значения**.  
  
2.  В **Имя прогнозируемого столбца** столбец, убедитесь, что **Bike Buyer** выбран для каждой модели.  
  
3.  В **Показать** столбец, выберите каждую из моделей.  
  
     По умолчанию выбраны все модели в структуре интеллектуального анализа данных. Можно выбрать любую из моделей, однако в данном учебнике следует оставить выбранными все модели.  
  
4.  В **прогнозируемое значение** столбец, выберите **1**. То же значение автоматически вводится для каждой модели, имеющей такой же прогнозируемый столбец.  
  
5.  Выберите **диаграмма точности прогнозов** вкладки.  
  
     При переходе на вкладку прогнозирующий запрос выполняется для получения прогнозов для проверочных данных, а результаты сравниваются относительно известных значений. Результаты выводятся в виде диаграммы.  
  
     Если указана с помощью определенного целевого результата **прогнозируемое значение** параметр, на диаграмме точности прогнозов отображает результаты случайного предположения, а результаты идеальной модели.  
  
    -   Случайный выбор строка показывает, насколько точна модель могла бы стать без использования все данные для информирования ее прогнозов: то есть разделения 50 на 50 одного из двух значений. На диаграмме точности прогнозов позволяет визуализировать, насколько лучше модель выполняет по сравнению со случайным предположением.  
  
    -   Линия идеальной модели представляет верхнюю границу точности. В нем показано максимальное возможных преимущество, которое можно получить, если модель точного прогноза.  
  
     Модели интеллектуального анализа данных, для которых вы создали будет обычно делятся между этими крайними. Любое повышение по сравнению со случайным предположением считается *точности прогнозов*.  
  
6.  Для нахождения линий, представляющих идеальную модель и модель случайного выбора, используйте условные обозначения.  
  
     Вы заметите, что `TM_Decision_Tree` модель обеспечивает максимальную точность прогноза, превосходят модели кластеризации и упрощенного алгоритма Байеса.  
  
 Подробное описание диаграммы точности прогнозов, подобной той, в этом занятии, см. в разделе [диаграмма точности прогнозов &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md).  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Проверка модели с фильтром &#40;учебник интеллектуального анализа данных&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Диаграмма точности прогнозов &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [Вкладка Диаграмма точности прогнозов &#40;интеллектуального анализа данных представление диаграммы точности&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)  
  
  
