---
title: "Метод getSendStringParametersAsUnicode (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3836d0ab-c3fb-41ff-bb89-10389594ae51
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 520e40a43f47536b34ef68ebebde73f199c8e915
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getsendstringparametersasunicode-method-sqlserverdatasource"></a>Метод getSendStringParametersAsUnicode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает **логическое** значение, указывающее, включена ли отправка параметров на сервер в Юникоде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getSendStringParametersAsUnicode()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если строковые параметры отправляются на сервер в Юникоде. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойство sendStringParametersAsUnicode имеет значение **true**, который является значением по умолчанию, строковые параметры отправляются на сервер в Юникоде. Если для свойства sendStringParametersAsUnicode задано значение **false**, строковые параметры отправляются на сервер в формате ASCII/MBCS, а не в ЮНИКОДЕ. Если sendStringParametersAsUnicode не задано, getSendStringParametersAsUnicode возвращает значение по умолчанию **true**.  
  
 Дополнительные сведения о свойстве соединения sendStringParametersAsUnicode см. в разделе [задание свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  