---
title: Тип буфера данных | Документы Microsoft
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
- data types [ODBC], buffers
- data buffers [ODBC], types
- buffers [ODBC], data
- C data types [ODBC], buffers
ms.assetid: 58bea3e9-d552-447f-b3ad-ce1dab213b72
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d270c7e2bdd525a585c31a5c29c6b784fa8d1105
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910481"
---
# <a name="data-buffer-type"></a>Тип данных буфера
Тип данных C буфера указывается приложением. С одной переменной это происходит, когда приложение выделяет переменную. С помощью универсального памяти — то есть памяти ссылается указатель типа void — это происходит, когда приложение приводит памяти для определенного типа. Драйвер обнаруживает этот тип одним из двух способов:  
  
-   **Аргумент типа буфера данных.** Буферы, используемые для передачи значений параметров и результирующий набор данных, такие как буфер связаны со *TargetValuePtr* в **SQLBindCol**, обычно имеется связанный тип аргумента, например  *TargetType* аргумент в **SQLBindCol**. В этом аргументе приложение передает идентификатор типа C, который соответствует типу буфера. Например, в вызове **SQLBindCol**, значение SQL_C_TYPE_DATE сообщает драйверу, что *даты* буфер является SQL_DATE_STRUCT:  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     Дополнительные сведения об идентификаторах типа см. в разделе [типы данных ODBC в](../../../odbc/reference/develop-app/data-types-in-odbc.md) подраздел, далее в этом разделе.  
  
-   **Предопределенный тип.** Буферов, используемых для отправки и получения параметров или атрибуты, такие как буфер, на который указывает *InfoValuePtr* аргумент в **SQLGetInfo**, имеют фиксированный тип, который зависит от указанного параметра. Драйвер предполагается, что буфер данных этого типа; приложение несет выделить буфер этого типа. Например, в вызове **SQLGetInfo**, драйвер предполагает буфер является 32-разрядное целое число, так как это параметр SQL_STRING_FUNCTIONS требует:  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 Драйвер использует тип данных C для интерпретации данных в буфере.
