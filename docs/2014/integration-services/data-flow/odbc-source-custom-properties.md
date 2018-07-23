---
title: Пользовательские свойства источника ODBC | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 362bbcd8-b7b0-4bab-8afe-1212b2ad1af9
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 876ace661fe3eeacc5f78f4d3ca0e0ac2165b4d2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231504"
---
# <a name="odbc-source-custom-properties"></a>Пользовательские свойства источника «ODBC»
  В следующей таблице описаны пользовательские свойства источника «ODBC». Все свойства могут быть заданы на основе выражений свойств служб SSIS.  
  
|Имя свойства|Тип данных|Описание|  
|-------------------|---------------|-----------------|  
|Соединение|Соединение ODBC|Соединение ODBC для получения доступа к базе данных-источнику.|  
|AccessMode|Integer (перечисление)|Режим, используемый для доступа к базе данных. Возможными значениями являются Table Name (0) и SQL Command (1).<br /><br /> По умолчанию применяется Table Name (0).|  
|BatchSize|Целочисленный|Размер пакета для массового извлечения. Это количество записей, извлекаемых в виде массива. Если выбранный поставщик ODBC не поддерживает массивы, размер пакета равен 1.|  
|BindCharColumnAs|Integer (перечисление)|Это свойство определяет, как источник ODBC привязывает столбцы, имеющие строковые типы с многобайтовой кодировкой, такие как SQL_CHAR, SQL_VARCHAR или SQL_LONGVARCHAR.<br /><br /> Возможными значениями являются Unicode (0) (которое привязывает столбцы как SQL_C_WCHAR) и ANSI (1) (которое привязывает столбцы как SQL_C_CHAR). По умолчанию применяется Unicode (0).<br /><br /> **Примечание**. Это свойство недоступно в **редакторе источника ODBC**, но может быть задано с помощью **расширенного редактора**.|  
|BindNumericAs|Integer (перечисление)|Это свойство определяет, как источник ODBC привязывает столбцы, имеющие числовые данные с типами данных SQL_TYPE_NUMERIC и SQL_TYPE_DECIMAL.<br /><br /> Возможными параметрами являются Char (0) (который привязывает столбцы как SQL_C_CHAR) и Numeric (1) (который привязывает столбцы как SQL_C_NUMERIC). По умолчанию применяется значение Char (0).<br /><br /> **Примечание**. Это свойство недоступно в **редакторе источника ODBC**, но может быть задано с помощью **расширенного редактора**.|  
|DefaultCodePage|Целочисленный|Кодовая страница, используемая для строковых выходных столбцов.<br /><br /> **Примечание**. Это свойство недоступно в **редакторе источника ODBC**, но может быть задано с помощью **расширенного редактора**.|  
|ExposeCharColumnsAsUnicode|Логическое значение|Это свойство определяет, как компонент предоставляет доступ к столбцам CHAR. Значением по умолчанию является FALSE, которое указывает, что доступ к столбцам CHAR предоставляется как к многобайтовым строкам с (DT_STR). Если задано значение TRUE, к столбцам CHAR предоставляется доступ как к строкам с расширенными символами (DT_WSTR).<br /><br /> **Примечание**. Это свойство недоступно в **редакторе источника ODBC**, но может быть задано с помощью **расширенного редактора**.|  
|FetchMethod|Integer (перечисление)|Метод, используемый для возврата данных. Возможными параметрами являются Row by row (0) и Batch (1). По умолчанию применяется значение Batch (1).<br /><br /> Дополнительные сведения об этих параметрах см. в разделе [ODBC Source](odbc-source.md).<br /><br /> **Примечание**. Это свойство недоступно в **редакторе источника ODBC**, но может быть задано с помощью **расширенного редактора**.|  
|SqlCommand|String|Команда SQL, которая должна быть выполнена, если для AccessMode задано значение «команда SQL».|  
|StatementTimeout|Целочисленный|Количество секунд, в течение которых должно происходить ожидание выполнения инструкции SQL, прежде чем будет выполнен возврат с ошибкой в приложение. Значение по умолчанию — 0. Значение 0 указывает, что система не следит за истечением времени ожидания.|  
|TableName|String|Имя таблицы с данными, которая используется, если для AccessMode задано значение «Имя таблицы».|  
|LobChunckSize|Целочисленный|Распределение размера фрагментов данных для столбцов LOB.|  
||||  
  
## <a name="see-also"></a>См. также  
 [Источник ODBC](odbc-source.md)   
 [Редактор источника ODBC &#40;страницы диспетчера соединений&#41;](../odbc-source-editor-connection-manager-page.md)  
  
  