---
title: Установите свойство (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Position
helpviewer_keywords:
- Position property [ADO]
ms.assetid: daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 407ef25ebc55685436f61acaa42cbdf964619b09
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280693"
---
# <a name="position-property-ado"></a>Свойства position (ADO)
Указывает текущую позицию внутри [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение, задающее смещение в байтах от начала текущей позиции в потоке. Значение по умолчанию — 0, представляющее первый байт в поток.  
  
## <a name="remarks"></a>Примечания  
 Можно переместить точку текущую позицию после конца потока. Если указать текущую позицию после конца потока, [размер](../../../ado/reference/ado-api/size-property-ado-stream.md) из **поток** объекта будет увеличено соответствующим образом. Все новые байты, добавляемые в этом случае будет иметь значение null.  
  
> [!NOTE]
>  **Позиция** всегда измеряет байт. Для текста потоков с использованием многобайтовых кодировок умножьте позицию размера символа для определения количества символов. Например для набора символов 2 байта, первый символ находится в положении 0, второй символ в позиции 2, третьего знака в позиции 4 и т. д.  
  
> [!NOTE]
>  Отрицательные значения не может использоваться для изменения текущего положения в **поток**. Можно использовать только положительные числа для **позиции**.  
  
> [!NOTE]
>  Для только для чтения **поток** объектов ADO не возвратит ошибку, если **позиции** задано значение больше **размер** из **поток**. Это не приводит к изменению размера **поток**, или измените **поток** содержимого каким-либо образом. Однако этого следует избегать, поскольку это приводит к бессмысленной **позиции**значение.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Charset (ADO)](../../../ado/reference/ado-api/charset-property-ado.md)
