---
title: Файл трассировки | Документы Microsoft
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
- trace files [ODBC]
- tracing options [ODBC], trace files
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb9089ed49e623247384557e8650731f6abc9816
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915270"
---
# <a name="trace-file"></a>Файл трассировки
Приложение указывает файл трассировки, задав **TraceFile** ключевое слово в записи реестра Odbc.ini или вызвав **SQLSetConnectAttr** с атрибутом SQL_ATTR_TRACEFILE соединения. Если файл не существует, если трассировка включена, диспетчер драйверов будет создан файл. Каждое приложение должно иметь свой собственный файл трассировки выделенный во избежание конфликтов. Приложение может использовать более одного файла трассировки; Программа установки может предоставить пользователю возможность выбора файлов трассировки. Если трассировка включена динамически, приложения можно также отобразить результаты трассировки, а не ведения журнала в файл трассировки.  
  
 Файл трассировки содержит журнал каждого вызова функции ODBC, с типами данных и значения всех аргументов. Он регистрирует все входные функции и заносит в журнал все возвращенные функции с коды возврата и состояния ошибки.  
  
 В ODBC 3 *.x*, параметры для функции соединения не предоставлены Библиотека трассировки.
