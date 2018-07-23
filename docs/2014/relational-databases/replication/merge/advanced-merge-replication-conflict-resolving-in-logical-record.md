---
title: Распознавание и разрешение конфликтов в логических записях | Документация Майкрософт
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
- logical records [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: f2e55040-ca69-4ccf-97d1-c362e1633f26
caps.latest.revision: 31
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1e12ca76aa43b61eef3b41e4ceadf587ce1f6824
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208854"
---
# <a name="detecting-and-resolving-conflicts-in-logical-records"></a>Detecting and Resolving Conflicts in Logical Records
  В разделе рассматриваются различные комбинации подходов к распознаванию конфликтов и устранению конфликтов, возможные при использовании логических записей. В репликации слиянием возникает конфликт, когда изменение одних и тех же данных производится более чем одним узлом, или же в репликации слиянием возникают определенные типы ошибок, такие как нарушение ограничений, когда изменяется репликация. Дополнительные сведения о распознавании и разрешении конфликтов см. в разделе [Расширенное обнаружение и разрешение конфликтов репликации слиянием](advanced-merge-replication-conflict-detection-and-resolution.md).  
  
 Чтобы указать уровень отслеживания конфликтов и разрешений, см. раздел [Указание уровня отслеживания и разрешения конфликтов для статей публикации слиянием](../publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md).  
  
## <a name="conflict-detection"></a>Обнаружение конфликтов  
 Способ обнаружения конфликтов в логических записях определяется двумя свойствами статьи: **column_tracking** и **logical_record_level_conflict_detection**. [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздние версии также поддерживают обнаружение на уровне логической записи.  
  
 Значением свойства статьи **logical_record_level_conflict_detection** может быть TRUE или FALSE. Значение должно быть задано только для родительской статьи верхнего уровня. Кроме того, его должны игнорировать все дочерние статьи. Если значение этого параметра FALSE, репликация слиянием обнаруживает конфликты, как в предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], основываясь исключительно на значениях свойства **column_tracking** для статьи. Если значение этого параметра TRUE, репликация слиянием игнорирует значение свойства **column_tracking** для статьи и определяет конфликт, если где-либо в логической записи были сделаны изменения. В качестве примера рассмотрен сценарий:  
  
 ![Логическая запись из трех таблиц со значениями](../media/logical-records-05.gif "Логическая запись из трех таблиц со значениями")  
  
 Конфликт обнаруживается, если два пользователя изменяют любые значения логической записи Customer2 в таблицах **Customers**, **Orders**, или **OrderItems** . В этом примере учитываются изменения, сделанные посредством инструкции UPDATE, но конфликт может быть также обнаружен, если изменения сделаны с помощью инструкций INSERT или DELETE.  
  
## <a name="conflict-resolution"></a>Устранение конфликтов  
 По умолчанию в репликациях слиянием для разрешения конфликтов используется логика, основанная на приоритетах. Если изменения, приводящие к конфликту, сделаны в базах данных двух подписчиков, предпочтение отдается изменениям подписчика с высшим приоритетом подписки; в случае одинаковых приоритетов побеждает подписчик, чьи изменения достигли издателя раньше. При обнаружении конфликтов на уровне строк или столбцов данные из строки победившего участника записываются поверх данных проигравшей базы данных.  
  
 Значением свойства статьи **logical_record_level_conflict_resolution** может быть TRUE или FALSE. Значение должно быть задано только для родительской статьи верхнего уровня. Кроме того, его должны игнорировать все дочерние статьи. При значении TRUE значение выигравшей логической записи записывается поверх проигравшей логической записи. При значении параметра FALSE, отдельные выигравшие строки могут быть взяты из различных подписчиков и издателей. Например, подписчик А может выиграть конфликт по строке из таблицы **Orders** , а подписчик В выигрывает по соответствующей строке из таблицы **OrderItems** table. Результатом будет логическая запись, содержащая данные из строки **Orders** подписчика А и строки **OrderItems** подписчика В.  
  
## <a name="interaction-of-conflict-resolution-and-detection-settings"></a>Взаимодействие настроек обнаружения и устранения конфликтов  
 Исходы конфликтов зависят от взаимодействия настроек обнаружения и разрешения конфликтов. В примере ниже предполагается использование устранения конфликта на основе приоритетов. При использовании логических записей, возможны следующие варианты.  
  
-   Обнаружение на уровне строк или столбцов, разрешение на уровне строк.  
  
-   Обнаружение на уровне столбцов, разрешение на уровне логических записей.  
  
-   Обнаружение на уровне строк, разрешение на уровне логических записей.  
  
-   Обнаружение на уровне логических записей, разрешение на уровне логических записей.  
  
### <a name="row-or-column-level-detection-row-level-resolution"></a>Обнаружение на уровне строк или столбцов, разрешение на уровне строк.  
 В этом примере публикация настраивается с помощью:  
  
-   параметр**column_tracking** принимает значения TRUE или FALSE;  
  
-   параметр**logical_record_level_conflict_detection** имеет значение FALSE;  
  
-   параметр**logical_record_level_conflict_resolution** имеет значение FALSE.  
  
 В этом случае обнаружение конфликтов осуществляется на уровне строк или столбцов, а разрешение — на уровне строк. С помощью этих настроек используется преимущество, когда все изменения в логической записи реплицируются как одно целое, но без обнаружения или разрешения конфликта на уровне логических записей.  
  
### <a name="column-level-detection-logical-record-resolution"></a>Обнаружение на уровне столбцов, разрешение на уровне логических записей.  
 В этом примере публикация настраивается с помощью:  
  
-   параметр**column_tracking** имеет значение TRUE;  
  
-   параметр**logical_record_level_conflict_detection** имеет значение FALSE;  
  
-   параметр**logical_record_level_conflict_resolution** имеет значение TRUE.  
  
 Издатель и подписчик начинают работать с одним и тем же набором данных, логическая запись определяется между таблицами **orders** и **customers** . Издатель изменяет столбец **custcol1** в таблице **customers** , а так же **ordercol1** в таблице **orders** . Подписчик изменяет **custcol1** в той же самой строке таблицы **customers** и столбец **ordercol2** в той же строке таблицы **orders** . Изменения одного и того же столбца в таблице **customer** приводят к конфликту, но изменения таблицы **orders** к конфликту не приводят.  
  
 Поскольку разрешение конфликтов производится на уровне логических записей, выигравшими изменениями, сделанными издателем, заменяются изменения, сделанные в таблицах подписчика во время обработки репликации.  
  
 ![Последовательность таблиц, показывающая изменения связанных строк](../media/logical-records-06.gif "Последовательность таблиц, показывающая изменения связанных строк")  
  
### <a name="row-level-detection-logical-record-resolution"></a>Обнаружение на уровне строк, разрешение на уровне логических записей.  
 В этом примере публикация настраивается с помощью:  
  
-   параметр**column_tracking** имеет значение FALSE;  
  
-   параметр**logical_record_level_conflict_detection** имеет значение FALSE;  
  
-   параметр**logical_record_level_conflict_resolution** имеет значение TRUE.  
  
 Издатель и подписчик запускаются с одинаковым набором данных. Издатель изменяет столбец **custcol1** в таблице **пользователи** . Подписчик изменяет столбец **custcol2** в таблице **customers** , а так же **ordercol2** в таблице **orders** . Изменения одной и той же строки в таблице **customers** приводят к конфликту, но изменения подписчиком таблицы **orders** к конфликту не приводят.  
  
 Поскольку разрешение конфликтов производится на уровне логических записей, во время синхронизации изменения, сделанные в таблицах подписчика, заменяются выигравшими изменениями, сделанными издателем.  
  
 ![Последовательность таблиц, показывающая изменения связанных строк](../media/logical-records-07.gif "Последовательность таблиц, показывающая изменения связанных строк")  
  
### <a name="logical-record-detection-logical-record-resolution"></a>Обнаружение на уровне логических записей, разрешение на уровне логических записей.  
 В этом примере публикация настраивается с помощью:  
  
-   параметр**logical_record_level_conflict_detection** имеет значение TRUE;  
  
-   параметр**logical_record_level_conflict_resolution** имеет значение TRUE.  
  
 Издатель и подписчик запускаются с одинаковым набором данных. Издатель изменяет столбец **custcol1** в таблице **пользователи** . Подписчик изменяет столбец **ordercol1** в таблице **orders** . Изменения не относятся к одной и той же строке или одним и тем же столбцам, но поскольку изменения произошли в одной и той же логической записи для **custid**=1, они распознаны как конфликт на уровне логической записи.  
  
 Поскольку разрешение конфликтов производится также на уровне логических записей, во время синхронизации изменения, сделанные в таблицах подписчика, заменяются выигравшими изменениями, сделанными издателем.  
  
 ![Последовательность таблиц, показывающая изменения связанных строк](../media/logical-records-08.gif "Последовательность таблиц, показывающая изменения связанных строк")  
  
## <a name="see-also"></a>См. также  
 [Группирование изменений в связанных строках с помощью логических записей](group-changes-to-related-rows-with-logical-records.md)  
  
  