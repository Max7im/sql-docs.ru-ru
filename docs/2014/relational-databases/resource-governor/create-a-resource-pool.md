---
title: Создание пула ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- resource pools [SQL Server], create
- Resource Governor, resource pool create
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
caps.latest.revision: 18
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a4b40dbe43d4307eb13a33faacaf58df1cc6ff81
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227374"
---
# <a name="create-a-resource-pool"></a>Создание пула ресурсов
  Можно создать пул ресурсов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Перед началом работы:**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **To create a resource pool, using:**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="LimitationsRestrictions"></a> ограничения  
 Максимальный процент использования ЦП должен быть больше минимального или равен ему. Максимальный процент использования памяти должен быть больше минимального или равен ему.  
  
 Сумма значений минимальных процентов использования ЦП и минимальных процентов использования памяти для всех пулов ресурсов не должна превышать 100.  
  
###  <a name="Permissions"></a> Permissions  
 Для создания пула ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="CreRPProp"></a> Создание пула ресурсов в среде SQL Server Management Studio  
 **Создание пула ресурсов с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните **Регулятор ресурсов**правой кнопкой мыши и выберите команду **Свойства**.  
  
3.  В сетке **Пулы ресурсов** щелкните первый столбец в пустой строке. Этот столбец отмечен звездочкой (*).  
  
4.  Дважды щелкните пустую ячейку в столбце **Имя** . Введите имя, которое следует присвоить пулу ресурсов.  
  
5.  Щелкните или дважды щелкните все прочие ячейки в строке, в которые необходимо внести изменения, и введите новые значения.  
  
6.  Чтобы сохранить изменения, нажмите кнопку **ОК**.  
  
##  <a name="CreRPTSQL"></a> Создание пула ресурсов с помощью Transact-SQL  
 **Создание пула ресурсов с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Выполните инструкцию `CREATE RESOURCE POOL`, указав значения свойств, которые необходимо присвоить.  
  
2.  Выполните инструкцию **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере создается пул ресурсов с именем `poolAdhoc`.  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Регулятор ресурсов](resource-governor.md)   
 [Активация регулятора ресурсов](enable-resource-governor.md)   
 [Resource Governor Resource Pool](resource-governor-resource-pool.md)   
 [Изменение параметров пула ресурсов](change-resource-pool-settings.md)   
 [Удаление пула ресурсов](delete-a-resource-pool.md)   
 [Настройка регулятора ресурсов с помощью шаблона](configure-resource-governor-using-a-template.md)   
 [Группа рабочей нагрузки регулятора ресурсов](resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](resource-governor-classifier-function.md)   
 [CREATE RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/create-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  