---
title: sp_helplanguage (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6567deb529d4a40f89fe34e8c56d57e8ce7a680a
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43063017"
---
# <a name="sphelplanguage-transact-sql"></a>sp_helplanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Выдает отчет о конкретном альтернативном языке или обо всех языках из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@language=** ] **"***языка***"**  
 Имя альтернативного языка, для которого следует отображать сведения. *Язык* — **sysname**, значение по умолчанию NULL. Если *языка* будет указан, возвращаются сведения о соответствующем языке. Если язык не указан, сведения обо всех языках из **sys.syslanguages** возвращается Просмотр в режиме совместимости.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**LangID**|**smallint**|Идентификационный номер языка.|  
|**DATEFORMAT**|**nchar(3)**|Формат даты.|  
|**DATEFIRST**|**tinyint**|Первый день недели: 1 — понедельник, 2 — вторник и так далее до 7 — воскресенье.|  
|**Обновление**|**int**|Версия последнего обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для данного языка.|  
|**name**|**sysname**|Имя языка.|  
|**alias**|**sysname**|Альтернативное имя языка.|  
|**месяцев**|**nvarchar(372)**|Названия месяцев.|  
|**shortmonths**|**nvarchar(132)**|Сокращенные названия месяцев.|  
|**дней**|**nvarchar(217)**|Названия дней.|  
|**код языка**|**int**|Код данной локали в Windows.|  
|**msglangid**|**smallint**|Идентификатор группы сообщений компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-information-about-a-single-language"></a>A. Возвращение сведений об отдельном языке  
 В следующем примере отображаются сведения об альтернативном языке `French`.  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>Б. Возвращение сведений обо всех языках  
 В следующем примере отображаются сведения обо всех установленных альтернативных языках.  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE (Transact-SQL)](../../t-sql/functions/language-transact-sql.md)   
 [SET LANGUAGE (Transact-SQL)](../../t-sql/statements/set-language-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
