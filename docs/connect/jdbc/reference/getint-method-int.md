---
title: "Метод getInt (int) | Документы Microsoft"
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
- SQLServerCallableStatement.getInt (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c86792bb-096e-4c58-8b9e-74491ccf83a6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ee815faa008d0ed4f007e5a3c3b81f7421146aef
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getint-method-int"></a>Метод getInt (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде **int** на Java по заданному индексу параметра языка программирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getInt(int index)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Индекс*  
  
 **Int** , указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getInt указывается с помощью метода getInt в интерфейсе java.sql.CallableStatement.  
  
 Этот метод поддерживается только в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] типы данных, которые могут безопасно возвращать целочисленное значение, такие как int, smallint, tinyint и bit. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод getInt &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getint-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  