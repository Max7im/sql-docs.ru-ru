---
title: Исключение повторяющихся строк (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fd83e73a0a7b94f7963531baa167669850ef0b8c
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43807620"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>Исключение повторяющихся строк (визуальные инструменты для баз данных)
  Если необходимо, чтобы результирующий набор содержал лишь уникальные значения, можно исключить повторяющиеся значения из результирующего набора.  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>Удаление повторяющихся строк из результирующего набора  
  
1.  Щелкните правой кнопкой мыши фон панели диаграмм, а затем в контекстном меню выберите пункт **Свойства** .  
  
2.  В окне свойств щелкните **Неповторяющиеся значения** и установите значение **Да**.  
  
     Конструктор запросов и представлений поместит ключевое слово DISTINCT перед списком отображаемых столбцов в инструкции SQL.  
  
    > [!NOTE]  
    >  При использовании ключевого слова DISTINCT изменение результирующего набора на панели результатов может оказаться невозможным.  
  
## <a name="see-also"></a>См. также  
 [Определение критериев поиска &#40;визуальных инструментах баз данных&#41;](visual-database-tools.md)   
 [Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](sort-and-group-query-results-visual-database-tools.md)  
  
  
