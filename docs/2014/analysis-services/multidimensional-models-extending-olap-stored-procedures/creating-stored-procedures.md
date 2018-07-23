---
title: Создание хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 22351d69fc7b2a7f229980607ae5b8dab6f0499b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279840"
---
# <a name="creating-stored-procedures"></a>Создание хранимых процедур
  Для использования любой хранимой процедуры необходимо, чтобы она была связана с классом среды CLR или модели COM. Класс должен быть установлен на сервере, обычно в виде [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® динамическую библиотеку (DLL) — и зарегистрирован как сборка на сервере или в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных.  
  
 Хранимые процедуры регистрируются на сервере или в базе данных. Серверные хранимые процедуры могут вызываться из контекста любого запроса. Доступ к хранимым процедурам базы данных имеется, только если контекст базы данных представляет собой базу данных, в которой определена хранимая процедура. Если функции из одной сборки вызывают функции из другой сборки, то необходимо зарегистрировать обе сборки в одном и том же контексте (сервера или базы данных). Для сервера или развернутой [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных на сервере, можно использовать [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для регистрации сборки. Для проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно использовать конструктор служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для регистрации сборки в проекте.  
  
> [!IMPORTANT]  
>  Использование сборок COM может представлять угрозу безопасности. По этой причине, а также по ряду других сборки COM в службах [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)]являются устаревшими. Поддержка сборок COM в последующих версиях может быть прекращена.  
  
## <a name="registering-a-server-assembly"></a>Регистрация серверной сборки  
 В обозревателе объектов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] список серверных сборок приведен в папке «Сборки» под экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Серверные сборки могут содержать как сборки .NET (среды CLR), так и библиотеки COM.  
  
### <a name="to-create-a-server-assembly"></a>Создание серверной сборки  
  
1.  Разверните экземпляр [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в обозревателе объектов щелкните правой кнопкой мыши **сборки** папку, а затем щелкните **новую сборку**. Откроется **Регистрация серверной сборки** диалоговое окно.  
  
2.  Для **тип** укажите тип сборки:  
  
    -   Для DLL-библиотеки управляемого кода (среда CLR) задайте сборку .NET.  
  
    -   Для DLL-библиотеки собственного кода (COM) укажите COM DLL.  
  
3.  Для **имя файла**, указать библиотеку DLL, содержащую хранимые процедуры.  
  
4.  Для **имя сборки**, укажите имя для сборки.  
  
5.  Если это отладочная сборка библиотеки, что вы собираетесь использовать для отладки хранимых процедур, выберите **включить отладочные данные** "флажок". Дополнительные сведения об отладке хранимых процедур см. в разделе [отладки хранимых процедур](debugging-stored-procedures.md).  
  
6.  Можно щелкнуть **ОК** для регистрации сборки, немедленно, или на панели инструментов поле диалогового окна, можно щелкнуть команду **скрипт** меню в скрипт действие регистрации, в окно запроса, в файл или буфер обмена.  
  
 После регистрации серверной сборки ее можно настроить, щелкнув правой кнопкой мыши в обозревателе объектов и выбрав **свойства**.  
  
## <a name="registering-a-database-assembly-on-the-server"></a>Регистрация сборки базы данных на сервере  
 В обозревателе объектов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] список сборок базы данных приведен в папке «Сборки» под базой данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Сборки баз данных могут содержать как сборки .NET (среда CLR), так и библиотеки COM.  
  
### <a name="to-create-a-database-assembly-on-a-server"></a>Создание сборки базы данных на сервере  
  
1.  Разверните экземпляр [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных в обозревателе объектов щелкните правой кнопкой мыши **сборки** папку, а затем щелкните **новую сборку**. Откроется **регистрация сборки базы данных** диалоговое окно.  
  
2.  Для **тип** укажите тип сборки:  
  
    -   Для DLL-библиотеки управляемого кода (среда CLR) задайте сборку .NET.  
  
    -   Для DLL-библиотеки собственного кода (COM) укажите COM DLL.  
  
3.  Для **имя файла**, указать библиотеку DLL, содержащую хранимые процедуры.  
  
4.  Для **имя сборки**, укажите имя для сборки.  
  
5.  Если это отладочная сборка библиотеки, что вы собираетесь использовать для отладки хранимых процедур, выберите **включить отладочные данные** "флажок". Дополнительные сведения об отладке хранимых процедур см. в разделе [отладки хранимых процедур](debugging-stored-procedures.md).  
  
6.  Можно щелкнуть **ОК** для регистрации сборки, немедленно, или на панели инструментов поле диалогового окна, можно щелкнуть команду **скрипт** меню в скрипт действие регистрации, в окно запроса, в файл или буфер обмена.  
  
 После регистрации сборки базы данных, его можно настроить, щелкнув правой кнопкой мыши в обозревателе объектов и выбрав **свойства**.  
  
## <a name="registering-a-database-assembly-in-a-project"></a>Регистрация сборки базы данных в проекте  
 В обозревателе объектов в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] список сборок базы данных приведен в папке «Сборки» под проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Сборки баз данных могут содержать как сборки .NET (среда CLR), так и библиотеки COM.  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a>Создание сборки базы данных в проекте служб Analysis Service  
  
1.  Разверните экземпляр [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных в обозревателе объектов щелкните правой кнопкой мыши **сборки** папку, а затем щелкните **создать ссылку на сборку**. Откроется **добавить ссылку** диалоговое окно. **.NET** вкладке **добавить ссылку** диалоговом окне приводится список существующих сборок .NET (CLR), хотя **проекты** вкладке перечисляются проекты.  
  
2.  Можно щелкнуть существующий компонент или проект и нажмите кнопку **добавить** для добавления его [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта. Чтобы добавить ссылку на DLL-ФАЙЛ, щелкните **Обзор** tab, чтобы найти файл. **Выбранные проекты и компоненты** списке отображаются имя, тип, версию и расположение для каждого компонента, который добавляется в проект.  
  
3.  По окончании выбора компонентов, щелкните элемент **ОК** Чтобы добавить их в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта.  
  
## <a name="script-format-for-an-assembly"></a>Формат скрипта для сборки  
 Регистрация сборки .NET довольно проста. Сборка .NET добавляется к базе данных в бинарном виде с использованием следующего формата:  
  
```  
<Create>  
   <ObjectDefinition>  
      <Assembly>  
         <Files>  
            <File>  
               <Name>filename</Name>  
               <Type>filetype</Type>  
               <Data>  
                  <Block>binarydatablock</Block>  
                  <Block>binarydatablock</Block>  
                  ...  
               </Data>  
            </File>  
         </Files>  
         <PermissionSet>PermissionSet</PermissionSet>  
      </Assembly>  
   <ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>См. также  
 [Управление сборками многомерной модели](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Определение хранимых процедур](defining-stored-procedures.md)  
  
  