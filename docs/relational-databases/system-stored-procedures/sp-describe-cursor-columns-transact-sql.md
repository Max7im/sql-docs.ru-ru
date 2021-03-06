---
title: процедура sp_describe_cursor_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_describe_cursor_columns
- sp_describe_cursor_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_cursor_columns
ms.assetid: 6eaa54af-7ba4-4fce-bf6c-6ac67cc1ac94
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a02701d091f2294af34450d3e370022a32cc143
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036237"
---
# <a name="spdescribecursorcolumns-transact-sql"></a>sp_describe_cursor_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выдает отчет об атрибутах столбцов результирующего набора серверного курсора.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_describe_cursor_columns   
   [ @cursor_return = ] output_cursor_variable OUTPUT   
    { [ , [ @cursor_source = ] N'local' ,   
          [ @cursor_identity = ] N'local_cursor_name' ]   
    | [ , [ @cursor_source = ] N'global' ,   
          [ @cursor_identity = ] N'global_cursor_name' ]   
    | [ , [ @cursor_source = ] N'variable' ,   
          [ @cursor_identity = ] N'input_cursor_variable' ]   
   }  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @cursor_return=] *output_cursor_variable* выходных данных  
 Имя объявленной переменной для получения выходных данных курсора. *output_cursor_variable* — **курсор**, не по умолчанию, и не может быть связан с какими-либо курсорами во время вызова sp_describe_cursor_columns. Возвращаемый курсор является прокручиваемым, динамическим и доступным только для чтения.  
  
 [ @cursor_source=] {N'local' | N'global' | N'variable'}  
 Указывает, задан ли возвращаемый курсор с помощью имени локального курсора, глобального курсора или курсорной переменной. Параметр — **nvarchar(30)**.  
  
 [ @cursor_identity=] N'*local_cursor_name*"  
 Имя курсора, созданного инструкцией DECLARE CURSOR с ключевым словом LOCAL или параметром LOCAL по умолчанию. *local_cursor_name* — **nvarchar(128)**.  
  
 [ @cursor_identity=] N'*global_cursor_name*"  
 Имя курсора, созданного инструкцией DECLARE CURSOR с ключевым словом GLOBAL или параметром GLOBAL по умолчанию. *global_cursor_name* — **nvarchar(128)**.  
  
 *global_cursor_name* также может быть именем серверного курсора API, открытого приложением ODBC и затем именованного вызовом SQLSetCursorName.  
  
 [ @cursor_identity=] N'*input_cursor_variable*"  
 Имя переменной курсора, связанной с открытым курсором. *input_cursor_variable* — **nvarchar(128)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="cursors-returned"></a>Возвращенные курсоры  
 процедура sp_describe_cursor_columns инкапсулирует отчет в виде [!INCLUDE[tsql](../../includes/tsql-md.md)] **курсор** выходного параметра. Это позволяет пакетам [!INCLUDE[tsql](../../includes/tsql-md.md)], хранимым процедурам и триггерам построчно обрабатывать выходные данные. Это также означает, что процедуру нельзя вызывать непосредственно из функций API баз данных. **Курсор** выходной параметр должен быть привязан к программной переменной, но API базы данных не поддерживают привязку **курсор** параметры или переменные.  
  
 В следующей таблице приводится описание курсора, возвращаемого с помощью процедуры sp_describe_cursor_columns.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|column_name|**sysname** (допускающие значение NULL)|Имя, назначенное столбцу результирующего набора. Столбец принимает значение NULL, если он был задан без сопутствующего предложения AS.|  
