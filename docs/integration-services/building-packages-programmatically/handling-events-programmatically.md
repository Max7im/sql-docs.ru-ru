---
title: "Программная обработка событий | Документы Microsoft"
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
- Integration Services packages, events
- SQL Server Integration Services packages, events
- SSIS events, programmatically handling
- packages [Integration Services], events
- DtsEventHandler object
- SSIS packages, events
- SSIS events
- events [Integration Services], programmatically
- tasks [Integration Services], events
- IDTSEvents interface
ms.assetid: 0f00bd66-efd5-4f12-9e1c-36195f739332
caps.latest.revision: 47
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 7235703f494bd1fb50e696aef537391ba23d1749
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="handling-events-programmatically"></a>Программная обработка событий
  В среде выполнения служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] имеется коллекция событий, возникающих до, во время и после проверки и выполнения пакета. Эти события можно зафиксировать двумя способами. Первый метод является реализацией <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> интерфейса в классе и указание класса в качестве параметра **Execute** и **проверки** методы пакета. Второй метод включает создание объектов <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>, которые могут содержать другие объекты служб [!INCLUDE[ssIS](../../includes/ssis-md.md)], например задачи и циклы, выполняемые при возникновении события <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents>. В данном разделе описаны эти два метода и приведены примеры кода, иллюстрирующие их использование.  
  
