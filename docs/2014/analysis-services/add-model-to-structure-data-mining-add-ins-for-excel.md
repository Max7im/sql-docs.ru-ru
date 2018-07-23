---
title: Добавление модели к структуре (надстройки интеллектуального анализа для Excel данных) | Документация Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models, creating
ms.assetid: 8efd5bf4-4e6a-4ee8-971a-6efaed5f3b76
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 71016faaac6126328e1565ef7644fcf0bdf74376
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241764"
---
# <a name="add-model-to-structure-data-mining-add-ins-for-excel"></a>Добавление модели к структуре (надстройки интеллектуального анализа данных для Excel)
  ![Добавление модели к структуре кнопку](media/dmc-addmodel.gif "добавления модели к структуре кнопки")  
  
 При нажатии кнопки **добавить модель к структуре**, запускается мастер, поможет вам создать новую модель интеллектуального анализа данных для использования с существующей структуры интеллектуального анализа данных. Это удобно, поскольку можно будет сравнить модели, основанные на одних данных, либо создать пользовательские модели.  
  
 Если экземпляр служб Analysis Services еще не содержит нужные данные, используйте [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41; ](create-mining-structure-sql-server-data-mining-add-ins.md) мастера для настройки структуры интеллектуального анализа данных. Можно также запустить один из мастеров моделирования и добавить новую модель в структуру, созданную мастером.  
  
 Для создания сложных моделей, с помощью алгоритмов, не поддерживаемых мастерами, создайте структуру интеллектуального анализа данных и затем добавьте модель с помощью **расширенный редактор запросов данных интеллектуального анализа данных**.  
  
## <a name="add-a-new-model-to-an-existing-structure"></a>Добавление новой модели в существующую структуру  
  
1.  На **интеллектуального анализа данных** ленты, щелкните стрелку под кнопкой **Дополнительно**, а затем выберите **добавить модель к структуре**.  
  
2.  В **Выбор структуры** диалоговом окне выберите структуру, содержащую данные, которые вы хотите использовать и нажмите кнопку **Далее**.  
  
     **Совет**: Если вы не уверены, какая структура интеллектуального анализа данных содержит нужные данные, используйте **модели документов** мастера для просмотра столбцов и базовую статистику о данных.  
  
     Если не удается найти структуру интеллектуального анализа данных, проверьте используемое соединение. Возможно, необходимо будет установить соединение с другим сервером.  
  
3.  В **выберите алгоритм интеллектуального анализа данных** диалоговом окне выберите алгоритм интеллектуального анализа данных для использования в новой модели интеллектуального анализа данных.  
  
     Обратите внимание, что диалоговое окно предоставляет гораздо больше параметров, чем обычно можно увидеть в мастерах. Модель можно создать на основе любого алгоритма, поддерживаемого на сервере служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], при условии совместимости данных.  
  
4.  Рекомендуется нажать кнопку **параметры** кнопку, чтобы открыть **параметры алгоритма** диалоговое окно и настроить параметры алгоритма. Этот режим представляет собой самый простой способ создания пользовательских моделей интеллектуального анализа данных.  
  
5.  Нажмите кнопку **Далее**.  
  
6.  В **Выбор столбцов** диалоговом окне просмотрите список столбцов и при необходимости измените назначение столбцов на одно из следующих значений:  
  
    -   **Входные данные**. Указывает, что столбец содержит переменные, которые влияют на результат и должны использоваться в качестве входных данных для модели.  
  
    -   **Входные данные и прогноз**. Указывает, что данные должны использоваться в качестве входных данных, а также что именно эти значения нужно спрогнозировать.  
  
    -   **Только прогноз**. Указывает, что данные не должны использоваться в качестве входных данных для модели.  
  
    -   **Key**. Для каждой модели требуется по крайней мере один ключ. В зависимости от типа модели, может также имеется возможность Дополнительные специальные ключи, такие как **SequenceKey** или **TimeKey**.  
  
    -   **Не используйте**. Указывает, что данные не должны использоваться в модели, даже если они присутствуют в структуре.  
  
7.  Нажмите кнопку обзора **(...)**  кнопку, чтобы открыть **Установка флагов столбцов модели** диалоговое окно.  
  
     Убедитесь, что использование каждого столбца данных подходит для этой модели. Это важный шаг, который позволит предотвратить ошибки во время обработки модели.  
  
     Например, если повторно использовать структуру, созданную для моделей на основе дерева принятия решений, и применить упрощенный алгоритм Байеса, столбцы с типом данных `Numeric` и типом содержимого `Continuous` нужно будет сгруппировать или заменить на дискретные переменные.  
  
     Если столбцы в структуре не применяются в новом алгоритме, их можно обойти, выбрав **не используйте**.  
  
8.  В **Установка флагов столбцов модели** диалоговое окно, просмотрите или установите флаги моделирования, если таковые имеются.  
  
     Флаги моделирования позволяют управлять среди прочего обработкой значений NULL. Дополнительные сведения см. в разделе [Флаги моделирования (интеллектуальный анализ данных)](data-mining/modeling-flags-data-mining.md).  
  
     Нажмите кнопку **ОК** при Готово, чтобы закрыть диалоговое окно.  
  
