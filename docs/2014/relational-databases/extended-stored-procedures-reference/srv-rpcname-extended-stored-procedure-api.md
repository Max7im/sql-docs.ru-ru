---
title: srv_rpcname (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_rpcname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcname
ms.assetid: 0a1424e4-3319-4836-b8d8-5e0344cc683f
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4415c7cd4ed79426403d73650d4502edace44fd8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324274"
---
# <a name="srvrpcname-extended-stored-procedure-api"></a>srv_ rpcname (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Возвращает компонент имени процедуры для текущей удаленной хранимой процедуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBCHAR * srv_rpcname (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, представляющую собой дескриптор соединения с клиентом (в данном случае — дескриптор, получивший удаленную хранимую процедуру). Структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *len*  
 Указатель на целочисленную переменную, принимающую длину имени базы данных. Если значением *len* является NULL, длина имени удаленной хранимой процедуры не возвращается.  
  
## <a name="returns"></a>Возвращает  
 Указатель DBCHAR на оканчивающуюся нулевым байтом строку для компонента имени текущей удаленной хранимой процедуры. Если текущей удаленной хранимой процедуры не существует, возвращается NULL, а значение *len* устанавливается равным -1.  
  
## <a name="remarks"></a>Примечания  
 Эта функция возвращает только имя удаленной хранимой процедуры. Она не включает необязательные описатели владельца, имени базы данных и номера удаленной хранимой процедуры.  
  
 Поскольку вызов **srv_rpcname** допускается и при отсутствии удаленной хранимой процедуры (информационной ошибки не возникает), эта функция дает возможность определить, существует ли удаленная хранимая процедура.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
