---
title: Меры и группы мер | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- measure groups [Analysis Services]
- measures [Analysis Services], about measures
- OLAP objects [Analysis Services], measures
- aggregate functions [Analysis Services]
- granularity
- measure groups [Analysis Services], about measure groups
- measures [Analysis Services]
- aggregations [Analysis Services], measures
- fact tables [Analysis Services]
ms.assetid: 4f0122f9-c3a5-4172-ada3-5bc5f7b1cc9a
caps.latest.revision: 42
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ba5a5c5b9ebf6bf7dcbf3b5340db941c7f662cf7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255636"
---
# <a name="measures-and-measure-groups"></a>Меры и их группы
  Куб содержит *меры* в *группах мер*, бизнес-логику, а также коллекцию измерений, дающих контекст для вычисления числовых данных, которые предоставляет мера. Меры и группы мер являются неотъемлемой частью куба. Куб не может существовать без них.  
  
 В этом разделе описываются [Measures](#bkmk_measure) и [Measure Groups](#bkmk_mg). Здесь также приведена следующая таблица с ссылками на инструкции по созданию и настройке мер и групп мер.  
  
|**Ссылка**|**Описание**|  
|--------------|---------------------|  
|[Создание мер и групп мер в многомерных моделях](create-measures-and-measure-groups-in-multidimensional-models.md)|Выберите один из способов создания мер и групп мер.|  
|[Настройка свойств мер](configure-measure-properties.md)|Если мастер кубов используется для запуска куба, возможно, потребуется изменить метод агрегирования, применить формат данных, настроить видимость для меры в клиентских приложениях или добавить выражение меры для работы с данными, прежде чем значения объединятся.|  
|[Настройка свойств группы мер](configure-measure-group-properties.md)|В многомерной модели группа мер соответствует таблице фактов в хранилище данных источника. Свойства в группе мер позволяют задавать поведение кэширования, хранения и директивы обработки, которые работают вместе на уровне группы мер. Конфигурация раздела частично определяется свойствами, заданными для объектов группы мер.|  
|[Использование агрегатных функций](use-aggregate-functions.md)|Понимание методов агрегирования, которые могут быть присвоены мере.|  
|[Определение полуаддитивного режима](define-semiadditive-behavior.md)|Полуаддитивный режим ссылается на агрегаты, которые являются допустимыми для одних измерений, но не других. Распространенным примером является баланс банковского счета. Может потребоваться выполнить агрегирование баланса по клиентам и областям, но не по времени. Например, нет смысла складывать баланс одного и того же счета за несколько дней подряд. Чтобы определить полуаддитивный режим, используйте мастер добавления бизнес-аналитики.|  
|[Связанные группы мер](linked-measure-groups.md)|Используйте существующую группу мер в других кубах той же базы данных или в других базах данных служб Analysis Services.|  
  
##  <a name="bkmk_measure"></a> Measures  
 Мера представляет собой столбец, содержащий количественно исчислимые данные, обычно числовые, для которых может быть выполнена статистическая обработка. Меры представляют некоторые аспекты организационных действий, выраженных в денежном (доход, прибыль или затраты) или числовом (уровень запасов, число сотрудников, клиентов или заказов) выражении, или как более сложные вычисления, включающие в себя бизнес-логику.  
  
 Каждый куб должен содержать по крайней мере одну меру, но большинство кубов имеют несколько мер, иногда сотни. Структурно меры часто сопоставляются с исходным столбцом в таблице фактов, где столбец предоставляет значения, используемые для наполнения меры. Кроме того, можно также определить меру с помощью многомерных выражений.  
  
 Меры являются контекстно-зависимыми и работают с числовыми данными в контексте, определяемым любыми включенными в запрос элементами. Например, мера, которая вычисляет **Товарооборот** будет поддерживаться `Sum` оператор и будет суммировать объемы продаж для каждого элемента измерения, включенного в запрос. Указывает ли запрос отдельные продукты, сводится ли к категории или делает срез по времени или местоположению, мера должна выполнять операции, допустимые для измерений, включенных в запрос.  
  
 В этом примере **товарооборот посредников** объединяется с различными уровнями иерархии **территории сбыта** .  
  
 ![Сводная таблица с мерами и измерениями, вызванной](../media/ssas-keyconcepts-pivot1-measures-dimensions.png "Сводная таблица с мерами и измерениями, вызванной")  
  
 Меры выдают правильные результаты, когда таблица фактов, содержащая числовые исходные данные, также содержит ссылки на таблицы измерений, которые используются в запросе. На примере товарооборота посредников, если каждая строка, хранящая объем продаж, содержит указатель на таблицу продуктов, таблицу дат или таблицу территории сбыта, то запросы, которые включают элементы из этих измерений, будут обработаны правильно.  
  
 Что произойдет, если мера не связана с измерениями, используемыми в запросе? Как правило, службы Analysis Services отображают меру по умолчанию, и значение будет одинаковым для всех элементов. В этом примере **продажи через Интернет**, которые состоят из заказов, напрямую размещенных клиентами через интернет-каталог, не имеют отношения к торговой организации.  
  
 ![Сводная таблица, показывающая повторяющиеся значения мер](../media/ssas-unrelatedmeasure.PNG "Сводная таблица, показывающая повторяющиеся значения мер")  
  
 Чтобы свести к минимуму вероятность возникновения такого поведения в клиентском приложении, можно создать несколько кубов или перспектив в одной базе данных, при этом каждый куб или перспектива должны содержать только связанные объекты. Связи, которые необходимо проверить, находятся между группой мер (сопоставляется с таблицей фактов) и измерениями.  
  
##  <a name="bkmk_mg"></a> Measure Groups  
 Меры в кубе группируются по базовым таблицам фактов в группы мер. Группы мер используются для связи измерений с мерами. Они применяются также для мер, которые в качестве статистической обработки производят подсчет числа различных объектов, — помещение каждой из таких мер в отдельную группу позволяет оптимизировать процесс статистической обработки.  
  
 Простой объект <xref:Microsoft.AnalysisServices.MeasureGroup> состоит из основной информации: имя группы, режим хранения и режим обработки. Он также содержит составные части: меры, измерения и разделы, которые составляют группу мер.  
  
## <a name="see-also"></a>См. также  
 [Кубы в многомерных моделях](cubes-in-multidimensional-models.md)   
 [Создание мер и групп мер в многомерных моделях](create-measures-and-measure-groups-in-multidimensional-models.md)  
  
  