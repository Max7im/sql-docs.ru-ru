---
title: Редактор задачи файловой системы (страница "Общие") | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.general.f1
helpviewer_keywords:
- File System Task Editor
ms.assetid: 51fe6614-3418-4eff-a28d-02ea31cc9aa9
caps.latest.revision: 43
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 120e86946f920a616b9df7c443441fb4ce6d5efc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37156655"
---
# <a name="file-system-task-editor-general-page"></a>Редактор задачи «Файловая система» (страница «Общие»)
  Используйте страницу **Общие** диалогового окна **Редактор задачи «Файловая система»** для настройки операции файловой системы, выполняемой задачей.  
  
 Дополнительные сведения об этой задаче см. в разделе [File System Task](control-flow/file-system-task.md).  
  
 Необходимо указать диспетчер подключений к источнику и назначению, установив свойства SourceConnection и DestinationConnection. Можно задать либо имена диспетчеров подключения файлов, которые указывают на файлы, используемые задачей в качестве источника или назначения, либо, если пути к файлам хранятся в переменных, имена этих переменных. Чтобы использовать переменные для хранения путей к файлам, вначале необходимо задать значение **True**для параметра соединения с источником IsSourcePathVariable и параметра соединения с назначением IsDestinationPatheVariable. После этого можно выбрать существующие системные или определенные пользователем переменные либо можно создать новые переменные. В диалоговом окне **Добавить переменную** можно настроить переменные и указать область их действия. Областью действия должна быть задача «Файловая система» или родительский контейнер. Дополнительные сведения см. в разделах [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md) и [Использование переменных в пакетах](../../2014/integration-services/use-variables-in-packages.md).  
  
> [!NOTE]  
>  Чтобы переопределить переменные, выбранные для `SourceConnection` и `DestinationConnection` свойства, введите выражения для **источника** и **назначения** свойства. Эти выражения вводятся на странице **Выражения** редактора задачи **Файловая система**. Например, чтобы задать путь к файлам, которые задача будет использовать в качестве назначения, может потребоваться в одном случае использовать переменную A, а в другом — переменную B.  
  
> [!NOTE]  
>  Задача «Файловая система» работает с одиночным файлом или каталогом. Поэтому данная задача не поддерживает использование символов-шаблонов для выполнения одинаковых операций на множестве файлов или каталогов. Чтобы заставить задачу «Файловая система» повторить операцию для множества файлов или каталогов, поместите ее в контейнер «цикл по каждому элементу». Дополнительные сведения см. в статье [File System Task](control-flow/file-system-task.md).  
  
 Можно использовать выражения для использования других переменных для  
  
## <a name="options"></a>Параметры  
 **IsDestinationPathVariable**  
 Укажите, хранится ли целевой путь в переменной. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**True**|Целевой путь хранится в переменной. При выборе этого значения отображается динамический параметр **DestinationVariable**.|  
|**False**|Целевой путь задается в диспетчере подключения файлов. При выборе этого значения отображается динамический параметр, `DestinationConnection`.|  
  
 **OverwriteDestination**  
 Укажите, может ли операция перезаписывать файлы в каталоге назначения.  
  
 **Название**  
 Введите уникальное имя для задачи «Файловая система». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Описание**  
 Введите описание задачи «Файловая система».  
  
 **Операция**  
 Выберите операцию файловой системы для выполнения. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Копировать каталог**|Скопируйте каталог. При выборе этого значения отображаются динамические параметры для источника и места назначения.|  
|**Копировать файл**|Скопируйте файл. При выборе этого значения отображаются динамические параметры для источника и места назначения.|  
|**Создать каталог**|Создайте каталог. При выборе этого значения отображаются динамические параметры для исходного и целевого каталога.|  
|**Удалить каталог**|Удалите каталог. При выборе этого значения отображаются динамические параметры для источника.|  
|**Удалить содержимое каталога**|Удалите содержимое каталога. При выборе этого значения отображаются динамические параметры для источника.|  
|**Удалить файл**|Удалите файл. При выборе этого значения отображаются динамические параметры для источника.|  
|**Переместить каталог**|Переместите каталог. При выборе этого значения отображаются динамические параметры для источника и места назначения.|  
|**Переместить файл**|Переместите файл. При выборе этого значения отображаются динамические параметры для источника и места назначения.<br /><br /> Примечание: При перемещении файла, не включают имя файла в путь к каталогу, введенного в качестве места назначения.|  
|**Переименовать файл**|Переименуйте файл. При выборе этого значения отображаются динамические параметры для источника и места назначения.<br /><br /> Примечание: При переименовании файла, включите новое имя файла в каталоге, укажите для назначения.|  
|**Задать атрибуты**|Задайте атрибуты файла или каталога. При выборе этого значения отображаются динамические параметры для источника и операции.|  
  
 `IsSourcePathVariable`  
 Укажите, хранится ли целевой путь в переменной. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение||  
|-----------|-|  
|**True**|Целевой путь хранится в переменной. При выборе этого значения отображается динамический параметр **SourceVariable**.|  
|**False**|Целевой путь задается в диспетчере подключения файлов. При выборе этого значения отображается динамический параметр **DestinationVariable**.|  
  
## <a name="isdestinationpathvariable-dynamic-options"></a>Динамические параметры IsDestinationPathVariable  
  
### <a name="isdestinationpathvariable--true"></a>IsDestinationPathVariable = True  
 **DestinationVariable**  
 Выберите имя переменной в списке или щелкните \<**Создать переменную...**> для создания переменной.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md), [Добавление переменной](../../2014/integration-services/add-variable.md)  
  
### <a name="isdestinationpathvariable--false"></a>IsDestinationPathVariable = False  
 `DestinationConnection`  
 Выберите диспетчер подключений файлов в списке или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
## <a name="issourcepathvariable-dynamic-options"></a>Динамические параметры IsSourcePathVariable  
  
### <a name="issourcepathvariable--true"></a>IsSourcePathVariable = True  
 **SourceVariable**  
 Выберите имя переменной в списке или щелкните \<**Создать переменную...**> для создания переменной.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md), [Добавление переменной](../../2014/integration-services/add-variable.md)  
  
### <a name="issourcepathvariable--false"></a>IsSourcePathVariable = False  
 `SourceConnection`  
 Выберите диспетчер подключений файлов в списке или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
## <a name="operation-dynamic-options"></a>Динамические параметры операции  
  
### <a name="operation--set-attributes"></a>Операция = Задать атрибуты  
 **Скрыта**  
 Укажите, виден ли файл или каталог.  
  
 **ReadOnly**  
 Укажите, доступен ли файл только для чтения.  
  
 **Архив**  
 Укажите, готов ли файл или каталог для архивирования.  
  
 **System**  
 Укажите, является ли файл файлом операционной системы.  
  
### <a name="operation--create-directory"></a>Операция = Создать каталог  
 `UseDirectoryIfExists`  
 Указывает, использует ли операция **Создать каталог** существующий каталог с указанным именем вместо создания нового каталога.  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Страница "Выражения"](expressions/expressions-page.md)  
  
  
