---
title: "Доступ по URL-АДРЕСУ (SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- URL access [Reporting Services]
- links [Reporting Services], URL access
- URL access [Reporting Services], about URL access
- parameters [Reporting Services], URL access
- report servers [Reporting Services], URL access
- hyperlinks [Reporting Services]
ms.assetid: 52c3f2a3-3d6d-4fee-9c46-83f366919398
caps.latest.revision: 43
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f91b97d1877e365813f3aa2445fabea1a263ab2b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="url-access-ssrs"></a>Доступ по URL-адресу (SSRS)
  Доступ по URL-адресу сервера отчетов в службах SQL Server Reporting Services (SSRS) позволяет отправлять команды серверу отчетов посредством запроса по URL-адресу. Например, можно настроить подготовку отчета на сервере отчетов, работающем в собственном режиме, или в библиотеке SharePoint. Ранее пользователи могли просматривать отчет с использованием определенного набора значений параметров отчета или просматривать только определенную представляющую интерес страницу отчета. Эти сведения можно инкапсулировать в URL адрес, используя параметры доступа по URL-адресу. Обработку отчета сервером отчетов можно настроить более подробно, внедрив параметры для форматов подготовки к просмотру или для внешнего вида обозревателя отчетов. Затем созданный URL-адрес можно непосредственно вставлять в электронное письмо или веб-страницу, чтобы дать возможность другим пользователям просматривать отчет в браузере в том же формате.  
  
 Другие действия, которые можно осуществлять посредством доступа по URL-адресу:  
  
-   Отправка команд средству просмотра HTML-страниц, например, для настройки внешнего вида  
  
-   Составление списка дочерних элементов папки каталога  
  
-   Получение XML-определения элемента каталога  
  
-   Подготовка определенного моментального снимка журнала отчета  
  
-   Управление сеансами отчетов  
  
 Полный список команд и параметров, применимых при доступе через URL-адрес, см. в разделе [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md).  
  
## <a name="url-access-concepts"></a>Основные понятия доступа через URL-адрес  
 Запросы по URL-адресу к серверу отчетов содержат параметры, обрабатываемые сервером отчетов. Способ обработки сервером отчетов запросов по URL-адресу зависит от параметров, префиксов параметров и от типов элементов, включенных в URL-адрес. URL-адреса серверов отчетов соответствуют рекомендациям по форматированию URL-адресов, изложенным в проекте стандарта, разработанном совместно специалистами W3C и IETF. В том, что касается URL-адресов, службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] по своим функциональным возможностям совместимы с большинством Интернет-браузеров или приложений, соответствующих стандарту адресации с использованием URL.  
  
### <a name="url-access-syntax"></a>Синтаксис доступа по URL-адресу  
 В запросах по URL-адресам могут содержаться несколько параметров, перечисленных в любом порядке. Параметры разделяются амперсандом (&); пары имя/значение разделяются знаком равенства (=).  
  
```  
  
rswebserviceurl  
?  
reportpath  
      [&prefix:param=value]...n]  
  
```  
  
### <a name="syntax-description"></a>Описание синтаксиса  
 *rswebserviceurl*  
 URL-адрес веб-службы сервера отчетов. При работе в основном режиме — URL-адрес веб-службы экземпляра сервера отчетов, настроенный в диспетчере конфигурации служб Reporting Services (см. статью [Настройка URL-адресов сервера отчетов (диспетчер конфигурации служб SSRS)](../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)). Например:  
  
```  
http://myrshost/reportserver  
https://machine.adventure-works.com/reportserver_MYNAMEDINSTANCE  
```  
  
 При работе в режиме интеграции с Sharepoint — URL-адрес прокси-сервера [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] на сайте SharePoint, интегрированном со службами [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Например:  
  
```  
http://myspsite/subsite/_vti_bin/reportserver  
```  
  
> [!TIP]  
>  Важно, чтобы URL-адрес содержал синтаксис прокси `_vti_bin` для отправки запроса с помощью центра администрирования SharePoint и прокси-сервера HTTP [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Прокси-сервер добавляет в HTTP-запрос контекст, необходимый для обеспечения правильного выполнения отчета для серверов отчетов в режиме интеграции с SharePoint.  
  
 *pathinfo*  
 Имя относительного пути элемента в базе данных сервера отчетов, работающем в собственном режиме, или полный URL-адрес элемента в каталоге SharePoint.  
  
 Путь элемента в каталоге. При работе в основном режиме — относительный путь элемента в базе данных сервера отчетов, начиная с символа косой черты (**/**). Например:  
  
```  
/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2  
```  
  
 При работе в режиме интеграции с Sharepoint — полный URL-адрес элемента в библиотеке SharePoint, включая расширение элемента. Например:  
  
```  
http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl  
```  
  
 **&**  
 Используется для разделения пар имен и значений в параметрах URL-адреса.  
  
 **prefix**  
 Необязательно. Префикс для параметра доступа по URL-адресу (например, `rs:` или `rc:`), обращающийся к определенному процессу, который выполняется на сервере отчетов.  
  
> [!NOTE]  
>  Если префикс параметра доступа по URL-адресу не указан, то параметр обрабатывается сервером отчетов как параметр отчета. В параметрах отчета не используется префикс параметров и учитывается регистр.  
  
 **param**  
 Имя параметра.  
  
 *value*  
 Текст URL-адреса, соответствующий значению используемого параметра.  
  
 **Примечание.** Список доступных параметров для доступа по URL-адресу см. в статье [URL Access Parameter Reference](../reporting-services/url-access-parameter-reference.md). Примеры передачи параметров отчета в URL-адресе см. в разделе [Pass a Report Parameter Within a URL](../reporting-services/pass-a-report-parameter-within-a-url.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описания задач|Ссылки|  
|-----------------------|-----------|  
|Доступ к элементам сервера отчетов, например, отчетам, общим источникам данных и ресурсам.|[Доступ к элементам сервера отчетов с помощью URL-адресов](../reporting-services/access-report-server-items-using-url-access.md)|  
|Передача отчету параметров отчета.|[Передать параметр отчета в URL-адрес](../reporting-services/pass-a-report-parameter-within-a-url.md)|  
|Задание локали для параметров отчета в строке доступа по URL-адресу, определяющей уникальные для локали форматы дат, валют и т.п.|[Выбранный язык для параметров отчета в URL-адрес](../reporting-services/set-the-language-for-report-parameters-in-a-url.md)|  
|Отправка настроек, уникальных для модуля подготовки отчетов, которые влияют на процесс подготовки.|[Указать настройки сведений об устройстве в URL-адрес](../reporting-services/specify-device-information-settings-in-a-url.md)|  
|Экспорт отчета непосредственно в формате файла, без просмотра в браузере.|[Экспорт отчета с помощью URL-адресов](../reporting-services/export-a-report-using-url-access.md)|  
|Открытие отчета и переход непосредственно к месту расположения строки.|[Поиск отчета с помощью URL-адресов](../reporting-services/search-a-report-using-url-access.md)|  
|Подготовка определенного моментального снимка журнала отчета.|[Обработка моментального снимка журнала отчета с помощью URL-адресов](../reporting-services/render-a-report-history-snapshot-using-url-access.md)|  
  
## <a name="see-also"></a>См. также  
 [Передать параметр отчета в URL-адрес](../reporting-services/pass-a-report-parameter-within-a-url.md)   
 [Ссылка на параметр доступа URL-адрес](../reporting-services/url-access-parameter-reference.md)   
 [Интеграция служб Reporting Services с помощью URL-адресов](../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [Поиск, просмотр и управление отчетами &#40; Построитель отчетов и службы SSRS &#41;](../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  