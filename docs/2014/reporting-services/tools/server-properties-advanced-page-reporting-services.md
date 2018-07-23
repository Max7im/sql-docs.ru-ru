---
title: Свойства сервера (страница "Дополнительно") — службы Reporting Services | Документация Майкрософт
ms.custom: ''
ms.date: 2016-10-18
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.advanced.f1
ms.assetid: 07b78a84-a6aa-4502-861d-349720ef790e
caps.latest.revision: 16
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8b8459ccb49c2e8d2d681cada3646d7d9aa447b5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37258130"
---
# <a name="server-properties-advanced-page---reporting-services"></a>Свойства сервера (страница «Дополнительно») — службы Reporting Services
  На этой странице можно задавать системные свойства сервера отчетов. Установить системные свойства можно несколькими способами. Данное средство предоставляет графический пользовательский интерфейс, позволяющий задавать свойства без необходимости написания кода.  
  
 Чтобы открыть эту страницу, в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру сервера отчетов, щелкните его правой кнопкой мыши и выберите пункт **Свойства**. Чтобы открыть эту страницу, нажмите кнопку **Дополнительно** .  
  
## <a name="options"></a>Параметры  
 **EnableMyReports**  
 Указывает, разрешено ли применение функции «Мои отчеты». Значение `true` указывает, что эта функция включена.  
  
 **MyReportsRole**  
 Имя роли, которая использовалась при создании политик безопасности для папок «Мои отчеты» пользователя. Значение по умолчанию — `My Reports Role`.  
  
 **EnableClientPrinting**  
 Определяет, доступен ли элемент управления ActiveX RSClientPrint для загрузки с сервера отчетов. Допустимые значения: `true` и `false`. Значение по умолчанию — `true`. Сведения о дополнительных настройках, необходимых для данного элемента управления, см. в разделе [Включение и отключение печати на стороне клиента для служб Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
 **EnableExecutionLogging**  
 Указывает, включено ли ведение журнала выполнения отчета. Значение по умолчанию — `true`. Дополнительные сведения о журнале выполнения сервера отчетов, см. в разделе [журнал выполнения сервера отчетов и представление ExecutionLog3](../report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
 **ExecutionLogDaysKept**  
 Количество суток, в течение которых необходимо хранить сведения о выполнении отчетов в журнале выполнения. Допустимые значения для этого свойства: `-1` через `2`,`147`,`483`,`647`. При значении, равном `-1`, записи из таблицы журнала выполнения не удаляются. Значение по умолчанию — `60`.  
  
 **SessionTimeout**  
 Продолжительность времени в секундах, в течение которого сеанс остается активным. Значение по умолчанию — `600`.  
  
 **SharePointIntegratedMode**  
 Это свойство доступно только для чтения и определяет режим работы сервера. Значение false означает, что сервер отчетов запущен в собственном режиме.  
  
 **SiteName**  
 Имя сайта сервера отчетов, отображаемое в заголовке страницы диспетчера отчетов. Значение по умолчанию — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Значением этого свойства может быть пустая строка. Максимальная длина составляет 8000 символов.  
  
 **StoredParametersLifetime**  
 Максимальное количество суток, в течение которых может храниться хранимый параметр. Допустимые значения: `-1`, `+1` через `2,147,483,647`. Значение по умолчанию — `180` дней.  
  
 **StoredParametersThreshold**  
 Максимальное количество значений параметра, которые могут быть сохранены на сервере отчетов. Допустимые значения: `-1`, `+1` через `2,147,483,647`. Значение по умолчанию — `1500`.  
  
 **UseSessionCookies**  
 Указывает, должны ли использоваться куки-файлы сеанса на сервере отчетов при обмене данными с браузерами клиентов. Значение по умолчанию — `true`.  
  
 **ExternalImagesTimeout**  
 Определяет время, в течение которого должен быть получен внешний файл изображения, прежде чем истечет время ожидания соединения. Значение по умолчанию — `600` секунд.  
  
 **SnapshotCompression**  
 Определяет, как происходит сжатие моментальных снимков. Значение по умолчанию — `SQL`. Допустимы следующие значения.  
  
 **SQL=** — моментальные снимки сжимаются при сохранении в базе данных сервера отчетов. Это текущая настройка поведения.  
  
 **Нет** — моментальные снимки не сжимаются.  
  
 **Все** — моментальные снимки сжимаются во всех вариантах хранения, в том числе в базе данных сервера отчетов и в файловой системе.  
  
 **SystemReportTimeout**  
 Применяемое по умолчанию значение времени ожидания обработки отчетов в секундах для всех отчетов, управляемых в пространстве имен сервера отчетов. Это значение может быть переопределено на уровне отчета. Если это свойство задано, сервер отчетов пытается остановить обработку отчета по истечении указанного времени. Допустимые значения: `-1` через `2`,`147`,`483`,`647`. Если значение равно `-1`, то при обработке отчетов в пространстве имен время ожидания не истекает. Значение по умолчанию — `1800`.  
  
 **SystemSnapshotLimit**  
 Максимальное количество моментальных снимков, которые хранятся для отчета. Допустимые значения: `-1` через `2`,`147`,`483`,`647`. Если значение равно `-1`, не ограничено моментального снимка.  
  
 **EnableIntegratedSecurity**  
 Определяет, поддерживается ли встроенная безопасность Windows для соединений с источниками данных отчетов. Значение по умолчанию — `True`. Допустимы следующие значения.  
  
 `True` = встроенная безопасность Windows включена.  
  
 `False` = встроенная безопасность Windows отключена. Источники данных отчета, настроенные для использования встроенной безопасности Windows, не будут запущены.  
  
 `EnableLoadReportDefinition`  
 Этот параметр определяет, могут ли пользователи выполнять нерегламентированные запросы из отчета построителя отчетов. Этот параметр определяет значение `EnableLoadReportDefinition` свойство на сервере отчетов.  
  
 Если отключить этот параметр, свойству будет присвоено значение false, и сервер отчетов не будет формировать отчеты с дополнительной информацией, в которых в качестве источника данных используется модель отчета. Любые вызовы метода LoadReportDefinition будут блокированы.  
  
 Отключение этого параметра снижает угрозу, при которой пользователи-злоумышленники запускают атаку типа «отказ в обслуживании», перегружая сервер отчетов запросами LoadReportDefinition.  
  
 **EnableRemoteErrors**  
 Включает информацию о внешних ошибках (например, информацию об ошибках в источниках данных для отчетов) в сообщения об ошибках, которые были возвращены пользователям, запрашивающим отчеты из удаленных компьютеров. Допустимые значения: `true` и `false`. Значение по умолчанию — `false`. Дополнительные сведения см. в разделе [Включение отслеживания удаленных ошибок (службы Reporting Services)](../report-server/enable-remote-errors-reporting-services.md).  
  
 **EnableReportDesignClientDownload**  
 Указывает, возможна ли загрузка пакета установки построителя отчетов с сервера отчетов. Если этот флажок снят, URL-адрес построителя отчетов окажется недействующим. Дополнительные сведения см. в разделе [Настройка доступа к построителю отчетов](../report-server/configure-report-builder-access.md).  
  
 **EditSessionCacheLimit**  
 Указывает количество записей кэша данных, которые могут быть активны в сеансе изменения отчета. По умолчанию количество задается равным 5.  
  
 **EditSessionTimeout**  
 Указывает время (в секундах) до завершения сеанса изменения отчета. Значение по умолчанию равно 7200 секундам (2 часам).  
  
 **EnableTestConnectionDetailedErrors**  
 Указывает, отправляются ли подробные сообщения об ошибках на клиентские компьютеры при использовании пользователями сервера отчетов для проверки соединения с источниками данных. Значение по умолчанию — `true`. Если включен режим `false`, отправляются только общие сообщения об ошибках.  
  
## <a name="see-also"></a>См. также  
 [Установка свойств сервера отчетов (среда Management Studio)](set-report-server-properties-management-studio.md)   
 [Подключение к серверу отчетов в среде Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Свойства Reporting Services](../report-server-web-service/net-framework/reporting-services-properties.md)   
 [Справка F1 по использованию сервера отчетов среде Management Studio](report-server-in-management-studio-f1-help.md)   
 [Свойства системы сервера отчетов](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)   
 [Написание скриптов для задач развертывания и администрирования](script-deployment-and-administrative-tasks.md)   
 [Включение и отключение рабочего пространства "Мои отчеты"](../report-server/enable-and-disable-my-reports.md)  
  
  