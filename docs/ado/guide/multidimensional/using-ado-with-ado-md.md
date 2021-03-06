---
title: Использование ADO с ADO MD | Документы Microsoft
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
- ADO, using with ADO MD
ms.assetid: cfae435e-2ac3-4312-8c1e-9ca4a74cd875
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d6aed08b40b25eb0f725697eb6fac8908894ebd
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273539"
---
# <a name="using-ado-with-ado-md"></a>Использование ADO с ADO MD
ADO и ADO MD, связанных, но отдельных объектные модели. ADO предоставляет объекты для соединения с источниками данных, выполнения команд, получение табличных данных и схеме метаданных в табличном формате и просматривать сведения об ошибке поставщика. ADO MD предоставляет объекты для получения многомерных данных и просмотр метаданных в многомерной схемой.  
  
 При работе с MDP, можно использовать ADO, ADO MD или оба вместе с приложением. С помощью ссылки на обе библиотеки в проект, будет иметь полный доступ к функции, предоставляемые вашей MDP.  
  
 Часто полезно для потребителей плоского табличного просмотреть представление многомерного набора данных. Это можно сделать с помощью ADO [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта. Указать источник для вашей [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) как ***источника*** параметр [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод **записей**, а не как источник для ADO MD **ячеек**.  
  
 Также может быть полезна для просмотра метаданных схемы в табличном режиме, а не как в иерархии объектов. ADO [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) метод [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта пользователь может открыть **записей** , содержащий сведения о схеме. ***QueryType*** параметр **OpenSchema** метод имеет несколько [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) значений, связанных с MDPs. Эти значения определяются следующим образом:  
  
-   **adSchemaCubes**  
  
-   **adSchemaDimensions**  
  
-   **adSchemaHierarchies**  
  
-   **adSchemaLevels**  
  
-   **adSchemaMeasures**  
  
-   **adSchemaMembers**  
  
 Чтобы использовать значения перечисления ADO с ADO MD свойствами или методами, проект должен содержать ссылки ADO и ADO MD библиотеки. Например, можно использовать ADO **adState** значения перечисления с ADO MD [состояние](../../../ado/reference/ado-md-api/state-property-ado-md.md) свойство. Дополнительные сведения о том, как установить ссылки на библиотеки см. в документации средства разработки.  
  
 Дополнительные сведения о методах и объектов ADO см. в разделе [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md).  
  
## <a name="see-also"></a>См. также  
 [Объектная модель ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (многомерные данные) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Общие сведения о многомерных схем и данных](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Программирование с использованием ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Работа с многомерными данными](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
