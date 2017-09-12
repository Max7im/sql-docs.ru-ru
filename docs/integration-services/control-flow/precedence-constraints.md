---
title: "Управление очередностью | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.precedenceconstraint.f1"
helpviewer_keywords: 
  - "задачи [службы Integration Services], управление очередностью"
  - "поток управления [службы Integration Services], управление очередностью"
  - "управление очередностью [службы Integration Services]"
  - "ограничения [службы Integration Services]"
  - "параметры последовательного выполнения [службы Integration Services]"
  - "контейнеры [службы Integration Services], управление очередностью"
ms.assetid: c5ce5435-fd89-4156-a11f-68470a69aa9f
caps.latest.revision: 51
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Управление очередностью
  Элементы управления очередностью связывает исполняемые объекты, контейнеры и задачи в пакетах в поток управления и задают условия, которые определяют, выполняются ли исполняемые объекты. В качестве исполняемого объекта могут быть контейнеры «цикл по элементам» и «цикл по каждому элементу», контейнеры последовательности, задача или обработчик события. Обработчики событий также используют управление очередностью для связывания своих исполняемых объектов в поток управления.  
  
 Элементы управления очередностью связывает два исполняемых объекта: ограничивающий исполняемый объект и исполняемый объект с ограничением. Ограничивающие исполняемые объекты выполняются перед исполняемыми объектами с ограничением, и в результате выполнения ограничивающих исполняемых объектов определяется, выполняются ли исполняемые объекты с ограничением. На следующей диаграмме представлены два исполняемых объекта, связанные элементы управлением очередностью.  
  
 ![Выполняемые объекты, соединенные ограничением очередностью](../../integration-services/control-flow/media/ssis-pcsimple.gif "Выполняемые объекты, соединенные ограничением очередностью")  
  
 При линейном потоке управления, то есть без ветвления, элементы управления очередностью сами управляют последовательностью, в которой запускаются задачи. Если поток управления содержит ветвления, ядро во время выполнения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] определяет порядок выполнения задачи и контейнеров, которые непосредственно следуют за ветвлением. Ядро во время выполнения также определяет порядок выполнения несвязанных рабочих процессов в потоке управления.  
  
 Архитектура вложенных контейнеров служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] позволяет всем контейнерам, за исключением контейнеров сервера задач, которые могут инкапсулировать только одну задачу, содержать другие контейнеры, каждый из которых имеет собственный поток управления. Контейнеры «цикл по элементам», «цикл по каждому элементу» и контейнеры последовательности могут включать несколько задач и другие контейнеры, которые, в свою очередь, могут содержать несколько задач и контейнеров. Например, пакет с задачей «Скрипт» и контейнером последовательности имеет управление очередностью, которое связывает задачу «Скрипт» и контейнер последовательности. Контейнер последовательности содержит три задачи «Скрипт», и его управления очередностью связывают три задачи «Скрипт» в поток управления. На следующей диаграмме показаны управления очередностью в пакете с двумя уровнями вложенности.  
  
 ![Ограничения очередностью в пакете](../../integration-services/control-flow/media/mw-dts-12.gif "Ограничения очередностью в пакете")  
  
 Так как пакет находится наверху иерархии контейнеров служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , несколько пакетов не могут быть связаны управлениями очередностью, однако можно добавить в пакет задачу «Выполнение пакета» и косвенно связать другой пакет в поток управления.  
  
 Управление очередностью можно настроить следующими способами:  
  
-   Задать операцию вычисления. Управление очередностью использует ограничение по значению, выражение, оба эти элемента или один из них для определения, выполняется ли исполняемый объект с ограничением.  
  
-   Если управление очередностью использует результат выполнения, в качестве результата выполнения могут быть заданы успех, ошибка или завершение.  
  
-   Если управление очередностью использует результат оценки, может быть задано выражение, значением которого является логическое значение.  
  
