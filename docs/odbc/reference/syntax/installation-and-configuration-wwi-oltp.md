---
title: Функция SQLSetDriverConnectInfo | Документы Microsoft
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
- SQLSetDriverConnectInfo function [ODBC]
ms.assetid: bfd4dfc2-fbca-4ef3-81e5-2706f2389256
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63dee07cc01051f42fa6552a38d99dd7678f7ab8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916741"
---
# <a name="sqlsetdriverconnectinfo-function"></a>Функция SQLSetDriverConnectInfo
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 3,81 ODBC: ODBC  
  
 **Сводка**  
 **SQLSetDriverConnectInfo** используется для настройки строки подключения в info маркер подключения для приложения **SQLDriverConnect** вызова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SQLRETURN SQLSetDriverConnectInfo(  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              InConnectionString,  
                SQLSMALLINT          StringLength1 );  
```  
  
## <a name="arguments"></a>Аргументы  
 *TokenHandle*  
 [Вход] Дескриптор токена.  
  
 *InConnectionString*  
 [Вход] Требуется полная строка подключения (в разделе синтаксиса в «Комментарии» в [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)), частичную строку соединения, или пустая строка.  
  
 *StringLength1*  
 [Вход] Длина **InConnectionString*, в символах, если строка Юникода или байтов, если строка ANSI или DBCS.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 То же, что [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) связанные с любой ошибки проверки входных данных, за исключением того, что будет использоваться диспетчер драйверов **HandleType** из SQL_HANDLE_DBC_INFO_TOKEN и **обработки** из *hDbcInfoToken*.  
  
## <a name="remarks"></a>Замечания  
 Всякий раз, когда драйвер возвращает значение SQL_ERROR или SQL_INVALID_HANDLE, диспетчер драйверов возвращает приложению ошибку (в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Каждый раз, когда драйвер возвращает SQL_SUCCESS_WITH_INFO, диспетчер драйверов будет получать диагностические данные из *hDbcInfoToken*и возвращают значение SQL_SUCCESS_WITH_INFO к приложению в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Приложения не должны напрямую вызывать эту функцию. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
