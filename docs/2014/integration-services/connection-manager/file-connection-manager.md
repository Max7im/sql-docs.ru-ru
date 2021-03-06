---
title: Диспетчер подключения файлов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: 33e9bb0dbb4030d09be6db95dda2a33245cd7288
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252696"
---
# <a name="file-connection-manager"></a>диспетчер соединения файлов
  Диспетчер соединения файлов позволяет пакету ссылаться на существующий файл или папку или создавать файл или папку в процессе выполнения. Например, можно установить ссылку на файл Excel. Некоторые компоненты из служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] используют данные, хранящиеся в файлах, для выполнения своей работы. Например, задача «Выполнение SQL» может ссылаться на файл, содержащий набор инструкций SQL. Другие компоненты выполняют операции с файлами. Например, задача «Файловая система» может ссылаться на файл для его копирования в другое расположение.  
  
## <a name="usage-types-of-the-file-connection-manager"></a>Типы применения в диспетчере соединения файлов  
 `FileUsageType` Свойство диспетчер подключения файлов определяет, как используется соединение файла. Диспетчер подключения файлов может создать файл или папку, а также использовать уже существующий файл или папку.  
  
 В следующей таблице перечислены значения `FileUsageType`.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`0`|Диспетчер подключения файлов использует существующий файл.|  
|`1`|Диспетчер подключения файлов создает файл.|  
|`2`|Диспетчер соединения файлов использует существующую папку.|  
|`3`|Диспетчер соединения файлов создает папку.|  
  
## <a name="multiple-file-or-folder-connections"></a>Соединения с несколькими файлами или папками  
 Диспетчер соединения файлов может ссылаться только на один файл или папку. Для создания ссылки на несколько файлов или папок используйте диспетчер соединения нескольких файлов вместо диспетчера соединений с файлом. Дополнительные сведения см. в статье [Multiple Files Connection Manager](multiple-files-connection-manager.md).  
  
## <a name="configuration-of-the-file-connection-manager"></a>Настройка диспетчера соединения файлов  
 При добавлении к пакету диспетчер соединения файлов [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают, разрешит соединение файла во время выполнения, устанавливает свойства подключения файла и добавляет подключения файла в диспетчер соединений `Connections` коллекцию пакета.  
  
 `ConnectionManagerType` Свойства диспетчера соединений присваивается `FILE`.  
  
 Диспетчер соединения файлов можно настроить следующим образом.  
  
-   Определить тип применения.  
  
-   Определить файл или папку.  
  
 Можно задать свойство ConnectionString для диспетчера соединений с файлами, указывая выражение в окне "Свойства" [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Но чтобы избежать ошибки проверки при использовании выражения для указания файла или папки, добавьте путь к файлу или папке в пункте **Файл/папка**в **Редакторе диспетчера подключения файлов**.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Файл/папка](../file-connection-manager-editor.md).  
  
 Сведения о программной настройке диспетчера соединений см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
