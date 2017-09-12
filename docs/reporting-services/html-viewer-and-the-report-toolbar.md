---
title: "Просмотра HTML-страниц и панель инструментов отчета | Документы Microsoft"
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTML Viewer [Reporting Services]
- report toolbar [Reporting Services]
ms.assetid: cd86b319-babd-45af-a6a4-f659fdcc40c3
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 70ffdb98f998c46946452a2753b63f9f4bd95dfa
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="html-viewer-and-the-report-toolbar"></a>Средство просмотра HTML-страниц и панель инструментов отчета
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] есть средство просмотра HTML-страниц, которое предназначено для отображения отчетов по запросу в том виде, в каком они запрашиваются с сервера отчетов. Средство просмотра HTML-страниц обеспечивает платформу для просмотра отчетов в формате HTML. Она включает в себя панель инструментов отчета, раздел параметров, раздел учетных данных и схему документа. Панель инструментов отчета в средстве просмотра HTML-страниц предлагает функции, которые можно использовать для работы с отчетом, включая параметры экспорта, поэтому можно просмотреть отчет в форматах, отличных от HTML. Раздел параметров и схема документа появляются только тогда, когда открываются отчеты, настроенные для использования параметров и управления схемой документа.  
  
 Хотя изменять панель инструментов отчета нельзя, можно настроить параметры URL-адреса отчета таким образом, чтобы в отчете она не отображалась. Дополнительные сведения о том, как скрыть панель инструментов отчета, см. в разделе [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md).  
  
