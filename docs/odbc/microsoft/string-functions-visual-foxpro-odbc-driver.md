---
title: Строковые функции (драйвер ODBC для Visual FoxPro) | Документы Microsoft
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
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1f89dabb9d46b29a4ec362cd012ff96de60c10e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904959"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Строковые функции (Visual FoxPro драйвер ODBC)
В следующей таблице перечислены функции обработки строк ODBC, поддерживаемые Visual FoxPro драйвера ODBC. Если Visual FoxPro грамматики для той же функции отличается от синтаксиса ODBC, отображается Visual FoxPro эквивалент.  
  
|Грамматика ODBC|Грамматика Visual FoxPro|  
|------------------|---------------------------|  
|ASCII *(строковое_выражение)*|ASC *(строковое_выражение)*|  
|CHAR- *(код)*|CHR *(строковое_выражение)*|  
|CONCAT *(строковое_выражение1, строковое_выражение2)*|*строковое_выражение1 + строковое_выражение2*|  
|РАЗНИЦА *(строковое_выражение1, строковое_выражение2)*||  
|Вставить *(строковое_выражение1, начало, длина, строковое_выражение2)*|STUFF *(строковое_выражение1, начало, длина, строковое_выражение2)*|  
|LCASE *(строковое_выражение)*|НИЖЕ *(строковое_выражение)*|  
|СЛЕВА *(строковое_выражение число)*||  
|Длина *(строковое_выражение)*|Функция LEN *(строковое_выражение)*|  
|Функция LTRIM *(строковое_выражение)*||  
|ПОВТОРИТЕ *(строковое_выражение число)*|РЕПЛИЦИРОВАТЬ *(строковое_выражение число)*|  
|ЗАМЕНИТЕ *(строковое_выражение1, строковое_выражение2, string_exp3)*|STRTRAN *(строковое_выражение1, строковое_выражение2, string_exp3)*|  
|ПРАВО *(строковое_выражение число)*||  
|RTRIM *(строковое_выражение)*||  
|Функция SOUNDEX *(строковое_выражение)*||  
|МЕСТО *(число)*||  
|Подстрока *(строковое_выражение, начало, длина)*|SUBSTR *(строковое_выражение, начало, длина)*|  
|UCASE *(строковое_выражение)*|ВЕРХНЯЯ *(строковое_выражение)*|
