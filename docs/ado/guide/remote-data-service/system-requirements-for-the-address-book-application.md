---
title: Требования к системе для адреса книги приложения | Документы Microsoft
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
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: da385405-1c9a-478b-9bf6-fba70015324c
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 063a8d6dd6001c612bb52efa2773deafa546fd86
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274543"
---
# <a name="system-requirements-for-the-address-book-application"></a>Требования к системе для применение адресной книги
Настройка примера приложения адресную книгу, должны отвечать следующим требованиям программного обеспечения и базы данных:  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="software-requirements"></a>Требования к программному обеспечению  
 Требования к программному обеспечению сервера компьютер для запуска этого веб-приложения включают:  
  
-   Microsoft Windows NT® Server 4.0 с пакетом обновления 3 или более поздней версии или Microsoft Windows® 2000 Server.  
  
-   Microsoft Internet Information Services (IIS) версии 3.0 или более поздней версии, с помощью Active Server Pages.  
  
 Требования к программному обеспечению клиентских компьютеров для запуска этого веб-приложения включают:  
  
-   Microsoft Internet Explorer 4.0 или более поздней версии.  
  
-   Microsoft Windows NT 4.0 рабочей станции или сервера, Windows 2000 или Microsoft Windows 98.  
  
## <a name="database-requirements"></a>Требования к базе данных  
 Для использования этого примера требуются:  
  
-   Сервер базы данных оперативной Microsoft® SQL Server версии 6.5 или более поздней версии.  
  
-   Привилегий для создания базы данных и заполнить ее образцами данными.  
  
-   Проверка заполненных данные с помощью Enterprise Manager или служебные программы ISQL (вызываемой Query Analyzer в SQL Server 7.0).  
  
 Если вы не имеете привилегий, администратор базы данных может потребоваться настройка системы и предоставьте разрешение базы данных, или настроить базу данных для вас.  
  
## <a name="see-also"></a>См. также  
 [Скрипт SQL адресной книги](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)   
 [Объект DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Выполнение примера приложения адресной книги](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


