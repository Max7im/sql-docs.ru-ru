---
title: "Регистрация имени участника-службы (SPN) для сервера отчетов | Документы Microsoft"
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
ms.assetid: dda91d4f-77cc-4898-ad03-810ece5f8e74
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9518d1bd3ee166a0f21292ca08130214afc841be
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="register-a-service-principal-name-spn-for-a-report-server"></a>зарегистрировать имя участника-службы для сервера отчетов
  При развертывании служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в сети, где для взаимной проверки подлинности используется протокол Kerberos, а сервер отчетов настроен для запуска от учетной записи пользователя домена, необходимо создать для службы сервера отчетов имя участника-службы (SPN).  
  
## <a name="about-spns"></a>Сведения об именах участников-служб  
 Имя участника-службы представляет собой уникальный идентификатор службы в сети, использующей проверку подлинности по протоколу Kerberos. Оно состоит из класса службы, имени узла и номера порта. В сети с проверкой подлинности по протоколу Kerberos имя участника-службы для сервера должно быть зарегистрировано либо со встроенной учетной записью компьютера (например, «Сетевая служба» или «Локальная система»), либо с учетной записью пользователя. Регистрация имен участников-служб для встроенных учетных записей производится автоматически. Если же служба запускается от учетной записи пользователя домена, необходимо вручную зарегистрировать имя участника-службы для применяемого типа учетной записи.  
  
 Чтобы создать имя субъекта-службы, можно воспользоваться программой командной строки **SetSPN** . Дополнительные сведения см. в следующих разделах:  
  
-   [Setspn](http://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (http://technet.microsoft.com/library/cc731241(WS.10).aspx).  
  
-   [Синтаксис имен субъектов-служб (SPN) SetSPN (Setspn.exe)](http://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (http://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx).  
  
 Для ее запуска на контроллере домена необходимо быть администратором домена.  
  
## <a name="syntax"></a>Синтаксис  
 Синтаксис команд, применяющийся в программе SetSPN для создания имени участника-службы для сервера отчетов, выглядит следующим образом.  
  
```  
Setspn -s http/<computername>.<domainname>:<port> <domain-user-account>  
```  
  
 **SetSPN** входит в комплект Windows Server. Аргумент **-s** добавляет имена субъектов-служб после проверки на отсутствие дубликатов. **Примечание. -s** доступен в Windows Server, начиная с Windows Server 2008.  
  
 **HTTP** — класс службы. Веб-служба сервера отчетов работает в компоненте HTTP.SYS. Создание имени участника-службы для компонента HTTP имеет один побочный эффект: всем веб-приложениям, запускаемым компонентом HTTP.SYS (включая размещенные в службе IIS), будут предоставляться билеты на основе учетной записи пользователя домена. Если эти службы запускаются от имени других учетных записей, то запросы на проверку подлинности будут завершаться ошибкой. Чтобы избежать этой проблемы, необходимо настроить все HTTP-приложения для запуска от одной и той же учетной записи либо назначить для каждого из приложений заголовок, а для каждого из узлов создать отдельное имя участника-службы. При настройке заголовков узлов изменения в DNS придется вносить вне зависимости от настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Значения, заданные для \< *computername*>, \< *domainname*>, и \< *порт*> определяют уникальный сетевой адрес компьютера, на котором размещен сервер отчетов. Это может быть как локальное имя узла, так и полное доменное имя. Если вы только один домен и используется порт 80, можно опустить \< *domainname*> и \< *порт*> командной строки. \<*Учетная запись пользователя домена*> является учетная запись пользователя, под которой выполняется служба сервера отчетов, для которого необходимо зарегистрировать имя участника-службы.  
  
## <a name="register-an-spn-for-domain-user-account"></a>Регистрация имени участника-службы для учетной записи пользователя домена  
  
#### <a name="to-register-an-spn-for-a-report-server-service-running-as-a-domain-user"></a>Регистрация имени участника-службы для службы сервера отчетов, которая запускается от имени пользователя домена  
  
1.  Установите службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и настройте службу сервера отчетов для запуска от учетной записи пользователя домена. Не забывайте, что пользователи не смогут соединиться с сервером отчетов до тех пор, пока не будут выполнены все описанные ниже шаги.  
  
2.  Войдите на контроллер домена как администратор домена.  
  
3.  Откройте окно командной строки.  
  
4.  Скопируйте следующую команду, заменив заполнители значениями для конкретной сети:  
  
    ```  
    Setspn -s http/<computer-name>.<domain-name>:<port> <domain-user-account>  
    ```  
  
     Например: `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`  
  
5.  Выполните команду.  
  
6.  Откройте файл **RsReportServer.config** и найдите раздел `<AuthenticationTypes>` .  
  
7.  Добавьте `<RSWindowsNegotiate/>` в качестве первой записи этого раздела для включения NTLM.  
  
## <a name="see-also"></a>См. также  
 [Настройка учетной записи службы &#40; Диспетчер конфигурации служб SSRS &#41;](http://msdn.microsoft.com/library/25000ad5-3f80-4210-8331-d4754dc217e0)   
 [Настройка учетной записи службы сервера отчетов &#40; Диспетчер конфигурации служб SSRS &#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Управление сервером отчетов служб Reporting собственный режим служб](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  