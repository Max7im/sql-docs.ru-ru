---
title: Свойство SQLState | Документы Microsoft
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
- Error::GetSQLState
- Error::SQLState
- Error::get_SQLState
helpviewer_keywords:
- SQLState property
ms.assetid: f9e25967-54b0-444d-af2a-0d2c75365d3e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 97aa3d77696162e99f94876a19083ce96d5773e5
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281933"
---
# <a name="sqlstate-property"></a>Свойство SQLState
Указывает состояние SQL для заданной [ошибка](../../../ado/reference/ado-api/error-object.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает из пяти символов **строка** значение, которое соответствует стандарту ANSI SQL и указывающее код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Используйте **SQLState** свойство для чтения код ошибки пяти знаков, поставщик возвращает при возникновении ошибки во время обработки инструкции SQL. Например при использовании поставщика Microsoft OLE DB для ODBC с базой данных Microsoft SQL Server, кодах ошибок состояния SQL берутся из ODBC, либо на основе ODBC ошибки или ошибок, возникших в Microsoft SQL Server, а затем сопоставляются с ODBC ошибки. Эти коды ошибок описаны в стандарте ANSI SQL, но может быть реализована по-разному в разных источниках.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Описание, HelpContext, файл справки, NativeError, номер, источника и пример свойства SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Описание, HelpContext, файл справки, NativeError, номер, источник и пример свойства SQLState (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
