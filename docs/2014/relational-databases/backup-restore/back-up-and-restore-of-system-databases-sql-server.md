---
title: Резервное копирование и восстановление системных баз данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- system databases [SQL Server], backing up and restoring
- restoring system databases [SQL Server]
- backing up [SQL Server], system databases
- database backups [SQL Server], system databases
- servers [SQL Server], backup
ms.assetid: aef0c4fa-ba67-413d-9359-1a67682fdaab
caps.latest.revision: 57
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 81645730d3a854eff8b318ef04ee234f6206b4d0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197554"
---
# <a name="back-up-and-restore-of-system-databases-sql-server"></a>Резервное копирование и восстановление системных баз данных (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает набор баз данных системного уровня, которые называются*системными базами данных*и жизненно важны для работы экземпляра сервера. После каждого значительного обновления необходимо обязательно создавать резервные копии ряда системных баз данных: **msdb**, **master**и **model**. Если какая-нибудь из баз данных на экземпляре сервера использует репликацию, то необходимо также создавать резервную копию системной базы данных **distribution** . Резервные копии системных баз данных позволят восстановить систему [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в случае сбоя, например отказа жесткого диска.  
  
 В следующей таблице перечислены все системные базы данных.  
  
|Системная база данных|Описание|Необходимость создавать резервные копии|Модель восстановления|Комментарии|  
|---------------------|-----------------|---------------------------|--------------------|--------------|  
|[master](../databases/master-database.md)|База данных, в которой хранятся все системные данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|Да|Простой|Создавайте резервные копии базы данных **master** с такой частотой, которая необходима для адекватной защиты данных. Рекомендуем составить расписание регулярного резервного копирования, которое можно дополнить созданием резервных копий после значительных обновлений.|  
|[model](../databases/model-database.md)|Шаблон для всех баз данных, создаваемых на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Да|Настраивается пользователем<sup>1</sup>|Резервные копии базы данных **model** создаются только в том случае, если они необходимы для предприятия (например сразу же после настройки параметров базы данных).<br /><br /> **Рекомендация.** Рекомендуется по мере необходимости создавать только полные резервные копии базы данных **model**. Поскольку база данных **model** невелика и редко изменяется, создавать резервную копию журнала не обязательно.|  
|[msdb](../databases/msdb-database.md)|База данных, используемая агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для планирования предупреждений и заданий и для записи операторов. База данных**msdb** также содержит такие таблицы журнала, как таблицы резервных копий и журнала восстановления.|Да|Простая (по умолчанию)|Создавайте резервную копию базы данных **msdb** после каждого ее обновления.|  
|[Resource](../databases/resource-database.md) (RDB)|База данных только для чтения, которая содержит копии всех системных объектов, поставляемых с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Нет|—|База данных **Resource** находится в файле mssqlsystemresource.mdf, в котором содержится только код. Поэтому [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может создать резервную копию базы данных **Resource** .<br /><br /> Примечание. Исходя из того, что файл mssqlsystemresource.mdf является простым двоичным файлом (EXE), а не файлом базы данных, для создания его резервной копии можно выполнить простое резервное копирование файла или диска. Нельзя использовать восстановление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для резервных копий. Восстановить резервную копию файла mssqlsystemresource.mdf можно будет только вручную; при этом следует соблюдать осторожность, чтобы не перезаписать текущую базу данных **Resource** устаревшей или потенциально небезопасной версией.|  
|[tempdb](../databases/tempdb-database.md)|Рабочая область для хранения временных или промежуточных результирующих наборов. Эта база данных создается заново при каждом запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При отключении экземпляра сервера любые сведения, содержащиеся в базе данных **tempdb** , удаляются навсегда.|Нет|Простой|Создать резервную копию системной базы данных **tempdb** нельзя.|  
|[Настройка распространения](../replication/configure-distribution.md)|База данных, которая существует только в том случае, если сервер настроен как распространитель репликации. Эта база данных содержит метаданные и данные журнала для всех типов репликации, а также транзакции для репликации транзакций.|Да|Простой|Сведения о том, когда следует создавать резервные копии базы данных **distribution**, см. в статье [Создание резервных копий реплицируемых баз данных и восстановление из них](../replication/administration/back-up-and-restore-replicated-databases.md).|  
  
 <sup>1</sup> сведения о текущей модели восстановления, модели, см. в разделе [Просмотр или изменение модели восстановления базы данных &#40;SQL Server&#41; ](view-or-change-the-recovery-model-of-a-database-sql-server.md) или [sys.databases &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).  
  
## <a name="limitations-on-restoring-system-databases"></a>Ограничения восстановления системных баз данных  
  
-   Системные базы данных могут быть восстановлены только из резервных копий, созданных той версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которая запущена на данном экземпляре сервера. Например, чтобы восстановить системную базу данных на экземпляре сервера, на котором выполняется на [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 1.  
  
-   Для восстановления любой базы данных должен быть запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для запуска экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо, чтобы база данных **master** была доступна и хотя бы частично пригодна к использованию. Если база данных **master** непригодна к использованию, ее можно вернуть в нормальное состояние следующими способами.  
  
    -   Восстановить базу данных **master** на основе актуальной резервной копии.  
  
         Если экземпляр сервера удалось запустить, базу данных **master** можно восстановить из полной резервной копии.  
  
    -   Перестроить базу данных **master** с нуля.  
  
         Если серьезное повреждение базы данных **master** не позволяет запустить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], базу данных **master**нужно перестроить. Дополнительные сведения см. в разделе [Перестроение системных баз данных](../databases/system-databases.md).  
  
        > [!IMPORTANT]  
        >  При перестроении базы данных **master** все системные базы данных также перестраиваются.  
  
-   В некоторых случаях для проблем, связанных с восстановлением табличного шаблона базы данных модели, может потребоваться перестроение системных баз данных или замена MDF- и LDF-файлов базы данных модели. Дополнительные сведения см. в разделе [Перестроение системных баз данных](../databases/system-databases.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание полной резервной копии базы данных (SQL Server)](create-a-full-database-backup-sql-server.md)  
  
-   [Выполнение полного восстановления базы данных (простая модель восстановления)](complete-database-restores-simple-recovery-model.md)  
  
-   [Восстановление базы данных master (Transact-SQL)](restore-the-master-database-transact-sql.md)  
  
-   [Просмотр или изменение модели восстановления базы данных (SQL Server)](view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  
-   [Перемещение системных баз данных](../databases/move-system-databases.md)  
  
## <a name="see-also"></a>См. также  
 [База данных распространителя](../../relational-databases/replication/distribution-database.md)   
 [База данных master](../databases/master-database.md)   
 [База данных msdb](../databases/msdb-database.md)   
 [База данных model](../databases/model-database.md)   
 [База данных Resource](../databases/resource-database.md)   
 [База данных tempdb](../databases/tempdb-database.md)  
  
  
