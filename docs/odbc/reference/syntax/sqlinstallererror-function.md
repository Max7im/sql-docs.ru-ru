---
title: Функция SQLInstallerError | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallerError
helpviewer_keywords:
- SQLInstallerError [ODBC]
ms.assetid: e6474b79-4d55-458f-81ce-abfafe357f83
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c76d89a69ade4aca9c915db8d960cc749f8ca2a7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32918031"
---
# <a name="sqlinstallererror-function"></a>Функция SQLInstallerError
**Соответствия**  
 Появился в версии: ODBC 3.0  
  
 **Сводка**  
 **SQLInstallerError** возвращает сведениями о состоянии и ошибки для установщика функций ODBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE SQLInstallerError(  
     WORD      iError,  
     DWORD *   pfErrorCode,  
     LPSTR     lpszErrorMsg,  
     WORD      cbErrorMsgMax,  
     WORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Аргументы  
 *iError*  
 [Вход] Номер ошибки записи. Допустимые номера: от 1 до 8.  
  
 *pfErrorCode*  
 [Выход] Код ошибки установщика. (Дополнительные сведения см. в разделе «Комментарии».)  
  
 *lpszErrorMsg*  
 [Выход] Указатель хранилища для текста сообщения об ошибке.  
  
 *cbErrorMsgMax*  
 [Вход] Максимальная длина *szErrorMsg* буфера. Это должно быть меньше или равно SQL_MAX_MESSAGE_LENGTH конечное значение null знак «минус».  
  
 *cbErrorMsgMax*  
 [Вход] Максимальная длина *szErrorMsg* буфера. Это должно быть меньше или равно SQL_MAX_MESSAGE_LENGTH конечное значение null знак «минус».  
  
 *pcbErrorMsg*  
 [Выход] Указатель на общее количество байтов (за исключением знака завершения null) для возврата в *lpszErrorMsg*. Если количество байтов, доступных для возврата больше или равно *cbErrorMsgMax*, текст сообщения об ошибке в *lpszErrorMsg* усекается до *cbErrorMsgMax* минус байтов символов конечное значение NULL. *PcbErrorMsg* аргумент может быть пустой указатель.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **SQLInstallerError** не публикует значения погрешности для себя. **SQLInstallerError** вернет значение SQL_NO_DATA, если это не удается получить информацию об ошибках (в этом случае *pfErrorCode* не определено). Если **SQLInstallerError** не может получить доступ к значения ошибок по любой причине, который возвращает значение SQL_ERROR, **SQLInstallerError** возвращает значение SQL_ERROR, но не публикует все значения ошибки. Если вы не знаете длина строки предупреждение (*lpszErrorMsg*), можно задать *lpszErrorMsg* значение NULL, вызов **SQLInstallerError**. **SQLInstallerError** будет возвращается длина строки предупреждение в *cbErrorMsgMax*. Если буфер сообщения об ошибке слишком короткий **SQLInstallerError** возвращает SQL_SUCCESS_WITH_INFO, а правильный *pfErrorCode* значение для **SQLInstallerError**.  
  
 Чтобы определить, произошла ли усечения в сообщении об ошибке, приложение можно сравнить значение в *cbErrorMsgMax* аргумент фактическую длину текста сообщения записываются *pcbErrorMsg* аргумент. Если усечение происходит, длина правильно буфера должно быть выделено под *lpszErrorMsg* и **SQLInstallerError** должен вызываться с соответствующим свойством *iError*запись.  
  
## <a name="comments"></a>Комментарии  
 Приложение вызывает **SQLInstallerError** при предыдущим вызовом функции установщика ODBC возвращает значение FALSE. Функции установки установщика и драйвера или транслятор ODBC блога ноль или более ошибок только в том случае, если функция завершается с ошибкой (возвращает значение FALSE); Таким образом, приложение вызывает **SQLInstallerError** только после сбоя установки ODBC-функции.  
  
 Ошибка очереди установщика ODBC сбрасывается каждый раз, когда вызывается функция новый установщика. Таким образом приложение не может ожидать получения ошибок для функций, отличных от из последнего вызова функции установщика.  
  
 Чтобы получить несколько ошибок для вызова функции, приложение вызывает **SQLInstallerError** несколько раз.  
  
 Если нет дополнительных сведений, **SQLInstallerError** вернет значение SQL_NO_DATA, *pfErrorCode* аргумент не определен, *pcbErrorMsg* аргумент равен 0, и *lpszErrorMsg* аргумент содержит один символ завершения null (если не *cbErrorMsgMax* аргумент равен 0).
