---
title: "Создание матрицы (построитель отчетов и службы SSRS) | Документы Microsoft"
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
ms.assetid: 493e63b9-ecd0-4054-97ec-92d84e9b8182
caps.latest.revision: 12
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2ae4ec5004c6299dc8201daa18ab89b432cab845
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="create-a-matrix-report-builder-and-ssrs"></a>Создание матрицы (построитель отчетов 3.0 и службы SSRS)
  Матрица используется для отображения сгруппированных данных и сводной информации. Данные можно группировать по нескольким полям либо выражениям в группах строк и столбцов. Матрицы обеспечивают функциональность, подобную перекрестным и сводным таблицам. Во время выполнения, по мере объединения данных отчета и областей данных матрица растет на странице в горизонтальном и вертикальном направлении. Значения в ячейках матрицы отображают статистические значения пересечения групп строк и столбцов, которым принадлежит ячейка. Строки и столбцы можно форматировать, чтобы выделить нужные данные. Можно также включить переключатели детализации, которые по умолчанию скрывают подробные данные, чтобы пользователи могли по желанию отобразить подробные сведения.  
  
 После завершения проектирования можно продолжить разработку матрицы для улучшения условий просмотра пользователями. Дополнительные сведения см. в разделе [Управление отображением области данных табликса на странице отчетов (построитель отчетов и службы SSRS)](../../reporting-services/report-design/controlling-the-tablix-data-region-display-on-a-report-page.md).  
  
 Чтобы быстро приступить к работе с матрицами, см. раздел [Учебник. Создание матричного отчета (построитель отчетов)](../../reporting-services/tutorial-creating-a-matrix-report-report-builder.md).  
  
> [!NOTE]  
>  Списки можно публиковать отдельно от отчета как элементы отчета. Дополнительные сведения см. в разделе [Элементы отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-parts-report-builder-and-ssrs.md).  
  
##  <a name="AddingMatrix"></a> Добавление матрицы к отчету  
 Добавьте матрицу в область конструктора из вкладки «Вставка» на ленте. Предусмотрена возможность добавить матрицу с использованием мастера «Таблица» или «Матрица», что включает создание соединения с источником данных и набора данных, а также настройку матрицы или добавление матрицы на основе шаблона матрицы.  
  
> [!NOTE]  
>  Мастер доступен только в [!INCLUDE[ssRBDenali](../../includes/ssrbdenali-md.md)].  
  
 В целях описания способа настройки таблицы от начала до конца в этом разделе используется шаблон матрицы.  Первоначально в матрице имеется группа строк, группа столбцов, угловая ячейка и ячейка данных, как показано на следующем рисунке.  
  
 ![Пустая матрица с 1 строкой и 1 группой столбцов](../../reporting-services/report-design/media/rs-matrixtemplatenew.gif "Пустая матрица с 1 строкой и 1 группой столбцов")  
  
 При выборе матрицы в области конструктора появляются маркеры строк и столбцов, как показано на следующем рисунке.  
  
 ![Новая матрица добавлен с панели элементов, выбранных](../../reporting-services/report-design/media/rs-matrixtemplatenewselected.gif "новой матрицы добавлен с панели элементов, выбранных")  
  
 Добавьте группу, перетащив поля набора данных в панель групп строк и групп столбцов в панель «Группирование». Первое поле, которое перетаскивается на панель группы строк или столбцов, замещает первоначальную пустую группу по умолчанию. Затем для каждой ячейки можно применить форматирование, в зависимости от содержащихся в ней данных.  
  
 ![Матрица, строка категорий и группа столбцов географических объектов](../../reporting-services/report-design/media/rs-basicmatrixdesign.gif "Матрица, строка категорий и группа столбцов географических объектов")  
  
 В режиме просмотра матрица расширяется для отображения значений группы строк и группы столбцов. В ячейках выводятся сводные значения, как показано на следующем рисунке.  
  
 ![Предварительный просмотр обработанной матрицы с расширенными группами](../../reporting-services/report-design/media/rs-basicmatrixpreview.gif "Предварительный просмотр обработанной матрицы с расширенными группами")  
  
 Первоначальная матрица является шаблоном на основе области данных табликса. Можно продолжить разработку матрицы, добавив вложенные или смежные группы строк либо столбцов или даже строки подробностей. Дополнительные сведения см. в разделе [Изучение возможностей области данных табликса (построитель отчетов и службы SSRS)](../../reporting-services/report-design/exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md).  
  
  
