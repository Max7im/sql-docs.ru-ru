---
title: Несколько активных инструкций и подключений | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b548b6d1b1aa7e7b260abcc9f507e2dbd566e7c1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912649"
---
# <a name="multiple-active-statements-and-connections"></a>Несколько активных инструкций и соединений
Некоторые драйверы и СУБД Ограничьте число инструкций и соединений, которые могут быть активны одновременно. Эти числа могут быть как один. Дополнительные сведения см. в разделе Параметры SQL_MAX_CONCURRENT_ACTIVITIES и SQL_MAX_DRIVER_CONNECTIONS в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание, функции и [оператор обрабатывает](../../../odbc/reference/develop-app/statement-handles.md) и [ Дескрипторы соединений](../../../odbc/reference/develop-app/connection-handles.md).
