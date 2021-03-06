---
title: Наблюдение за выполнением пакетов и других операций | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 97005d3d222019da9fad96ea9c4ab427acd1a384
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279780"
---
# <a name="monitoring-for-package-executions-and-other-operations"></a>Наблюдение за выполнением пакетов и других операций
  Вы можете отслеживать выполнения пакета [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , проверки проекта и другие операции с помощью одного или нескольких из следующих средств. Такие средства, как отводы данных, доступны только для проектов, которые развертываются на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
-   Журналы  
  
     Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](integration-services-ssis-logging.md).  
  
-   Отчеты  
  
     Дополнительные сведения см. в статье [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).  
  
-   Представления  
  
     Дополнительные сведения см. в статье [Представления (каталог служб Integration Services)](/sql/integration-services/system-views/views-integration-services-catalog).  
  
-   Счетчики производительности  
  
     Дополнительные сведения см. в статье [Performance Counters](performance-counters.md).  
  
-   Отводы данных  
  
## <a name="operation-types"></a>Типы операций  
 В отслеживаются операции нескольких разных типов `SSISDB` каталога, на [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] сервера. Каждая операция может иметь несколько связанных с ней сообщений. Каждое сообщение можно отнести к одному из нескольких разных типов. Например, сообщение может иметь тип «информация», «предупреждение» или «ошибка». Полный список типов сообщений см. в документации по представлению Transact-SQL [catalog.operation_messages (база данных SSISDB)](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database). Полный список типов операций см. в статье [catalog.operations (база данных SSISDB)](/sql/integration-services/system-views/catalog-operations-ssisdb-database).  
  
 Для указания состояния операции используются девять различных типов состояний. Полный список типов состояний см. в представлении [catalog.operations (база данных SSISDB)](/sql/integration-services/system-views/catalog-operations-ssisdb-database)  
  
## <a name="related-content"></a>См. также  
 Запись в блоге [Общие сведения о T-SQL API служб SSIS](http://go.microsoft.com/fwlink/?LinkId=249051)на сайте blogs.msdn.com.  
  
  
