---
title: Сохранение результатов трассировки в таблицу (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0098c6b18e36d1d30ccc818a8f4f98f916fcb78d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163745"
---
# <a name="save-trace-results-to-a-table-sql-server-profiler"></a>сохранять результаты трассировки в таблицу (SQL Server Profiler)
  В этом подразделе описывается, как сохранять результаты трассировок в таблицу базы данных с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-save-trace-results-to-a-table"></a>Сохранение результатов трассировки в таблицу  
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Отображается диалоговое окно **Свойства трассировки**.  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки**не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис**выберите пункт **Параметры**и снимите флажок **Начать трассировку немедленно после установления соединения** .  
  
2.  В поле **Имя трассировки** введите имя трассировки и нажмите кнопку **Сохранить в таблицу**.  
  
3.  В диалоговом окне **Соединение с сервером** подключитесь к содержащей таблицу трассировок базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
4.  В диалоговом окне **Целевая таблица** выберите базу данных из списка **База данных**.  
  
5.  В списке **Владелец** выберите владельца трассировки.  
  
6.  В списке **Таблица** введите или выберите имя таблицы для сохранения результатов трассировки. Нажмите кнопку **ОК.**  
  
7.  В диалоговом окне **Свойства трассировки** установите флажок **Максимальное число строк (тыс.)**, чтобы задать максимальное число строк для сохранения.  
  
## <a name="see-also"></a>См. также  
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  