---
title: Срез исходного куба (мастер интеллектуального анализа данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.slicesourcecube.f1
ms.assetid: 16485608-d3b9-49ee-8baa-948038cdd7ec
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6024c1e58b48c8661eaa15a0ea85c464103403ae
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37326554"
---
# <a name="slice-source-cube-data-mining-wizard"></a>Срез исходного куба (мастер интеллектуального анализа данных)
  Можно использовать диалоговое окно **Срез исходного куба** для ограничения данных, используемых при обучении модели. Обычно куб содержит данные, относящиеся к разным измерениям и атрибутам, такие как все магазины, все регионы и все товары. Не имеет смысла обучать модель на неограниченных сочетаниях атрибутов, поэтому следует использовать это диалоговое окно в целях выбора конкретного набора для использования в обучении модели.  
  
 Например, в кубе AdventureWorks можно применить разделение по определенной линии товаров, региону и году для получения доступа к части данных.  
  
 Если вы не знакомы со срезами и кубами, рекомендуется просмотреть следующие статьи.  
  
-   [Задайте свойства среза секции &#40;служб Analysis Services&#41;](multidimensional-models/set-the-partition-slice-property-analysis-services.md)  
  
-   [Создание и управление ими локальной секции &#40;служб Analysis Services&#41;](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
> [!NOTE]  
>  Обратите внимание, что динамические функции многомерных выражений (такие как [Generate (многомерное выражение)](/sql/mdx/generate-mdx) или [Except (многомерное выражение)](/sql/mdx/except-mdx-function)) не поддерживаются в свойстве Slice для секций. Необходимо определить срез с помощью явных кортежей или ссылок на элементы.  
>   
>  Например, вместо использования [: &#40;диапазон&#41; &#40;многомерных Выражений&#41; ](/sql/mdx/range-mdx) для определения диапазона, потребуется перечислить каждый элемент по конкретным годам.  
>   
>  Если необходимо определить сложный срез, рекомендуется идентифицировать кортежи в срезе с помощью скрипта изменения XMLA. Затем можно использовать средство командной строки ascmd или SSIS [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) для запуска скрипта и создания указанного набора элементов непосредственно перед секционированием.  
  
 **Дополнительные сведения:** [Мастер интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Создание реляционной структуры интеллектуального анализа данных](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Параметры  
 **Dimension**  
 Выберите измерение, которое необходимо разделить.  
  
 **Hierarchy**  
 Выберите иерархию, которую необходимо разделить. Можно выбрать любой уровень иерархии, но атрибуты, используемые в модели, будут представлены только на выбранном уровне.  
  
 Например, если выбрать иерархию Geography и выбрать в качестве уровня Country, то нельзя создать модель, в которой используется City в качестве атрибута. И наоборот, если выбран City как уровень иерархии, по которому производится срез, то нельзя создать модель интеллектуального анализа данных на основе Country.  
  
 **Оператор**  
 Выберите оператор для использования при создании выражения среза.  
  
 Например, если в качестве иерархии выбрана Geography, то можно выбрать оператор = и ввести «Европа» в качестве фильтра, чтобы получить доступ к данным куба только для Европы.  
  
 **Критерий фильтра**  
 Введите выражение, используемое в качестве критерия фильтрации куба в выбранном измерении.  
  
 **Параметры**  
 Этот параметр не используется для моделей интеллектуального анализа данных.  
  
## <a name="see-also"></a>См. также  
 [Завершение работы мастера &#40;мастер интеллектуального анализа данных&#41;](completing-the-wizard-data-mining-wizard.md)   
 [Справка F1 мастера интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Укажите использование столбца модели интеллектуального &#40;мастер интеллектуального анализа данных&#41;](specify-mining-model-column-usage-data-mining-wizard.md)  
  
  