|ordinal_position|**int**|Позиция столбца относительно крайнего левого столбца в результирующем наборе. Первый столбец находится в позиции 0.|  
|column_characteristics_flags|**int**|Битовая маска параметров, хранящихся в переменной DBCOLUMNFLAGS OLE DB. Может представлять собой одно из следующих значений или их сочетание.<br /><br /> 1 = закладка<br /><br /> 2 = фиксируемая длина<br /><br /> 4 = допускающий значения NULL<br /><br /> 8 = управление версиями строк<br /><br /> 16 = обновляемый столбец (устанавливается для проецируемых столбцов курсора, не имеющего предложения FOR UPDATE. Если таковой столбец имеется, то аргумент может указываться только один раз для курсора).<br /><br /> При сочетании битовых значений применяются характеристики комбинируемых значений. Например, если битовое значение равно 6, столбец имеет фиксированную длину (2) и допускает значения NULL (4).|  
|column_size|**int**|Предельно допустимый размер значения данного столбца.|  
|data_type_sql|**smallint**|Число, определяющее тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данного столбца.|  
|column_precision|**tinyint**|Максимальная точность столбца согласно *bPrecision* значение в OLE DB.|  
|column_scale|**tinyint**|Количество цифр справа от десятичной запятой для **числовых** или **десятичное** типы данных согласно *bScale* значение в OLE DB.|  
|order_position|**int**|Если столбец участвует в сортировке результирующего набора, позиция столбца в ключе сортировки относительно крайнего левого столбца.|  
|order_direction|**varchar(1)**(допускающие значение NULL)|A — Столбец входит в ключ сортировки, которая производится по возрастанию.<br /><br /> D — Столбец входит в ключ сортировки, которая упорядочивается по убыванию.<br /><br /> NULL — Столбец не участвует в сортировке.|  
|hidden_column|**smallint**|0 = данный столбец отображается в списке выбора.<br /><br /> 1 = зарезервировано для использования в будущем.|  
|columnid|**int**|Идентификатор базового столбца. Если столбец результирующего набора строится из выражения, значение columnid равно -1.|  
|objectid|**int**|Идентификатор объекта или базовой таблицы, служащих источником столбца. Если столбец результирующего набора строится из выражения, значение objectid равно -1.|  
|dbid|**int**|Идентификатор базы данных, в которой находится таблица этого столбца. Если столбец результирующего набора строится из выражения, значение dbid равно -1.|  
|dbname|**sysname**<br /><br /> (допускает значение NULL)|Имя базы данных, содержащей базовую таблицу, служащую источником столбца. Если столбец результирующего набора строится из выражения, значение dbname равно NULL.|  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_describe_cursor_columns описывает атрибуты столбцов в результирующем наборе серверного курсора, такие как имя и тип данных, для каждого курсора. Процедура sp_describe_cursor используется для получения описания глобальных атрибутов серверного курсора. Процедура sp_describe_cursor_tables используется для получения отчета по базовым таблицам, на которые ссылается курсор. Чтобы получить отчет по серверным курсорам [!INCLUDE[tsql](../../includes/tsql-md.md)], видимым в соединении, используется процедура sp_cursor_list.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 В следующем примере открывается глобальный курсор и используется процедура `sp_describe_cursor_columns` для формирования отчета по столбцам этого курсора.  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a global cursor.  
DECLARE abc CURSOR KEYSET FOR  
SELECT LastName  
FROM Person.Person;  
GO  
OPEN abc;  
  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_describe_cursor_columns.  
DECLARE @Report CURSOR;  
  
-- Execute sp_describe_cursor_columns into the cursor variable.  
EXEC master.dbo.sp_describe_cursor_columns  
    @cursor_return = @Report OUTPUT  
    ,@cursor_source = N'global'   
    ,@cursor_identity = N'abc';  
  
-- Fetch all the rows from the sp_describe_cursor_columns output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
   FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_describe_cursor_columns.  
CLOSE @Report;  
DEALLOCATE @Report;  
GO  
-- Close and deallocate the original cursor.  
CLOSE abc;  
DEALLOCATE abc;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Курсоры](../../relational-databases/cursors.md)   
 [CURSOR_STATUS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-status-transact-sql.md)   
 [DECLARE CURSOR (Transact-SQL)](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [процедура sp_describe_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-transact-sql.md)   
 [Хранимая процедура sp_cursor_list &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursor-list-transact-sql.md)   
 [процедура sp_describe_cursor_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-tables-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
