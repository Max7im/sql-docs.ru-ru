---
title: Кэширование шаблонов (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 79d5d5ea1cd40d1a2fc167d16da4fa2e2af65a43
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236584"
---
# <a name="template-caching-sqlxml-40"></a>Кэширование шаблонов (SQLXML 4.0)
  Кэширование шаблонов значительно повышает производительность. Если установлено кэширование шаблонов, при первом выполнении шаблон располагается в памяти. Это повышает производительность последующего выполнения шаблона.  
  
 Размер кэша шаблонов можно задать, добавив в реестр следующий ключ:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Размер кэша необходимо указывать, исходя из объема доступной памяти и количества используемых шаблонов. Значение по умолчанию **TemplateCacheSize** равно 31. Размер кэша можно увеличить, если доступ к шаблону кажется медленным, или уменьшить при небольшом объеме памяти.  
  
 Для повышения производительности рекомендуется установить **TemplateCacheSize** выше, чем количество обычно используемых шаблонов. Если **TemlateCacheSize** меньше, чем число имеющихся шаблонов, производительность снижается по мере число шаблонов. **TemplateCacheSize** можно задать до максимального размера в 128.  
  
 При каждом использовании кэшированного шаблона проверяется время изменения файла шаблона, чтобы при необходимости его обновить. Это происходит потому, что копия на диске новее копии в кэше.  
  
> [!NOTE]  
>  Параметры шаблона и свойства команд не кэшируются.  
  
## <a name="see-also"></a>См. также  
 [Кэширование схем &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)   
 [Кэширование XSL &#40;SQLXML 4.0&#41;](xsl-caching-sqlxml-4-0.md)  
  
  
