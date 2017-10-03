---
title: "Добавление задачи потока данных программным образом | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- adding Data Flow task
- SSIS data flow
- data flow task [Integration Services], adding
- MainPipe object
ms.assetid: 0ca03712-a82e-4aa7-949b-f869a8936ddf
caps.latest.revision: 48
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0a7b0c3e51d7df76689f16ed91f60972d171bd9a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="adding-the-data-flow-task-programmatically"></a>Добавление задачи потока данных программным образом
  Среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] включает задачу потока данных, представленную пространством имен <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> в объектной модели. Задача потока данных — это специализированная высокопроизводительная задача, предназначенная для преобразования и перемещения данных во время выполнения пакета. Как и другие задачи, задача потока данных упакована в объект <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, и с точки зрения подсистемы выполнения эта задача является просто одной из задач в пакете. Однако поток данных содержит дополнительные объекты, называемые компонентами потока данных. Эти компоненты выполняют перемещение данных из источника в место назначения, иногда посредством преобразования. Эти компоненты определяют направление перемещения и способ преобразования данных. Настройка задачи потока данных включает добавление компонентов в задачу, а затем их соединение для установления потока данных и выполнения требуемого преобразования.  
  
 Существует три типа компонентов в задачу потока данных: **Источники потока данных**, **преобразования потока данных**, и **назначения потока данных**, показанный в этом порядке в [!INCLUDE[ssIS](../../includes/ssis-md.md)] элементов конструктора. Эти типы также называются просто источниками, преобразованиями и назначениями. Как видно из имен, поток данных направляется из источника в компонент преобразования, а затем назначению. Это простое описание потока данных, иллюстрирующее понятие, но задача потока данных является достаточно гибкой и мощной для обработки нескольких источников и объединения нескольких преобразований, отправляющих выходные данные нескольким назначениям.  
  
 Задача потока данных добавляется в пакет так же, как и другие задачи. После добавления задачи она настраивается путем добавления компонентов в задачу потока данных, настройки и соединения компонентов в задаче.  
  
## <a name="sample"></a>Образец  
 В следующем образце кода показан способ добавления задачи потока данных в пакет. Этот пример требует наличия ссылок на сборки Microsoft.SqlServer.PipelineHost, Microsoft.SqlServer.DTSPipelineWrap и Microsoft.SqlServer.ManagedDTS.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      Executable e = p.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;   
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim e As Executable = p.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As TaskHost = CType(e, TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись в блоге [EzAPI – Updated for SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=243223), на сайте blogs.msdn.com.  
  
## <a name="see-also"></a>См. также:  
 [Программный поиск компонентов потока данных](../../integration-services/building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
  
  