---
title: Определение режима редактирования | Документы Microsoft
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
- editing data [ADO], edit mode
- ADO, editing data
ms.assetid: 4c7e010d-08cd-4e22-9b32-23c36f02f88c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5971234a7e758318acaac80b830d312327e14e8
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270353"
---
# <a name="determining-edit-mode"></a>Определение режима редактирования
ADO поддерживает редактирования буфера, связанное с текущей записью. **EditMode** свойство указывает ли были внесены изменения в этот буфер или ли создана новая запись. Используйте **EditMode** для определения состояния редактирования текущей записи. Можно проверить для ожидающих изменений, если был прерван процесс редактирования и определить, следует ли использовать **обновление** или **CancelUpdate** метод.  
  
 **EditMode** возвращает одно из **EditModeEnum** константы, перечисленные в следующей таблице.  
  
|Константа|Описание|  
|--------------|-----------------|  
|**как таковые**|Указывает, что ни одна из операций редактирования идет.|  
|**adEditInProgress**|Указывает, что данные в текущей записи были изменены, но не сохранены.|  
|**adEditAdd**|Указывает, что **AddNew** был вызван метод, и текущую запись в буфер копирования считается новой записью, не были сохранены в базе данных.|  
|**adEditDelete**|Указывает, что текущая запись была удалена.|  
  
 **EditMode** может возвращать допустимое значение только в том случае, если текущая запись. **EditMode** вернет ошибку, если **BOF** или **EOF** — **True** или если текущая запись была удалена.