9. В **Готово** диалогового окна введите имя и описание для новой модели интеллектуального анализа данных.  
  
     В зависимости от созданного типа модели возможны следующие варианты.  
  
    -   Найдите готовую модель интеллектуального анализа данных после ее построения.  
  
    -   Воспользуйтесь детализацией углублением из модели до исходных данных.  
  
         Дополнительные сведения см. в разделе [детализацию для модели интеллектуального анализа данных](data-mining/drillthrough-on-mining-models.md).  
  
10. Нажмите кнопку **Готово** для сохранения изменений. После этого новая модель будет развернута на сервере и обработана.  
  
### <a name="related-options"></a>Связанные параметры  
  
|Параметр|Комментарии|  
|------------|--------------|  
|**Выбрать структуру или модель** диалоговое окно|Выберите существующую структуру интеллектуального анализа данных, которая будет использоваться в качестве основы для построения новой модели.  Выбранная структура должна находиться в текущем соединении. Если это не так, измените соединение с помощью [подключение к данным источника &#40;клиент интеллектуального анализа данных для Excel&#41; ](connect-to-source-data-data-mining-client-for-excel.md) средство.|  
|**Выберите алгоритм интеллектуального анализа данных** диалоговое окно|Список алгоритмов интеллектуального анализа данных зависит от подключения к серверу. В выпусках Standard и Enterprise служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] есть различные алгоритмы. Системный администратор также может добавлять пользовательские алгоритмы.<br /><br /> Если ни одного алгоритма не видно, убедитесь, что установлено подключение к экземпляру служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|**Параметры алгоритма** диалоговое окно|С помощью этих параметров можно настроить каждый алгоритм, задавая параметры, относящиеся к аналитическому методу. Также можно задать начальное значение, чтобы результаты моделей можно было воспроизвести в разных обучающих проходах.<br /><br /> Дополнительные сведения см. в разделе [параметры алгоритма &#40;SQL Server Data Mining Add-ins&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md).|  
|**Установка флагов столбцов модели** диалоговое окно|Флаги моделирования могут улучшить модель, поскольку указывают, каким образом следует обрабатывать отсутствующие данные. Дополнительные сведения см. в разделе [Флаги моделирования (интеллектуальный анализ данных)](data-mining/modeling-flags-data-mining.md).|  
  
###  <a name="Bkmk_mdlcolumn"></a> Задание типа использования столбца  
 При добавлении новой модели в существующую структуру интеллектуального анализа данных необходимо указать, как в этой модели будет использоваться каждый столбец данных из структуры интеллектуального анализа данных. Будет заметно, что параметры, приведенные в этом мастере, куда более подробные, чем параметры для структуры интеллектуального анализа данных. Почему?  
  
 Дело в том, что при одновременном создании модели и структуры с помощью мастера многие параметры, определяющие использование данных алгоритмом, задаются автоматически. Однако при добавлении новой модели в существующую необходимо просмотреть все параметры вручную и указать, следует ли использовать данные для анализа, верен ли тип данных и т. д.  
  
 Возможно получение сообщения об ошибке при применении новых алгоритмов к существующим данным, но эти сообщения обычно содержат подробные сведения о том, что нужно сделать, чтобы модель была обработана. Ниже рассматриваются типовые проблемы.  
  
-   Модель ожидает тип данных, отличный от того, который содержится в структуре.  
  
     Некоторые алгоритмы могут работать только с числами, другие — только с текстом. Если данные имеют неверный тип для новой модели, возможно, для обеспечения обработки модели необходимо будет изменить структуру.  
  
-   Структура интеллектуального анализа данных не содержит прогнозируемый атрибут.  
  
     Модели кластеризации можно построить без прогнозируемых значений. Однако для других моделей обычно необходимо указать один столбец для прогноза.  
  
-   Состав данных несовместим с выбранным алгоритмом.  
  
     Для некоторых типов анализа требуются данные, структурированные в соответствии с определенными правилами. Это касается моделей прогнозирования и взаимосвязей. Можно легко добавить новые модели схожего типа, возможно с изменениями, однако данные не будут работать с другими алгоритмами.  
  
### <a name="requirements"></a>Требования  
 Чтобы создать модель интеллектуального анализа данных, необходимо установить соединение с экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Дополнительные сведения о том, как создание или изменение соединения см. в разделе [подключение к данным источника &#40;клиент интеллектуального анализа данных для Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Если необходимая структура интеллектуального анализа данных недоступна для просмотра, она могла быть сохранена в другом экземпляре или в другой базе данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Сведения о том, как переключиться на другое соединение интеллектуального анализа, см. в разделе [соединиться с сервером интеллектуального анализа данных](connect-to-a-data-mining-server.md).  
  
## <a name="see-also"></a>См. также  
 [Создание модели интеллектуального анализа данных](creating-a-data-mining-model.md)   