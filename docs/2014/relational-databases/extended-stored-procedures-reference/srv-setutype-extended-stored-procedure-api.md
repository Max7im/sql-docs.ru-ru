---
title: srv_setutype (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
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
- srv_setutype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
caps.latest.revision: 31
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 44d61cd675c1d1236cc6359a99d285d1995fdd1b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311534"
---
# <a name="srvsetutype-extended-stored-procedure-api"></a>srv_setutype (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Устанавливает определяемый пользователем тип данных для столбца строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *column*  
 Указывает, какой столбец устанавливать. Нумерация столбцов начинается с 1.  
  
 *user_type*  
 Указывает код определяемого пользователем типа данных.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL. Если столбец не существует, возвращает значение FAIL.  
  
## <a name="remarks"></a>Примечания  
 Столбец имеет два типа данных: фактический и определяемый пользователем. Определяемый пользователем тип данных используется [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения действительного определяемого пользователем типа данных столбца, и сведения об описании столбца, например допустимость значения NULL и возможность обновления (если таковые существуют).  
  
 Функцию **srv_setutype** можно вызвать в любое время после определения *column* с помощью функции **srv_describe** и до передачи последней строки.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также  
 [srv_describe (интерфейс API расширенных хранимых процедур)](srv-describe-extended-stored-procedure-api.md)  
  
  
