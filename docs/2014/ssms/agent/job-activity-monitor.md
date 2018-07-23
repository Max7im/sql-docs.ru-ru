---
title: Монитор активности заданий | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.ACTIVITYMON.F1
- sql12.ag.jobactivitymonitor.alljobs.f1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4896661e08c340fe9d61861b44f8915332d7b688
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253386"
---
# <a name="job-activity-monitor"></a>Монитор активности заданий
  Эта страница позволяет просматривать текущую активность заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Выберите пункт **Фильтр** для отбора выводимых заданий. Сетка **Активность заданий агента** доступна только для чтения. Щелкните заголовки столбцов для сортировки этой сетки. Для изменения задания дважды щелкните его, чтобы открыть диалоговое окно **Свойства задания** . Щелкните правой кнопкой мыши задание в сетке, чтобы запустить его на выполнение всех его шагов, запуска определенного шага задания, отключения или включения, обновления, удаления задания, просмотра его журнала и просмотра свойств задания. Нажмите кнопку **Обновить** для обновления сетки с текущими данными.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Имя задания.  
  
 **Enabled**  
 Указывает, включено задание (**да**) или отключено (**нет**).  
  
 **Состояние** <sup>1</sup>  
 Текущее состояние задания.  
  
 **Результат последнего запуска**  
 Состояние задания при последнем запуске.  
  
 **Последний запуск**  
 Дата и время последнего запуска задания с использованием локальной даты и времени сервера.  
  
 **Следующий запуск** <sup>1</sup>  
 Дата и время запланированного следующего запуска задания с использованием локальной даты и времени сервера.  
  
 **Категория**  
 Категория, присвоенная заданию.  
  
 **Готово к запуску**  
 **Да** , если задание можно запустить; **Нет** , если задание запустить нельзя. Задание нельзя запустить, если оно не содержит шагов или если в нем не указан целевой сервер.  
  
 **Назначено**  
 **Да** , если заданию назначено расписание; **Нет** , если у задания нет расписания.  
  
 <sup>1</sup>только членами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin фиксированной серверной роли и группы администраторов сервера могут видеть значения в этом столбце. Члены роли SQLAgentOperatorRole не могут видеть значения в этом столбце.  
  
#### <a name="to-open-the-job-activity-monitor"></a>Как открыть монитор активности заданий  
  
-   В **обозревателе объектов**разверните сервер, раскройте узел **Агент SQL Server**, щелкните правой кнопкой мыши **Монитор активности заданий**, затем выберите пункт **Просмотр активности заданий**.  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за активностью заданий](monitor-job-activity.md)  
  
  