---
title: "Службы Integration Services (SSIS) разработки и средства управления | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- studio environments [Integration Services]
- tools [Integration Services], Business Intelligence Development Studio
- Business Intelligence Development Studio, Integration Services in
- SQL Server Management Studio [Integration Services]
- SSIS, studio environments
- SQL Server Integration Services, studio environments
- tools [Integration Services], SQL Server Management Studio
ms.assetid: 4eb73e65-d9f3-4ac6-a408-abfa85afc537
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bae8b462da5b34b7eb5200eac3d23e1122e9bbc3
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-development-and-management-tools"></a>Разработка Integration Services (SSIS) и средства управления
  Службы[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] содержат две интегрированные среды для работы со службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:  
  
-   Среда[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] предназначена для разработки пакетов [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , необходимых для бизнес-решения. Среда[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] предоставляет проект [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , в котором можно создавать пакеты.  
  
-   Среда[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] предназначена для управления пакетами в рабочей среде.  
  
## <a name="sql-server-data-tools"></a>SQL Server Data Tools  
 Работая в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], можно выполнять следующие задачи:  
  
-   Запускать мастер импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для создания основных пакетов, которые осуществляют копирование данных из источника в место назначения.  
  
-   Создавать пакеты, содержащие сложные потоки управления, потоки данных, событийно-управляемую логику и ведение журнала.  
  
-   Проверять и запускать отладку для пакетов при помощи функций диагностики и наблюдения в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] и функций отладки в [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
-   Создавать настройки для обновления свойств пакетов и объектов пакетов в процессе выполнения.  
  
-   Создавать программу развертывания, при помощи которой можно устанавливать пакеты и их зависимости на другие компьютеры.  
  
-   Сохранять копии пакетов для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] базы данных msdb, [!INCLUDE[ssIS](../includes/ssis-md.md)] хранилище пакетов, а в файловой системе.  
  
 Дополнительные сведения о [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]см. в разделе [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/hh272686.aspx).  
  
## <a name="sql-server-management-studio"></a>Среда SQL Server Management Studio  
 Среда[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] предоставляет службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , применяемую для управления пакетами и контроля за выполнением пакетов, а также для определения влияния и преобразования данных для объектов [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Работая в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], можно выполнять следующие задачи:  
  
-   Создавать папки для систематизации пакетов нужным для организации образом.  
  
-   Запускать пакеты, хранимые на локальном компьютере, при помощи программы выполнения пакетов.  
  
-   Запустите программу выполнения пакетов для создания командной строки, которую можно использовать в программе командной строки **dtexec** (dtexec.exe).  
  
-   Проводить операции импорта и экспорта пакетов с базой данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb, хранилищами пакетов [!INCLUDE[ssIS](../includes/ssis-md.md)] и с файловой системой.  
