---
title: 'SQL, чтобы дата C: | Документы Microsoft'
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
- converting data from SQL to C types [ODBC], date
- date data type [ODBC]
- data conversions from SQL to C types [ODBC], date
ms.assetid: 703c7960-9cf4-4d7a-9920-53b29c184f97
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d99ebd45ffa463ccfd66bd751dd7415b35a8f5d1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908869"
---
# <a name="sql-to-c-date"></a>SQL, чтобы дата C:
Идентификатор для типа данных ODBC SQL дата является:  
  
 SQL_TYPE_DATE  
  
 Следующая таблица показывает ODBC C типы данных, к которым может быть преобразован даты данных SQL. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > байт символов<br /><br /> 11 < = *BufferLength* < = байт символов<br /><br /> *BufferLength* < 11|Данные <br /><br /> Усеченные данные<br /><br /> Не определено.|10<br /><br /> Длина данных в байтах<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Длина символьной<br /><br /> 11 < = *BufferLength* < = Длина символьной строки<br /><br /> *BufferLength* < 11|Данные <br /><br /> Усеченные данные<br /><br /> Не определено.|10<br /><br /> Длина данных в символах<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Байтовая длина данных > *BufferLength*|Данные <br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|н/д<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Нет []|Данные |6 [c]|н/д|  
|SQL_C_TYPE_TIMESTAMP|Нет []|Данные [b]|16 [c]|н/д|  
  
 [] значение *BufferLength* учитывается для этого преобразования. Драйвер предполагает, что размер **TargetValuePtr* — это размер типа данных C.  
  
 [b] поля времени структура отметки времени принимают нулевое значение.  
  
 [c] это размер соответствующие типы данных C.  
  
 При преобразовании в символьный C Дата данных SQL результирующая строка находится в «*гггг*-*мм*-*дд*» формата. Этот формат не влияют настройки Windows® страны.
