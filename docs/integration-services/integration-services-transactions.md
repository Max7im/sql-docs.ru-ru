---
title: "Транзакции служб Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "контейнеры [службы Integration Services], транзакции"
  - "транзакции [службы Integration Services], о транзакциях в пакетах"
  - "задачи [службы Integration Services], транзакции"
  - "транзакции [службы Integration Services]"
ms.assetid: 3c78bb26-ddce-4831-a5f8-09d4f4fd53cc
caps.latest.revision: 51
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Транзакции служб Integration Services
  Пакеты используют транзакции для связывания выполняемых в базе данных задачами операций в атомарные объекты, и, таким образом, сохраняют целостность данных. Все типы контейнеров служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (пакеты, контейнеры циклов по элементам и по каждому элементу, контейнеры последовательности, а также серверы задач, которые содержат каждую задачу) могут быть настроены для использования транзакций. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предоставляют три параметра для настройки транзакций: **NotSupported**, **Supported**и **Required**.  
  
-   **Required** указывает, что контейнер запускает транзакцию, если она еще не запущена родительским контейнером. Если транзакция уже существует, контейнер с ней соединяется. Например, если пакет, не настроенный для поддержки транзакций, содержит контейнер последовательности, использующий параметр **Required** , то контейнер последовательности начнет свою собственную транзакцию. Если бы пакет был настроен для использования параметра **Required** , контейнер последовательности соединился бы с транзакцией пакета.  
  
-   **Supported** указывает, что контейнер не запускает транзакцию, но соединяется с любой транзакцией, запущенной родительским контейнером. Например, если пакет с четырьмя задачами «Выполнение SQL» запускает транзакцию и все четыре задачи используют параметр **Supported** , то обновления базы данных, выполненные задачами «Выполнение SQL», откатываются при ошибке обновления любой из этих задач. Если пакет не начинает транзакцию, четыре задачи «Выполнение SQL» не связаны транзакцией и в случае ошибки обновления базы данных одной из задач отменяются только обновления этой задачи.  
  
-   **NotSupported** указывает, что контейнер не начинает транзакцию и не соединяется с существующей транзакцией. Транзакция, запущенная родительским контейнером, не влияет на дочерние контейнеры, которые не были настроены на поддержку транзакций. Например, если пакет был настроен на запуск транзакции, а контейнер «цикл по элементам» в пакете использует параметр **NotSupported** , то в случае неудачи откат каких-либо задач в контейнере «цикл по элементам» невозможен.  
  
 Настройка транзакций происходит с помощью свойства контейнера TransactionOption. Установить это свойство можно в окне **Свойства** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]или программным путем.  
  
> [!NOTE]  
>  Cвойствo **TransactionOption** влияет на то, применяется ли значение свойства **IsolationLevel** , запрашиваемого контейнером. Дополнительные сведения см. в описании свойства **IsolationLevel** в разделе [Установка свойств пакета](../integration-services/set-package-properties.md).  
  
### Настройка пакета на использование транзакций  
  
-   [Настройка пакета для использования транзакций](../Topic/Configure%20a%20Package%20to%20Use%20Transactions.md)  
  
## Внешние ресурсы  
  
-   Запись в блоге, [Как использовать транзакции в службах SQL Server Integration Services SSIS](http://go.microsoft.com/fwlink/?LinkId=157783), на сайте www.mssqltips.com  
  
## См. также  
 [Наследуемые транзакции](../Topic/Inherited%20Transactions.md)   
 [Множественные транзакции](../Topic/Multiple%20Transactions.md)  
  
  