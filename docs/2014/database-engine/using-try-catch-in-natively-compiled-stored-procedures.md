---
title: Использование конструкции Try... Catch в хранимых процедурах, скомпилированных в собственном | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f730e70c-4f92-411d-9984-289e241e43ee
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ea88c4e37cb7c062beec1db9b05549446585cc33
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395380"
---
# <a name="using-trycatch-in-natively-compiled-stored-procedures"></a>Использование блоков try..catch в хранимых процедурах, скомпилированных в собственном коде
  Внутри скомпилированной хранимой процедуры можно использовать блоки try..catch. Поддерживаются приведенные ниже конструкции.  
  
-   ERROR_LINE  
  
-   ERROR_MESSAGE  
  
-   ERROR_NUMBER  
  
-   ERROR_PROCEDURE  
  
-   ERROR_SEVERITY  
  
-   ERROR_STATE  
  
```tsql  
CREATE PROCEDURE test_try_catch  
with native_compilation, schemabinding, execute as owner   
as  
begin atomic with (transaction isolation level = snapshot, language = N'us_english')  
  
  BEGIN TRY  
    -- generate error  
    declare @i int = 1,  
    @j int = 0  
    select @i/@j  
  END TRY  
  BEGIN CATCH  
    -- Execute error retrieval routine.  
    SELECT  
    ERROR_SEVERITY() AS ErrorSeverity  
    ,ERROR_STATE() AS ErrorState  
    ,ERROR_PROCEDURE() AS ErrorProcedure  
    ,ERROR_LINE() AS ErrorLine  
    ,ERROR_MESSAGE() AS ErrorMessage  
  END CATCH  
end  
go  
  
exec test_try_catch  
go  
```  
  
## <a name="see-also"></a>См. также  
 [Скомпилированные в собственном коде хранимые процедуры](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
