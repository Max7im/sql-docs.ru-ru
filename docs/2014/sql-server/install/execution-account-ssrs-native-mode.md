---
title: Учетная запись выполнения (собственный режим служб SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.executionaccount.F1
ms.assetid: 440b5a09-5fd4-4c3a-b510-f3c33cbf1c82
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e18c8c37eba48fa2732a07f4906137cdd299fdd3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312814"
---
# <a name="execution-account-ssrs-native-mode"></a>Учетная запись выполнения (службы Reporting Services в собственном режиме)
  Эта страница используется для настройки учетной записи, которая используется для автоматической обработки. Такая учетная запись используется в особых случаях, если недоступны другие учетные данные:  
  
-   Когда сервер отчетов соединен с источником данных, который не требует учетных данных. Примерами источников данных, для которых может не потребоваться использование учетных данных, являются XML-документы и некоторые клиентские приложения баз данных.  
  
-   Когда сервер отчетов соединен с другим сервером для получения внешних файлов изображений или других ресурсов, ссылки на которые есть в отчете.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме.  
  
 Настраивать эту учетную запись не обязательно, но, если этого не сделать, возможности использования внешних изображений и соединений с некоторыми источниками данных будут ограничены. При получении внешних файлов изображений сервер отчетов проверяет возможность анонимного соединения. Если соединение защищено паролем, сервер отчетов использует учетную запись автоматической обработки отчетов для соединения с удаленным сервером. При получении данных для отчета сервер отчетов олицетворяет текущего пользователя, запрашивает ввод пользователем учетных данных, использует сохраненные учетные данные или использует учетную запись автоматической обработки отчетов, если в свойствах соединения с источником данных в качестве типа учетных данных задано значение **Нет** . Для сервера отчетов не допускается делегирование или олицетворение учетных данных его служб при соединении с другими компьютерами, поэтому необходимо использование учетной записи автоматической обработки отчетов в случае недоступности других учетных данных.  
  
 Должна быть указана учетная запись, отличная от используемой для запуска учетной записи службы. Если она настроена, то сохраняется в файле RSReportServer.config как зашифрованное значение. При использовании сервера отчетов в конфигурации масштабного развертывания эту учетную запись необходимо настраивать одинаково на каждом из серверов отчетов.  
  
 Можно использовать любую учетную запись пользователя Windows. Для получения наилучших результатов выберите учетную запись, имеющую разрешения на чтение и на вход в сеть, для поддержки соединений с другими компьютерами. Эта учетная запись должна обладать разрешениями на чтение для любого внешнего файла изображения или данных, который необходимо использовать в отчете. Не следует определять локальную учетную запись, если все источники данных и внешние изображения, предназначенные для отчета, не хранятся на компьютере сервера отчетов. Используйте эту учетную запись только для автоматической обработки отчетов.  
  
> [!NOTE]  
>  При использовании выпуска [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] со службами Advanced Services эту учетную запись следует настраивать только в том случае, если в отчете есть ссылки на внешние изображения и для доступа к ним требуются определенные разрешения. В SQL Server Express не поддерживается соединение с источником данных на удаленном сервере. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2012](http://go.microsoft.com/fwlink/?linkid=232473).  
  
 Чтобы открыть эту страницу, запустите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager и выберите **учетная запись выполнения** в области навигации. Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Параметры  
 **Задание учетной записи выполнения**  
 Выделите учетную запись.  
  
 **Учетная запись**  
 Введите учетную запись пользователя домена Windows в следующем формате: *\<домен>\\<учетная запись пользователя\>*.  
  
 **Пароль**  
 Задайте пароль.  
  
 **Подтверждение пароля**  
 Введите пароль еще раз.  
  
## <a name="see-also"></a>См. также  
 [Разделы справки F1 диспетчера конфигурации служб Reporting Services &#40;собственный режим служб SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Хранение зашифрованных данных сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Настройка учетной записи автоматического выполнения (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
  
  