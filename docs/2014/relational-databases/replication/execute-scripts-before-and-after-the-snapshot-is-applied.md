---
title: Выполнение скриптов до и после применения моментального снимка | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], scripts
- scripts [SQL Server replication], snapshots
- snapshot replication [SQL Server], scripts
- scripts [SQL Server replication]
ms.assetid: 9a6872c2-9bed-477f-9d2f-332d640edcf2
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fde608be7281ca66856f63db3a2626863c1a30f1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320054"
---
# <a name="execute-scripts-before-and-after-the-snapshot-is-applied"></a>Выполнение скриптов до и после применения моментального снимка
  Можно указать скрипты для выполнения на подписчике до и после применения моментального снимка. Скрипты могут использоваться по различным причинам, таким как создание учетных имен и схем (владельцы объекта) на каждом подписчике.  
  
 Вы указываете размещение файла для каждого скрипта, и агент моментальных снимков копирует файлы скриптов в текущую папку моментальных снимков при каждой обработке моментального снимка. При применении моментального снимка агент распространителя или агент слияния запускает скрипт, предшествующий моментальному снимку, перед любым из скриптов реплицируемых объектов. Агент распространителя или агент слияния запускает скрипт, следующий за моментальным снимком, после применения всех других скриптов реплицируемых объектов и применения данных. После того как применение моментального снимка завершено и файлы скриптов успешно выполнены, файлы скриптов удаляются из рабочего каталога на подписчике.  
  
 Скрипт запускается при помощи служебной программы **sqlcmd** . До развертывания скрипта запустите его с помощью **sqlcmd** , чтобы убедиться, что он выполняется должным образом. Содержимое скриптов, которые выполняются до и после применения моментального снимка, должно быть повторяемым. Например, если вы создаете таблицу в скрипте, необходимо сначала проверить ее существование и предпринять соответствующее действие, если таблица существует. Скрипт должен быть повторяемым, потому что, если необходимо повторно инициализировать подписку, для которой уже был применен скрипт, скрипт будет применен повторно, когда новый моментальный снимок будет применяться в процессе повторной инициализации.  
  
 При сжатии файла моментального снимка (посредством его помещения в CAB-файл [!INCLUDE[msCoName](../../includes/msconame-md.md)] ) скрипты так же сжимаются и помещаются в CAB-файл. После того как сжатый файл моментального снимка передан подписчику и распакован в рабочий каталог на подписчике, выполняются все скрипты, помеченные как скрипты, предшествующие моментальному снимку. Аналогично любой скрипт, выполняющийся после моментального снимка, распаковывается и выполняется на подписчике как последний шаг в применении моментального снимка.  
  
 **Выполнение скриптов до и после применения моментального снимка**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Практическое руководство: выполнение скриптов до и после применения моментального снимка \(среда SQL Server Management Studio\)](execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   Программирование репликации на [!INCLUDE[tsql](../../includes/tsql-md.md)]: [Настройка свойств моментального снимка &#40;программирование репликации на языке Transact-SQL&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>См. также  
 [Инициализация подписки с помощью моментального снимка](initialize-a-subscription-with-a-snapshot.md)   
 [Параметры моментального снимка](snapshot-options.md)  
  
  
