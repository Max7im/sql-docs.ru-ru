---
title: Доставка электронной почтой в службах Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], e-mail
- e-mail [Reporting Services]
- mail [Reporting Services]
ms.assetid: fda2f130-97b9-4258-9dbb-e93a70f4d08a
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: de8849902a313391f414367ca6e51fb64c6dffdc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303544"
---
# <a name="e-mail-delivery-in-reporting-services"></a>Доставка электронной почтой в службах Reporting Services
  Службы SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают модуль доставки электронной почты, что дает возможность доставлять по электронной почте отчеты отдельным пользователям или группам пользователей. Модуль доставки электронной почты настраивается с помощью диспетчера конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и путем изменения файлов конфигурации этих служб.  
  
 Чтобы послать или получить отчет по электронной почте, вы указываете либо стандартную подписку, либо управляемую данными подписку. Можно подписаться или распространить только один отчет за один раз. Нельзя создать подписку, рассылающую несколько отчетов в одном электронном сообщении. Дополнительные сведения о подписках см. в разделе [создание, изменение и удаление стандартных подписок &#40;служб Reporting Services в собственном режиме&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint &#124; SharePoint 2010 и SharePoint 2013<br /><br /> **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме|  
  
## <a name="e-mail-delivery-options"></a>Параметры доставки электронной почты  
 Электронная почта сервера отчетов рассылает отчеты следующим образом.  
  
-   Посылает уведомление и гиперссылку на созданный отчет.  
  
-   Отправляет уведомление в поле «Тема» сообщения электронной почты. По умолчанию поле «Тема» в определении подписки включает следующие переменные, которые заменяются сведениями из отчета, когда обрабатывается подписка:  
  
     **@ReportName** указывает название отчета;  
  
     **@ExecutionTime** указывает дату выполнения отчета.  
  
     Можно объединить эти переменные со статическим текстом или изменить текст в поле «Тема» для каждой подписки.  
  
-   Посылает внедренный или прикрепленный отчет. Формат подготовки отчетов и веб-браузер определяют, является ли отчет внедренным или прикрепленным.  
  
     Если браузер поддерживает HTML 4.0 и MHTML, а вы выбираете формат подготовки отчета веб-архива, то отчет внедряется в текст сообщения. Все другие форматы подготовки отчета (CSV, PDF и т. д.) рассылают отчеты в виде вложений. Эту функцию можно отключить в файле конфигурации RSReportServer.  
  
     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не проверяют размер вложения или сообщения перед отправкой отчета. Если вложение или сообщение превышает максимальный предел, допустимый почтовым сервером, отчет не будет доставлен. Для больших отчетов выберите другой вариант доставки отчетов (например, URL-адрес или уведомление).  
  
 При создании подписки устанавливаются параметры доставки отчетов, которые определяют, как доставляется отчет. Например, при выборе в подписке параметра **Включить ссылку** электронное сообщение будет содержать гиперссылку на отчет.  
  
## <a name="role-based-e-mail-settings"></a>Настройки электронной почты, основанные на ролях  
 При подписке на отчет параметры электронной почты, с которыми вы работаете, меняются в зависимости от того, включает ли ваша роль задачу «Управление отдельными подписками» или задачу «Управление всеми подписками».  
  
|Задача|Доступные настройки|  
|----------|------------------------|  
|Управление отдельными подписками|Отображает поля, которые позволяют пользователю работать автоматически и послать отчет самому себе. В этом режиме поля, которые принимают псевдонимы электронной почты, недоступны.|  
|Управление всеми подписками|Отображает поля, которые обеспечивают более широкое распространение, включая "Кому:", "Копия:", "СК:" и "Ответить:", предоставляющие дополнительные способы направить отчет большему числу подписчиков. Доступность полей псевдонимов электронной почты определяется через параметры файла конфигурации RSReportServer.|  
  
## <a name="specifying-e-mail-addresses-in-a-subscription"></a>Указание адресов электронной почты в подписке  
 Если отчеты распространяются через корпоративную сеть, и используется шлюз SMTP к серверу [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange, введите псевдоним электронной почты (как при отправке электронного сообщения). Если доставка относится к внешней учетной записи электронной почты, введите полный адрес электронной почты. Если вы указываете дополнительные адреса электронной почты для добавления других лиц в подписку, подписчики получают точную копию отчета, созданного при этой подписке.  
  
 Сервер отчетов не проверяет адреса электронной почты и не получает адреса электронной почты с почтового сервера. Нужно знать заранее, какой адрес электронной почты будет использоваться. По умолчанию можно послать по электронной почте отчеты на любую допустимую учетную запись электронной почты в пределах или за пределами вашей организации. Установки конфигурации могут быть использованы, однако для ограничения доставки электронной почты до узлов почтового сервера, идентифицируемых по имени, можно указать дополнительные узлы, если хотите поддержать доставку электронной почты людям, которые не являются элементами вашей организации.  
  
 Электронное сообщение, используемое для доставки отчета, должно быть отправлено от имени учетной записи электронной почты, которая определяется почтовым сервером. Установка конфигурации указывает учетную запись электронной почты. Учетная запись электронной почты используется для всех отчетов, рассылаемых модулем доставки по электронной почте; нельзя указать несколько учетных записей или изменять учетную запись для отдельных отчетов.  
  
## <a name="e-mail-server-configuration"></a>Настройка почтового сервера  
 Сервер отчетов подключается к почтовому серверу через стандартное соединение. Он не использует подключение, зашифрованное с помощью Secure Sockets Layer (SSL). Почтовый сервер должен быть удаленным или локальным сервером Simple Mail Transport Protocol (SMTP), находящимся в той же сети, что и сервер отчетов.  
  
 Дополнительные сведения о настройке сервера отчетов в собственном режиме см. в следующих разделах:  
  
-   [Настройка сервера отчетов для доставки электронной почты &#40;диспетчер конфигурации служб SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
  
-   [Параметры электронной почты — Configuration Manager &#40;собственный режим служб SSRS&#41;](../install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)  
  
 Дополнительные сведения о настройке сервера отчетов в режиме интеграции с SharePoint см. в следующих разделах:  
  
-   [Настройка электронной почты для приложения служб Reporting Services &#40;SharePoint 2010 и SharePoint 2013&#41;](../install-windows/configure-e-mail-for-a-reporting-services-service-application.md)  
  
## <a name="see-also"></a>См. также  
 [Задачи и разрешения](../security/tasks-and-permissions.md)   
 [Подписки и доставка &#40;службы Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Управляемые данными подписки](data-driven-subscriptions.md)   
 [Назначения ролей](../security/role-assignments.md)  
  
  
