---
title: Редактирование таблиц | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d976c1c2ed5d79f4baaf59365a0ea812cfe15a19
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35333008"
---
# <a name="edit-tables"></a>Редактирование таблиц
  На вкладке **Таблицы** можно изменять таблицы и столбцы, выбранные в базе данных-источнике Oracle. Эта вкладка содержит следующие элементы.  
  
 **Список «Таблица»**  
 Список таблиц состоит из трех столбцов:  
  
-   **Имя таблицы Oracle**: имя таблицы с указанием схемы.  
  
-   **Экземпляр отслеживания**: имя экземпляра отслеживания, используемое для именования объектов отслеживания изменений данных по экземплярам. Значение экземпляра отслеживания не может быть равно NULL. Если имя не указано, то оно образуется из имен исходных схемы и таблицы в формате `<schema-name>_<table-name>.` Длина имени экземпляра отслеживания не должна превышать 100 символов, а само имя должно быть уникальным в рамках базы данных. Щелкните любую ячейку в этом столбце, чтобы изменить **capture_instance**вручную.  
  
-   **Роль безопасности**: имя роли базы данных, используемой для получения доступа к данным об изменениях. Щелкните любую ячейку в этом столбце, чтобы изменить **security_role**вручную.  
  
 **Добавить таблицы**  
 Нажмите кнопку **Добавить таблицы** , чтобы открыть диалоговое окно "Выбор таблицы", где вы можете [добавить таблицы в экземпляр CDC](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md). Если доступ к базе данных Oracle осуществляется впервые в ходе данного сеанса, необходимо [Connect to Oracle](../../integration-services/change-data-capture/connect-to-oracle.md).  
  
 **Изменить**  
 Выберите таблицу из списка, а затем **Правка** , чтобы открыть диалоговое окно **Свойства** этой таблицы, позволяющее [Изменение свойств таблицы](../../integration-services/change-data-capture/edit-the-table-properties.md).  
  
> [!NOTE]  
>  Нельзя изменить сопоставление типа для таблиц, у которых уже есть зеркальные таблицы. Это можно сделать только для новых таблиц.  
  
 **Удалить**  
 Выберите таблицу из списка и нажмите **Удалить** , чтобы удалить таблицу из экземпляра CDC.  
  
## <a name="see-also"></a>См. также:  
 [Как изменить свойства экземпляра CDC](../../integration-services/change-data-capture/how-to-edit-the-cdc-instance-properties.md)   
 [Выбор таблиц и столбцов Oracle](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  
