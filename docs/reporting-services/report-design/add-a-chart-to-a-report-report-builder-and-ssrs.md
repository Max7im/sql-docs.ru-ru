---
title: Добавление диаграммы в отчет (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.suite: pro-bi
ms.topic: conceptual
ms.assetid: a6b595dc-f775-4a53-8554-74a0bf9335ec
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 32c4e133d6bf1e7152f55a260bcee4caa4c641ff
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43276911"
---
# <a name="add-a-chart-to-a-report-report-builder-and-ssrs"></a>Добавление диаграммы в отчет (построитель отчетов и службы SSRS)
  Если в отчете с разбиением на страницы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] необходимо создать сводку данных в визуальном формате, можно использовать область данных "Диаграмма". Важно выбрать тип диаграммы, подходящий для типа представляемых данных. От этого зависит, насколько успешно можно будет интерпретировать данные, представленные в виде диаграммы. Дополнительные сведения см. в разделе [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md).  
  
 Самым простым способом добавления диаграммная область данных в отчет является запуск мастера создания диаграмм. Мастер поддерживает гистограммы, графики, круговые диаграммы, линейчатые диаграммы и диаграммы с областями. Диаграммы этих и других типов также можно добавить вручную.  
  
 Добавив диаграммную область данных в область конструктора, можно перетаскивать поля набора данных отчета с числовыми и нечисловыми данными на панель «Данные диаграммы». Щелкните в области данных диаграммы, чтобы отобразить панель "Данные диаграммы" с ее тремя областями: "Группы рядов", "Группы категорий" и "Значения".  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-add-a-chart-to-a-report-by-using-the-chart-wizard"></a>Добавление диаграммы в отчет с помощью мастера диаграмм  
  
1.  > [!NOTE]  
    >  Мастер диаграмм доступен только в построителе отчетов.  
  
     На вкладке **Вставка** нажмите кнопку **Диаграмма**, а затем щелкните **Мастер диаграмм**.  
  
2.  Выполните шаги **мастера создания диаграмм** .  
  
3.  На вкладке **Корневая папка** нажмите кнопку **Выполнить** , чтобы вывести отчет, готовый для просмотра.  
  
4.  На вкладке **Выполнение** нажмите кнопку **Конструктор** , чтобы продолжить работу с отчетом.  
  
## <a name="to-add-a-chart-to-a-report"></a>Добавление диаграммы к отчету  
  
1.  Создайте отчет и определите набор данных. Дополнительные сведения см. в разделе [Наборы данных отчета (службы SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md).  
  
2.  На вкладке **Вставка** выберите **Диаграмма**, затем **Вставить диаграмму**.  
  
3.  Щелкните область конструктора в месте, где должен располагаться левый верхний угол диаграммы, а затем перетащите курсор мыши в место, где будет располагаться правый нижний угол диаграммы.  
  
     Откроется диалоговое окно **Выбор типа диаграммы** .  
  
4.  Выберите тип диаграммы, который нужно добавить в отчет. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Щелкните диаграмму, чтобы отобразить панель **Данные диаграммы** .  
  
6.  Добавьте одно или несколько полей в область **Значения** . Эти данные будут выведены на оси значений.  
  
7.  Добавьте поле группирования в область **Группы категорий** . При добавлении этого поля в область **Группы категорий** автоматически создается поле группирования. Каждая группа представляет собой точку данных в рядах.  
  
8.  Чтобы получить сводку данных по категориям, щелкните правой кнопкой мыши набор данных и выберите пункт **Свойства ряда**. В текстовом поле **Категория** выберите из раскрывающегося списка поле категории. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. На вкладке **Корневая папка** нажмите кнопку **Выполнить** , чтобы вывести отчет, готовый для просмотра.  
  
10. На вкладке **Выполнение** нажмите кнопку **Конструктор** , чтобы продолжить работу с отчетом.  
  
 На диаграммах с осями (гистограмма, линейчатая диаграмма) на оси категорий могут отображаться не все метки категорий. Дополнительные сведения об изменении меток оси см. в разделе [Задание интервала оси (построитель отчетов и службы SSRS)](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Типы диаграмм (построитель отчетов и службы SSRS)](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [Точки данных со значением NULL и пустые точки в диаграммах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [Учебник. Добавление в отчет линейчатой диаграммы (построитель отчетов)](http://go.microsoft.com/fwlink/?LinkId=198052)   
 [Учебник. Добавление в отчет линейчатой диаграммы (конструктор отчетов)](http://go.microsoft.com/fwlink/?LinkId=198042)   
 [Учебник. Добавление в отчет круговой диаграммы (построитель отчетов)](http://go.microsoft.com/fwlink/?LinkId=198051)   
 [Учебник. Добавление в отчет круговой диаграммы (конструктор отчетов)](http://go.microsoft.com/fwlink/?LinkId=198041)  
  
  