-   Укажите, оценивается ли управление очередностью одно или совместно с другими ограничениями, применимыми к исполняемому объекту с ограничением.  
  
## Операции вычисления  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляют следующие операции вычисления:  
  
-   Ограничение, использующее только результат выполнения ограничивающего исполняемого объекта для определения, выполняется ли исполняемый объект с ограничением. Результатом выполнения приоритетного ограничивающего объекта может быть завершение, успех или ошибка. Это операция по умолчанию.  
  
-   Выражение, оцениваемое для определения, выполняется ли исполняемый объект с ограничением. Если результатом оценки этого выражения является TRUE, исполняемый объект с ограничением выполняется.  
  
-   Выражение и ограничение, объединяющие требования результатов выполнения ограничивающего исполняемого объекта и результатов, возвращаемых после оценки выражения.  
  
-   Выражение или ограничение, использующие результаты выполнения ограничивающего исполняемого объекта или результаты, возвращаемые после оценки выражения.  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] использует цвет для определения типа элементов управления очередностью. Успешное ограничение отмечается зеленым, неуспешное — красным, завершенное — синим. Для отображения текстовых меток в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , обозначающих тип ограничения, необходимо настроить специальные возможности конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Выражение должно быть действительным выражением служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , оно может содержать функции, операторы, а также системные и пользовательские переменные. Дополнительные сведения см. в разделах [Выражения в службах Integration Services (SSIS)](../../integration-services/expressions/integration-services-ssis-expressions.md) и [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md).  
  
## Результаты выполнения  
 Управление очередностью может использовать следующие результаты выполнения поодиночке или в сочетании с выражением.  
  
-   Завершение означает только то, что ограничивающий исполняемый объект завершился без учета результата, вследствие чего запустился исполняемый объект с ограничением.  
  
-   Успешное окончание означает, что для выполнения ограничивающего объекта с ограничением необходимо, чтобы приоритетный исполняемый объект был успешно завершен.  
  
-   Завершение с ошибкой означает, что для выполнения исполняемого объекта с ограничением необходимо, чтобы ограничивающий исполняемый объект завершился со сбоем.  
  
> [!NOTE]  
>  Только управления очередностью, являющиеся элементами одной коллекции **Precedence Constraint** , могут быть сгруппированы в логическом условии AND. Например, нельзя объединить элементы управления очередностью из двух контейнеров «цикл по каждому элементу».  
  
## Настройка элементов ограничения очередностью  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)], см. в разделе [Редактор управления очередностью](../Topic/Precedence%20Constraint%20Editor.md).  
  
 Дополнительные сведения о настройке этих свойств программными средствами см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.  
  
## Связанные задачи  
 Дополнительные сведения о задании этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующих разделах:  
  
-   [Установка свойств управления очередностью](../Topic/Set%20the%20Properties%20of%20a%20Precedence%20Constraint.md)  
  
-   [Установка значения элементов управления очередностью с помощью контекстного меню](../Topic/Set%20the%20Value%20of%20a%20Precedence%20Constraint%20by%20Using%20the%20Shortcut%20Menu.md)  
  
-   [Соединение задач и контейнеров с помощью элементов управления очередностью по умолчанию](../Topic/Connect%20Tasks%20and%20Containers%20by%20Using%20a%20Default%20Precedence%20Constraint.md)  
  
     В этом разделе приведены сведения о настройке поведения по умолчанию для элементов управления очередностью, а также настройке исполняемых объектов с помощью элементов управления очередностью по умолчанию.  
  
## См. также  
 Техническая статья [Примеры выражений служб SSIS](http://go.microsoft.com/fwlink/?LinkId=220761)на сайте social.technet.microsoft.com  
  
## См. также  
 [Добавление выражений к элементам управления очередностью](../Topic/Add%20Expressions%20to%20Precedence%20Constraints.md)   
 [Множественные элементы управления очередностью](../Topic/Multiple%20Precedence%20Constraints.md)  
  
  