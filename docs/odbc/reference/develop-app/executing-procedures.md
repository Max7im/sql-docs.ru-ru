---
title: Выполнение процедур | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], executing
ms.assetid: a75e497a-4661-438a-a10e-f598c65f81be
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d61929c1d2afb756be5157f3378ff0fe6b4d7e95
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910779"
---
# <a name="executing-procedures"></a>Выполнение процедур
ODBC определяет стандартные escape-последовательность выполнения процедур. Синтаксис этой последовательности и пример кода, который его использует, в разделе [вызовы процедур](../../../odbc/reference/develop-app/procedure-calls.md).  
  
 Для выполнения процедуры, приложение выполняет следующие действия:  
  
1.  Задает значения всех параметров. Дополнительные сведения см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md)далее в этом разделе.  
  
2.  Вызовы **SQLExecDirect** и передает его строка, содержащая инструкцию SQL, который выполняет процедуру. Этот оператор можно использовать escape-последовательность, определяются синтаксиса ODBC или СУБД; инструкции, которые используют синтаксис СУБД не взаимозаменяемы.  
  
3.  Когда **SQLExecDirect** вызывается драйвер:  
  
    -   Получает текущие значения параметров и преобразует их при необходимости. Дополнительные сведения см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md)далее в этом разделе.  
  
    -   Вызывает процедуру в источнике данных и отправляет его значение преобразованного параметра. Как драйвер вызывает процедуру, относящиеся к драйверу. Например он может изменить инструкцию SQL, чтобы использовать источник данных грамматику SQL и отправить эту инструкцию для выполнения, или он может вызвать процедуру напрямую с помощью механизма удаленного вызова процедур (RPC), определенный в протоколе потока данных СУБД.  
  
    -   Возвращает значения ввода вывода или выходных параметров или возвращаемого значения процедуры, при условии, что процедура завершается успешно. Эти значения могут оказаться недоступными, пока после обработки всех других результатов (количество строк и результирующих наборов) сформированное такой процедурой. Если процедура завершается ошибкой, драйвер возвращает все ошибки.
