---
title: Выполнение хранимых процедур (OLE DB) | Документация Майкрософт
description: Выполнение хранимых процедур (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- OLE DB Driver for SQL Server, stored procedures
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: f60e7913713b0b1877b8a8c9ef6a2f6644f78ef7
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43037824"
---
# <a name="stored-procedures---running"></a>Выполнение хранимых процедур
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  При выполнении инструкций вызов хранимой процедуры в источнике данных (вместо выполнения или подготовки инструкции непосредственно в клиентском приложении) может обеспечить следующее:  
  
-   высокую производительность;  
  
-   низкие издержки сети;  
  
-   лучшую согласованность;  
  
-   большую точность;  
  
-   дополнительные возможности.  
  
 Драйвер OLE DB для SQL Server поддерживает три следующих механизмов, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать хранимые процедуры для возврата данных:  
  
-   Каждая инструкция SELECT в хранимой процедуре формирует результирующий набор.  
  
-   Процедура может возвращать данные через выходные параметры.  
  
-   Процедура может иметь целочисленный код возврата.  
  
 Приложение должно быть способно обработать все эти данные, возвращаемые хранимыми процедурами.  
  
 Разные поставщики OLE DB возвращают выходные параметры и значения на разных этапах во время обработки результатов. В случае с драйвером OLE DB для SQL Server выходные параметры и коды возврата недоступны, пока потребитель не получил результирующий набор или не отменил получение результирующего набора, возвращаемого хранимой процедурой. Коды возврата и выходные параметры возвращаются сервером в последнем пакете потока табличных данных.  
  
 Поставщики используют свойство DBPROP_OUTPUTPARAMETERAVAILABILITY для сообщения о возвращении выходных параметров и возвращаемых значений. Это свойство доступно в наборе свойств DBPROPSET_DATASOURCEINFO.  
  
 Драйвер OLE DB для SQL Server присваивает свойству DBPROP_OUTPUTPARAMETERAVAILABILITY значение DBPROPVAL_OA_ATROWRELEASE, указывая, что коды возврата и выходные параметры не будут возвращены, пока результирующий набор не будет обработан или освобожден.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры](../../oledb/ole-db/stored-procedures.md)  
  
  
