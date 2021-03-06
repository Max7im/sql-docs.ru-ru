---
title: Программное управление пакетами и папками | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 98e5bd7267162f28d6a6cfb7222adb395095d952
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275510"
---
# <a name="managing-packages-and-folders-programmatically"></a>Программное управление пакетами и папками
  В процессе программирования при работе с пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может возникнуть необходимость определить, существует ли отдельный пакет или папка, либо управлять папками, где хранятся пакеты. Класс <xref:Microsoft.SqlServer.Dts.Runtime.Application> из пространства имен <xref:Microsoft.SqlServer.Dts.Runtime> предоставляет разнообразные методы, выполняющие эти требования.  
  
##  <a name="exists"></a> Определение существования пакета или папки  
 Чтобы определить программным способом, существует ли сохраненный пакет, перед попыткой загрузить и выполнить его вызовите один из следующих методов:  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|  
  
 Чтобы определить программным способом, существует ли папка, перед попыткой получить список пакетов, хранящихся в этой папке, вызовите один из следующих методов:  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|  
  

  
##  <a name="managing"></a> Управление пакетами и папками  
 Класс <xref:Microsoft.SqlServer.Dts.Runtime.Application> пространства имен <xref:Microsoft.SqlServer.Dts.Runtime> предоставляет дополнительные методы для управления пакетами и папками, в которых эти пакеты хранятся.  
  
###  <a name="managing_rempkg"></a> Удаление пакета  
 Для удаления сохраненного пакета программным способом вызовите один из следующих методов:  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|  
  

  
###  <a name="managing_create"></a> Создание папки  
 Для создания папки хранения программным способом вызовите один из следующих методов:  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|  
  

  
###  <a name="managing_remfldr"></a> Удаление папки  
 Для удаления папки хранения программным способом вызовите один из следующих методов:  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|  
  
  
  
###  <a name="managing_rename"></a> Переименование папки  
 Для переименования папки хранения программным способом вызовите один из следующих методов:  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|  
  

  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services  **<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Управление пакетами (службы SSIS)](../service/package-management-ssis-service.md)   
 [Программное перечисление доступных пакетов](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
