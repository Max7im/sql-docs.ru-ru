---
title: Обновление данных | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ed34a235a489feb13d31ef38e84e821cce961dc
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273133"
---
# <a name="updating-data"></a>Обновление данных
Обновление поведения и функциональных возможностей во многом зависит от обновления режима (тип блокировки), тип курсора и положения курсора.  
  
 Используйте **обновление** метод, чтобы сохранить любые изменения, внесенные в текущую запись **набора записей** объект с момента вызова **AddNew** метода или с момента изменять любые значения полей в существующей записи. **Записей** объект должен поддерживать обновлений.  
  
 Если **записей** объект поддерживает обновление пакета, можно кэшировать внесение нескольких изменений в одну или несколько записей локально до вызова **UpdateBatch** метод. При изменении текущей записи или добавления новой записи, при вызове **UpdateBatch** метода ADO будет автоматически вызывать **обновление** метод, чтобы сохранить все ожидающие изменения для текущей записи, прежде чем передает пакет изменений к поставщику.  
  
 Текущая запись остаются актуальными, после вызова метода **обновление** или **UpdateBatch** методы.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Режим интерпретации](../../../ado/guide/data/immediate-mode.md)  
  
-   [Пакетный режим](../../../ado/guide/data/batch-mode.md)  
  
-   [Обработка транзакций](../../../ado/guide/data/transaction-processing.md)
