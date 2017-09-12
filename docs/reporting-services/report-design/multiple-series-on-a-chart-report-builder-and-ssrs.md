---
title: "Несколько рядов на диаграмме (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b99e4398-1fba-4824-958f-5c75d10485ea
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e3e3fa82b79529b1e128260f020b8e98225e26fe
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="multiple-series-on-a-chart-report-builder-and-ssrs"></a>Несколько рядов на диаграмме (построитель отчетов и службы SSRS)
  Если в диаграмме представлено несколько рядов, необходимо определить лучший способ сравнения рядов. Для отображения относительных пропорций каждого ряда можно использовать диаграмму с накоплением. Если сравниваются только два ряда с общей осью категорий (x), используйте вспомогательную ось. Это удобно при отображении двух связанных рядов данных, например, цены и количества или доходов и налогов. Если диаграмма становится трудной для восприятия, попробуйте использовать несколько областей диаграммы, чтобы визуально отделить ряды друг от друга.  
  
 Помимо использования функций диаграмм важно решить, какой тип диаграмм следует использовать для определенных данных. Если поля в наборе данных связаны, используйте диаграмму диапазонов.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-stacked-and-100-stacked-charts"></a>Использование нормированных диаграмм и диаграмм с накоплением  
 Диаграммы с накоплением обычно используются для отображения нескольких рядов в одной области диаграммы. Используйте диаграммы с накоплением, когда отображаемые данные близко связаны. Также рекомендуется отображать в диаграмме с накоплением не более четырех рядов. Если необходимо сравнить долю каждого ряда в общем количестве, используйте гистограмму, линейчатую диаграмму или нормированную диаграмму с областями. Эти диаграммы позволяют вычислить относительный процент, который составляет каждый ряд по отношению ко всей категории. Дополнительные сведения см. в разделах [Диаграммы с областями (построитель отчетов и службы SSRS)](../../reporting-services/report-design/area-charts-report-builder-and-ssrs.md), [Линейчатые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md) и [Гистограммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md).  
  
## <a name="using-the-secondary-axis"></a>Использование вспомогательной оси  
 Когда к диаграмме добавляется новый ряд, он отображается с использованием основных осей x и y. Когда необходимо сравнить значения, выраженные в разных единицах измерения, используйте *вспомогательную ось* , которая позволяет отображать два ряда на отдельных осях. Вспомогательная ось удобна для сравнения значений, выраженных в разных единицах измерения. Вспомогательная ось рисуется с противоположной стороны от основной оси. В диаграмме допускается использование только основной и вспомогательной оси. Вспомогательная ось обладает теми же свойствами, что и основная. Дополнительные сведения см. в разделе [Построение данных на вспомогательной оси (построитель отчетов и службы SSRS)](../../reporting-services/report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md).  
  
 Если необходимо отобразить больше двух рядов с разными диапазонами данных, попробуйте разместить ряды в разных областях диаграммы.  
  
## <a name="using-chart-areas"></a>Использование областей диаграммы  
 Диаграмма является контейнером верхнего уровня, который включает внешнюю границу, заголовок диаграммы и условные обозначения. По умолчанию диаграмма содержит одну область диаграммы. Область диаграммы не видна на самой диаграмме, но ее можно рассматривать как контейнер, который содержит только метки осей, заголовок оси и область построения для одного или нескольких рядов. На следующем рисунке представлено понятие областей диаграммы с одной диаграммой.  
  
 ![Показывает схему области диаграммы](../../reporting-services/report-design/media/chartareasdiagram.gif "показывает схему области диаграммы")  
  
 С помощью диалогового окна **Свойства области диаграммы** можно задать двумерную или трехмерную ориентацию всех рядов в области диаграммы, выровнять несколько областей диаграммы внутри одной диаграммы и определить цвета на области построения. При определении новой области диаграммы в диаграмме, которая содержит только одну область диаграммы по умолчанию, доступное пространство для области диаграммы делится на две части и новая область диаграммы размещается под первой областью.  
  
 Каждый ряд можно связать только с одной областью диаграммы. Как правило, все ряды добавляются в область диаграммы по умолчанию. При использовании диаграмм с областями, гистограмм, линейчатых и точечных диаграмм все комбинации этих рядов можно отобразить в одной области диаграммы. Например, в одной области диаграммы можно отобразить ряд столбцов и ряд строк. Преимуществом использования одной области диаграммы для нескольких рядов является удобство сравнения данных для конечных пользователей.  
  
 Линейчатые, лепестковые и фигурные диаграммы несовместимы с другими типами диаграмм в одной области диаграммы. Для проведения сравнений с несколькими рядами линейчатого, лепесткового или фигурного типа нужно выбрать один из следующих вариантов.  
  
-   Преобразовать все ряды в области диаграммы в один тип диаграммы.  
  
-   Создать новую область диаграммы и перенести один или несколько рядов из области диаграммы по умолчанию в эту новую область.  
  
 Использование нескольких областей диаграммы в одной диаграмме также полезно при попытке сравнения данных разного порядка значений. Например, если в первом ряду содержатся данные в диапазоне от 10 до 20, а во втором ряду содержатся данные в диапазоне от 400 до 800, то значения в первом ряду могут оказаться плохо различимыми. Попробуйте разделить ряды по разным областям диаграммы. Дополнительные сведения см. в разделе [Задание области диаграммы для ряда (построитель отчетов и службы SSRS)](../../reporting-services/report-design/specify-a-chart-area-for-a-series-report-builder-and-ssrs.md).  
  
## <a name="using-range-charts"></a>Использование диаграмм диапазонов  
 В диаграммах диапазонов имеется по два значения на каждую точку данных. Если в диаграмме есть два ряда на одной оси категорий (x), то чтобы показать различие двух рядов, можно использовать диаграмму диапазонов. Диаграммы диапазонов больше всего подходят для отображения нижних и верхних значений. Например, если в первом ряду содержатся данные по самым крупным продажам по всем дням января, а во втором ряду содержатся самые мелкие продажи по всем дням января, то чтобы показать различие между самыми крупными и самыми мелкими продажами за каждый день, можно использовать диаграмму диапазонов. Дополнительные сведения см. в разделе [Диаграммы диапазонов (построитель отчетов и службы SSRS)](../../reporting-services/report-design/range-charts-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Диаграммы &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Отображение ряда с несколькими диапазонами данных на диаграмме &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/displaying-a-series-with-multiple-data-ranges-on-a-chart.md)   
 [Типы диаграмм &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)  
  
  