---
title: "DATEDIFF (выражение служб SSIS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DATEDIFF statement
- dates [Integration Services], DATEDIFF
ms.assetid: 449b327f-47c7-4709-8bc6-4ee9a35cc330
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0c771f4788199c26fae2cfe46dfd66a18d67fcb6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="datediff-ssis-expression"></a>DATEDIFF (выражение служб SSIS)
  Возвращает числовое значение границ дат или времени между двумя указанными датами. Параметр *datepart* указывает границы даты и времени, которые необходимо сравнить.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DATEDIFF(datepart, startdate, endate)  
```  
  
## <a name="arguments"></a>Аргументы  
 *datepart*  
 Параметр, который указывает, какую часть даты сравнивать и для какой вернуть значение.  
  
 *startdate*  
 Начальная дата периода.  
  
 *endate*  
 Конечная дата периода.  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Замечания  
 В следующей таблице перечислены части дат и сокращения, распознаваемые средством оценки выражений.  
  
|datepart|Сокращения|  
|--------------|-------------------|  
|Год|yy, yyyy|  
|Квартал|qq, q|  
|Месяц|mm, m|  
|День года|dy, y|  
|День|dd, d|  
|Неделя|wk, ww|  
|День недели|dw, w|  
|Час|Hh|  
|Минута|mi, n|  
|Вторая|ss, s|  
|Миллисекунда|Ms|  
  
 DATEDIFF возвращает NULL, если хотя бы один аргумент имеет значение NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Произойдет ошибка при передаче недопустимой даты, а также в случае, если единица времени или даты не является строкой или если дата начала либо конца не является датой.  
  
 Если конечная дата является более ранней, чем начальная, то функция возвращает отрицательное число. Если начальные и конечные даты равны друг другу или находятся в одном интервале, то функция возвращает ноль.  
  
## <a name="ssis-expression-examples"></a>Примеры выражений служб SSIS  
 Этот пример вычисляет количество дней между двумя литералами даты. Если дата имеет формат «мм/дд/гггг», то эта функция возвращает 7.  
  
```  
DATEDIFF("dd", (DT_DBTIMESTAMP)"8/1/2003", (DT_DBTIMESTAMP)"8/8/2003")  
```  
  
 Этот пример возвращает количество месяцев между литералом даты и текущей датой.  
  
```  
DATEDIFF("mm", (DT_DBTIMESTAMP)"8/1/2003",GETDATE())  
```  
  
 Этот пример возвращает количество недель между датой в столбце **ModifiedDate** и переменной **YearEndDate** . Если **YearEndDate** имеет тип данных **date** , то явного приведения не требуется.  
  
```  
DATEDIFF("Week", ModifiedDate,@YearEndDate)  
```  
  
## <a name="see-also"></a>См. также  
 [Функция DATEADD &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEPART &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [ДЕНЬ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [МЕСЯЦ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [ГОД &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Функции &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  