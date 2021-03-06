---
title: Создание базы данных изменения SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- oraIns
ms.assetid: 4f79c24a-e99a-4a06-8637-51eeec406259
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a70454b82f13b6bee786ad660b6e69985bafc8aa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287700"
---
# <a name="create-the-sql-server-change-database"></a>Создание базы данных изменения SQL Server
  При запуске мастера создания экземпляра открывается страница «Создание базы данных CDC». На странице «Создание базы данных CDC» содержатся сведения о новом экземпляре CDC, а также создается новая база данных изменений.  
  
 При создании новой базы данных CDC она должна быть подготовлена для работы CDC SQL Server, для чего потребуется имя входа, которое является членом предопределенной роли сервера `sysadmin` .  
  
 Если пользователь, запускающий мастер создания экземпляра CDC Oracle, не является членом предопределенной роли сервера `sysadmin` , то открывается диалоговое окно «Соединение с SQL Server», где необходимо ввести учетные данные члена роли sysadmin, чтобы обеспечить выполнение в базе данных задачи обеспечения работы CDC SQL Server. При создании базы данных CDC имя входа `sysadmin` удаляется, а работа возобновляется с первоначальным именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которое использовалось для входа в консоль конструктора Oracle.  
  
> [!IMPORTANT]  
>  Для выполнения остальных задач, кроме обеспечения работы CDC SQL Server в базе данных, имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использовавшееся для запуска мастера создания экземпляра, должно принадлежать к предопределенной роли сервера `dbcreator` и обладать разрешениями UPDATE на базу данных MSXDBCDC.  
  
 Сведения о вводе данных в диалоговое окно «Подключение к SQL Server» см. в разделе [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md).  
  
## <a name="options"></a>Параметры  
 **Экземпляр CDC Oracle**  
 Укажите следующие сведения для создаваемого экземпляра CDC.  
  
-   **Имя**. Введите имя новой службы. Оно также будет использоваться в качестве имени новой базы данных изменений.  
  
-   **Описание**. Введите описание нового экземпляра, чтобы проще идентифицировать его. Водить описание не обязательно.  
  
 **База данных изменений SQL Server**  
 Этот раздел используется для создания базы данных.  
  
1.  **Изменение базы данных**. Имя новой базы данных изменений. Этой базе данных назначается то же имя, которое было присвоено экземпляру. В этом поле, доступном только для чтения, отображается полный пусть к базе данных.  
  
2.  **Создание базы данных**. Щелкните **Создать базу данных** , чтобы создать ее.  
  
     Для создания базы данных имя входа должно быть членом роли сервера `sysasmin` . Дополнительные сведения см. в приведенном выше примечании о безопасности.  
  
     После создания базы данных можно нажать кнопку **Далее** , чтобы перейди к диалоговому окну [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md).  
  
## <a name="see-also"></a>См. также  
 [Как создать экземпляр базы данных изменения SQL Server](how-to-create-the-sql-server-change-database-instance.md)   
 [Служба CDC Oracle](the-oracle-cdc-service.md)  
  
  
