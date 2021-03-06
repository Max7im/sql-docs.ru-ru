---
title: Указание уровня отслеживания и разрешения конфликтов для статей публикации слиянием | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], levels
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 81e9ecb6-1d31-4a78-b32a-96f7f4d67077
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 37933a1c056e6e75902c31d01e164a770639a959
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37309504"
---
# <a name="specify-the-conflict-tracking-and-resolution-level-for-merge-articles"></a>Указание уровня отслеживания и разрешения конфликтов для статей публикации слиянием
  В данном разделе описывается указание уровня отслеживания и разрешения конфликтов для статей публикации слиянием в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 При синхронизации подписки на публикацию слиянием репликация проверяет наличие конфликтов, вызванных изменениями в одних и тех же данных, внесенных на издателе и подписчике. Можно указать, чтобы конфликты определялись на уровне строки, где любое изменение строки будет считаться конфликтом, либо на уровне столбца, где конфликтом будет считаться только изменение в одних и тех же строке и столбце. Разрешение конфликтов статей выполняется на уровне строки. Дополнительные сведения по определению и разрешению конфликтов при использовании логических записей см. в разделе [Detecting and Resolving Conflicts in Logical Records](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
-   **Для указания уровня отслеживания и разрешения конфликтов для статей публикации слиянием используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Если изменить уровень отслеживания после инициализации подписок, то эти подписки потребуется инициализировать повторно. Дополнительные сведения о последствиях изменения свойств см. в статье [Изменение свойств публикации и статьи](change-publication-and-article-properties.md).  
  
-   При отслеживании на уровне строк и столбцов устранение конфликтов всегда выполняется на уровне строк: победившая строка перезаписывает проигравшую строку. Репликация слиянием также позволяет указывать, что конфликты должны отслеживаться и разрешаться на уровне логических записей, но эти параметры недоступны из среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]. Сведения об установке данных параметров с помощью хранимых процедур репликации см. в разделе [Определение связи логических записей между статьями таблиц слияния](define-a-logical-record-relationship-between-merge-table-articles.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Выберите отслеживание на уровне строк или столбцов для статей публикации слиянием на вкладке **Свойства** диалогового окна **Свойства статьи**, которое доступно в мастере создания публикаций и диалоговом окне **Свойства публикации — \<публикация>**. Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](create-a-publication.md) и [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-row--or-column-level-tracking"></a>Указание уровня отслеживания на уровне строк или столбцов  
  
1.  На странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<публикация>** выберите таблицу.  
  
2.  Щелкните **Свойства статьи**, затем щелкните **Указать свойства выделенной статьи таблицы** или **Указать свойства всех статей таблиц**.  
  
3.  На вкладке **Свойства** диалогового окна **Свойства статьи — \<статья>** выберите одно из следующих значений для свойства **Уровень отслеживания**: **Отслеживание на уровне строк** или **Отслеживание на уровне столбцов**.  
  
4.  Если вы находитесь в диалоговом окне **Свойства публикации — \<публикация>**, нажмите кнопку **ОК**, чтобы сохранить изменения и закрыть диалоговое окно.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-specify-conflict-tracking-options-for-a-new-merge-article"></a>Настройка параметров отслеживания конфликтов для новой статьи публикации слиянием  
  
1.  На издателе базы данных публикации выполните хранимую процедуру [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) и присвойте параметру **@column_tracking**одно из приведенных ниже значений:  
  
    -   **true** — использовать для статьи отслеживание на уровне столбцов;  
  
    -   **false** — использовать отслеживание на уровне строк (значение по умолчанию).  
  
#### <a name="to-change-conflict-tracking-options-for-a-merge-article"></a>Изменение параметров отслеживания конфликтов для статьи публикации слиянием  
  
1.  Чтобы определить текущие параметры отслеживания конфликтов для статьи публикации слиянием, выполните хранимую процедуру [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql). Проверьте значение параметра **column_tracking** в результирующем наборе для статьи. Значение **1** показывает, что используется отслеживание конфликтов уровня столбца, а значение **0** — отслеживание конфликтов уровня строки.  
  
2.  В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). В качестве значения параметра **column_tracking** задайте значение **@property** , а параметру **@value**одно из приведенных ниже значений:  
  
    -   **true** — использовать для статьи отслеживание на уровне столбцов;  
  
    -   **false** — использовать отслеживание на уровне строк (значение по умолчанию).  
  
     В качестве значения параметра **1** параметрам **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
## <a name="see-also"></a>См. также  
 [Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Detecting and Resolving Conflicts in Logical Records](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md)   
 [Определение связи логических записей между статьями таблиц слияния](define-a-logical-record-relationship-between-merge-table-articles.md)   
 [Обнаружение и разрешение конфликтов репликации слиянием](../merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)  
  
  
