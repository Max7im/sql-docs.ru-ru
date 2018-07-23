---
title: Диалоговое окно «Параметры хранилища» (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.f1
- sql12.asvs.cubeeditor.cubebuilder.measuregroupstoragesettings.f1
ms.assetid: 80c41c71-226c-45fe-b9cf-af824b592fe1
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3d39d87c0896ba77d3e323dc762d2618098dfd39
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161315"
---
# <a name="storage-settings-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Настройки хранилища» (службы Analysis Services — многомерные данные)
  Используйте диалоговое окно **Настройки хранилища** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для задания свойств упреждающего кэширования, хранилища и уведомлений для измерения, куба, группы мер или секции. Диалоговое окно **Настройки хранилища** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] можно отобразить:  
  
-   Нажав кнопку с многоточием (**...** ) для `ProactiveCaching` значение свойства измерения, куба, группы мер или секции в **свойства** окно [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
-   Путем раскрытия группы мер на вкладке **Секции** окна **Конструктор кубов** , щелкнув **Настройки хранилища**.  
  
-   Путем раскрытия группы мер и выбора секции в сетке, соответствующей этой группе мер, на вкладке **Секции** окна **Конструктор кубов** , щелкнув **Настройки хранилища**.  
  
-   Путем раскрытия группы мер и выбора секции в сетке, соответствующей этой группе мер, на вкладке **Секции** окна **Конструктор кубов** , щелкнув **Настройки хранилища** на панели **Панель инструментов** вкладки **Секции** окна **Конструктор кубов**.  
  
## <a name="options"></a>Параметры  
  
|Термин|Определение|Значения|  
|----------|----------------|------------|  
|**Стандартные настройки**|Выберите, чтобы задействовать ползунок **Стандартные настройки** и использовать предопределенные настройки режима хранения и возможностей упреждающего кэширования.||  
|**Стандартные настройки**|Установите одну из следующих предустановленных настроек:<br /><br /> **ROLAP в реальном времени**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранилища ROLAP<br /><br /> Включить упреждающее кэширование<br /><br /> Удалять устаревшие данные из кэша с периодом задержки 0 секунд.<br /><br /> Приводить объект в режим в сети немедленно|  
||**HOLAP в реальном времени**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранилища HOLAP<br /><br /> Включить упреждающее кэширование<br /><br /> Удалять устаревшие данные из кэша с периодом задержки 0 секунд.<br /><br /> Обновлять кэш при изменении данных с интервалом бездействия в 0 секунд и без интервала прерывания бездействия<br /><br /> Приводить объект в режим в сети немедленно|  
||**Небольшая задержка MOLAP**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранения MOLAP<br /><br /> Включить упреждающее кэширование<br /><br /> Удалять устаревшие данные из кэша с периодом задержки 30 минут<br /><br /> Обновлять кэш при изменении данных с интервалом бездействия в 10 секунд и интервалом прерывания бездействия в 10 минут<br /><br /> Приводить объект в режим в сети немедленно|  
||**MOLAP со средней задержкой**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранения MOLAP<br /><br /> Включить упреждающее кэширование<br /><br /> Удалять устаревшие данные из кэша с периодом задержки 4 часа<br /><br /> Обновлять кэш при изменении данных с интервалом бездействия в 10 секунд и интервалом прерывания бездействия в 10 минут<br /><br /> Приводить объект в режим в сети немедленно|  
||**Автоматический MOLAP**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранения MOLAP<br /><br /> Включить упреждающее кэширование<br /><br /> Обновлять кэш при изменении данных с интервалом бездействия в 0 секунд и без интервала прерывания бездействия|  
||**Запланированный MOLAP**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранения MOLAP<br /><br /> Разрешить упреждающее кэширование<br /><br /> Периодически обновляет кэш с интервалом перестроения в 1 день|  
||**MOLAP**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранения MOLAP|  
|**Пользовательский параметр**|Выберите, чтобы явно установить параметры режима хранения, упреждающего кэширования и уведомлений.||  
|**Параметры**|Щелкните, чтобы вывести диалоговое окно **Параметры хранилища** и явно задать параметры режима хранения, упреждающего кэширования и уведомлений. Дополнительные сведения о диалоговом окне **Параметры хранилища** см. в разделе [Диалоговое окно "Параметры хранилища" (службы Analysis Services — многомерные данные)](storage-options-dialog-box-analysis-services-multidimensional-data.md).||  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Упреждающее кэширование &#40;секций&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)   
 [Хранилище куба &#40;службы Analysis Services — многомерные данные&#41;](multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)  
  
  