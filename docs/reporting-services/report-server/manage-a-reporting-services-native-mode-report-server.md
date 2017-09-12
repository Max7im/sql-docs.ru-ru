---
title: "Управление сервером отчетов служб Reporting собственный режим служб | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
ms.assetid: 6ca03a09-d6a8-4c93-ba12-1c99dcbfb618
caps.latest.revision: 10
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: aadfbe555fa1334f9101f799e60cccdcca7e68fd
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="manage-a-reporting-services-native-mode-report-server"></a>Управление сервером отчетов служб Reporting Services в собственном режиме
  Этот раздел содержит описание процедур по настройке экземпляра сервера отчетов в собственном режиме с использованием диспетчера конфигурации служб Reporting Services.  
  
## <a name="in-this-section"></a>В этом разделе  
 Подразделы в этом разделе организованы по категориям, что упрощает поиск необходимых инструкций. Подразделы первого раздела содержат описания основных задач по настройке конфигурации сервера отчетов, работающего в собственном режиме. Подразделы второго раздела посвящены дополнительным параметрам конфигурации. Подразделы третьего раздела помогут выполнить настройку конфигурации сервера отчетов для работы в режиме интеграции с SharePoint.  
  
### <a name="basic-configuration"></a>Основная конфигурация  
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)  
 Представляет шаги запуска программы настройки служб Reporting Services.  
  
 [Настройка учетной записи службы (диспетчер конфигурации служб SSRS)](http://msdn.microsoft.com/library/25000ad5-3f80-4210-8331-d4754dc217e0)  
 Объясняет, как задать учетную запись и пароль службы сервера отчетов.  
  
 [Регистрация имени участника-службы для сервера отчетов](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md)  
 Показывает, как вручную зарегистрировать имя участника-службы для сервера отчетов, который запускается от учетной записи пользователя домена в сети, где используется проверка подлинности по протоколу Kerberos.  
  
 [Настройка URL-адреса (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)  
 Описывает, как назначить один или несколько URL-адресов для получения доступа к веб-службе сервера отчетов и к диспетчеру отчетов.  
  
 [Создание базы данных сервера отчетов, работающего в собственном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)  
 Представляет шаги создания базы данных сервера отчетов. Этот шаг требуется для развертывания установки служб Reporting Services.  
  
### <a name="advanced-or-optional-configuration"></a>Дополнительные или необязательные параметры настройки  
 [Настройка масштабного развертывания сервера отчетов в основном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 Представляет шаги настройки нескольких серверов отчетов для совместного использования базы данных сервера отчетов.  
  
 [Настройка сервера отчетов для работы с электронной почтой (диспетчер конфигурации служб Reporting Services)](http://msdn.microsoft.com/en-us/b838f970-d11a-4239-b164-8d11f4581d83)  
 Содержит шаги настройки сервера отчетов для доставки по электронной почте.  
  
 [настроить брандмауэр для доступа к серверу отчетов](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
 Описывает, как открыть порты для передачи входящих запросов и ответов от сервера отчетов.  
  
 [Настройка сервера отчетов, работающего в основном режиме, для локального администрирования (службы SSRS)](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)  
 Описывает дополнительные действия, необходимые для подключения к диспетчеру отчетов или сервера отчетов с помощью `http://localhost`.  
  
 [Настройка сервера отчетов для удаленного администрирования](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md)  
 Описывает, как настроить экземпляр удаленного сервера отчетов для удаленного соединения и настройки с другого компьютера.  
  
 [включать и отключать компоненты служб Reporting Services](../../reporting-services/report-server/turn-reporting-services-features-on-or-off.md)  
 Объясняет, как удалить неиспользуемые компоненты после установки служб Reporting Services.  
  
 [Включение отслеживания удаленных ошибок (службы Reporting Services)](../../reporting-services/report-server/enable-remote-errors-reporting-services.md)  
 Поясняет, как задать свойства сервера на сервере отчетов для возвращения дополнительных сведений об условиях возникновения ошибок на удаленных серверах.  
  
## <a name="see-also"></a>См. также раздел  
 [Настройка и администрирование сервера отчетов (службы Reporting Services в собственном режиме)](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)   
 [Настройка и администрирование сервера отчетов &#40; Службы Reporting Services в режиме SharePoint &#41;](../../reporting-services/report-server-sharepoint/configuration-and-administration-of-a-report-server.md)  
  
  