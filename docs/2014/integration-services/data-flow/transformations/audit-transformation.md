---
title: Преобразование "Аудит" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittrans.f1
helpviewer_keywords:
- environment data in packages [Integration Services]
- Audit transformation
ms.assetid: 8c143682-9c81-4150-83d6-1d9678151d37
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4cbe349fb83fea587874271c340853f8f38d2197
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176131"
---
# <a name="audit-transformation"></a>преобразование «Аудит»
  Преобразование «Аудит» позволяет включать поток данных в пакет для передачи данных о среде, в которой запускается этот пакет. Например, в поток данных можно добавлять имя пакета, компьютера и оператора. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] предусмотрены системные переменные, предоставляющие эти сведения.  
  
## <a name="system-variables"></a>Системные переменные  
 В приведенной ниже таблице описаны системные переменные, применяемые в преобразовании «Аудит».  
  
|Системная переменная|Индекс |Описание|  
|---------------------|-----------|-----------------|  
|`ExecutionInstanceGUID`|0|Идентификатор GUID, определяющий экземпляр выполнения пакета.|  
|`PackageID`|1|Уникальный идентификатор пакета.|  
|`PackageName`|2|Имя пакета.|  
|`VersionID`|3|Версия пакета.|  
|`ExecutionStartTime`|4|Время начала выполнения пакета.|  
|`MachineName`|5|имя компьютера.|  
|`UserName`|6|Имя входа пользователя, который запустил пакет.|  
|`TaskName`|7|Имя задачи потока данных, с которой связано преобразование «Аудит».|  
|**TaskId**|8|Уникальный идентификатор задачи потока данных.|  
  
## <a name="configuration-of-the-audit-transformation"></a>Настройка преобразования «Аудит»  
 Чтобы настроить преобразование «Аудит», необходимо добавить имя нового выходного столбца в выход преобразования, затем сопоставить системную переменную с выходным столбцом. Можно сопоставить одну системную переменную с несколькими столбцами.  
  
 Это преобразование имеет один вход и один выход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор преобразования «Аудит»** см. в разделе [Audit Transformation Editor](../../audit-transformation-editor.md).  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../../common-properties.md)  
  
-   [Пользовательские свойства преобразований](transformation-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md).  
  
  
