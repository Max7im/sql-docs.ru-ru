---
title: Скрытие или закрепление столбцов | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e588e16549a609fe15f0f7d7eaf89a010a5bde2c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="hide-or-freeze-columns"></a>Скрытие или закрепление столбцов 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Если в конструкторе моделей некоторые столбцы не нужно отображать в таблице, то их можно временно скрыть. Скрытый столбец освобождает пространство на экране, позволяя добавлять новые столбцы или работать только с необходимыми столбцами данных. Скрыть или отобразить столбцы можно через меню **Столбец** в конструкторе моделей или через меню заголовка столбца, которое вызывается нажатием правой кнопкой мыши. Чтобы область модели оставалась видимой при переходе в другую область при прокрутке, можно закрепить определенные столбцы в одной области.  
  
> [!IMPORTANT]  
>  Возможность скрытия столбцов предусмотрена не для защиты данных, а только для упрощения и уменьшения списка столбцов, видимых в конструкторе моделей или отчетах. Для защиты данных можно задать роли безопасности. Роли дают возможность сделать метаданные и данные видимыми только для тех объектов, которые определены в роли. Дополнительные сведения см. в разделе [ролей](../../analysis-services/tabular-models/roles-ssas-tabular.md).  
  
 Можно выбрать скрытие столбца во время работы в конструкторе моделей или в отчетах. Если скрыть все столбцы, то вся таблица в конструкторе моделей будет выглядеть пустой.  
  
> [!NOTE]  
>  Если необходимо скрыть много столбцов, то вместо этого можно создать перспективу. Перспектива — это пользовательское представление данных, упрощающее работу с подмножествами взаимосвязанных данных. Дополнительные сведения см. в разделе [Создание перспектив и управление ими](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)  
  
### <a name="to-hide-an-individual-column"></a>Скрытие отдельного столбца  
  
1.  В конструкторе моделей выберите таблицу со столбцом, который необходимо скрыть.  
  
2.  Щелкните столбец правой кнопкой мыши, выберите команду **Скрыть столбцы**, а затем выберите **Из конструктора и отчетов**, **Из отчетов**или **Из конструктора**.  
  
### <a name="to-hide-multiple-columns"></a>Скрытие нескольких столбцов  
  
1.  В конструкторе моделей выберите таблицу со столбцом, который необходимо скрыть.  
  
2.  В меню **Столбец** выберите пункт **Скрыть и показать**.  
  
3.  В диалоговом окне **Скрытие и отображение столбцов** найдите столбцы, которые нужно скрыть, и снимите для них флажки **В конструкторе** , **В отчетах**либо оба флажка.  
  
4.  Нажмите кнопку **ОК**.  
  
### <a name="to-freeze-columns"></a>Закрепление столбцов  
  
1.  В конструкторе моделей выберите таблицу со столбцом, который нужно закрепить.  
  
2.  Выберите один или несколько столбцов для закрепления.  
  
3.  В меню **Столбцы** выберите пункт **Закрепить**.  
  
    > [!NOTE]  
    >  При закреплении столбцов они перемещаются влево или в начало таблицы в конструкторе. При освобождении столбца он не возвращается в исходное местоположение.  
  
## <a name="see-also"></a>См. также  
 [Таблицы и столбцы](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)   
 [Перспективы](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
