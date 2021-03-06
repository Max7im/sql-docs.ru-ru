---
title: Основной интерфейс соответствия | Документы Microsoft
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
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- core-level interface conformance levels [ODBC]
ms.assetid: aaaa864a-6477-45ff-a50a-96d8db66a252
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c45fdfe2b01ddfd34e7db391b799b95ce696da8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913989"
---
# <a name="core-interface-conformance"></a>Основной интерфейс соответствия
Все драйверы ODBC должна обладать по крайней мере основной уровень соответствия интерфейса. Так как функции в базовом уровне требованиям большая часть универсальных взаимодействующие приложения, драйвер может работать с таких приложений. Функции в базовом уровне также соответствуют для функции, определенные в спецификации ISO CLI и необходимые компоненты, определенные в спецификации Open CLI группы. Драйвер ODBC уровня ядра интерфейс совместимую позволяет приложению выполнять любые из следующих:  
  
-   Выделить и освободить все типы дескрипторов, путем вызова метода **SQLAllocHandle** и **SQLFreeHandle**.  
  
-   Использовать все формы **SQLFreeStmt** функции.  
  
-   Привязать столбцы результирующего набора путем вызова **SQLBindCol**.  
  
-   Обработки динамических параметров, включая массивы параметров ввода только в направлении, путем вызова **SQLBindParameter** и **SQLNumParams**. (Параметры в направлении выходные данные являются компонентов 203 в [согласованности интерфейс на уровне 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Укажите смещение привязки.  
  
-   Используйте диалоговое окно данных времени выполнения, включающие вызовы **SQLParamData** и **SQLPutData**.  
  
-   Управление курсоры и курсоры, путем вызова **SQLCloseCursor**, **SQLGetCursorName**, и **SQLSetCursorName**.  
  
-   Получить доступ к описанию (метаданные) результирующих наборов, вызвав **SQLColAttribute**, **SQLDescribeCol**, **SQLNumResultCols**, и **SQLRowCount** . (Использование этих функций для столбца с номером 0 для получения метаданных закладки компонент 204 в [согласованности интерфейс на уровне 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Запрос словаря данных путем вызова функции каталога **SQLColumns**, **SQLGetTypeInfo**, **SQLStatistics**, и **SQLTables**.  
  
     Драйвер не требуется для поддержки многокомпонентных именах таблиц базы данных и представлений. (Дополнительные сведения см. в разделе компонент 101 [согласованности интерфейс на уровне 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md) и 201 в [согласованности интерфейс на уровне 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).) Тем не менее некоторые возможности из спецификации SQL-92, например квалификации столбца или имен индексов, синтаксически сравнимы многокомпонентных имен. Отсутствует список функций ODBC не предназначен для введения новых параметров в эти аспекты SQL-92.  
  
-   Управление источниками данных и подключений, путем вызова **SQLConnect**, **SQLDataSources**, **SQLDisconnect**, и **SQLDriverConnect**. Получение сведений о драйверах, независимо от того, какие ODBC уровня они поддерживают, путем вызова **SQLDrivers**.  
  
-   Подготовка и выполнение инструкции SQL, путем вызова **SQLExecDirect**, **SQLExecute**, и **SQLPrepare**.  
  
-   Выберите одну строку результирующего набора или несколько строк в прямом направлении только путем вызова метода **SQLFetch** или вызвав **SQLFetchScroll** с *FetchOrientation* аргумент значение SQL_FETCH_NEXT.  
  
-   Получить, вызвав несвязанного столбца в части, **SQLGetData**.  
  
-   Получить текущие значения всех атрибутов, вызвав **SQLGetConnectAttr**, **SQLGetEnvAttr**, и **SQLGetStmtAttr**и задать значения по умолчанию все атрибуты и установить некоторые атрибуты в нестандартные значения путем вызова **SQLSetConnectAttr**, **SQLSetEnvAttr**, и **SQLSetStmtAttr**.  
  
-   Управлять некоторые поля дескрипторов, путем вызова **SQLCopyDesc**, **SQLGetDescField**, **SQLGetDescRec**, **SQLSetDescField**, и **SQLSetDescRec**.  
  
-   Получить диагностические сведения, вызвав **SQLGetDiagField** и **SQLGetDiagRec**.  
  
-   Обнаружение возможности драйверов путем вызова **SQLGetFunctions** и **SQLGetInfo**. Кроме того, определить результат все замененные фрагменты текста, внесенные в инструкцию SQL перед их отправкой к источнику данных, вызвав **SQLNativeSql**.  
  
-   Используйте синтаксис **SQLEndTran** Фиксация транзакции. Драйвер уровня ядра не обязательно должна поддерживать значение true, транзакции. Таким образом для атрибута соединения SQL_ATTR_AUTOCOMMIT приложения нельзя указать SQL_ROLLBACK ни SQL_AUTOCOMMIT_OFF. (Дополнительные сведения см. в разделе компонент 109 [согласованности интерфейс на уровне 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
-   Вызовите **SQLCancel** для отмены диалогового окна данных во время выполнения и в многопоточной среде, для отмены выполнения функции ODBC в другом потоке. Интерфейс уровня ядра соответствия не предусматривает поддержку для асинхронного выполнения функций, а также использование **SQLCancel** для отмены асинхронного выполнения функции ODBC. Не платформы, и драйвер ODBC не обязательно должен быть несколько потоков для драйвера для проведения независимых действий, в то же время. Тем не менее в многопоточной среде, драйвер ODBC должен быть поточно ориентированного. Сериализация запросов из приложения — совместимые способ реализации этой спецификации, несмотря на то, что он может создать значительное снижение производительности.  
  
-   Получить SQL_BEST_ROWID столбец идентификации строк таблиц, путем вызова **SQLSpecialColumns**. (Поддержка SQL_ROWVER компонент 208 в [согласованности интерфейс на уровне 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)  
  
    > [!IMPORTANT]  
    >  Драйверы ODBC необходимо реализовать функции уровень соответствия основной интерфейс.
