---
title: Статический SQL | Документы Microsoft
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
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff2144ae69c48098324bc0b97ca9c33d5159adc3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915185"
---
# <a name="static-sql"></a>Статический SQL
Embedded SQL, показанные в [пример Embedded SQL](../../odbc/reference/embedded-sql-example.md) известен как статический SQL. Поскольку являются статическими; инструкций SQL в программе вызывается статический SQL то есть они не изменяют при каждом запуске программы. Как описано в предыдущем разделе, эти инструкции, компилируются при компиляции остальные части программы.  
  
 Статический SQL работает также во многих случаях и может использоваться в любом приложении, для которого доступ к данным можно определить во время разработки программы. Например программа ввода заказа всегда используется той же инструкции вставить новый заказ, и системе бронирования авиабилетов всегда использует той же инструкции, чтобы изменить состояние рабочее место для зарезервированных. Каждая из этих инструкций будет обобщить с помощью переменных узла. разные значения могут быть вставлены в заказе на продажу и различных рабочих мест может быть зарезервирована. Поскольку такие инструкции могут быть жестко запрограммированы в программе, такие программы имеют преимущество инструкций необходимо проанализировать, проверки и оптимизации только один раз во время компиляции. Это приводит к появлению кода относительно быстро.
