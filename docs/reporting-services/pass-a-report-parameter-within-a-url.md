---
title: "Передать параметр отчета в URL-адрес | Документы Microsoft"
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
helpviewer_keywords:
- URL access [Reporting Services], passing parameters
- passing parameters [Reporting Services]
ms.assetid: f93a94cc-27b5-435a-aa85-69e6ec6459ad
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e3b076b74a6082e34dc9c489c0383fd6a5c3bd4f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="pass-a-report-parameter-within-a-url"></a>Передать параметр отчета в URL-адресе
  Чтобы передать параметры в отчет, можно включить их в URL-адрес отчета. Такие параметры URL-адреса не снабжаются префиксами, поскольку они передаются непосредственно в подсистему обработки отчетов.  
  
> [!IMPORTANT]  
>  Важно, чтобы URL-адрес содержал синтаксис прокси `_vti_bin` для отправки запроса с помощью центра администрирования SharePoint и прокси-сервера HTTP [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Прокси-сервер добавляет в HTTP-запрос контекст, необходимый для обеспечения правильного выполнения отчета для серверов отчетов в режиме интеграции с SharePoint.  
>   
>  Если не указывать синтаксис прокси, то нужно добавить к параметру префикс *rp:*.  
  
 Все параметры запроса могут иметь соответствующие параметры отчета. Параметр запроса можно передать в отчет. Дополнительные сведения см. в статье [Построение запроса в конструкторе реляционных запросов (построитель отчетов и службы SSRS)](../reporting-services/report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).  
  
> [!IMPORTANT]  
>  В параметрах отчета учитывается регистр символов.  
  
> [!NOTE]  
>  Параметры отчета учитывают регистр символов и используют следующие специальные символы:  
>   
>  -   Все пробельные символы в строке URL-адресов заменяются символами «%20» в соответствии со стандартами кодировки URL-адресов.  
> -   Пробел в секции параметров URL-адреса заменяется символом плюса (+).  
> -   Точка с запятой в любой части строки заменяется символами «%3A».  
> -   Браузер должен автоматически выполнить необходимую кодировку URL-адреса. Пользователю нет необходимости выполнять кодировку символов вручную.  
  
 Чтобы задать параметр отчета в URL-адресе, используйте следующий синтаксис:  
  
```  
  
parameter=value  
```  
  
 Например, чтобы указать параметры ReportMonth и ReportYear, заданные в отчете, используйте следующий URL-адрес для сервера отчетов, работающего в собственном режиме:  
  
```  
http://myrshost/ReportServer?/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2&ReportMonth=3&ReportYear=2008  
```  
  
 Например, чтобы указать те же два параметра, заданные в отчете, используйте следующий URL-адрес для сервера отчетов, работающего в режиме интеграции c SharePoint. Обратите внимание на `/_vti_bin`!  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl&ReportMonth=3&ReportYear=2008  
```  
  
 Чтобы задать параметру значение NULL, используйте следующий синтаксис:  
  
```  
  
parameter  
:isnull=true  
  
```  
  
 Например:  
  
```  
SalesOrderNumber:isnull=true  
```  
  
 Чтобы задать значение **Boolean** , используйте 0 для значения ложь и 1 для значения верно. Чтобы задать значение **Float** , включите десятичный разделитель для языкового стандарта сервера  
  
> [!NOTE]  
>  Если отчет содержит параметр отчета, имеющий значение по умолчанию, а свойство **Prompt** имеет значение **false** (то есть в диспетчере отчетов не выбрано свойство Подсказка пользователю), передать значение этого параметра отчета в URL-адресе невозможно. Это позволяет администраторам запретить пользователям добавлять и изменять значения определенных параметров отчета.  
  
##  <a name="bkmk_examples"></a> Дополнительные примеры  
 В следующем примере URL-адрес содержит пробелы и многозначные параметры.  
  
-   Имя папки «Группы образования пользователя SQL Server» содержит пробелы, которые заменяются знаком «+».  
  
-   Имя отчета «Отчет по командному проекту» содержит пробелы, которые заменяются знаком «+».  
  
-   Передает два параметра: «teamgrouping2» со значением «xgroup» и «teamgrouping1» со значением «ygroup».  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup  
```  
  
 В следующем примере URL-адрес содержит многозначный параметр «OrderID». Формат многозначного параметра должен повторять имя параметра для каждого значения.  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup&OrderID=747&OrderID=787&OrderID=12  
```  
  
 В следующем примере URL-адреса передается один параметр *SellStartDate* со значением "1.7.2005" для сервера отчетов, работающего в основном режиме.  
  
```  
http://myserver/ReportServer/Pages/ReportViewer.aspx?%2fProduct_and_Sales_Report_AdventureWorks&SellStartDate=7/1/2005  
```  
  
## <a name="see-also"></a>См. также  
 [Доступ к URL-адрес &#40; Службы SSRS &#41;](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа URL-адрес](../reporting-services/url-access-parameter-reference.md)  
  
  