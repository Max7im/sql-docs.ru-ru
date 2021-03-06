---
title: Использование окна "Свойства" в среде Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing properties
- Properties window [SQL Server Management Studio]
- complex properties [SQL Server Management Studio]
ms.assetid: 903d4aca-f57c-43d9-a893-702eceaa7004
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 555dfa484669e6b0600102d56da59e98c1cad857
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43059845"
---
# <a name="use-the-properties-window-in-management-studio"></a>Использование окна «Свойства» в среде Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Окно свойств описывает состояние элемента в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], например соединение или оператор Showplan, и сведения об объектах базы данных, таких как таблицы, представления и конструкторы.  
  
 Окно свойств можно использовать для просмотра свойств текущего соединения. Многие свойства в окне свойств доступны только для чтения, однако могут быть изменены другими средствами среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Например, свойство «База данных» запроса в окне свойств доступно только для чтения, но может изменяться на панели инструментов.  
  
### <a name="to-view-properties-using-the-properties-window"></a>Просмотр свойств с помощью окна свойств  
  
1.  Если окна свойств нет на экране, выберите **Окно "Свойства"** в меню **Вид** или нажмите клавишу F4.  
  
2.  Выберите объект, который необходимо просмотреть.  
  
3.  Найдите в окне свойств соответствующее свойство.  
  
### <a name="to-view-connection-properties-of-a-query-window"></a>Просмотр свойств соединения окна запроса  
  
1.  Если окна свойств нет на экране, выберите **Окно "Свойства"** в меню **Вид** или нажмите клавишу F4.  
  
2.  В окне свойств можно увидеть все свойства соединения.  
  
### <a name="to-view-the-properties-of-a-showplan-operator"></a>Просмотр свойств инструкции оператора Showplan  
  
1.  В меню **Запрос** выберите пункт **Включить действительный план выполнения**.  
  
2.  В редакторе SQL-запросов введите текст запроса и выполните его.  
  
3.  Если окна свойств нет на экране, выберите **Окно "Свойства"** в меню **Вид** или нажмите клавишу F4.  
  
4.  На вкладке **План выполнения** редактора SQL-запросов нажмите значки инструкций для просмотра сведений об инструкциях в окне свойств.  
  
## <a name="see-also"></a>См. также:  
 [Окно "Свойства" (среда Management Studio)](http://msdn.microsoft.com/library/6a9a1389-df8d-4cfc-928b-eccbf884a22d)  
  
  
