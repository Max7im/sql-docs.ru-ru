---
title: Состояние свойства (ADO) | Документы Microsoft
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
- Command25::State
helpviewer_keywords:
- State property [ADO]
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7224efc2976873ff0326aa23a18df1cccbce230
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282033"
---
# <a name="state-property-ado"></a>Свойство State (ADO)
Указывает все соответствующие объекты, является ли открытое или закрытое состояние объекта. Если объект выполняется асинхронный метод, указывает ли текущее состояние объекта соединения, выполняется или получение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **длинные** значение, которое может быть [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) значение. Значение по умолчанию — **adStateClosed**.  
  
## <a name="remarks"></a>Примечания  
 Можно использовать **состояние** свойства, чтобы определить текущее состояние данного объекта в любое время.  
  
 Объект **состояние** свойство может принимать набор значений. Например, если при выполнении инструкции, это свойство будет объединенное значение **adStateOpen** и **adStateExecuting**.  
  
 **Состояние** свойство доступно только для чтения.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>См. также  
 [ConnectionString, ConnectionTimeout и пример свойства состояния (Visual Basic)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout и пример свойства состояния (VC ++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
