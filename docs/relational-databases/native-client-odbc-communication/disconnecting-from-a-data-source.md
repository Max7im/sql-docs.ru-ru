---
title: Отключение от источника данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 54ed7e67a6e54626329df085dc80d8b475382bdc
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43062573"
---
# <a name="disconnecting-from-a-data-source"></a>Отсоединение от источника данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Когда приложение завершило использование источника данных, он вызывает **SQLDisconnect**. **SQLDisconnect** освобождает все инструкции, выделенных для подключения и отсоединяет драйвер от источника данных. После отсоединения приложение может вызвать [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) для освобождения дескриптора соединения. Перед завершением работы приложение также вызывает **SQLFreeHandle** для освобождения дескриптора среды.  
  
 После отсоединения приложение может повторно использовать выделенный дескриптор соединения, либо для соединения с другим источником данных, либо для повторного соединения с тем же. Для принятия решения о сохранении соединения или отсоединении и повторном соединении, разработчик приложения должен рассмотреть сравнительную стоимость каждого варианта. Соединение с источником данных и сохранение соединения в различных окружениях могут оказаться в разной степени затратными. Чтобы сделать выбор, следует также проанализировать вероятность и временные затраты других операций в том же источнике данных. Также приложению может потребоваться более одного соединения.  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с SQL Server &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
