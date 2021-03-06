---
title: Объединение данных с помощью преобразования "Объединить все" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- merging datasets [Integration Services]
- merging inputs [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 78304403-a81c-4101-b87e-ec80ddfdac98
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5b113a2ca169ebc1f49a522d51800b09b9a30343
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221814"
---
# <a name="merge-data-by-using-the-union-all-transformation"></a>Выполнение слияния данных с помощью преобразования «Объединить все»
  Чтобы добавить и настроить преобразование «Объединить все», в пакет уже должны быть включены хотя бы одна задача потока данных и два источника данных.  
  
 Преобразование «Объединить все» объединяет несколько входов. Первый вход, связываемый с преобразованием, будет ссылочным, а все последующие — дополнительными. Выход содержит столбцы ссылочного входа.  
  
### <a name="to-combine-inputs-in-a-data-flow"></a>Комбинирование входов в потоке данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]дважды щелкните пакет в обозревателе решений, чтобы открыть его в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , а затем выберите вкладку **Поток данных** .  
  
2.  Из **области элементов**перетащите преобразование «Объединить все» в область конструктора на вкладке **Поток данных** .  
  
3.  Подключите преобразование «Объединить все» к потоку данных, перетащив соединитель из источника данных или предыдущего преобразования в преобразование «Объединить все».  
  
4.  Дважды щелкните преобразование «Объединить все».  
  
5.  В **Редакторе преобразования «Объединить все»** сопоставьте столбец входа со столбцом в списке **Имя выходного столбца** , щелкнув строку и выбрав столбец в списке входов. Выберите **\<игнорировать>** в списке ввода, чтобы не сопоставлять столбец.  
  
    > [!NOTE]  
    >  Сопоставление двух столбцов требует, чтобы метаданные этих столбцов совпадали.  
  
    > [!NOTE]  
    >  Столбцы дополнительного входа, не сопоставленные со ссылочными столбцами, получают на выходе значения NULL.  
  
6.  При необходимости можно изменить имена столбцов в списке **Имя выходного столбца** .  
  
7.  Повторите шаги 5 и 6 для каждого столбца каждого входа.  
  
8.  Нажмите кнопку **ОК**.  
  
9. Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также  
 [UNION All Transformation](union-all-transformation.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)   
 [Пути служб Integration Services](../integration-services-paths.md)   
 [Задача потока данных] ((.. /.. /Control-Flow/Data-Flow-Task.MD)  
  
  
