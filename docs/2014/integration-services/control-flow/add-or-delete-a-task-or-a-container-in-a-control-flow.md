---
title: Добавление задачи или контейнера в поток управления или удаление их из него | Документы Майкрософт
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
- containers [Integration Services], adding
- adding tasks
- adding containers
- tasks [Integration Services], adding
ms.assetid: 653084c6-87a3-45d5-b458-914ecf24d56a
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1546a8bf4d0da741d63cb8bd8d4b2f849cf921d2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256940"
---
# <a name="add-or-delete-a-task-or-a-container-in-a-control-flow"></a>Добавление задачи или контейнера в поток управления или удалить их из него
  При работе в конструкторе потока управления окно «Область элементов» конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] содержит задачи, которые службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляют для построения потока управления в пакете. Дополнительные сведения об области элементов см. в разделе [SSIS Toolbox](../ssis-toolbox.md).  
  
 Пакет может содержать несколько экземпляров одной задачи. Каждый экземпляр задачи в пакете уникально идентифицируется, следовательно, можно настроить каждый экземпляр независимо от других.  
  
 При удалении задачи, элементы управления очередностью, которые соединяли задачу с другими задачами и контейнерами потока управления, также удаляются.  
  
 Следующие процедуры описывают способы добавления или удаления задачи или контейнера в потоке управления пакета.  
  
### <a name="to-add-a-task-or-a-container-to-a-control-flow"></a>Добавление задачи или контейнера к потоку управления  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток управления** .  
  
4.  Чтобы открыть **Область элементов**, выберите пункт **Область элементов** в меню **Вид** .  
  
5.  Раскройте **Элементы потока управления** и **Задачи обслуживания**.  
  
6.  Перетащите задачи и контейнеры из **области элементов** в область конструктора на вкладке **Поток управления** .  
  
7.  Подключите задачу или контейнер в рамках потока управления пакетами перетаскиванием его соединителя на другой компонент в потоке управления.  
  
8.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
### <a name="to-delete-a-task-or-a-container-from-a-control-flow"></a>Удаление задачи или контейнера из потока управления  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений. Выполните одно из следующих действий.  
  
    -   Перейдите на вкладку **Поток управления** , щелкните правой кнопкой мыши задачу или пакет, которые необходимо удалить, и затем выберите пункт **Удалить**.  
  
    -   Откройте **обозреватель пакетов**. В папке **Исполняемые объекты** щелкните правой кнопкой мыши задачу или контейнер, которые необходимо удалить, затем выберите пункт **Удалить**.  
  
3.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также  
 [Задачи служб Integration Services](integration-services-tasks.md)   
 [Контейнеры служб Integration Services](integration-services-containers.md)   
 [Поток управления](control-flow.md)  
  
  
