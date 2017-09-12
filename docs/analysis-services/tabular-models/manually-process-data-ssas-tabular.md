---
title: "Обработка данных (табличные службы SSAS) вручную | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.datarefreshprogressdb.f1
ms.assetid: 0918c04c-c1e6-45b4-acfa-96fa578e684b
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6d421c1f625ee182497be3fbbff0c19f727f1a2b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="manually-process-data-ssas-tabular"></a>Обработка данных вручную (табличные службы SSAS)
  В этом разделе описан процесс обработки данных рабочей области вручную в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 При создании табличной модели, использующей внешние данные, данные можно обновить вручную с помощью команды «Обработать». Можно обработать одну таблицу, все таблицы, все таблицы в модели либо одну или несколько секций. Обработка данных может потребовать повторного вычисления данных.  Обработка данных означает получение последних данных из внешних источников. Повторное вычисление означает обновление результатов вычисления формул на основе этих данных.  
  
 Разделы данной темы:  
  
-   [Обработка данных вручную](#bkmk_mahually_process)  
  
-   [Ход обработки данных](#bkmk_data_process_progress)  
  
##  <a name="bkmk_mahually_process"></a> Обработка данных вручную  
  
#### <a name="to-process-data-for-a-single-table-or-all-tables-in-a-model"></a>Обработка данных для одной таблицы или всех таблиц в модели  
  
1.  В конструкторе моделей щелкните таблицу, которую необходимо обработать.  
  
2.  Выберите в меню **Модель** пункт **Обработать**, а затем пункт **Обработать** или **Обработать все**.  
  
#### <a name="to-process-data-for-all-tables-using-the-same-connection"></a>Обработка данных для всех таблиц, использующих одно соединение  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]выберите в меню **Модель** пункт **Существующие соединения**.  
  
2.  В диалоговом окне **Существующие соединения** выберите соединение и нажмите **Обработать**.  
  
#### <a name="to-process-data-for-one-or-more-partitions"></a>Обработка данных для одного или нескольких разделов  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]выберите в меню **Модель** пункт **Обработать**, а затем пункт **Обработать секции**.  
  
2.  В диалоговом окне **Обработка секций** в разделе **Режим**выберите один из следующих режимов обработки.  
  
    |Режим|Description|  
    |----------|-----------------|  
    |**Обработка. По умолчанию**|Обнаруживает состояние обработки объекта секции и выполняет обработку, необходимую для перевода необработанных или частично обработанных объектов секции в полностью обработанное состояние. Выполняется загрузка данных для пустых таблиц и секций; иерархии, вычисляемые столбцы и связи строятся или перестраиваются.|  
    |**Обработка. Полная**|Обрабатывает объект секций и все объекты, которые в нем содержатся. Если объект, который обрабатывается методом полной обработки, уже был обработан, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удаляют все данные объекта, а затем обрабатывают его. Этот тип обработки требуется при внесении структурных изменений в объект.|  
    |**Обработка данных**|Выполняется загрузка данных в секцию или таблицу без перестроения иерархий или связей или повторного вычисления вычисленных столбцов и мер.|  
    |**Обработка с очисткой**|Удаляет все данные из секции.|  
    |**Обработка с добавлением**|Постепенно обновляет секцию с включением новых данных.|  
  
3.  В списке секций выберите разделы для обработки и нажмите кнопку **ОК**.  
  
##  <a name="bkmk_data_process_progress"></a> Ход обработки данных  
 Диалоговое окно **Ход обработки данных** позволяет наблюдать за обработкой данных, импортированных в модель из внешнего источника. Чтобы открыть это диалоговое окно, выберите в меню **Модель** пункт **Обработать секции**, **Обработать таблицу** или **Обработать все**.  
  
 **Состояние**  
 Сообщает об успешности операции обработки.  
  
 **Сведения**  
 Перечисляет импортированные таблицы и представления, сообщает количество импортированных строк и предоставляет ссылку на отчет о неполадках.  
  
 **Прервать обновление**  
 Нажмите, чтобы остановить операцию обработки. Этот параметр может оказаться полезным в том случае, если операция развертывания занимает слишком много времени или обнаружено слишком много ошибок.  
  
## <a name="see-also"></a>См. также  
 [Обработка данных (табличные службы SSAS)](../../analysis-services/tabular-models/process-data-ssas-tabular.md)   
 [Устранение неполадок обработки данных (табличные службы SSAS)](../../analysis-services/troubleshoot-process-data-ssas-tabular.md)  
  
  