---
title: "Построитель отчетов в SQL Server 2016 | Документы Microsoft"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- "10428"
helpviewer_keywords:
- overview of Report Builder
- getting started
ms.assetid: 55bf4f9c-d037-412f-ae57-3fc39ce32fa5
caps.latest.revision: 35
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c2a8702fcee392936451e4a55a4b97327de2b97d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="report-builder-in-sql-server-2016"></a>Построитель отчетов в SQL Server 2016
  [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] — это инструмент создания отчетов с разбиением на страницы, предназначенный для корпоративных пользователей, которые предпочитают работать в автономной среде вместо использования конструктора отчетов в Visual Studio.  Во время проектирования отчета с разбиением на страницы вы создаете определение отчета, в котором указано, откуда и какие брать данные, а также как их отображать. При запуске отчета обработчик получает заданное определение отчета, извлекает данные и объединяет их с макетом отчета, чтобы создать отчет. Отчеты можно предварительно просмотреть из [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] , опубликовать в собственном режиме или в режиме интеграции с SharePoint на сервере отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , откуда его смогут запустить другие пользователи.  
  
 ![rs_GettingStartedReport](../../reporting-services/report-builder/media/rs-gettingstartedreport.png "rs_GettingStartedReport")  
  
 Функция разбиения на страницы представляет собой матрицу с группами строк и столбцов, спарклайнами, индикаторами и итоговой круговой диаграммой в угловой ячейке, а также карту с двумя наборами географических данных, представленными цветом и размером кругов.  
  
##  <a name="JumpStartReptCreation"></a> Начало создания отчета  
  
-   **Начало работы с общим набором данных**. Общие наборы данных — это запросы на основе общего источника данных, сохраненные в собственном режиме или в режиме интеграции с SharePoint на сервере отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   **Начало работы с мастером таблиц, матриц или диаграмм**. Выберите соединение с источником данных, перетащите поля, чтобы создать запрос к набору данных, выберите макет и стиль и настройте отчет.  
  
-   **Начало работы с мастером карт** для создания отчетов, в которых отображаются объединенные данные в географическом или геометрическом контексте. На карте могут размещаться пространственные данные из запроса [!INCLUDE[tsql](../../includes/tsql-md.md)] или из файла фигуры ESRI (Environmental Systems Research Institute, Inc.). Файл фигуры (ESRI). Также можно добавлять мозаичный фон карты [!INCLUDE[msCoName](../../includes/msconame-md.md)] Bing.  
  
-   **Начало работы с элементами отчета**. Элементы отчетов — это элементы, опубликованные отдельно в собственном режиме или в режиме интеграции с SharePoint на сервере отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Они могут использоваться повторно в других отчетах. Как элементы отчетов можно публиковать такие элементы отчетов, как таблицы, матрицы, диаграммы и изображения.  
  
##  <a name="DesignRept"></a> Разработка отчета  
  
-   **Создание отчетов с разбиением на страницы с использованием следующих макетов отчетов: табличных, матричных, с диаграммами и произвольной формы.** Табличные отчеты целесообразно применять для данных, представленных в виде столбцов; матричные отчеты (такие, как перекрестные или сводные таблицы) — для сводных данных, а отчеты с диаграммами — для графических данных. Для других форматов данных используется произвольный тип отчета. В отчеты можно внедрять другие отчеты и диаграммы наряду со списками, графическими изображениями и элементами управления для динамических веб-приложений.  
  
-   **Отчеты на основе различных источников данных.** Построение отчетов с использованием данных из любых источников, для которых есть управляемый поставщик данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], поставщик OLE DB или источник данных ODBC. Можно создавать отчеты, использующие реляционные и многомерные данные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], Oracle, Hyperion и других баз данных. Чтобы получить данные из любого источника XML-данных, можно воспользоваться модулем обработки XML-данных. Для разработки пользовательских источников данных можно использовать функции, возвращающие табличное значение.  
  
