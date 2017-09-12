---
title: "Переименование экземпляра служб Analysis Services | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instances of Analysis Services, renaming
- renaming instances of Analysis Services
- names [Analysis Services], renaming instances
- names [Analysis Services]
ms.assetid: 87494741-4a2e-4fed-8061-418fd1e111c3
caps.latest.revision: 53
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ce3a87eed86b8f876c8bf9bdde305166c2681d18
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="rename-an-analysis-services-instance"></a>Переименование экземпляра служб Analysis Services
  Существующий экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно переименовать с помощью средства **переименования экземпляра** , установленного вместе со средой Management Studio (веб-установка).  
  
> [!IMPORTANT]  
>  При переименовании экземпляра средство переименования экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] выполняется с расширенными правами доступа, обновляя имя службы Windows, учетные записи безопасности и записи реестра, связанные с этим экземпляром. Чтобы обеспечить выполнение этих действий, не забудьте перед запуском средства выполнить вход от имени администратора локальной системы.  
  
 Средство переименования экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не изменяет программную папку, созданную для исходного экземпляра. Не изменяйте имя программной папки для соответствия переименованному экземпляру. В случае изменения имени папки программа установки, возможно, не сможет выполнить исправление установки или ее удаление.  
  
> [!NOTE]  
>  Средство переименования экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не поддерживается в кластерной среде.  
  
### <a name="to-rename-an-instance-of-analysis-services"></a>Подключение к экземпляру служб Analysis Services  
  
1.  Запустите средство **переименования экземпляра** ( **asinstancerename.exe**) из папки C:\Program Files (x86)\Microsoft SQL Server\130\Tools\Binn\ManagementStudio.  
  
2.  В диалоговом окне **Переименование экземпляра** в списке **Экземпляр для переименования** выберите экземпляр, который необходимо переименовать.  
  
3.  В поле **Новое имя экземпляра** введите новое имя для экземпляра.  
  
4.  Проверьте правильность имени пользователя и пароля и нажмите кнопку **Переименовать**.  
  
     Экземпляр служб Analysis Services будет остановлен и перезапущен в процессе изменения имени.  
  
### <a name="post-rename-checklist"></a>Контрольный список действий после переименования  
  
1.  Чтобы возобновить доступ к базам данных, выполняющимся на переименованном экземпляре, потребуется вручную изменить соединения с данными в Excel или в других клиентских приложениях. Также следует проверить все стандартные соединения, например общие источники данных служб Reporting Services, файлы ODC Excel и файлы подключения семантических моделей бизнес-аналитики, которые могут ссылаться на переименованный экземпляр. Дополнительные сведения см. в разделе [Подключение к службам Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md).  
  
2.  Обновите скрипты PowerShell или AMO, обычно используемые для резервного копирования, синхронизации и обработки баз данных.  
  
3.  Обновите свойства проекта у проектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , с которыми вы работаете в среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Для экземпляров сервера в табличном режиме необходимо обязательно обновить свойство «Workspace Server» (сервер рабочей области) в файле model.bim, а также свойство «Server» (сервер) проекта.  
  
4.  В зависимости от того, каким образом была задана учетная запись службы, может потребоваться обновить имена входа для баз данных или права на доступ к файлам, предоставляющий службе разрешение на доступ к данным (например, если учетная запись службы используется для обработки данных или доступа к связанным объектам на другом сервере).  
  
     Обновление имени входа для базы данных или разрешений на доступ к файлам обязательно, если для подготовки службы к работе использовалась виртуальная учетная запись. Виртуальные учетные записи основываются на именах служб, поэтому при переименовании экземпляра одновременно обновляется и имя виртуальной учетной записи. В результате все ранее созданные для предыдущего экземпляра имена входа и разрешения становятся недействительными.  
  
     Это показывается в следующем примере. Предположим, что сервер в табличном режиме установлен как экземпляр под именем «Tabular» с использованием виртуальной учетной записи по умолчанию. При этом конфигурация будет следующей:  
  
    1.  Имя экземпляра = \<server > \TABULAR  
  
    2.  Имя службы = MSOLAP$TABULAR  
  
    3.  Виртуальная учетная запись = NT Service\ MSOLAP$TABULAR  
  
     Теперь допустим, что экземпляр переименован в «TAB2». В результате изменения имени конфигурация будет выглядеть следующим образом:  
  
    1.  Имя экземпляра = \<server > \TAB2  
  
    2.  Имя службы = MSOLAP$TAB2  
  
    3.  Виртуальная учетная запись = NT Service\ MSOLAP$TAB2  
  
     Как видно, разрешения базы данных и файлов, ранее предоставленные учетной записи «NT Service\ MSOLAP$TABULAR», теперь недействительны. Чтобы обеспечить нормальную работу выполняемых службой задач и операций, необходимо предоставить новые разрешения на базу данных и файлы учетной записи «NT Service\ MSOLAP$TAB2».  
  
  