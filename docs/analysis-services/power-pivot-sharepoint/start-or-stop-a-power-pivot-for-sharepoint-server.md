---
title: "Запуск или остановка службы PowerPivot для SharePoint Server | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e38e6366-9f20-4db0-b2a8-da7d5adf00eb
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5f512a256765bbba4b1f641fb9752bd09fae4696
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="start-or-stop-a-power-pivot-for-sharepoint-server"></a>Запуск и остановка службы PowerPivot для SharePoint Server
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и экземпляр службы [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] работают совместно на одном и том же локальном сервере приложений, обеспечивая поддержку согласованной обработки запросов и данных на ферме SharePoint.  
  
 Этот раздел состоит из следующих подразделов.  
  
 [Зависимости служб](#dependencies)  
  
 [Запуск и остановка служб](#startstop)  
  
 [Последствия остановки сервера службы PowerPivot](#effects)  
  
##  <a name="dependencies"></a> Зависимости служб  
 Системная служба [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] зависит от локального экземпляра сервера Analysis Services, установленного на том же физическом сервере. При остановке системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] необходимо также вручную остановить локальный экземпляр сервера Analysis Services. Если одна служба работает без другой, то возникают ошибки выделения ресурсов для обработки данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
 Сервер Analysis Services должен работать самостоятельно только в случае диагностики или устранения неполадок. Во всех остальных случаях серверу необходима системная служба [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , которая работает локально на том же сервере.  
  
##  <a name="startstop"></a> Запуск и остановка служб  
 Всегда пользуйтесь центром администрирования для запуска или остановки системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и экземпляра сервера Analysis Services. Центр администрирования дает возможность останавливать и запускать эти службы одновременно с одной страницы. Кроме того, в нем предусмотрено задание таймера **Запуск или остановка одной или нескольких служб** , используемое для перезапуска служб, которые, как он полагает, должны работать. Если системная служба [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] или службы Analysis Services остановлены с помощью других средств, не входящих в SharePoint, то они будут перезапущены при срабатывании задания таймера.  
  
 Запуск и остановка служб — это действие, относящееся к физическому экземпляру службы. Если на ферме есть дополнительные серверы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, другие серверы на ферме продолжат принимать запросы на данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
 Нельзя останавливать или запускать все физические службы фермы одновременно. Необходимо выбирать каждый сервер и только тогда запускать или останавливать конкретную службу.  
  
 Нельзя запустить, приостановить или остановить системную службу [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для определенного веб-приложения, но можно удалить службу из списка подключений по умолчанию, чтобы сделать ее недоступной. Дополнительные сведения см. в разделе [Подключение приложения службы PowerPivot к веб-приложению SharePoint в центре администрирования](../../analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md).  
  
1.  В центре администрирования в разделе **Системные параметры**нажмите **Управление службами на сервере**.  
  
2.  В разделе «Сервер» в верхней части страницы щелкните стрелку вниз и выберите пункт **Изменить сервер**.  
  
3.  Выберите сервер SharePoint, который имеет системную службу [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] или экземпляр [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] , который необходимо запустить или остановить.  
  
4.  Выберите службу и затем действие. Не забывайте запускать или останавливать службы парами. При запуске или остановке системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] убедитесь, что экземпляр сервера Analysis Services, работающий на том же компьютере, также запущен или остановлен.  
  
##  <a name="effects"></a> Последствия остановки сервера службы PowerPivot  
 В следующей таблице описываются последствия остановки системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и служб Analysis Services на сервере SharePoint.  
  
|Воздействие на аргумент|Description|  
|---------------|-----------------|  
|Существующие запросы|Запросы, выполняемые на сервере Analysis Services, будут немедленно остановлены. Пользователь получит сообщение об ошибке «Данные не обнаружены» или «Соединение с источником данных отсутствует».|  
|Существующие задания обновления данных, обрабатываемые в данные момент|Задания, выполняемые на текущем сервере Analysis Services, будут немедленно остановлены. Обновление данных завершится с ошибкой, и в журнале обновления данных появится запись об ошибке.<br /><br /> Перед остановкой службы можно просмотреть состояние текущих заданий, используя страницу проверки состояния задания в центре администрирования SharePoint.<br /><br /> Даже если известно, какие задания выполняются в данный момент, невозможно посмотреть саму очередь, чтобы узнать, какие другие задания будут вскоре запущены.|  
|Существующие данные обновляют запросы в очереди|Запросы на обновление данных по расписанию остаются в очереди на обработку на протяжении всего цикла расписания (т. е. они остаются в очереди до следующего запуска). Если к тому времени системная служба [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] не перезапущена, запрос на обновление данных будет удален и в журнале будет сделана запись об ошибке.|  
|Новые запросы на данные или обновление данных|Если на ферме только один сервер [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint и он останавливается, новые запросы для данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] не будут обрабатываться и при попытке запросить данные будет выдаваться ошибка "Данные не найдены".<br /><br /> Если есть дополнительные серверы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, запрос будет передан на один из доступных серверов.|  
|Данные об использовании|Когда службы остановлены, данные об использовании не собираются.|  
  
## <a name="see-also"></a>См. также  
 [Настройка учетных записей служб Power Pivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)  
  
  