---
title: Тип данных C закладки | Документы Microsoft
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
- C data types [ODBC], bookmark C data type
- pseudo-type identifiers [ODBC], bookmark C data type
- data types [ODBC], pseudo-type identifiers
- bookmarks [ODBC]
- bookmark C data type [ODBC]
ms.assetid: add88e48-ada3-4c0c-a5ac-e78903d3ff41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f4566f0851b67e239ec11acff9883940caae69d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905539"
---
# <a name="bookmark-c-data-type"></a>Тип данных C закладки
Тип данных C закладки позволяет приложению получить закладки. Закладка C типы используются только для извлечения значения закладки, которые могут быть переменную длину; они не должны преобразоваться в другие типы данных. Приложение извлекает закладки, либо из 0 столбец результирующего набора с **SQLBulkOperations** (с помощью операции SQL_ADD), **SQLFetch**, **SQLFetchScroll**, или **SQLGetData**. Дополнительные сведения см. в разделе [закладки](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 В следующей таблице перечислены значения *CType* тип данных C закладку, введите тип данных ODBC C, реализующий тип данных C закладки и определение этих данных из SQL. З.  
  
> [!NOTE]  
>  Тип данных SQL_C_BOOKMARK является устаревшим. ODBC 3 *.x* приложения не должны использовать SQL_C_BOOKMARK. ODBC 3 *.x* драйверы должны поддерживать SQL_C_BOOKMARK только в том случае, если для работы с ODBC 2. *x* приложений, которые его используют. Диспетчер драйверов сопоставляет SQL_C_VARBOOKMARK SQL_C_BOOKMARK, когда приложение работает с ODBC 2. *x* драйвера.  
  
|Идентификатор типа C|Определение типа ODBC C|Тип C|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(Устаревшее)|ЗАКЛАДКА|unsigned long int|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|
