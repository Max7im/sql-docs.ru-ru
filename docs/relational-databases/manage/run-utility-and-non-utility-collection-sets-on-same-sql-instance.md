---
title: "Запуск наборов элементов сбора для служебной программы и для других целей на одном экземпляре SQL | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d6f1a687472d2ee83f48fe273008a0d60f51bc58
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="run-utility-and-non-utility-collection-sets-on-same-sql-instance"></a>Запуск наборов элементов сбора для служебной программы и для других целей на одном экземпляре SQL
  Набор элементов сбора служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживается параллельно с наборами элементов сбора, не касающимися служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Таким образом, управляемый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно наблюдать по другим наборам элементов сбора, поскольку он является элементом служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако при регистрации экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] все функции сбора данных, не относящиеся к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должны быть отключены.  
  
 После регистрации экземпляра в UCP наборы элементов сбора, не относящиеся к служебной программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , можно будет перезапустить. Следует, однако, отметить, что все наборы элементов сбора, находящиеся в управляемом экземпляре, передают свои данные в хранилище данных управления для программы (UMDW).  
  
 Чтобы наборы элементов сбора служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работали параллельно с наборами элементов сбора, не относящимися к служебной программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо учитывать следующее.  
  
-   Поддерживается параллельная работа наборов элементов сбора.  
  
-   Существующие сборщики данных необходимо отключать при регистрации экземпляров в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Чтобы передать требования проверки, перед созданием UCP, а также перед регистрацией экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо запустить следующие хранимые процедуры:  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     Если не запустить эти хранимые процедуры перед запуском мастера создания UCP или мастера добавления управляемого экземпляра, то операция завершится неудачей.  
  
-   Для всех наборов элементов сбора в управляемом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо использовать хранилище UMDW (sysutility_mdw) служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Настройка хранилища данных точки управления служебной программы (служебная программа SQL Server)](../../relational-databases/manage/configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  