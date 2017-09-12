---
title: "Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b6f587b40c53ff64b484b86a324b92ca5de21b77
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)
Чтобы вывести в отчете [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с разбиением на страницы рекурсивные данные, отражающие связь между родительским и дочерним объектами, представленную полями набора данных, можно задать выражение группы области данных на основании дочернего поля и установить свойство Parent на основании родительского поля.  
  
 Обычно группы рекурсивной иерархии используются для отображения иерархических данных, например, отношений подчиненных в структуре организации. Набор данных включает в себя список сотрудников и руководителей, причем имена руководителей также перечислены в списке сотрудников.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Создание рекурсивных иерархий  
 Чтобы создать рекурсивную иерархию в области данных табликса, нужно задать для поля выражение группы, задающее дочерние данные, а свойству Parent группы присвоить поле, задающее родительские данные. Например, если набор данных содержит идентификатор сотрудника и идентификатор руководителя, нужно присвоить выражению группы идентификатор сотрудника, а свойству Parent — идентификатор руководителя.  
  
 Группа, которая определена как рекурсивная иерархия (то есть группа, которая использует свойство Parent), может иметь только одно выражение группы. Можно использовать функцию **Level** для дополнения текстового поля, чтобы выровнять имена служащих на основе их уровней в иерархии.  
  
 Дополнительные сведения см. в разделе [Добавление или удаление группы в области данных &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) и [создать группу рекурсивной иерархии &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Агрегатные функции, поддерживающие рекурсию  
 Для вычисления сводных данных в рекурсивных иерархиях можно использовать агрегатные функции служб Reporting Services, принимающие параметр *Recursive* . Параметр **Recursive** поддерживают следующие функции: [Sum](../../reporting-services/report-design/report-builder-functions-sum-function.md), [Avg](../../reporting-services/report-design/report-builder-functions-avg-function.md), [Count](../../reporting-services/report-design/report-builder-functions-count-function.md), [CountDistinct](../../reporting-services/report-design/report-builder-functions-countdistinct-function.md), [CountRows](../../reporting-services/report-design/report-builder-functions-countrows-function.md), [Max](../../reporting-services/report-design/report-builder-functions-max-function.md), [Min](../../reporting-services/report-design/report-builder-functions-min-function.md), [StDev](../../reporting-services/report-design/report-builder-functions-stdev-function.md), [StDevP](../../reporting-services/report-design/report-builder-functions-stdevp-function.md), [Sum](../../reporting-services/report-design/report-builder-functions-sum-function.md), [Var](../../reporting-services/report-design/report-builder-functions-var-function.md)и [VarP](../../reporting-services/report-design/report-builder-functions-varp-function.md). Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>См. также  
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Область данных Табликса &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Справочник по агрегатным функциям &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)   
 [Tables &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Матрицы &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Списки &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)    
 [Таблицы, матрицы и списки &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  