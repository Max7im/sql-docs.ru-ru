---
title: Добавление записей с помощью AddNew | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: cab4adff-f22f-4fb1-9217-f8138c795268
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 36827d102d7e6ef0850c557eb6555135343fbec0
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270093"
---
# <a name="adding-records-using-addnew-method"></a>Добавление записей с помощью AddNew-метод
Это обычный синтаксис **AddNew** метод:

 *набор записей*. AddNew *списка полей*, *значения*

 *Списка полей* и *значения* аргументы являются необязательными. *Список полей* является одиночным именем или массив имена или порядковые номера поля в новой записи.

 *Значения* аргумент имеет одно значение или массив значений для поля в новой записи.

 Как правило, если планируется добавить в одну запись будет вызывать **AddNew** метод без аргументов. В частности, вы будете вызывать **AddNew**; задайте **значение** каждого поля в новой записи; а затем вызвать **обновление** или **UpdateBatch**, или оба. Можно убедиться в том, к **записей** поддерживает добавление новых записей с помощью **поддерживает** свойство с **adAddNew** константы перечисления.

 Следующий код использует этот метод для добавления нового Shipper пример **записей**. SQL Server автоматически предоставляет значение поля ShipperID. Таким образом код не пытается задать значение поля для новых записей.

```
'BeginAddNew1.1
If objRs.Supports(adAddNew) Then
    With objRs
        .AddNew
        .Fields("CompanyName") = "Sample Shipper"
        .Fields("Phone") = "(931) 555-6334"
        .Update
    End With
End If
'EndAddNew1.1
```

## <a name="remarks"></a>Примечания
 Так как этот код использует несвязанный **записей** с клиентский курсор в пакетном режиме, необходимо повторно подключить **записей** к источнику данных с новым **подключения** объект перед вызовом **UpdateBatch** метод, чтобы учесть изменения в базу данных. Это делается с помощью новой функции легко **GetNewConnection**.
