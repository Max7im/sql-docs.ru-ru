---
title: Элемент (XMLA) RESTORE | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Restore Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Restore
- urn:schemas-microsoft-com:xml-analysis#Restore
- microsoft.xml.analysis.restore
helpviewer_keywords:
- Restore command
ms.assetid: bb5a0c92-3927-4fa4-975b-6e4d79e0a912
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 682806680604606d54c133617b2150b975cf8c03
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275660"
---
# <a name="restore-element-xmla"></a>Элемент Restore (XML для аналитики)
  Восстанавливает [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных из файла резервной копии.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Restore>  
      <DatabaseName>...</DatabaseName>  
      <DatabaseID>...</DatabaseID>  
      <File>...</File>  
      <Security>...</Security>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <Locations>...</Locations>  
      <DbStorageLocation>...</DbStorageLocation>  
   </Restore>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[AllowOverwrite](../xml-elements-properties/allowoverwrite-element-xmla.md), [DatabaseName](../xml-elements-properties/name-element-xmla.md), [DatabaseID](../xml-elements-properties/id-element-xmla.md), [файл](../xml-elements-properties/file-element-xmla.md), [расположения](../xml-elements-properties/locations-element-xmla.md), [пароль](../xml-elements-properties/password-element-xmla.md), [Безопасности](../xml-elements-properties/security-element-xmla.md), [DbStorageLocation](../xml-elements-properties/dbstoragelocation-element.md)|  
  
## <a name="remarks"></a>Примечания  
 `Restore` Команда восстанавливает [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, указанной в `DatabaseName` элемент из файла резервной копии и при необходимости восстанавливает удаленные секции из удаленных файлов резервной копии.  
  
 В зависимости от режима хранения, используемые объекты, хранящиеся в файле резервной копии `Restore` команда восстанавливает данные, перечисленные в следующей таблице.  
  
|Режим хранения|Сведения|  
|------------------|-----------------|  
|Многомерный OLAP (MOLAP)|Исходные данные, агрегаты и метаданные|  
|Гибридный OLAP (HOLAP)|Агрегаты и метаданные|  
|Реляционный OLAP (ROLAP)|Метаданные|  
  
 Во время `Restore` команды на устанавливается монопольная блокировка [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, указанной в `DatabaseName` элемент. Блокировка снимается после `Restore` выполнения команды.  
  
 Дополнительные сведения о резервном копировании и восстановлении баз данных, см. в разделе [резервного копирования, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду восстановления, должен иметь разрешение на чтение из папки резервного копирования, указанной для каждого восстанавливаемого файла. Чтобы восстановить базу данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , которая не установлена на сервере, пользователь также должен быть членом роли сервера для этого экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Чтобы перезаписать базу данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , пользователь должен быть членом одной из следующих ролей: роль сервера для экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или роль базы данных с разрешениями "Полный доступ (Администратор)" в восстанавливаемой базе данных.  
  
> [!NOTE]  
>  После восстановления существующей базы данных пользователь, выполнявший восстановление, может утратить доступ к этой базе данных. Потеря доступа может произойти в случае, если на время создания резервной копии этот пользователь не был членом роли сервера и роли базы данных с разрешением «Полный доступ (Администратор)».  
  
## <a name="see-also"></a>См. также  
 [Резервное копирование элемента &#40;XML для Аналитики&#41;](backup-element-xmla.md)   
 [Элемент Batch &#40;XML для Аналитики&#41;](batch-element-xmla.md)   
 [Элемент Parallel &#40;XML для Аналитики&#41;](../xml-elements-properties/parallel-element-xmla.md)   
 [Элемент Synchronize &#40;XML для Аналитики&#41;](synchronize-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  
