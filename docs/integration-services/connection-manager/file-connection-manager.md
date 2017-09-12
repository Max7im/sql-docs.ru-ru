---
title: "Диспетчер подключения файлов | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.fileconnectionmanager.f1
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- files [Integration Services]
- connection managers [Integration Services], File
- connections [Integration Services], files
- File connection manager
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
caps.latest.revision: 50
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 8397673c7ed9dfe8ae02871f9077ed7286e49863
ms.openlocfilehash: 25e93783e4d7d7b6cdaeab98937dee1da2ebef0b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="file-connection-manager"></a>диспетчер соединения файлов
  Диспетчер соединения файлов позволяет пакету ссылаться на существующий файл или папку или создавать файл или папку в процессе выполнения. Например, можно установить ссылку на файл Excel. Некоторые компоненты из служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] используют данные, хранящиеся в файлах, для выполнения своей работы. Например, задача «Выполнение SQL» может ссылаться на файл, содержащий набор инструкций SQL. Другие компоненты выполняют операции с файлами. Например, задача «Файловая система» может ссылаться на файл для его копирования в другое расположение.  
  
## <a name="usage-types-of-the-file-connection-manager"></a>Типы применения в диспетчере соединения файлов  
 Свойство **FileUsageType** диспетчера соединения файлов определяет, как используется соединение файла. Диспетчер подключения файлов может создать файл или папку, а также использовать уже существующий файл или папку.  
  
 В следующей таблице приводятся значения **FileUsageType**.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Диспетчер подключения файлов использует существующий файл.|  
|**1**|Диспетчер подключения файлов создает файл.|  
|**2**|Диспетчер соединения файлов использует существующую папку.|  
|**3**|Диспетчер соединения файлов создает папку.|  
  
## <a name="multiple-file-or-folder-connections"></a>Соединения с несколькими файлами или папками  
 Диспетчер соединения файлов может ссылаться только на один файл или папку. Для создания ссылки на несколько файлов или папок используйте диспетчер соединения нескольких файлов вместо диспетчера соединений с файлом. Дополнительные сведения см. в статье [Multiple Files Connection Manager](../../integration-services/connection-manager/multiple-files-connection-manager.md).  
  
## <a name="configuration-of-the-file-connection-manager"></a>Настройка диспетчера соединения файлов  
 Когда в пакет добавляется диспетчер подключения файлов, службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений, который в процессе выполнения создает соединение файла, устанавливает свойства подключения файла и добавляет подключения файла в коллекцию **Connections** пакета.  
  
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **FILE**.  
  
 Диспетчер соединения файлов можно настроить следующим образом.  
  
-   Определить тип применения.  
  
-   Определить файл или папку.  
  
 Можно задать свойство ConnectionString для диспетчера соединений с файлами, указывая выражение в окне "Свойства" [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Но чтобы избежать ошибки проверки при использовании выражения для указания файла или папки, добавьте путь к файлу или папке в пункте **Файл/папка**в **Редакторе диспетчера подключения файлов**.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Файл/папка](../../integration-services/connection-manager/file-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="file-connection-manager-editor"></a>редактор диспетчера подключения файлов
  Диалоговое окно **Редактор диспетчера подключения файлов** задает свойства, используемые при подключении к файлу или папке.  
  
> [!NOTE]  
>  Можно задать свойство ConnectionString для диспетчера соединений с файлами, указывая выражение в окне "Свойства" [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Но чтобы избежать ошибки проверки при использовании выражения для указания файла или папки, добавьте путь к файлу или папке в пункте **Файл/папка**в **Редакторе диспетчера подключения файлов**.  
  
 Дополнительные сведения о диспетчере подключения файлов см. в разделе [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md).  
  
### <a name="options"></a>Параметры  
 **Тип применения**  
 Укажите, будет ли **Диспетчер подключения файлов** подключаться к существующему файлу или папке или создаст новый файл или папку.  
  
|Значение|Description|  
|-----------|-----------------|  
|Создать файл|Во время выполнения создается новый файл.|  
|Существующий файл|Использовать существующий файл.|  
|Создать папку|Во время выполнения создается новая папка.|  
|Существующая папка|Использовать существующую папку.|  
  
 **Файл / Папка**  
 Если **Файл**, укажите нужный файл.  
  
 Если **Папка**, укажите нужную папку.  
  
 **Обзор**  
 Выберите файл или папку в диалоговом окне **Выбор файла** или **Выбор папки** .  
  
  