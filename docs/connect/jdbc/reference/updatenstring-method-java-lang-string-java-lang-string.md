---
title: Метод updateNString (java.lang.String, java.lang.String) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6daca03f-c60f-4842-b9e3-11d136e78312
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41c12f32b1b42153baa79543ca284872040763ba
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38040872"
---
# <a name="updatenstring-method-javalangstring-javalangstring"></a>Метод updateNString (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет значение **String** с помощью указанной метки столбцов в заданном столбце.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateNString(java.lang.String columnLabel,  
                          java.lang.String nString)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ColumnLabel состоит из*  
  
 Значение типа **String**, содержащее метку столбца.  
  
 *nString*  
  
 Объект **строка** объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateNString указывается с помощью метода updateNString в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает Java **строка** к выбранному **nchar**, **nvarchar(max)**, **ntext**, и **xml** столбцы. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateNString &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
