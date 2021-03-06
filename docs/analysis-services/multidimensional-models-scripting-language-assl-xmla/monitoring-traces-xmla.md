---
title: Наблюдение за трассировками (XMLA) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 24aab35b34ed9339ec2d7950efab21a94b2c0d96
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="monitoring-traces-xmla"></a>Наблюдение за трассировками (XMLA)
  Можно использовать [Subscribe](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md) в XML для аналитики (XMLA) для наблюдения за существующей трассировкой, определенной в экземпляре команда [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. **Subscribe** команда возвращает результаты трассировки в виде набора строк.  
  
## <a name="specifying-a-trace"></a>Задание трассировки  
 [Объекта](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) свойство **Subscribe** команды должен содержать либо ссылку на объект [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра или трассировки на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра. Если **объекта** свойство не указано или не указан идентификатор трассировки в **объекта** свойства **Subscribe** команда отслеживает трассировку сеанса по умолчанию для явного сеанса, указанного в заголовке SOAP для команды.  
  
## <a name="returning-results"></a>Возвращаемые результаты  
 **Subscribe** команда возвращает набор строк, содержащий события трассировки, захваченные указанной трассировки. **Subscribe** команда возвращает результаты трассировки, пока не будет отменена командой [отменить](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) команды.  
  
 Набор строк содержит столбцы, перечисленные в следующей таблице.  
  
|Столбец|Data type|Description|  
|------------|---------------|-----------------|  
|EventClass|Целочисленный|Класс события, полученного трассировкой.|  
|EventSubclass|Long integer|Подкласс события, полученного трассировкой.|  
|CurrentTime|DateTime|Время начала события, если доступно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|StartTime|DateTime|Время начала события, если доступно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|EndTime|DateTime|Время окончания события, если оно известно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».<br /><br /> Этот столбец не заполняется для классов событий, описывающих начало процесса или действия.|  
|Длительность|Long integer|Общее время (в миллисекундах), прошедшее для события.|  
|CPUTime|Long integer|Общее время процессора (в миллисекундах), прошедшее для события.|  
|JobID|Long integer|Идентификатор задания для процесса.|  
|SessionID|Строковые значения|Идентификатор сеанса, к которому относится происшедшее событие.|  
|SessionType|Строковые значения|Тип сеанса, к которому относится происшедшее событие.|  
|ProgressTotal|Long integer|Общий ход выполнения, о котором сообщает событие, в числовом или количественном выражении.|  
|IntegerData|Long integer|Целочисленные данные, связанные с событием. Содержимое этого столбца зависит от класса событий и подкласса событий.|  
|ObjectID|Строковые значения|Идентификатор объекта, к которому относится происшедшее событие.|  
|ObjectType|Строковые значения|Тип объекта, указанного в ObjectName.|  
|ObjectName|String|Имя объекта, к которому относится происшедшее событие.|  
|ObjectPath|String|Иерархический путь объекта, к которому относится происшедшее событие. Путь представлен в виде строки идентификаторов объектов, разделенной запятыми, для родителей объекта, указанного в ObjectName.|  
|ObjectReference|Строковые значения|XML-представление ссылки объекта для объекта, указанного в ObjectName.|  
|NestLevel|Целочисленный|Уровень транзакции, к которой относится происшедшее событие.|  
|NumSegments|Long integer|Количество сегментов данных, затронутых или открытых командой, к которой относится происшедшее событие.|  
|Severity|Целочисленный|Степень серьезности исключения для события. Столбец может содержать одно из следующих значений.<br /><br /> <br /><br /> 0: успех<br /><br /> <br /><br /> 1: сведения<br /><br /> <br /><br /> 2: предупреждение<br /><br /> <br /><br /> 3: ошибка|  
|Успешно|Логическое значение|Указывает, выполнена ли команда успешно или окончилась неудачей.|  
|Ошибка|Long integer|Номер ошибки события, если это применимо.|  
|ConnectionID|Строковые значения|Идентификатор соединения, к которому относится происшедшее событие.|  
|DatabaseName|Строковые значения|Имя базы данных, к которой относится происшедшее событие.|  
|NTUserName|Строковые значения|Имя пользователя Windows, связанного с событием.|  
|NTDomainName|String|Домен пользователя Windows, связанного с событием.|  
|ClientHostName|Строковые значения|Имя компьютера, на котором выполняется клиентская программа. Данный столбец заполняется значениями, переданными клиентским приложением.|  
|ClientProcessID|Long integer|Идентификатор процесса клиентского приложения.|  
|ApplicationName|String|Имя клиентского приложения, установившего соединение с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми клиентским приложением, а не отображаемым именем программы.|  
|NTCanonicalUserName|String|Каноническое имя пользователя Windows пользователя, связанного с событием.|  
|SPID|Строковые значения|Идентификатор процесса сервера (SPID) сеанса, к которому относится происшедшее событие. Значение этого столбца непосредственно соответствует идентификатору сеанса, указанному в заголовке SOAP сообщения XMLA, к которому относится происшедшее событие.|  
|TextData|Строковые значения|Текстовые данные, связанные с событием. Содержимое этого столбца зависит от класса событий и подкласса событий.|  
|ServerName|Строковые значения|Имя экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], к которому относится происшедшее событие.|  
|RequestParameters|Строковые значения|Параметры параметризированного запроса или команды XMLA, к которой относится происшедшее событие.|  
|RequestProperties|Строковые значения|Свойства метода XMLA, к которому относится происшедшее событие.|  
  
## <a name="see-also"></a>См. также:  
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
