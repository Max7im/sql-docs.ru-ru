---
title: 'SQL, чтобы время C: | Документы Microsoft'
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
- converting data from SQL to C types [ODBC], time
- time data type [ODBC]
- data conversions from SQL to C types [ODBC], time
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b66aeca41cd705a21e7d6aa6d306a9032e86bba9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908599"
---
# <a name="sql-to-c-time"></a>SQL, чтобы время C:
Идентификатор для времени, которое имеет тип данных ODBC SQL:  
  
 SQL_TYPE_TIME  
  
 Следующая таблица показывает ODBC C типы данных, к которым может быть преобразован SQL данных времени. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > байт символов<br /><br /> *9* <= *BufferLength* < = байт символов<br /><br /> *BufferLength* < 9|Данные <br /><br /> Усеченные данные в []<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Длина символьной<br /><br /> *9* <= *BufferLength* < = Длина символьной строки<br /><br /> *BufferLength* < 9|Данные <br /><br /> Усеченные данные в []<br /><br /> Не определено.|Длина данных в символах<br /><br /> Длина данных в символах<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Байтовая длина данных > *BufferLength*|Данные <br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|н/д<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Нет [b]|Данные |6 [d]|н/д|  
|SQL_C_TYPE_TIMESTAMP|Нет [b]|Данные [c]|16 [d]|н/д|  
  
 [] времени доли секунды усекаются.  
  
 [b] значение *BufferLength* учитывается для этого преобразования. Драйвер предполагает, что размер **TargetValuePtr* — это размер типа данных C.  
  
 [c] полей дат структура отметки времени устанавливаются в текущую дату, а поле долей секунды структура отметки времени присваивается нулевое значение.  
  
 [d] это размер соответствующие типы данных C.  
  
 При преобразовании данных SQL времени в символьный C результирующая строка находится в «*hh*:*мм*:*ss*» формата. Этот формат не влияют настройки Windows® страны.
