---
title: Драйвер OLE DB для SQL Server | Документы Майкрософт
description: Компоненты драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 2836438e6dc5eb501d67e724397acbdf1a0a956a
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43020673"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Компоненты драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server содержит следующие компоненты:  

|Компонент|Описание|  
|---------------|-----------------|  
|msoledbsql.dll|Файл библиотеки динамической компоновки (DLL), содержащий все драйвера OLE DB для функций сервера SQL Server.|  
|msoledbsqlr.rll|Сопутствующий файл ресурса для драйвера OLE DB для SQL Server библиотеки.|   
|msoledbsql.h|Драйвер OLE DB для SQL Server файла заголовка, который содержит все новые определения, необходимые для использования драйвера OLE DB для SQL Server. Этот файл заголовка заменяет файл заголовка sqloledb.h.<br /><br /> Примечание: Можно дать ссылку msoledbsql.h и sqloledb.h в одной программе до тех пор, пока что sqloledb.h указывается первым.|  
|msoledbsql.lib|Файл библиотеки, необходимый для прямого вызова [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) функцию, которая является частью драйвера OLE DB для SQL Server.<br /><br /> Примечание. Если в программном коде есть ссылка на файл msoledbsql.lib, необходимо убедиться, что файл msoledbsql.dll находится в системном пути разработчика и в системных путях пользователей, использующих данное приложение.|  

## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