## <a name="receiving-idtsevents-callbacks"></a>Получение обратных вызовов IDTSEvents  
 Разработчики, создающие и программно выполняющие пакеты, могут получать уведомления о событиях во время проверки и выполнения с помощью интерфейса <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents>. Это делается путем создания класса, реализующего <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> интерфейс и этот класс как параметр **проверки** и **Execute** методы пакета. Методы класса затем вызываются подсистемой выполнения при возникновении события.  
  
 Класс <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> — это класс, в котором уже реализован интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents>. Поэтому другой альтернативой прямой реализации <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> является создание производного от <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> класса и переопределение событий, требующих отклика. Затем этот класс указывается как параметр **проверки** и **Execute** методы <xref:Microsoft.SqlServer.Dts.Runtime.Package> для получения обратных вызовов событий.  
  
 В следующем образце кода показан класс, производный от <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents>, переопределяющий метод <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnPreExecute%2A>. Затем класс предоставляется как aparameter для **проверки** и **Execute** методы пакета.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      MyEventsClass eventsClass = new MyEventsClass();  
  
      p.Validate(null, null, eventsClass, null);  
      p.Execute(null, null, eventsClass, null, null);  
  
      Console.Read();  
    }  
  }  
  class MyEventsClass : DefaultEvents  
  {  
    public override void OnPreExecute(Executable exec, ref bool fireAgain)  
    {  
      // TODO: Add custom code to handle the event.  
      Console.WriteLine("The PreExecute event of the " +  
        exec.ToString() + " has been raised.");  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim eventsClass As MyEventsClass = New MyEventsClass()  
  
    p.Validate(Nothing, Nothing, eventsClass, Nothing)  
    p.Execute(Nothing, Nothing, eventsClass, Nothing, Nothing)  
  
    Console.Read()  
  
  End Sub  
  
End Module  
  
Class MyEventsClass  
  Inherits DefaultEvents  
  
  Public Overrides Sub OnPreExecute(ByVal exec As Executable, ByRef fireAgain As Boolean)  
  
    ' TODO: Add custom code to handle the event.  
    Console.WriteLine("The PreExecute event of the " & _  
      exec.ToString() & " has been raised.")  
  
  End Sub  
  
End Class  
```  
  
## <a name="creating-dtseventhandler-objects"></a>Создание объектов DtsEventHandler  
 Подсистема выполнения обеспечивает гибкую и мощную систему обработки событий и уведомления о них с помощью объекта <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>. Эти объекты позволяют создавать с помощью обработчика событий целые рабочие процессы, выполняющиеся только при возникновении события, которому принадлежит обработчик событий. Объект <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> является контейнером, выполняющимся только при возникновении соответствующего события в родительском объекте. Эта архитектура позволяет создавать изолированные рабочие процессы, выполняющиеся в ответ на возникновение событий в контейнере. Поскольку объекты <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> являются синхронными, выполнение не возобновляется до тех пор, пока не будут возвращены обработчики событий, связанные с событием.  
  
 В следующем примере кода показано, как создать объект <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>. Код добавляет <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> к коллекции <xref:Microsoft.SqlServer.Dts.Runtime.Package.Executables%2A> пакета, а затем создает объект <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> для события <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> задачи. Задача <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> добавляется к обработчику событий, который выполняется при возникновении события <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> для первой задачи <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>. В этом примере предполагается, что для тестирования существует файл с именем «C:\Windows\Temp\DemoFile.txt». При первом запуске образца файл успешно копируется и обработчик событий не вызывается. Во второй раз при выполнении образца, первый <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> не удается скопировать файл (так как значение <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask.OverwriteDestinationFile%2A> — **false**), вызывается обработчик события, второй <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> удаляет исходный файл, а пакет сообщает о сбое из-за возникшей ошибки.  
  
## <a name="example"></a>Пример  
  
```csharp  
using System;  
using System.IO;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string f = "DemoFile.txt";  
      Executable e;  
      TaskHost th;  
      FileSystemTask fst;  
  
      Package p = new Package();  
  
      p.Variables.Add("sourceFile", true, String.Empty,  
        @"C:\Windows\Temp\" + f);  
      p.Variables.Add("destinationFile", true, String.Empty,  
        Path.Combine(Directory.GetCurrentDirectory(), f));  
  
      // Create a first File System task and add it to the package.  
      // This task tries to copy a file from one folder to another.  
      e = p.Executables.Add("STOCK:FileSystemTask");  
      th = e as TaskHost;  
      th.Name = "FileSystemTask1";  
      fst = th.InnerObject as FileSystemTask;  
  
      fst.Operation = DTSFileSystemOperation.CopyFile;  
      fst.OverwriteDestinationFile = false;  
      fst.Source = "sourceFile";  
      fst.IsSourcePathVariable = true;  
      fst.Destination = "destinationFile";  
      fst.IsDestinationPathVariable = true;  
  
      // Add an event handler for the FileSystemTask's OnError event.  
      DtsEventHandler ehOnError = (DtsEventHandler)th.EventHandlers.Add("OnError");  
  
      // Create a second File System task and add it to the event handler.  
      // This task deletes the source file if the event handler is called.  
      e = ehOnError.Executables.Add("STOCK:FileSystemTask");  
      th = e as TaskHost;  
      th.Name = "FileSystemTask2";  
      fst = th.InnerObject as FileSystemTask;  
  
      fst.Operation = DTSFileSystemOperation.DeleteFile;  
      fst.Source = "sourceFile";  
      fst.IsSourcePathVariable = true;  
  
      DTSExecResult vr = p.Validate(null, null, null, null);  
      Console.WriteLine("ValidationResult = " + vr.ToString());  
      if (vr == DTSExecResult.Success)  
      {  
        DTSExecResult er = p.Execute(null, null, null, null, null);  
        Console.WriteLine("ExecutionResult = " + er.ToString());  
        if (er == DTSExecResult.Failure)  
          if (!File.Exists(@"C:\Windows\Temp\" + f))  
            Console.WriteLine("Source file has been deleted by the event handler.");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim f As String = "DemoFile.txt"  
    Dim e As Executable  
    Dim th As TaskHost  
    Dim fst As FileSystemTask  
  
    Dim p As Package = New Package()  
  
    p.Variables.Add("sourceFile", True, String.Empty, _  
      "C:\Windows\Temp\" & f)  
    p.Variables.Add("destinationFile", True, String.Empty, _  
      Path.Combine(Directory.GetCurrentDirectory(), f))  
  
    ' Create a first File System task and add it to the package.  
    ' This task tries to copy a file from one folder to another.  
    e = p.Executables.Add("STOCK:FileSystemTask")  
    th = CType(e, TaskHost)  
    th.Name = "FileSystemTask1"  
    fst = CType(th.InnerObject, FileSystemTask)  
  
    fst.Operation = DTSFileSystemOperation.CopyFile  
    fst.OverwriteDestinationFile = False  
    fst.Source = "sourceFile"  
    fst.IsSourcePathVariable = True  
    fst.Destination = "destinationFile"  
    fst.IsDestinationPathVariable = True  
  
    ' Add an event handler for the FileSystemTask's OnError event.  
    Dim ehOnError As DtsEventHandler = CType(th.EventHandlers.Add("OnError"), DtsEventHandler)  
  
    ' Create a second File System task and add it to the event handler.  
    ' This task deletes the source file if the event handler is called.  
    e = ehOnError.Executables.Add("STOCK:FileSystemTask")  
    th = CType(e, TaskHost)  
    th.Name = "FileSystemTask1"  
    fst = CType(th.InnerObject, FileSystemTask)  
  
    fst.Operation = DTSFileSystemOperation.DeleteFile  
    fst.Source = "sourceFile"  
    fst.IsSourcePathVariable = True  
  
    Dim vr As DTSExecResult = p.Validate(Nothing, Nothing, Nothing, Nothing)  
    Console.WriteLine("ValidationResult = " + vr.ToString())  
    If vr = DTSExecResult.Success Then  
      Dim er As DTSExecResult = p.Execute(Nothing, Nothing, Nothing, Nothing, Nothing)  
      Console.WriteLine("ExecutionResult = " + er.ToString())  
      If er = DTSExecResult.Failure Then  
        If Not File.Exists("C:\Windows\Temp\" + f) Then  
          Console.WriteLine("Source file has been deleted by the event handler.")  
        End If  
      End If  
    End If  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
## <a name="see-also"></a>См. также:  
 [Службы Integration Services & #40; Службы SSIS & #41; Обработчики событий](../../integration-services/integration-services-ssis-event-handlers.md)   
 [Добавить обработчик событий в пакет](http://msdn.microsoft.com/library/5e56885d-8658-480a-bed9-3f2f8003fd78)  
  
  