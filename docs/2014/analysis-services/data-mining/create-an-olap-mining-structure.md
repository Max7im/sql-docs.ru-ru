---
title: Создание структуры интеллектуального анализа данных OLAP | Документация Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 21cbdc9d-d33c-4026-b9ef-1be2bd92b3b1
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 060b2fc3a8cfcb54470d21dace787cd1ccbc025c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232434"
---
# <a name="create-an-olap-mining-structure"></a>Создание структуры интеллектуального анализа данных OLAP
  Создание модели интеллектуального анализа данных на основе куба OLAP или другого многомерного хранилища данных имеет множество преимуществ. Решение OLAP содержит огромное количество данных, которые уже хорошо организованы, очищены и правильно отформатированы. Однако сложность данных такова, что пользователи вряд ли смогут найти значительные шаблоны путем случайного перебора. Интеллектуальный анализ данных обеспечивает возможность выявления новых связей и принятия соответствующих решений.  
  
 В этом разделе содержатся сведения о создании структуры интеллектуального анализа OLAP, основанной на измерении и связанных мерах в существующем многомерном решении.  
  
 [Требования](#bkmk_Reqs)  
  
 [Обзор процесса интеллектуального анализа данных OLAP](#bkmk_Overview)  
  
 [Сценарии использования интеллектуального анализа данных в решениях OLAP](#bkmk_OLAP_Scenarios)  
  
 [Фильтры](#bkmk_Filters)  
  
 [Использование вложенных таблиц](#bkmk_Nested)  
  
 [Измерения интеллектуального анализа данных](#bkmk_DMDimension)  
  
##  <a name="bkmk_Reqs"></a> Требования к структуре и моделям интеллектуального анализа OLAP  
 При разработке модели интеллектуального анализа OLAP источник данных должен уже существовать в базе данных, которая использовалась для построения куба. Нельзя подключиться к удаленному кубу и построить объекты интеллектуального анализа данных. Объекты куба должны быть доступны внутри одного решения вместе с базой данных и создаваемой структурой интеллектуального анализа.  
  
 Если оригинальные файлы проекта отсутствуют или их изменение нежелательно, то можно выбрать в Visual Studio флажок **Импорт с сервера (многомерный режим или интеллектуальный анализ данных)** для получения копии метаданных и объектов решения. После выполнения команды можно изменить цель развертывания, источники данных и работать с объектами кубов, не затрагивая существующие объекты.  
  
 Дополнительные сведения см. в разделе [Импорт проекта интеллектуального анализа данных с помощью мастера импорта служб Analysis Services](import-a-data-mining-project-using-the-analysis-services-import-wizard.md).  
  
##  <a name="bkmk_Overview"></a> Обзор процесса интеллектуального анализа данных OLAP  
 Запустите мастер интеллектуального анализа данных. Для этого щелкните правой кнопкой мыши узел **Структуры интеллектуального анализа данных** в обозревателе решений и выберите команду  **Создать структуру интеллектуального анализа данных**. Мастер помогает выполнить следующие шаги по созданию структуры для новой структуры и модели.  
  
1.  **Выбор метода определения**. Здесь в качестве типа источника данных выберите **На основе существующего куба**.  
  
    > [!NOTE]  
    >  Куб OLAP, используемый в качестве источника данных, должен существовать внутри одной базы данных вместе со структурой интеллектуального анализа, как было описано выше. Кроме того, куб, созданный надстройкой PowerPivot для Excel, не может использоваться в качестве источника интеллектуального анализа данных.  
  
2.  **Создание структуры интеллектуального анализа данных**. Определите, что следует создавать: просто структуру или структуру с моделью интеллектуального анализа данных.  
  
     Кроме того, необходимо выбрать соответствующий алгоритм анализа данных. Советы по выбору алгоритма для определенных целей см. в статье HYPERLINK «ms-help://SQL111033/as_1devconc/html/ed1fc83b-b98c-437e-bf53-4ff001b92d64.htm» «Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)».  
  
3.  **Выбор измерения исходного куба**. Этот шаг соответствует выбору источника данных. Нужно выбрать одно измерение, содержащее наиболее важные данные, используемые для обучения модели. Данные можно будет добавить и позже или отфильтровать измерение.  
  
4.  **Выбор ключа варианта**. В рамках выбранного измерения найдите атрибут (столбец), который будет служить уникальным идентификатором данных варианта.  
  
     Как правило, столбец выбирается автоматически, но можно выбрать и другой столбец, если есть несколько ключей.  
  
5.  **Выбор столбцов уровня варианта**. Здесь необходимо найти атрибуты из выбранного измерения и связанные меры, релевантные анализу. Этот шаг соответствует выбору столбцов из таблицы.  
  
     Мастер автоматически включает для просмотра и выбора меры, созданные с помощью атрибутов из выбранного измерения.  
  
     Например, если куб содержит меру, которая вычисляет фрахт на основе географического расположения клиента, то при выборе измерения «Клиент» в качестве основного источника данных для моделирования мера будет предложена в качества кандидата на добавление в модель. Будьте осторожны, добавляя слишком большое число мер, которые уже напрямую связаны с атрибутами, так как между столбцами уже существует одна явная связь. Сила ожидаемой корреляции может скрыть другие связи, которые могли быть выявлены в других случаях.  
  
6.  **Использование столбцов для модели**. Для каждого атрибута или меры, добавленных в структуру, следует указать, будет ли атрибут использоваться для предсказания или в качестве входных данных. Если этот параметр не будет указан, то данные будут обработаны, но не будут учтены при анализе. Однако они будут доступны в качестве фоновых данных для последующей детализации.  
  
7.  **Добавить вложенные таблицы**. Щелкните, чтобы добавить связанные таблицы. В диалоговом окне **Выбор измерения группы мер** можно выбрать одно из нескольких измерений, связанных с текущим измерением.  
  
     Далее, в диалоговом окне **Выбор ключа вложенной таблицы** определите, каким образом новое измерение связано с измерением, содержащим данные варианта.  
  
     В диалоговом окне **Выбор столбцов вложенной таблицы** выберите атрибуты и меры из нового измерения, которое будет использовано в анализе. Кроме того, нужно указать, будет ли вложенный атрибут использован для прогнозирования.  
  
     После добавления всех вложенных атрибутов, вернитесь на страницу **Указать использование столбца модели интеллектуального анализа**и нажмите кнопку **Далее**.  
  
8.  **Определение содержимого и типа данных столбцов**. К этому моменту были добавлены все данные, которые будут использованы в анализе, остается указать *тип данных* и *тип содержимого* для каждого атрибута.  
  
     В модели OLAP нельзя автоматически выявлять типы данных, поскольку тип данных уже определен многомерным решением и не может быть изменен. Ключи также определяются автоматически. Дополнительные сведения см. в разделе [Типы данных (интеллектуальный анализ данных)](data-types-data-mining.md).  
  
     *Тип содержимого* , выбираемый для каждого столбца, который используется в модели, сообщает алгоритму, каким образом следует обрабатывать данные. Дополнительные сведения см. в разделе [Типы содержимого (интеллектуальный анализ данных)](content-types-data-mining.md).  
  
9. **Срез исходного куба**. Здесь можно определить фильтры в кубе, чтобы выбрать только подмножество данных и обучить более целевые модели.  
  
     Куб можно отфильтровать, выбрав измерение, уровень иерархии, содержащей используемые критерии, и введя условие, которое будет использоваться в качестве фильтра.  
  
10. **Создание проверочного набора**. На этой странице указывается, какой объем данных следует выделить для использования в тестировании модели. Если данные будут поддерживать несколько моделей, то разумно создать набор контрольных данных, чтобы тестировать все модели по одним и тем же данным.  
  
     Дополнительные сведения см. в разделе [Тестирование и проверка (интеллектуальный анализ данных)](testing-and-validation-data-mining.md).  
  
11. **Завершение работы мастера**. На этой странице задается имя новой структуры интеллектуального анализа данных и имя связанной модели интеллектуального анализа данных, а затем структура и модель сохраняются.  
  
     На этой странице можно задать следующие параметры.  
  
    -   **Разрешить детализацию**  
  
    -   **Создать измерение модели интеллектуального анализа данных**  
  
    -   **Создать куб с использованием измерения модели интеллектуального анализа данных**  
  
     Дополнительные сведения об этих параметрах см. далее в этом разделе [Общие сведения об измерения интеллектуального анализа и детализации](#bkmk_DMDimension).  
  
 На данном этапе структура интеллектуального анализа данных и ее модель представляют собой лишь метаданные. Для получения результатов необходимо обработать структуру и модель.  
  
##  <a name="bkmk_OLAP_Scenarios"></a> Сценарии использования интеллектуального анализа данных с данными OLAP  
 Кубы OLAP часто содержат настолько большое количество элементов и измерений, что иногда бывает трудно понять, откуда следует начинать интеллектуальный анализ данных. Чтобы определить закономерности в организации данных куба, обычно определяется одно интересующее измерение, и затем начинают исследоваться связанные с ним закономерности. В следующей таблице содержится список нескольких обычных задач интеллектуального анализа данных OLAP, описывающих образцы сценариев, в которых можно применять эти задачи, и определяющих алгоритм интеллектуального анализа данных, используемый в каждой задаче.  
  
|Задача|Образец сценария|Алгоритм|  
|----------|---------------------|---------------|  
|Группировка элементов в кластеры|Разделение на сегменты измерения потребителей на основе свойств элементов потребителей, продукции, покупаемой потребителями, и суммы денег, которую тратят потребители.|[!INCLUDE[msCoName](../../includes/msconame-md.md)] )|  
|Поиск требуемых или нестандартных элементов|Определение требуемых или нестандартных запасов в измерении запасов на основе продаж, прибыли, местоположения и размера запасов.|[!INCLUDE[msCoName](../../includes/msconame-md.md)] )|  
|Поиск требуемых или нестандартных ячеек|Определение продаж магазина, отличающихся от обычных трендов.|[!INCLUDE[msCoName](../../includes/msconame-md.md)] )|  
|Поиск корреляций|Идентифицируйте факторы, связанные с простоем сервера, включая регион, тип машины, ОС и дату покупки.|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Упрощенный алгоритм Байеса|  
  
##  <a name="bkmk_Filters"></a> Создание срезов куба и. модели фильтрации  
 Создание среза куба во время построения модели похоже на создание фильтра для реляционной модели интеллектуального анализа данных. В реляционной модели фильтр для источника данных определяется в качестве предложения WHERE в инструкции SQL. В кубе нужно выбрать редактор для создания инструкции фильтра с помощью многомерных выражений.  
  
 Например, куб может содержать сведения о покупках продукции по всему миру, однако для маркетинговой кампании нужно создать модель на основе анализа клиентов-женщин в возрасте старше 30 лет, проживающих в Великобритании.  
  
 Для этого случая нужно создать два фильтра.  
  
-   Для первого фильтра следует выбрать измерение "География", иерархию для "Региона" и затем в списке **Выражение фильтра** выбрать из возможных значений вариант "Великобритания".  
  
-   Для второго фильтра следует выбрать измерение "Клиент", атрибут "Пол" и "Женщины" из списка значений атрибутов.  
  
 После создания структуры интеллектуального анализа данных можно изменять как определение данных куба, так и критерии фильтра. Дополнительные сведения см. в статье [Filter the Source Cube for a Mining Structure](../filter-the-source-cube-for-a-mining-structure.md).  
  
 Как на вкладке **Структура интеллектуального анализа данных** , так и на вкладке **Модель интеллектуального анализа данных** можно добавить фильтр к существующей структуре интеллектуального анализа, нажав кнопку **Определить срез куба**. Диалоговое окно **Срез куба** позволяет построить действительное многомерное выражение фильтра, выбрав значение из раскрывающегося списка.  
  
> [!WARNING]  
>  Обратите внимание, что интерфейс для конструирования и просмотра кубов в среде [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]был изменен. Дополнительные сведения см. в разделе [Просмотр данных и метаданных в кубе](../multidimensional-models/browse-data-and-metadata-in-cube.md).  
  
 Для куба можно добавить столько фильтров, сколько потребуется для получения данных, необходимых для модели интеллектуального анализа данных. Также можно определить срезы на конкретных срезах куба. Например, если в структуре содержатся две вложенные таблицы, основанные на продуктах, то можно ограничить одну таблицу мартом 2004 года, а другую — апрелем того же года. В результате получится модель, которую затем можно использовать для прогнозирования объема покупок в апреле на основании покупок, совершенных в марте.  
  
##  <a name="bkmk_Nested"></a> Использование вложенных таблиц в модели интеллектуального анализа данных OLAP  
 Если для построения модели на основе данных куба используется мастер интеллектуального анализа данных, то можно добавить таблицы, указав имена связанных измерений и сопоставив атрибуты или меры для добавления в модель.  
  
 Если, например, основным измерением для данных варианта является "Клиент", то можно добавить в качестве связанного измерения измерение "Продукты", поскольку есть вероятность, что один клиент мог заказывать разные продукты в течение какого-то времени, а куб уже связывает каждого клиента с некоторым множеством продуктов через таблицы фактических заказов.  
  
 Вложенные таблицы добавляются на странице мастера **Использование столбцов модели интеллектуального анализа данных** путем нажатия кнопки **Добавить вложенные таблицы**. Открывается диалоговое окно, где можно выбрать связанное измерение, а также необходимые меры. Вариант и вложенные измерения должны быть связаны внешним ключом, при этом меры должны использовать один из атрибутов, уже включенных в вариант или вложенные таблицы. К сожалению, эти ограничения не позволяют реально сузить область выбора, поэтому будьте очень осторожны при выборе атрибутов, которые могут оказаться полезными для моделирования.  
  
 Для каждого атрибута или меры, добавляемых во вложенную таблицу, следует указать, будет ли использоваться вложенный атрибут для прогнозирования, выбрав параметр **Прогнозируемый** или **Входные данные** в диалоговом окне **Выбор столбцов вложенной таблицы** . Если один из параметров не будет указан, то данные будут добавлены в структуру интеллектуального анализа, но не будут использованы для анализа.  
  
 Для каждого атрибута и меры нужно также указать, будет ли атрибут дискретным, дискретизированным или непрерывным. Мастер предварительно выбирает значение по умолчанию на основе типа данных атрибута, однако может потребоваться их изменение, в зависимости от требований алгоритма. Если выбрать тип содержимого, не совместимого с алгоритмом (например, при использовании непрерывного числового типа с упрощенной моделью Байеса), то сообщение об ошибке будет выдано только при попытке обработки модели.  
  
 После задания этих параметров мастер добавит вложенную таблицу в таблицу вариантов. Именем по умолчанию для вложенной таблицы является имя вложенного измерения, но можно переименовать вложенную таблицу и ее столбцы. Для добавления нескольких вложенных таблиц в структуру интеллектуального анализа данных следует повторить эту процедуру.  
  
 Возможность использования данных вложенной таблицы — это очень мощная функция интеллектуального анализа данных SQL Server, при этом в кубе возможности использования связанных подмножеств данных практически не ограничены.  
  
##  <a name="bkmk_DMDimension"></a> Общие сведения об измерения интеллектуального анализа и детализации  
 Параметр **Разрешить детализацию**позволяет отправлять запросы к данным базового куба во время просмотра модели. Эти данные не содержатся в новом измерении интеллектуального анализа данных, однако база данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может использовать привязки к данным для получения сведений из исходного куба.  
  
 Параметр **Создание измерения модели интеллектуального анализа данных**позволяет сформировать новое измерение внутри существующего куба, содержащего шаблоны, выявленные алгоритмом. Иерархия внутри нового измерения определяется в основном по типу модели. Например, представление модели кластеризации является в целом плоским, при этом узел «Все» находится наверху иерархии, а все кластеры — на следующем уровне. В отличие от этого измерение, создаваемое для модели дерева решений, может иметь очень глубокую иерархию, представляющую ответвления дерева.  
  
 Параметр **Создание куба с помощью измерения модели интеллектуального анализа данных**позволяет экспортировать новое измерение интеллектуального анализа данных в новый куб. Любые объекты, необходимые для детализации в измерении интеллектуального анализа данных, включаются автоматически.  
  
> [!WARNING]  
>  Создание измерений интеллектуального анализа данных поддерживается только следующими типами моделей: модели на основе алгоритма кластеризации (Майкрософт), алгоритм деревьев принятия решений (Майкрософт) или алгоритм взаимосвязей (Майкрософт).  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Столбцы структуры интеллектуального анализа данных](mining-structure-columns.md)   
 [Столбцы модели интеллектуального анализа данных](mining-model-columns.md)   
 [Свойства модели интеллектуального анализа данных](mining-model-properties.md)   
 [Свойства структур интеллектуального анализа данных и их столбцов](properties-for-mining-structure-and-structure-columns.md)  
  
  