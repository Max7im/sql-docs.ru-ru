---
title: Export Column Transformation Editor (страница "столбцы") | Документация Майкрософт
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
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b427d8a727f0db31b63d43efbe00378c7ef0f18b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207454"
---
# <a name="export-column-transformation-editor-columns-page"></a>Редактор преобразования «Экспорт столбца» (страница «Столбцы»)
  Страница **Столбцы** диалогового окна **Редактор преобразования «Экспорт столбца»** используется для задания столбцов в потоке данных, извлекаемых в файлы. Можно указать, будет ли преобразование «Экспорт столбца» добавлять данные в конец файла или перезаписывать существующий файл.  
  
 Дополнительные сведения о редакторе преобразований «Экспорт столбца» см. в разделе [Export Column Transformation](data-flow/transformations/export-column-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Извлечь столбец**  
 Производится выбор из списка входных столбцов, содержащих текстовые данные или изображения. Все строки должны иметь определения для параметров **Извлечь столбец** и **Столбец пути к файлу**.  
  
 **Столбец пути к файлу**  
 Производится выбор из списка входных столбцов, содержащих пути к файлам и имена файлов. Все строки должны иметь определения для параметров **Извлечь столбец** и **Столбец пути к файлу**.  
  
 **Разрешить добавление**  
 Определяет, будет ли преобразование добавлять данные к существующим файлам. Значение по умолчанию — `false`.  
  
 **Принудительное усечение**  
 Определяет, будет ли преобразование удалять содержимое существующих файлов перед записью данных. Значение по умолчанию — `false`.  
  
 **Запись BOM**  
 Определяет, будет ли в файл записываться метка порядка следования байтов (BOM). Метка BOM записывается только если данные имеют `DT_NTEXT` или тип данных DT_WSTR и не добавляется к существующему файлу данных.  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Export Column Transformation Editor &#40;странице вывода ошибок&#41;](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
