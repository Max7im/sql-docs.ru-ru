---
title: "MSSQLSERVER_10520 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 57ba200cf6381ddc6d100d516bcf5f0168bb7262
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver10520"></a>MSSQLSERVER_10520
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10520|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_PARAM_NOT_ALLOWED|  
|Текст сообщения|Не удается создать структуру плана '%.*ls', поскольку для параметра @type указано значение '%!s', а для параметра '%!s' указано значение, отличное от NULL. Для заданного типа этот параметр должен иметь значение NULL. Укажите для этого параметра значение NULL либо измените его тип таким образом, чтобы он допускал значение, отличное от NULL.|  
  
## <a name="explanation"></a>Объяснение  
Для типа, указанного в @type, требуется значение NULL, но предоставлено значение, отличное от NULL.  
  
## <a name="user-action"></a>Действие пользователя  
Укажите для этого параметра значение NULL либо измените его тип таким образом, чтобы он допускал значение, отличное от NULL.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Структуры плана](~/relational-databases/performance/plan-guides.md)  
  
