---
title: Обработка ошибок и сообщений | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, about error handling
- errors [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], about messages
- ODBC error handling
- SQL_INVALID_HANDLE return code
- errors [ODBC], about error handling
- messages [ODBC]
ms.assetid: 74ea9630-e482-4a46-bb45-f5234f079b48
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f4fa349dd10030c91910842d5b33d7a1fab471f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410959"
---
# <a name="handling-errors-and-messages"></a>Обработка ошибок и сообщений
  Когда приложение вызывает функцию ODBC, драйвер выполняет функцию и возвращает диагностические сведения двумя способами: код возврата указывает общий успех или сбой функции ODBC, а диагностические записи предоставляют подробные сведения о функция. Диагностическая запись состоит из записи заголовка и записи состояния. При успешном выполнении функции возвращается как минимум одна диагностическая запись, запись заголовка.  
  
 Диагностические сведения используются во время разработки для перехвата программных ошибок, например недопустимых дескрипторов и синтаксических ошибок в жестко запрограммированных инструкциях SQL. Она также используется во время выполнения для захвата ошибок и предупреждений времени выполнения, например усечения данных, нарушения правил и синтаксических ошибок в инструкциях SQL, введенных пользователем. Программная логика обычно основана на кодах возврата.  
  
 Например, после того, приложение вызывает **SQLFetch** для получения строк в результирующем наборе, код возврата указывает, был ли достигнут конец результирующего набора (SQL_NO_DATA), если информационные сообщения были возвращены (SQL_SUCCESS_ WITH_INFO), или если возникает ошибка (SQL_ERROR).  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента возвращает отличное от SQL_SUCCESS, приложение может вызвать **SQLGetDiagRec** для получения сведений или сообщений об ошибках. Используйте **SQLGetDiagRec** для прокрутки вверх и вниз, сообщение, если имеется более одного сообщения.  
  
 Код возврата SQL_INVALID_HANDLE всегда указывает на программную ошибку, поэтому не должен встречаться во время выполнения. Все другие коды возврата предоставляют сведения времени выполнения, хотя SQL_ERROR может означать программную ошибку.  
  
 Исходный [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного API DB-Library для C, позволяет приложению устанавливать обработку ошибок обратного вызова и функции обработки сообщений, возвращающие ошибки или сообщения. Некоторые инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], например PRINT, RAISERROR, DBCC и SET, возвращают свои результаты функции обработки сообщений DB-Library, а не результирующему набору. Однако API-интерфейс ODBC не имеет такой возможности обратного вызова. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента обнаруживает сообщения, приходящие обратно из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], он присваивает коду возврата значение SQL_SUCCESS_WITH_INFO или SQL_ERROR и возвращает сообщение в виде одной или нескольких диагностических записей. Таким образом, приложение ODBC должно внимательно проверять так, наличие этих кодов возврата и вызов **SQLGetDiagRec** для получения данных сообщения.  
  
 Сведения об ошибках трассировки см. в разделе [трассировка доступа к данным](http://go.microsoft.com/fwlink/?LinkId=125805). Сведения об улучшениях для отслеживания ошибок, появившихся в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], см. в разделе [доступ к диагностическим сведениям в журнале расширенных событий](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Обработка инструкций, выдающих сообщения](processing-statements-that-generate-messages.md)  
  
-   [Диагностические записи и поля](diagnostic-records-and-fields.md)  
  
-   [Собственные номера ошибок](native-error-numbers.md)  
  
-   [SQLSTATE &#40;коды ошибок ODBC&#41;](sqlstate-odbc-error-codes.md)  
  
-   [Сообщения об ошибках](error-messages.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (ODBC)](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
