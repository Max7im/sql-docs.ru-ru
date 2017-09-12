---
title: "Обновление данных (надстройка MDS для Excel) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58dbe99a-288d-4f1c-9cd5-704d6836c945
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6159c4b30b0cd2c4f718efaddc7c915f1fb43dfd
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="refreshing-data-mds-add-in-for-excel"></a>Обновление данных (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], обновление данных, когда требуется получить последние данные из репозитория MDS без открытия нового листа. Обновить можно либо все, либо только выделенные ячейки. Эта возможность может оказаться полезной при вставке столбцов с пользовательскими формулами или других данных, которые не управляются MDS и которые нужно сохранить.  
  
## <a name="when-you-can-refresh-mds-managed-data"></a>Когда можно обновлять данные, управляемые MDS  
 Можно обновлять на активном листе данные, управляемые MDS, если активный лист уже содержит данные, управляемые MDS. Если на листе изменялись значения атрибутов или добавлялись новые элементы, то необходимо опубликовать изменения, прежде чем появится возможность обновления.  
  
## <a name="refreshing-a-selection"></a>Обновление выделенных ячеек  
 Обновить можно либо все, либо только выделенные ячейки. Выбранные ячейки должны быть смежными. Если выделена область из непрерывных ячеек, будут обновлены все ячейки, управляемые службами MDS, в этом множестве, при этом будут отображены значения, которые хранятся на сервере в данное время. Неизмененные строки и столбцы, которые не управляются MDS, не затрагиваются.  
  
## <a name="what-happens-when-you-refresh-mds-managed-data"></a>Что происходит при обновлении данных, управляемых MDS  
 Что именно происходит с данными, управляемыми MDS, на листе при обновлении данных в [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]зависит от того, какие изменения произошли в репозитории MDS с тех пор, когда вы в последний раз загружали эти данные.  
  
-   Если в репозиторий были добавлены новые элементы, то они добавляются в конец листа и подсвечиваются зеленым цветом.  
  
-   Если из репозитория удалены элементы, то они удалятся и с листа.  
  
-   Если в репозитории MDS изменились значения атрибутов, то значение на листе обновляется значением из репозитория MDS. Цвет ячейки не изменяется.  
  
> [!WARNING]  
>  -   Если на активном листе существуют неуправляемые данные в строках ниже строк с данными, управляемыми MDS, то эти данные могут быть перезаписаны. Это происходит при обновлении листа и добавлении новых строк, управляемых MDS, которые перекрывают неуправляемые данные.  
> -   Комментарии в ячейках, управляемых MDS, при обновлении удаляются.  
  
## <a name="how-to-refresh-mds-managed-data"></a>Как обновить данные, управляемые MDS  
 В группе ленты **Подключение и загрузка** под кнопкой **Обновить** есть две команды: **Обновить все** и **Обновить выделенные**. По умолчанию эта кнопка на ленте выполняет действие **Обновить все**. Чтобы обновить весь лист значениями с сервера, нажмите кнопку **Обновить** или выберите команду **Обновить все** . Чтобы обновить только некоторые ячейки листа, выделите их (выделенные ячейки должны быть смежными) и выберите команду **Обновить выделенные** .  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Установите соединение с базой данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Соединение с репозиторием MDS (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|Загрузка данных MDS в Excel.|[Export Data to Excel from Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Соединения (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
-   [Обзор экспорта данных в Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [Надстройка Master Data Services для Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
  