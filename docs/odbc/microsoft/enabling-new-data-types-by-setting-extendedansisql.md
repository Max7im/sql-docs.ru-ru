---
title: Включение новых типов данных, задав ExtendedAnsiSQL | Документы Microsoft
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
- extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c9f7c4c66bebb2404ef8477ed85e0f36edc1407
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32902499"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Включение новых типов данных, задав ExtendedAnsiSQL
Два новых типа данных доступны в базы данных Jet 4.0, если установлен флаг ExtendedAnsiSQL: SQL_DECIMAL и SQL_NUMERIC. По умолчанию точность и масштаб, 18 и 0 соответственно. Доступ к ней через ODBC, который типизируется как SQL_DECIMAL или SQL_NUMERIC данных будет сопоставлен Microsoft Jet десятичное вместо валюты.  
  
 При отключении флаг ExtendedAnsiSQL нельзя создавать таблицы с десятичным или числовым типам, и эти типы не будут отображаться в SQLGetTypeInfo(). Тем не менее если таблица содержит новые типы данных, их можно использовать с типами данных.
