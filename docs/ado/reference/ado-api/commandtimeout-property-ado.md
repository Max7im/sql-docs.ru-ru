---
title: Свойство CommandTimeout (ADO) | Документы Microsoft
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
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1addc5de70e53087cdcbaa77fea87211958cbcdc
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276873"
---
# <a name="commandtimeout-property-ado"></a>Свойство CommandTimeout (ADO)
Указывает время ожидания при выполнении команды перед прекращением попытки и созданием ошибки.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение, которое указывает, в секундах время ожидания выполнения команды. По умолчанию используется значение 30.  
  
## <a name="remarks"></a>Примечания  
 Используйте **CommandTimeout** свойство [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта или [команда](../../../ado/reference/ado-api/command-object-ado.md) объект, чтобы Отмена [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) метод вызов из-за задержки от использования сетевой трафик или большим числом операций сервера. Если задать интервал в **CommandTimeout** свойство истекает до завершения команды выполнения, возникает ошибка и ADO отменяет команду. Если это свойство равно нулю, ADO будет ожидать неопределенное время до завершения выполнения. Убедитесь, что поставщик и данные источника, к которой вы пишете код поддержки **CommandTimeout** функциональные возможности.  
  
 **CommandTimeout** на **подключения** объекта не оказывает влияния на **CommandTimeout** на **команда** объекта же **подключения**, то есть **команда** объекта **CommandTimeout** свойства не наследует значение **подключения** объекта **CommandTimeout** значение.  
  
 На **подключения** объекта, **CommandTimeout** остается свойства чтения и записи после **подключения** открыт.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление примере свойства (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Свойство ConnectionTimeout (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
