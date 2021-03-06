---
title: Обработка исключений SMO | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 942550cf7897ef1da84e31c2dfee8207eb0262b0
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085844"
---
# <a name="handling-smo-exceptions"></a>Обработка исключений SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  В управляемом коде при возникновении ошибок вызываются исключения. Методы и свойства объектов SMO не сообщают об ошибке или успешном выполнении в возвращаемом значении. Исключения могут быть перехвачены и обработаны в обработчике исключений.  
  
 В объектах SMO существуют различные классы исключений. Сведения об исключении можно извлечь из свойств исключения, таких как свойство **Message** , которое предоставляет текстовое сообщение об исключении.  
  
 Инструкции обработки исключения зависят от конкретного языка программирования. Например, в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic это **Catch** инструкции.  
  
## <a name="inner-exceptions"></a>Внутренние исключения  
 Исключения могут быть общими и конкретными. Общие исключения содержат набор конкретных исключений. Несколько инструкций **Catch** можно использовать, чтобы обработать ожидаемые ошибки и позволить остальным ошибкам пройти через обработку общих исключений. Исключения часто происходят в каскадной последовательности. Часто исключение объекта SMO может быть вызвано исключением SQL. Чтобы это обнаружить, можно последовательно использовать свойство **InnerException** , чтобы определить исходное исключение, которое вызвало конечное исключение верхнего уровня.  
  
> [!NOTE]  
>  **SQLException** исключение объявлено в **System.Data.SqlClient** пространства имен.  
  
 ![Диаграмма, показывающая уровни, из которых могут вызываться исключения](../../../relational-databases/server-management-objects-smo/create-program/media/exception-flow.gif "диаграмма, показывающая уровни, из которых могут вызываться исключения")  
  
 Диаграмма показывает поток исключений по уровням приложения.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).
  
## <a name="catching-an-exception-in-visual-basic"></a>Перехват исключения на языке Visual Basic  
 Данный пример кода показывает, как использовать **попробуйте... CATCH... Наконец** [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] инструкции для перехвата исключения объекта SMO. Все исключения объектов SMO имеют тип SmoException и перечислены в справке по объектам SMO. Последовательность внутренних исключений отображается, чтобы показать основание ошибки. Дополнительные сведения см. в разделе [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] документация по .NET.  
  
```VBNET
'This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace is included.
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.
'Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.
Dim op As [Operator]
op = New [Operator](srv.JobServer, "Test_Operator")
op.Create()
'Start exception handling.
Try
    'Create the operator again to cause an SMO exception.
    Dim opx As OperatorCategory
    opx = New OperatorCategory(srv.JobServer, "Test_Operator")
    opx.Create()
    'Catch the SMO exception
Catch smoex As SmoException
    Console.WriteLine("This is an SMO Exception")
    'Display the SMO exception message.
    Console.WriteLine(smoex.Message)
    'Display the sequence of non-SMO exceptions that caused the SMO exception.
    Dim ex As Exception
    ex = smoex.InnerException
    Do While ex.InnerException IsNot (Nothing)
        Console.WriteLine(ex.InnerException.Message)
        ex = ex.InnerException
    Loop
    'Catch other non-SMO exceptions.
Catch ex As Exception
    Console.WriteLine("This is not an SMO exception.")
End Try
``` 
  
## <a name="catching-an-exception-in-visual-c"></a>Перехват исключения на языке Visual C#  
 В этом примере кода показано, как использовать инструкцию **Try…Catch…Finally** в Visual C# для перехвата исключения объекта SMO. Все исключения объектов SMO имеют тип SmoException и перечислены в справке по объектам SMO. Последовательность внутренних исключений отображается, чтобы показать основание ошибки. Дополнительные сведения см. в документации по языку Visual C#.  
  
```csharp  
{   
//This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace to be included.   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.   
//Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.   
op = new Operator(srv.JobServer, "Test_Operator");   
op.Create();   
//Start exception handling.   
try {   
    //Create the operator again to cause an SMO exception.   
    OperatorCategory opx;   
    opx = new OperatorCategory(srv.JobServer, "Test_Operator");   
    opx.Create();   
}   
//Catch the SMO exception   
catch (SmoException smoex) {   
    Console.WriteLine("This is an SMO Exception");   
   //Display the SMO exception message.   
   Console.WriteLine(smoex.Message);   
   //Display the sequence of non-SMO exceptions that caused the SMO exception.   
   Exception ex;   
   ex = smoex.InnerException;   
   while (!object.ReferenceEquals(ex.InnerException, (null))) {   
      Console.WriteLine(ex.InnerException.Message);   
      ex = ex.InnerException;   
    }   
    }   
   //Catch other non-SMO exceptions.   
   catch (Exception ex) {   
      Console.WriteLine("This is not an SMO exception.");   
}   
}  
```  
  
  
