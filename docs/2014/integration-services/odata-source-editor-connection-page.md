---
title: Редактор источника OData (страница «соединение») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- Sql12.dts.designer.odatasource.connection.f1
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f3ae477a34a296ade90fb50dde0a600cf81ac18a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213274"
---
# <a name="odata-source-editor-connection-page"></a>Редактор источника OData (страница «Подключение»)
  Страница **Диспетчер соединений** диалогового окна **Редактор источника OData** служит для выбора диспетчера соединений OData для источника. На этой странице также можно задать путь к коллекции или ресурсу, а также параметры запроса, чтобы указать, какие данные нужно получить из источника OData. Дополнительные сведения об источнике OData см. в разделе [OData Source](data-flow/odata-source.md).  
  
## <a name="static-options"></a>Статические параметры  
 **Диспетчер соединений OData**  
 Выберите из списка существующий диспетчер соединений или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Создайте новый диспетчер соединений с помощью диалогового окна **Редактор диспетчера соединений OData** .  
  
 **Использование пути к коллекции или ресурсу**  
 Укажите метод выбора данных из источника.  
  
|Параметр|Описание|  
|------------|-----------------|  
|Коллекция|Извлечение данных из источника OData с помощью имени коллекции.|  
|Путь к ресурсу|Извлечение данных из источника OData с помощью пути к ресурсу.|  
  
 **Параметры запроса**  
 Укажите параметры запроса.  Например: $top=5  
  
 **URL-адрес канала**  
 Отображает доступный только для чтения URL-адрес канала на основе параметров, выбранных в этом диалоговом окне.  
  
 **Предварительный просмотр**  
 Предварительный просмотр результатов в диалоговом окне **Предварительный просмотр** . В окне**Предварительный просмотр** может отображаться до 20 строк.  
  
## <a name="dynamic-options"></a>Динамические параметры  
  
### <a name="use-collection-or-resource-path--collection"></a>Использование пути к коллекции или ресурсу = коллекция  
 **Коллекция**  
 Выберите коллекцию из раскрывающегося списка.  
  
### <a name="use-collection-or-resource-path--resource-path"></a>Использование пути к коллекции или ресурсу = путь к ресурсу  
 **Resource path**  
 Введите путь к ресурсу. Например: Employees  
  
## <a name="see-also"></a>См. также  
 [Редактор источника OData &#40;страница "столбцы"&#41;](../../2014/integration-services/odata-source-editor-columns-page.md)   
 [Редактор источника OData &#40;странице вывода ошибок&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md)   
 [Диспетчер подключений OData](connection-manager/odata-connection-manager.md)  
  
  
