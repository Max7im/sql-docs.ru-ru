---
title: "Удаление записей с помощью метода Delete | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, deleting records
- deleting records [ADO]
- editing data [ADO], Delete method
- Delete method [ADO]
ms.assetid: bfed5cfa-7f57-463b-9da2-0c612a079d30
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6975a45ddf15f1a42709fe7c4ab069ba0aa37bea
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="deleting-records-using-the-delete-method"></a>Удаление записей с помощью метода Delete
С помощью **удаление** метод помечает текущей записи или группы записей в **записей** объект для удаления. Если **записей** объекта не допускает удаление записей происходит ошибка. Если вы находитесь в режим немедленного обновления, удаления происходит в базе данных немедленно. Если запись не может успешно удалены (из-за нарушения целостности базы данных, например), запись будет оставаться в режиме редактирования после вызова **обновления.** Это означает, что необходимо отменить обновление с использованием [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) перед перемещением текущей записи (например, с помощью [закрыть](../../../ado/reference/ado-api/close-method-ado.md), [переместить](../../../ado/reference/ado-api/move-method-ado.md), или [ NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)).  
  
 При работе в пакетном режиме обновления записи, помечаются для удаления из кэша и фактическое удаление происходит при вызове **UpdateBatch** метод. (Чтобы просмотреть список удаленных записей, задайте **фильтра** свойства **adFilterAffectedRecords** после **удалить** называется.)  
  
 При попытке извлечь значения полей из записи удаленных выдает ошибку. После удаления текущей записи, удаленная запись остается в текущей до перехода к другой записи. Один раз перемещении из удаленной записи, он больше не доступен.  
  
 Если вложить удалений в транзакции, можно восстановить удаленные записи с помощью **RollbackTrans** метод. Если вы находитесь в пакетный режим обновления, можно отменить Ожидается удаление или группой ожидающих удаления с помощью **CancelBatch** метод.  
  
 Если происходит сбой попытки удалить записи из-за конфликта с базовыми данными (например, запись уже был удален другим пользователем), поставщик возвращает предупреждения, чтобы **ошибки** коллекции, но не остановки программы выполнение. Ошибка во время выполнения возникает только в том случае, если запрошенными записями конфликтуют.  
  
 Если **уникальной таблицы** динамическое свойство имеет значение и **записей** является результатом выполнения операции СОЕДИНЕНИЯ на нескольких таблицах **удалить** будет удалять только строки из таблицы, указанной в **уникальной таблицы** свойство.  
  
 **Удаление** метод принимает необязательный аргумент, который позволяет указать, какие записи подвержены **удалить** операции. Только допустимые значения для этого аргумента: одно из следующих ADO **AffectEnum** перечисляемые константы:  
  
-   **adAffectCurrent** затрагивает только текущую запись.  
  
-   **adAffectGroup** затрагивает только те записи, которые удовлетворяют текущего **фильтра** значение свойства. **Фильтра** свойству необходимо присвоить значение **FilterGroupEnum** значение или массив **закладки** для использования этого параметра.  
  
 Ниже приведен пример указания **adAffectGroup** при вызове **удалить** метод. Этот пример добавляет некоторые записи в образце **записей** и обновляет базу данных. А затем фильтрует **записей** с помощью **adFilterAffectedRecords** фильтра константа перечислимого типа, который оставляет только те записи, добавленные в **набора записей.** Наконец, он вызывает **удаление** метод и указывает, что все записи, удовлетворяющие текущим **фильтра** значение свойства (новые записи) должен быть удален.  
  
```  
'BeginDeleteGroup  
    'add some bogus records  
    With objRs  
        For i = 0 To 8  
            .AddNew  
            .Fields("CompanyName") = "Shipper Number " & i + 1  
            .Fields("Phone") = "(425) 555-000" & (i + 1)  
            .Update  
        Next i  
  
        ' update  
        .UpdateBatch  
  
        'filter on newly added records  
        .Filter = adFilterAffectedRecords  
        Debug.Print "Deleting the " & .RecordCount & _  
                    " records you just added."  
  
        'delete the newly added bogus records  
        .Delete adAffectGroup  
        .Filter = adFilterNone  
        Debug.Print .RecordCount & " records remain."  
    End With  
'EndDeleteGroup  
```