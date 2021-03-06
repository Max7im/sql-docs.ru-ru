---
title: sys.database_usage (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- database_usage
- database_usage_TSQL
- sys.database_usage_TSQL
- sys.database_usage
dev_langs:
- TSQL
helpviewer_keywords:
- database_usage
- sys.database_usage
ms.assetid: be6820de-60bf-4ddd-ace7-4077893d630f
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 1816ab7f6e4ad35453c61fed8670c27b1f0ac833
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027389"
---
# <a name="sysdatabaseusage-azure-sql-database"></a>sys.database_usage (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **Примечание: Это относится только к базе данных SQL Azure версии 11.**  
  
 Выводит количество, тип и длительность существования баз данных на [!INCLUDE[ssSDS](../../includes/sssds-md.md)] сервера.  
  
 **Sys.database_usage** представление содержит следующие столбцы.  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|time|Дата возникновения событий использования.|  
|sku|Тип уровня службы для базы данных: **Web**, **бизнеса**, **основные**, **стандартный**, **уровня "премиум"**|  
|quantity|Максимальное число баз данных номера SKU, который существовал в течение этого дня.|  
  
## <a name="permissions"></a>Разрешения  
 Доступ только для чтения к этому представлению доступна для всех пользователей с разрешениями на подключение к **master** базы данных.  
  
## <a name="remarks"></a>Примечания  
 **Sys.database_usage** представление возвращает одну строку за каждый день вашей подписки.  
  
## <a name="see-also"></a>См. также  
 [Сведения о ценах на базы данных SQL](http://go.microsoft.com/fwlink/?LinkID=394978)   
 [Учетные записи и выставление счетов в базе данных Azure SQL для Windows](http://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
