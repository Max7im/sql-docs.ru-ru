---
title: SQL Server, объект Backup Device | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
caps.latest.revision: 18
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d24d22fe3a2790f9dce20902b34cd192e572c3bd
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43811640"
---
# <a name="sql-server-backup-device-object"></a>SQL Server, объект Backup Device
  **Устройство резервного копирования** предоставляет счетчики для контроля над устройствами резервного копирования и операциями восстановления Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Контролировать устройства резервного копирования нужно, если необходимо определить пропускную способность, состояние или производительность операций резервного копирования и восстановления для каждого из устройств. Чтобы контролировать пропускную способность операции резервного копирования или восстановить всю **базу данных**, используйте счетчик **Пропускная способность резервного копирования/восстановления в байтах/с** объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [SQL Server, Databases Object](sql-server-databases-object.md).  
  
 В следующей таблице описан счетчик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Устройство резервного копирования** .  
  
|Счетчики устройств резервного копирования SQL Server|Описание|  
|---------------------------------------|-----------------|  
|**Пропускная способность устройства, байт/с**|Пропускная способность операций чтения и записи (в байтах на секунду) для устройства резервного копирования при создании резервной копии базы данных или ее восстановлении. Этот счетчик существует, только если выполняется операция резервного копирования или восстановления.|  
  
## <a name="see-also"></a>См. также  
 [Устройства резервного копирования (SQL Server)](../backup-restore/backup-devices-sql-server.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](monitor-resource-usage-system-monitor.md)  
  
  
