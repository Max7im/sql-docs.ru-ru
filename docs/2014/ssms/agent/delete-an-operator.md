---
title: Удаление оператора | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- removing operators
- deleting operators
- dropping operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], deleting with Management Studio
ms.assetid: 2b7b8627-082d-4189-8584-abd3a9b604cf
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c058a71effc1837f2f949af53009d247dba5528d
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43819310"
---
# <a name="delete-an-operator"></a>Удаление оператора
  В этом разделе описано, как удалить оператора, чтобы он больше не получал уведомлений от агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Удаление оператора с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 При удалении оператора также удаляются все связанные с ним уведомления.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Удалять операторов могут члены предопределенной роли сервера **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-an-operator"></a>Удаление оператора  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, содержащий оператора, которого нужно удалить.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните значок «плюс», чтобы развернуть папку **Операторы** .  
  
4.  Щелкните правой кнопкой мыши оператор, который необходимо удалить, и выберите пункт **Удалить**.  
  
5.  В диалоговом окне **Удаление объекта** убедитесь, что выбран верный оператор, и нажмите кнопку **ОК**. Если нужно, чтобы предупреждения и задания, предназначенные удаленному оператору, получал другой оператор, установите флажок **Переназначить** и выберите любого оператора из списка  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-an-operator"></a>Удаление оператора  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- deletes operator 'Test Operator' and reassigns all alerts and jobs sent to that operator to 'François Ajenstat'  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_operator @name = 'Test Operator',  
        @reassign_to_operator = 'François Ajenstat';  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_delete_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-operator-transact-sql).  
  
  
