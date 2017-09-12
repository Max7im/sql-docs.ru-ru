---
title: "Настройки сведений об устройстве PDF | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], PDF rendering
- PDF [Reporting Services]
ms.assetid: 9a4aabe5-dbdc-4884-b999-1200983fee47
caps.latest.revision: 41
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e02ae92cfb973c7287fde080628fcc26cb784276
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="pdf-device-information-settings"></a>Настройки сведений об устройстве PDF
  В следующей таблице перечислены настройки сведений об устройстве, предназначенные для подготовки отчетов к просмотру в формате PDF.  
  
|Настройка|Значение|  
|-------------|-----------|  
|**Столбцы**|Задаваемое число столбцов в отчете. Это значение переопределяет исходные параметры отчета.|  
|**ColumnSpacing**|Интервал между столбцами, который должен быть задан для отчета. Это значение переопределяет исходные параметры отчета.|  
|**DpiX**|Разрешение устройства вывода по оси x.|  
|**DpiY**|Разрешение устройства вывода по оси y.|  
|**EndPage**|Последняя подготавливаемая к просмотру страница отчета. Значением по умолчанию является значение для **StartPage**.|  
|**HumanReadablePDF**|Показывает, необходимо ли производить сжатие PDF-файла, что упростит чтение исходные данные. Значение по умолчанию — **false.**|  
|**MarginBottom**|Задаваемая ширина нижнего поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, 1in). Это значение переопределяет исходные параметры отчета.|  
|**MarginLeft**|Задаваемая ширина левого поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, 1in). Это значение переопределяет исходные параметры отчета.|  
|**MarginRight**|Задаваемая ширина правого поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, 1in). Это значение переопределяет исходные параметры отчета.|  
|**MarginTop**|Задаваемая ширина верхнего поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, 1in). Это значение переопределяет исходные параметры отчета.|  
|**PageHeight**|Задаваемая высота страницы отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, 11in). Это значение переопределяет исходные параметры отчета.|  
|**PageWidth**|Задаваемая ширина страницы отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка «in» (например, 8,5in). Это значение переопределяет исходные параметры отчета.|  
|**StartPage**|Первая подготавливаемая к просмотру страница отчета. Значение **0** указывает, что к просмотру подготовлены все страницы. Значение по умолчанию — **1**.|  
  
## <a name="see-also"></a>См. также  
 [Передача настроек сведений об устройстве для модулей подготовки отчетов](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модуля подготовки отчетов в RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник по &#40; Службы SSRS &#41;](../reporting-services/technical-reference-ssrs.md)  
  
  