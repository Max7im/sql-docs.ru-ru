---
title: Коллекция столбцов (ADOX) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Index::Columns
- Table::Columns
- Key::Columns
- Columns
helpviewer_keywords:
- Columns collection [ADOX]
ms.assetid: 23b9fea8-4f76-4a51-95ce-1a6ce4560b34
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65b5ae6a15ee5da44c2876c75dc21e658b50fed6
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285203"
---
# <a name="columns-collection-adox"></a>Коллекция столбцов (ADOX)
Содержит все [столбца](../../../ado/reference/adox-api/column-object-adox.md) объекты из таблицы, индекса или ключа.  
  
## <a name="remarks"></a>Примечания  
 [Append](../../../ado/reference/adox-api/append-method-adox-columns.md) метод **столбцы** является уникальным для ADOX. Возможные действия:  
  
-   Добавить новый столбец в коллекцию с **Append** метод.  
  
 Остальные свойства и методы являются стандартными коллекциям ADO. Возможные действия:  
  
-   Доступ к столбцу в коллекции с [элемент](../../../ado/reference/ado-api/item-property-ado.md) свойство.  
  
-   Возвращает число столбцов, содержащихся в коллекции с [число](../../../ado/reference/ado-api/count-property-ado.md) свойство.  
  
-   Удаление столбца из коллекции с помощью [удалить](../../../ado/reference/adox-api/delete-method-adox-collections.md) метод.  
  
-   Обновление объектов в коллекции в соответствии с текущей базы данных в схеме с [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод.  
  
> [!NOTE]
>  Произойдет ошибка при наращивании **столбца** для **столбцы** коллекцию [индекс](../../../ado/reference/adox-api/index-object-adox.md) Если **столбца** не существует в [Таблицы](../../../ado/reference/adox-api/table-object-adox.md) , добавляется к уже [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) коллекции.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Columns](../../../ado/reference/adox-api/columns-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Столбцы и таблицы добавьте методы примера имя свойства (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Подключение метода закрытия, пример свойство типа таблицы (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Ключи добавить метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule-пример свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Пример свойства SortOrder (Visual Basic)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