## <a name="report-toolbar"></a>Панель инструментов отчета  
 Панель инструментов отчета обеспечивает следующие возможности при работе со страницами: навигации, масштабирования, обновления, поиска, экспорта, печати и работы с каналами данных для отчетов, подготовленных к просмотру в модуле подготовки HTML-отчетов.  
  
 Возможность печати является дополнительной. Когда она доступна, на панели инструментов отчета появляется значок принтера. При первом использовании щелчок значка принтера загружает элемент управления ActiveX, который необходимо установить. После установки этого элемента управления при щелчке значка принтера открывается диалоговое окно «Печать», в котором можно выбрать принтер из списка принтеров, настроенных для данного компьютера. Доступность печати определяется настройками сервера и браузера. Дополнительные сведения см. в разделе [Печать отчетов из браузера с помощью элемента управления печатью &#40; Построитель отчетов и службы SSRS &#41; ](../reporting-services/report-builder/print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) и [Включение и отключение печати на стороне клиента для служб Reporting Services](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
 Панель инструментов отчета подобна той, что показана на иллюстрации ниже. В некоторых конкретных случаях панель инструментов отчета может отличаться от изображенной на иллюстрации, в зависимости от функций отчета или доступных параметров подготовки к просмотру.  
  
 ![Report toolbar](../reporting-services/media/ssrs-htmlviewer-toolbar.png "Report toolbar")  
  
 Следующая таблица описывает часто используемые функции на панели инструментов отчета. Каждая функция определяется элементом управления, который используется для получения доступа к ней.  
  
|Используйте этот значок или элемент управления||Чтобы|  
|------------------------------|-|--------|  
|![Элементы управления навигацией по страницам](../reporting-services/media/htmlviewer-pagenav.gif "Элементы управления навигацией по страницам")|**Элементы управления навигацией по страницам**|Открыть первую или последнюю страницу отчета, перелистать отчет страницу за страницей, открыть определенную страницу в отчете. Чтобы просмотреть определенную страницу, введите номер страницы и нажмите клавишу ВВОД.|  
|![Элементы управления отображением страниц](../reporting-services/media/htmlviewer-pagesize.gif "Элементы управления отображением страниц")|**Элементы управления отображением страниц**|Увеличить или уменьшить отображаемый размер страницы отчета. В дополнение к изменениям размеров в процентном отношении можно выбрать параметр **Ширина страницы** , чтобы подогнать горизонтальный размер страницы отчета по размеру окна браузера или **Вся страница** , чтобы подогнать вертикальный размер страницы отчета по размеру окна браузера. Режим **Масштаб** поддерживается в обозревателе [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 5.5 и более поздних версиях.|  
|![Поле поиска](../reporting-services/media/htmlviewer-search.gif "Поле поиска")|**Поле поиска**|Искать содержимое в отчете, введя слово или фразу, которую нужно найти (максимальная длина значения составляет 256 знаков). Поиск не зависит от регистра и начинается на странице или в разделе, выбранном в настоящий момент. Только видимое содержимое включается в операцию поиска. Для поиска следующих вхождений того же значения нажмите кнопку **Далее**.|  
|![Форматы экспорта](../reporting-services/media/htmlviewer-export.GIF "Форматы экспорта")|**Форматы экспорта**|Открыть новое окно браузера и подготовить отчет к просмотру в выбранном формате. Доступные форматы определяются модулями подготовки отчетов, которые установлены на сервере отчетов. Формат TIFF рекомендуется для печати. Нажмите кнопку **Экспорт** , чтобы просмотреть отчет в выбранном формате.|  
|![Значок схемы документа](../reporting-services/media/htmlviewer-docmap.GIF "Значок схемы документа")|**Значок схемы документа**|Показать или скрыть панель схемы документа в отчете, включающем в себя такую схему. Схема документа — это элемент управления навигацией по отчету, подобный панели навигации на веб-сайте. Можно перейти к определенной группе, странице или вложенному отчету, щелкнув соответствующий элемент схемы документа.|  
|![Значок принтера](../reporting-services/media/printer-icon.gif "Значок принтера")|**Значок принтера**|Открыть диалоговое окно «Печать», чтобы указать параметры печати и распечатать отчет. При первом использовании щелчок значка вызывает приглашение загрузить элемент управления печатью.|  
||**Значки «Показать» и «Скрыть»**|Показать или скрыть поля значений параметров и кнопку **Просмотр отчета** в отчете, содержащем параметры.|  
|![Кнопка обновления обозревателя на панели инструментов отчета](../reporting-services/media/htmlviewer-refresh.GIF "кнопку обновления в браузере на панели инструментов отчета")|**Значок обновления отчета**|Обновить отчет. Данные для активных отчетов будут обновлены. Кэшированные отчеты будут заново загружены из местоположения, в котором они хранятся.|  
|![htmlviewer_datafeed](../reporting-services/media/htmlviewer-datafeed.gif "htmlviewer_datafeed")|**Значок канала данных**|Создание каналов данных с помощью отчетов.|  
|![ssrs_powerbi_button_reportwviewer](../reporting-services/media/ssrs-powerbi-button-reportwviewer.png "ssrs_powerbi_button_reportwviewer")|**Закрепление на панели мониторинга Power BI**|Закрепить поддерживаемые элементы отчета в [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Если кнопка не видна, сервер отчетов не интегрирован с [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  Дополнительные сведения см. в разделе [Интеграция сервера отчетов с Power BI (диспетчер конфигурации)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).|  
  
### <a name="about-export-formats"></a>О форматах экспорта  
 На панели инструментов отчета можно выбрать варианты просмотра отчета из множества различных форматов. Доступные форматы определяются модулями подготовки отчетов, которые установлены на сервере отчетов. При выборе другого формата используется второе окно браузера для отображения отчета с помощью средства просмотра, связанного с выбранным форматом экспорта. Если для выбранного формата нет доступного средства просмотра, можно выбрать другой формат.  
  
 Следующие форматы экспорта включены в установку сервера отчетов по умолчанию. Список доступных форматов экспорта может отличаться от перечисленных ниже.  
  
|Формат экспорта|Description|  
|-------------------|-----------------|  
|XML|Просмотреть отчет в виде XML. Отчеты, просматриваемые в формате XML, открываются в новом окне браузера.|  
|CSV|Просмотреть отчет в формате текста, разделенного запятыми. Отчет открывается в приложении, связанном с типом файлов CSV.|  
|PDF|Просмотреть отчет с использованием клиентского средства просмотра PDF. Чтобы использовать этот формат, необходимо стороннее средство просмотра PDF-файлов (например, Adobe Acrobat Reader).|  
|MHTML|Просмотреть отчет в MIME-закодированном формате HTML, который хранит изображения и связанное содержимое вместе с отчетом.|  
|Excel|Просмотреть отчет в [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel в виде XLSX-файла.|  
|PowerPoint|Просмотреть отчет в [!INCLUDE[msCoName](../includes/msconame-md.md)] PowerPoint в виде PPTX-файла.|  
|TIFF-файл|Просмотреть отчет в средстве просмотра TIFF по умолчанию. Для некоторых клиентов [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows этим средством является программа просмотра изображений и факсов. Выберите этот формат, чтобы просмотреть отчет в виде макета страницы.|  
|Word|Просмотреть отчет в [!INCLUDE[msCoName](../includes/msconame-md.md)] Word в виде DOCX-файла.|  
  
## <a name="parameters"></a>Параметры  
 Параметры — это значения, используемые, чтобы выбрать конкретные данные (в частности, они используются для завершения запроса, выбирающего данные для отчета, или для фильтрации результирующего набора). В число параметров, которые обычно используются в отчетах, входят даты, имена и идентификаторы. При указании значения для параметра отчет содержит только те данные, которые соответствуют этому значению; например данные о сотрудниках, отобранные на основе параметра «Идентификатор сотрудника». Параметры связаны с полями в отчете. После указания параметра нажмите кнопку **Просмотр отчета** , чтобы получить данные.  
  
 Автор отчета определяет, какие значения параметров являются действительными для каждого отчета. Администратор отчета также может устанавливать значения параметров. Чтобы выяснить, какие значения параметров допустимы для отчета, обратитесь к конструктору или администратору отчета.  
  
## <a name="credentials"></a>Учетные данные  
 Учетные данные — это значения имени пользователя и пароля, с помощью которых предоставляется доступ к источнику данных. После указания учетных данных нажмите кнопку **Просмотр отчета** , чтобы получить данные. Если для работы с отчетом требуется войти в систему, данные, для просмотра которых имеется разрешение, могут отличаться от данных, которые видит другой пользователь. Соответственно, два пользователя могут выполнить один и тот же отчет и получить разные результаты. В дополнение: некоторые отчеты содержат скрытые области, которые открываются в зависимости от входных учетных данных пользователя или параметров, выбранных в самом отчете. Скрытые области в отчете исключаются из операций поиска, и по этой причине будут получены другие результаты поиска в случае, когда все части отчета являются видимыми.  
  
## <a name="see-also"></a>См. также  
 [Задание учетных данных и сведениях о соединении для источников данных отчета](../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Поиск, просмотр и управление отчетами &#40; Построитель отчетов и службы SSRS &#41;](../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Экспорт отчетов (построитель отчетов и службы SSRS)](../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)  
  
  