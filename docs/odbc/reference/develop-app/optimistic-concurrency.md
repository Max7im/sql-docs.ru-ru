---
title: Оптимистический параллелизм | Документы Microsoft
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
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- optimistic concurrency [ODBC]
ms.assetid: 9d71e09e-bc68-4c1f-9229-ed2a7be7d324
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95593c35e55f899c3fb062adf4f5edde197f813c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914349"
---
# <a name="optimistic-concurrency"></a>Оптимистический параллелизм
*Оптимистический параллелизм* наследует его имя от оптимистичный допущения, редко возникает конфликтов между транзакциями; конфликта имен говорят, что когда другая транзакция обновляет или удаляет строку данных доступной для чтения в промежутке Текущая транзакция и время он обновляется или удаляется. Это противоположность *пессимистичный параллелизм* или блокировки, в котором разработчик приложения считается, что такие конфликты распространены.  
  
 При оптимистическом параллелизме остается строки разблокировать пока наступает время обновить или удалить их. В этот момент строка повторное считывание и проверки, если он был изменен после последнего прочтения. Если строка была изменена, то update или delete завершается ошибкой и будет предпринята снова.  
  
 Чтобы определить, были ли изменены строки, его новая версия проверяется кэшированная версия строки. Эту проверку могут быть основаны на версии строк, например столбец отметки времени в SQL Server или значения каждого столбца в строке. Версии строк не поддерживают многие СУБД.  
  
 Источник данных или приложением, можно реализовать оптимистичного параллелизма. В любом случае приложение должно использовать уровень изоляции низкий транзакции, такие как Read Committed; Применение более высокого уровня инвертирует повышения параллелизма, создаваемое за счет использования оптимистичного параллелизма.  
  
 Если источником данных реализована оптимистичного параллелизма, приложение задает атрибута инструкции SQL_ATTR_CONCURRENCY SQL_CONCUR_ROWVER или SQL_CONCUR_VALUES. Чтобы обновить или удалить строку, он выполняет позиционированного обновления или инструкции delete или вызовы **SQLSetPos** как если бы пессимистичный параллелизм; драйвер или источник данных возвращает SQLSTATE 01001 (конфликт операции с курсором), если Update или delete происходит сбой из-за конфликта имен.  
  
 Если само приложение реализует оптимистичного параллелизма, атрибута инструкции SQL_ATTR_CONCURRENCY устанавливает SQL_CONCUR_READ_ONLY для чтения строки. Если он будет сравнить версии строк и неизвестно, в столбец версий строк, он вызывает метод **SQLSpecialColumns** с параметром SQL_ROWVER, чтобы определить имя этого столбца.  
  
 Приложение обновляет или удаляет строку путем увеличения параллелизма для SQL_CONCUR_LOCK (Чтобы получить доступ на запись к строке) и выполнения **обновление** или **удаление** инструкции с **ГДЕ**  была предложение, которое указывает версию или значений в строке, когда приложение его чтение. Если строка была изменена после этого, инструкция завершится ошибкой. Если **ГДЕ** предложение для уникальной идентификации строки, инструкция также может обновить или удалить другие строки; версии строк всегда уникальной идентификации строк, но значения строк уникальной идентификации строк только в том случае, если они содержат первичный ключ.
