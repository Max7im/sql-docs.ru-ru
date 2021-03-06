---
title: Обработка данных (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5003c84d74f5c75fd840f3bc06f128031f6ffb18
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216254"
---
# <a name="process-data-ssas-tabular"></a>Обработка данных (табличные службы SSAS)
  При импорте данных в табличную модель в режиме кэширования создается моментальный снимок данных на момент импорта. В некоторых случаях эти данные могут оказаться неизменяемыми, и тогда обновлять их в модели не требуется. Однако с большей вероятностью импортированные данные будут регулярно изменяться, поэтому для того, чтобы модель отражала самые актуальные данные из источников данных, необходимо обрабатывать (обновлять) данные и проводить повторный расчет вычисляемых данных. Чтобы обновить данные в модели, выполните действие обработки для всех таблиц, для отдельной таблицы, секции или соединения с источником данных.  
  
 Действия процесса при создании проекта модели необходимо инициировать вручную в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. После развертывания модели операции процесса можно выполнить с помощью [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или запланировать с помощью скрипта. Описываемые здесь задачи относятся ко всем действиям процессов, которые можно выполнять во время разработки моделей в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения о действиях по обработке для развернутой модели см. в разделе [Process Database, Table, or Partition](tabular-models/process-database-table-or-partition-analysis-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Обработка данных вручную &#40;табличные службы SSAS&#41;](manually-process-data-ssas-tabular.md)|Описывает обработку данных рабочей области модели вручную.|  
|[Устранение неполадок в данных процесса &#40;табличные службы SSAS&#41;](troubleshoot-process-data-ssas-tabular.md)|Описывает устранение неполадок при операциях обработки.|  
  
  