-   **Изменение существующих отчетов.** С помощью [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]можно настроить и обновить отчеты, созданные в конструкторе отчетов [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
-   **Изменение данных** путем фильтрации, группирования и сортировки либо путем добавления формул и выражений.  
  
-   **Добавление диаграмм, датчиков, инфокривых и индикаторов** позволяет наглядно отобразить сводные данные и представлять большие объемы статистической информации в легко доступном виде.  
  
-   **Добавление интерактивных функций** , например схем документов, кнопок отображения и скрытия, а также ссылок для детализации вложенных отчетов и детализированных отчетов. С помощью параметров и фильтров можно отфильтровать данные для пользовательских представлений.  
  
-   **Внедрение или размещение ссылок на изображения** и другие ресурсы, в том числе на внешнее содержимое.  
  
##  <a name="ManageRpt"></a> Управление отчетом  
  
-   **Сохранение определения отчета** на компьютере или на сервере отчетов, откуда можно управлять отчетом и предоставить к нему доступ другим пользователям.  
  
-   **Выбор формата представления данных** во время открытия или после открытия отчета. Можно выбрать следующие формы представления отчета: веб-страница, страница документа и приложение. Доступны следующие форматы: HTML, MHTML, PDF, XML, CSV, TIFF, Word и Excel.  
  
-   **Настройка подписок.** После публикации отчета на сервере отчетов или на сервере отчетов в режиме интеграции с SharePoint можно настроить отчет на выполнение в определенное время, создать журнал отчета и организовать подписку по электронной почте.  
  
-   **Создание потоков данных** с помощью отчета с использованием модуля подготовки Atom отчетов служб Reporting Services.  
  
> [!NOTE]  
>  Опубликованные отчеты управляются на сервере отчетов или сервере отчетов в режиме интеграции с SharePoint администратором сервера отчетов. Администраторы сервера отчетов могут определить безопасность, задать свойства и задать расписание операций, таких как журнал отчета и доставка отчета по электронной почте. Они могут создать общие расписания и источники данных, и сделать их доступными для общего использования. Администраторы также управляют всеми каталогами сервера отчетов. Возможности управления зависят от назначенных пользователю разрешений.  
  
## <a name="see-also"></a>См. также  
  [Запуск построителя отчетов](../../reporting-services/report-builder/start-report-builder.md)  
  
  [Установка построителя отчетов](../../reporting-services/install-windows/install-report-builder.md)

  [Новые возможности служб Reporting Services и построителя отчетов для SQL Server 2016](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)  
  Описываются новые функции этой версии [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)].   
  [Учебник. Создание стандартного отчета с диаграммой в режиме «вне сети»](../../reporting-services/report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md)  
 Содержатся общие сведения о [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] и мастерах, которые могут помочь в создании отчетов. Учебник содержит набор данных для работы, поэтому соединяться с источником данных не нужно.  
  
 [Планирование отчета (построитель отчетов)](../../reporting-services/report-design/planning-a-report-report-builder.md)  
 Содержит сведения о некоторых соображениях, которые важно учесть перед началом создания отчета.  
  
 [Основные понятия разработки отчетов (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-authoring-concepts-report-builder-and-ssrs.md)  
 Определены основные понятия, используемые в документации по [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] .  
  
 [Представление конструктора отчетов (построитель отчетов)](../../reporting-services/report-builder/report-design-view-report-builder.md)  
 Поясняет назначение различных панелей и областей представления конструктора отчетов.  
  
 [Представление конструктора общих наборов данных (построитель отчетов)](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)  
 Поясняет назначение различных панелей и областей представления конструктора общих наборов данных.  
  
 [Сочетания клавиш (построитель отчетов)](../../reporting-services/report-builder/keyboard-shortcuts-report-builder.md)  
 Описываются клавиши, которые можно использовать для навигации и проектирования отчетов в [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)].  
  

