---
title: "Интеграция со средой CLR и транзакции | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
caps.latest.revision: "19"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 91af8f269dce39e8e707c570aba606f743b1a7e6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="clr-integration-and-transactions"></a>Интеграция со средой CLR и транзакции
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]**System.Transactions** пространство имен предоставляет новую платформу транзакций, полностью интегрированную с ADO.NET и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интеграция CLR среды выполнения (CLR). **System.Transactions** и ADO.NET работают вместе, чтобы расширить и упростить использование локальных и распределенных транзакций в управляемых приложениях.  
  
> [!NOTE]  
>  Определяемая пользователем процедура (UDP) среды CLR не может устанавливать соединение с тем же сервером, на котором она запускается (соединение, замкнутое на себя), и выполнить прикрепление в той же транзакции. Если предпринимается такая попытка, то попытка соединения будет заблокирована, а управление не будет передано обратно определяемой пользователем процедуре. Это приведет к ошибке времени ожидания (сообщение 1206) в определяемой пользователем процедуре.  
  
 Дополнительные сведения о транзакциях и платформе .NET Framework см. в разделах «Выполнение транзакций» и «Использование транзакций» пакета SDK для платформы .NET Framework.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Повышение транзакции](../../relational-databases/clr-integration-data-access-transactions/transaction-promotion.md)  
 Содержит описание возможности повысить уровень транзакции и использования этой функции.  
  
 [Доступ к текущей транзакции](../../relational-databases/clr-integration-data-access-transactions/accessing-the-current-transaction.md)  
 Содержит описание получения доступа к транзакции, которая выполняется в данный момент внутрипроцессно на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Использование System.Transactions](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md)  
 Описывает использование **System.Transactions** интерфейс программирования (API) в управляемом приложении.  
  
 [Время существования транзакций](../../relational-databases/clr-integration-data-access-transactions/transaction-lifetimes.md)  
 Содержит описание различий во времени существования между транзакциями, запущенными в хранимых процедурах [!INCLUDE[tsql](../../includes/tsql-md.md)], и транзакциями, запущенными в приложениях CLR.  
  
## <a name="see-also"></a>См. также:  
 [Доступ к данным из объектов среды CLR для работы с базами данных](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  