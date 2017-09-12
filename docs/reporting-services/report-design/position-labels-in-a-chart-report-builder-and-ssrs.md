---
title: "Положение меток на диаграмме (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5db74e0b-8be8-4b47-b386-faab56dffa9b
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 53f0d4b0c6aed30746af82de7d5f1caf5e42721c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="position-labels-in-a-chart-report-builder-and-ssrs"></a>Размещение меток на диаграмме (построитель отчетов и службы SSRS)
  Поскольку в отчете [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с разбиением на страницы формы всех типов диаграмм различны, метки точек данных помещаются в оптимальные положения, не ухудшающие удобочитаемость диаграммы. Позиции меток по умолчанию зависят от типа диаграммы:  
  
-   на диаграммах с накоплением метки могут располагаться только внутри рядов;  
  
-   на воронкообразных и пирамидальных диаграммах метки помещаются за пределами столбца;  
  
-   на круговых диаграммах метки помещаются внутри отдельных срезов;  
  
-   на линейчатых диаграммах метки помещаются за пределами столбцов, представляющих точки данных;  
  
-   на полярных диаграммах метки помещаются за пределами круговой области, представляющей точки данных.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-the-position-of-point-labels-in-a-pie-chart"></a>Изменение положения меток точек на круговой диаграмме  
  
1.  Создайте круговую диаграмму.  
  
2.  В области конструктора щелкните правой кнопкой мыши диаграмму и выберите команду **Отобразить метки данных**.  
  
3.  Откройте панель «Свойства». На вкладке **Вид** щелкните **Свойства**.  
  
4.  Щелкните диаграмму в области конструктора. В панели «Свойства» отображаются свойства диаграммы.  
  
5.  В разделе **Общие** разверните узел **CustomAttributes** . Отобразится список атрибутов круговой диаграммы.  
  
6.  Выберите значение для свойства PieLabelStyle.  
  
## <a name="to-change-the-position-of-point-labels-in-a-funnel-or-pyramid-chart"></a>Изменение положения меток точек на воронкообразной или пирамидальной диаграмме  
  
1.  Создайте воронкообразную или пирамидальную диаграмму.  
  
2.  В области конструктора щелкните правой кнопкой мыши диаграмму и выберите команду **Отобразить метки данных**.  
  
3.  Откройте панель «Свойства». На вкладке **Вид** щелкните **Свойства**.  
  
4.  Щелкните диаграмму в области конструктора. В панели «Свойства» отображаются свойства диаграммы.  
  
5.  В разделе **Общие** разверните узел **CustomAttributes** . Отобразится список атрибутов воронкообразной диаграммы.  
  
6.  Для воронкообразной диаграммы выберите значение для свойства FunnelLabelStyle. Для воронкообразной диаграммы выберите значение для свойства PyramidLabelStyle.  
  
    > [!NOTE]  
    >  Если это свойство имеет значение **OutsideInColumn**, метки отображаются в вертикальном столбце. Положение столбца изменить невозможно.  
  
## <a name="to-change-the-position-of-point-labels-in-a-bar-chart"></a>Изменение положения меток точек на линейчатой диаграмме  
  
1.  Создайте линейчатую диаграмму.  
  
2.  В области конструктора щелкните правой кнопкой мыши диаграмму и выберите команду **Отобразить метки данных**.  
  
3.  Откройте панель «Свойства». На вкладке **Вид** щелкните **Свойства**.  
  
4.  Щелкните диаграмму в области конструктора. В панели «Свойства» отображаются свойства диаграммы.  
  
5.  В разделе **Общие** разверните узел **CustomAttributes** . Отобразится список атрибутов линейчатой диаграммы.  
  
6.  Выберите значение для свойства BarLabelStyle.  
  
 Если стиль линейчатой диаграммы имеет значение **Outside**, метки будут располагаться за пределами линейки, пока она помещается в области диаграммы. Если метку не удается поместить за пределами линейки, но ее можно расположить в области диаграммы, метка помещается внутри линейки в позиции, ближайшей к концу линейки.  
  
## <a name="to-change-the-position-of-point-labels-in-an-area-column-line-or-scatter-chart"></a>Изменение положения меток точек в диаграмме с областями, гистограмме, графике и точечной диаграмме  
  
1.  Создайте диаграмму с областями, гистограмму, график или точечную диаграмму.  
  
2.  В области конструктора щелкните правой кнопкой мыши диаграмму и выберите команду **Отобразить метки данных**.  
  
3.  Откройте панель «Свойства». На вкладке **Вид** щелкните **Свойства**.  
  
4.  Щелкните ряд в области конструктора. На панели «Свойства» отображаются свойства ряда.  
  
5.  В разделе **Данные** разверните узел **Точка данных** , а затем узел **Метка**.  
  
6.  Выберите значение для свойства Position.  
  
## <a name="see-also"></a>См. также  
 [Круговые диаграммы &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [Линейчатые диаграммы &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)   
 [Форматирование меток оси на диаграмме &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Форматирование меток оси в виде даты или валюты &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Отображение меток точек данных за пределами круговой диаграммы &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [Форматирование точек данных на диаграмме &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
  
  