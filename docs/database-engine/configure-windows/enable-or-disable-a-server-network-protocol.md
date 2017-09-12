---
title: "Включение или отключение сетевого протокола сервера | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network protocols [SQL Server], disabling
- remote connections [SQL Server], enabling using Configuration Manager
- protocols [SQL Server], enabling using Configuration Manager
- protocols [SQL Server], disabling using Configuration Manager
- disabling network protocols, Configuration Manager
- network protocols [SQL Server], enabling
- enabling network protocols, Configuration Manager
- surface area configuration [SQL Server], connection protocols
- connections [SQL Server], enabling remote using Configuration Manager
ms.assetid: ec5ccb69-61c9-4576-8843-014b976fd46e
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7bb0a9abeba4730bd2d5d4e57cd7b02b2b93b55c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# Включение или отключение сетевого протокола сервера
  Все сетевые протоколы устанавливаются программой установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но некоторые могут быть включены, а некоторые — нет. В этом разделе описано, как включить или отключить сетевой протокол сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или PowerShell. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] необходимо остановить и перезапустить, чтобы изменения вступили в силу.  
  
> [!IMPORTANT]  
>  Во время установки [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] для группы BUILTIN\Users добавляется имя входа. Благодаря этому все прошедшие проверку подлинности пользователи компьютера получают доступ к экземпляру [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] как члены роли public. Имя входа группы BUILTIN\Users можно удалить, чтобы ограничить доступ к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] только пользователям компьютера, у которых есть отдельные имена входа, или членам других групп Windows с именами входа.  
  
> [!WARNING]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и поставщики данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживают протоколы TLS 1.0 и SSL 3.0. Если применить другой протокол (например, TLS 1.1 или TLS 1.2), внеся изменения на уровне операционной системы SChannel, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может возникнуть ошибка.  
  
 **В этом разделе**  
  
-   **Включение или отключение сетевого протокола сервера с использованием следующего.**  
  
     [Диспетчер конфигурации SQL Server](#SSMSProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### Включение протокола SNP  
  
1.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на панели консоли раскройте **Сетевая конфигурация SQL Server**.  
  
2.  В области консоли щелкните **Протоколы для** *\<имя_экземпляра>*.  
  
3.  В области сведений щелкните правой кнопкой мыши протокол, который необходимо переключить, затем выберите **Включить** или **Отключить**.  
  
4.  В области консоли выберите **Службы SQL Server**.  
  
5.  В области сведений щелкните правой кнопкой мыши **SQL Server (***\<имя экземпляра>***)**, а затем нажмите кнопку **Перезапустить**, чтобы остановить и перезагрузить службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="PowerShellProcedure"></a> Использование SQL Server PowerShell  
  
#### Включение сетевого протокола сервера с использованием PowerShell  
  
1.  Откройте командную строку с использованием разрешений администратора.  
  
2.  Запустите Windows PowerShell из панели задач или нажмите кнопку "Пуск", а затем последовательно выберите "Все программы", "Стандартные", "Windows PowerShell" и "Windows PowerShell".  
  
3.  Импортируйте модуль **sqlps** , введя команду **Import-Module "sqlps"**  
  
4.  Выполните следующие инструкции, чтобы включить протокол TCP и протокол именованных каналов. Замените `<computer_name>` именем компьютера, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если настраивается именованный экземпляр, замените `MSSQLSERVER` именем экземпляра.  
  
     Чтобы отключить протоколы, установите для свойства `IsEnabled` значение `$false`.  
  
    ```  
    $smo = 'Microsoft.SqlServer.Management.Smo.'  
    $wmi = new-object ($smo + 'Wmi.ManagedComputer').  
  
    # List the object properties, including the instance names.  
    $Wmi  
  
    # Enable the TCP protocol on the default instance.  
    $uri = "ManagedComputer[@Name='<computer_name>']/ ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
    $Tcp = $wmi.GetSmoObject($uri)  
    $Tcp.IsEnabled = $true  
    $Tcp.Alter()  
    $Tcp  
  
    # Enable the named pipes protocol for the default instance.  
    $uri = "ManagedComputer[@Name='<computer_name>']/ ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Np']"  
    $Np = $wmi.GetSmoObject($uri)  
    $Np.IsEnabled = $true  
    $Np.Alter()  
    $Np  
    ```  
  
#### Настройка протоколов на локальном компьютере  
  
-   Если скрипт запускается локально и настраивает локальный компьютер, с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell можно сделать скрипт более гибким, динамически определяя имя локального компьютера. Для получения имени локального компьютера замените строку, устанавливающую переменную `$uri` , следующей строкой.  
  
    ```  
    $uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
    ```  
  
#### Перезапуск компонента Database Engine с использованием SQL Server PowerShell  
  
-   После включения или отключения протоколов необходимо остановить и перезапустить компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] , чтобы эти изменения вступили в действие. Выполните следующие инструкции, чтобы остановить и запустить экземпляр по умолчанию с использованием [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell. Чтобы остановить и запустить именованный экземпляр, замените `'MSSQLSERVER'` на `'MSSQL$<instance_name>'`.  
  
    ```  
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\<computer_name>  
    $Wmi = (get-item .).ManagedComputer  
    # Get a reference to the default instance of the Database Engine.  
    $DfltInstance = $Wmi.Services['MSSQLSERVER']  
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Start the service again.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache and display the state of the service.  
    $DfltInstance.Refresh(); $DfltInstance  
    ```  
  
  