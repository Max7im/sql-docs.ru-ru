---
title: "NEWSEQUENTIALID (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/08/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NEWSEQUENTIALID
- NEWSEQUENTIALID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- NEWSEQUENTIALID function
- GUIDs [SQL Server]
ms.assetid: e06d2cab-f1ff-42f1-8550-6aaec57be36f
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2a453b99d7ab0512e57275b5ad1805f5a66522ba
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="newsequentialid-transact-sql"></a>NEWSEQUENTIALID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает идентификатор GUID, имеющий значение, большее любого идентификатора GUID, который был прежде создан на указанном компьютере при помощи этой функции с момента запуска Windows. После перезагрузки Windows идентификатор GUID может вновь начинаться с более низкого диапазона, однако останется глобально уникальным. Если столбец GUID используется в качестве идентификатора строки, использование NEWSEQUENTIALID может ускорить работу по сравнению с использованием функции NEWID, поскольку функция NEWID вызывает непредсказуемый уровень нагрузки и использует меньшее число кэшированных страниц данных. Использование NEWSEQUENTIALID также помогает полностью заполнять страницы данных и страницы индекса.  
  
> [!IMPORTANT]  
>  Если важна конфиденциальность, то не следует применять эту функцию. Значение следующего формируемого идентификатора GUID можно предугадать и, следовательно, получить доступ к данным, связанным с этим идентификатором GUID.  
  
 NEWSEQUENTIALID является оболочкой для Windows [UuidCreateSequential](http://go.microsoft.com/fwlink/?LinkId=164027) функции.  
  
> [!WARNING]  
>  Функция UuidCreateSequential имеет зависимости оборудования. На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно разработать кластеры последовательные значения, при перемещении баз данных (например, автономные базы данных) на другие компьютеры. При использовании Always On и на [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)], может образоваться кластеры последовательные значения, если база данных переходит на другой компьютер.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NEWSEQUENTIALID ( )  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Замечания  
 Функцию NEWSEQUENTIALID() можно использовать только с ограничениями по умолчанию для столбцов таблицы типа **uniqueidentifier**. Например:  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT NEWSEQUENTIALID());   
```  
  
 Когда функция NEWSEQUENTIALID() используется в выражениях DEFAULT, она не может быть объединена с другими скалярными операторами. Например, нельзя выполнить следующее:  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT dbo.myfunction(NEWSEQUENTIALID()));  
```  
  
 В предыдущем примере `myfunction()` является пользовательской скалярной функцией, которая принимает и возвращает значение `uniqueidentifier`.  
  
 На функцию NEWSEQUENTIALID нельзя ссылаться в запросах.  
  
 Функцию NEWSEQUENTIALID можно использовать для формирования идентификаторов GUID, чтобы уменьшить число разбиений страниц и произвольных операций ввода-вывода на конечном уровне индексов.  
  
 Каждый идентификатор GUID, сформированный с помощью функции NEWSEQUENTIALID, является уникальным на данном компьютере. Идентификаторы GUID, сформированные с помощью функции NEWSEQUENTIALID, становятся уникальными для нескольких компьютеров, только если в компьютере-источнике имеется сетевая плата.  
  
## <a name="see-also"></a>См. также:  
 [NEWID &#40; Transact-SQL &#41;](../../t-sql/functions/newid-transact-sql.md)   
 [Операторы сравнения &#40; Transact-SQL &#41;](../../t-sql/language-elements/comparison-operators-transact-sql.md)  
  
  