##  <a name="AddingParentGroupChild"></a> Добавление родительской или дочерней группы в матрицу  
 Чтобы добавить группу, основанную на одном поле набора данных, перетащите это поле из панели данных отчета на соответствующую панель группы строк или столбцов на панели группировки. Перетащите поле в иерархию группы, чтобы установить ее связь с существующими группами. Перетащите поле в иерархию над существующей группой, чтобы создать родительскую группу, или ниже нее, чтобы создать дочернюю группу.  
  
 При помещении поля на панель **Группирование** происходит следующее.  
  
-   Автоматически создается новая группа с уникальным именем на основе имени поля. Выражению группы присваивается значение простой ссылки на имя поля, например `[Category]`.  
  
-   В области соответствующей группы строк или столбцов появится новая строка или столбец.  
  
-   В новом столбце появится ячейка группы строк для строк данных по умолчанию из набора данных отчета. Ячейки в теле табликса для этой строки теперь являются элементами группы строк. Если определена какая-либо группа столбцов, ячейки столбцов являются элементами этой группы столбов. Индикаторы групп визуально отображают членство в группе для каждой ячейки.  
  
 Для настройки группы после ее создания, используется диалоговое окно **Группа табликсов** . Можно переименовать группу, а также изменить или добавить дополнительные выражения к определению группы. Сведения о добавлении и удалении строк в таблице см. в разделе [Вставка или удаление строки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/insert-or-delete-a-row-report-builder-and-ssrs.md).  
  
 При выполнении отчета заголовки динамических столбцов расширяются вправо (или влево, если параметр матрицы Direction имеет значение RTL) на столько столбцов, сколько имеется уникальных значений групп. Динамические строки расширяются по странице вниз. Данные, отображающиеся в ячейках тела табликса, являются статистическими выражениями, основанными на пересечениях групп строк и столбцов, как показано на следующем рисунке.  
  
 ![Матрица, вложенных групп строк и столбцов с итогами](../../reporting-services/report-design/media/rs-basicmatrixnestedgroupstotalsdesign.gif "матрица, вложенные группы строк и столбцов с итогами")  
  
 В режиме просмотра отчет отображается в том виде, в каком показан на следующем рисунке.  
  
 ![Вложенные группы в режиме предварительного просмотра](../../reporting-services/report-design/media/rs-basicmatrixnestedgroupstotalspreview.gif "вложенных групп в режиме предварительного просмотра")  
  
 Чтобы записать выражение, задающее область, отличающуюся от области по умолчанию, необходимо указать имя набора данных, область данных или группу в агрегатной функции ALL. Чтобы вычислить процент значений каждой подкатегории в категории «Одежда», добавьте столбец в группу «Категория» рядом со столбцом Total, отформатируйте текстовое поле для отображения процентов и добавьте выражение, которое использует область по умолчанию в числителе и область группы категорий в знаменателе, как показано на следующем рисунке.  
  
 `=SUM(Fields!Linetotal.Value)/SUM(Fields! Linetotal.Value,"Category")`  
  
 Дополнительные сведения см. в разделе [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
  
##  <a name="AddingAdjacentGroup"></a> Добавление смежной группы в матрицу  
 Для добавления смежной группы, основанной на одном поле набора данных, используется контекстное меню панели группировки. Дополнительные сведения см. в разделе [Добавление или удаление группы в области данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md). На следующем рисунке показана группа на основе географических данных и смежная группа на основе года.  
  
 ![Смежные группы столбцов для Geography и Year](../../reporting-services/report-design/media/rs-basicmatrixadjacentgroupsdesign.gif "смежные группы столбцов для Geography и Year")  
  
 В следующем примере запрос фильтрует данные, чтобы вернуть значения только для Европы и только для 2003 и 2004 годов. Тем не менее, фильтры можно установить независимо в каждой группе. В режиме просмотра отчет отображается в том виде, в каком показан на следующем рисунке.  
  
 ![Просмотр смежных групп столбцов](../../reporting-services/report-design/media/rs-basicmatrixadjacentgroupspreview.gif "Предварительный просмотр смежных групп столбцов")  
  
 Чтобы добавить общий столбец для каждой смежной группы, щелкните ячейку определения группы столбцов и выберите **Добавить итог** . Рядом группой столбцов появится новый статический столбец со статистическим выражением суммы по умолчанию для каждого числового поля в существующих строках. Чтобы изменить выражение, измените его вручную, например `Avg([Sales])`. Дополнительные сведения см. в разделе [Добавление итога в группу или область данных табликса (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs.md).  
  
  
## <a name="see-also"></a>См. также:  
 [Справочник по агрегатным функциям &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)   
 [Примеры выражений &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)  
  
  