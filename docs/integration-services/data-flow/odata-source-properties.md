---
title: Свойства источника OData | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: acfc6c1305e493aeb24b1d2c92bbebd424ac42c7
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35400896"
---
# <a name="odata-source-properties"></a>Свойства источника OData
Если щелкнуть правой кнопкой **Источник OData** в потоке данных и выбрать **Свойства**, то свойства компонента **Источник OData** отображаются в окне **Свойства**.  

## <a name="properties"></a>Свойства 
|Свойство|Описание|  
|-|-|  
|CollectionName|Имя коллекции, которую нужно получить из службы OData. Свойство **CollectionName** используется в том случае, когда значение **UseResourcePath** равно False.<br /><br /> Это свойство поддерживает выражения, что позволяет задать значение во время выполнения. Но если метаданные коллекции не соответствуют метаданным, которые использовались во время разработки, то происходит ошибка проверки, из-за чего выполнение потока данных приводит к ошибке.|  
|DefaultStringLength|Это значение указывает длину по умолчанию для строковых столбцов без максимальной длины.<br /><br /> **По умолчанию:** 4000|  
|Запрос|Параметры запроса OData. Это свойство поддерживает выражения и может быть задано во время выполнения.|  
|ResourcePath|Это свойство используется в том случае, когда необходимо указать полный путь к ресурсу, а не просто выбрать имя коллекции. Это свойство используется в том случае, если значение **UseResourcePath** равно True.|  
|UseResourcePath|Если задано значение True, то значение **ResourcePath** добавляется к базовому URL-адресу для определения расположения канала OData. Если значение равно False, то используется значение **CollectionName** .<br /><br /> **По умолчанию:** False|  
  
## <a name="see-also"></a>См. также:
[Источник «OData»](odata-source.md)
