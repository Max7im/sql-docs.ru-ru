---
title: "Экспорт данных в Excel из служб Master Data Services | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
caps.latest.revision: 16
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7d2303d6a02bbed69b87e45120ee3de51f0278be
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="export-data-to-excel-from-master-data-services"></a>Export Data to Excel from Master Data Services
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]для работы с данными необходимо сначала экспортировать их из репозитория MDS.  
  
 Если перед загрузкой набора данных нужно отфильтровать его, см. раздел [Фильтрация данных перед их экспортом (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
### <a name="to-export-data-from-mds-into-excel"></a>Экспорт данных из MDS в Excel  
  
1.  Откройте Excel и на вкладке **Основные данные** установите соединение с репозиторием MDS. Дополнительные сведения см. в разделе [Соединение с репозиторием MDS (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  На панели **Обозреватель основных данных** выберите модель и версию. Заполняется список сущностей.  
  
    -   Если панель **Обозреватель основных данных** не видна, в группе **Соединение и загрузка** нажмите **Показать обозреватель**.  
  
    -   Если панель **Обозреватель основных данных** отключена, то причина этого заключается в том, что существующий лист уже содержит данные, управляемые MDS. Чтобы включить эту панель, откройте новый лист.  
  
3.  В области **Обозреватель основных данных** в списке сущностей дважды щелкните сущность, которую нужно загрузить.  
  
    > [!NOTE]  
    >  -   В Excel загружается только первый миллион элементов. Чтобы отфильтровать список перед загрузкой, на ленте в группе **Подключение и загрузка** нажмите кнопку **Фильтр**.  
    > -   В столбцах, которые являются ограниченными списками (атрибутами на основе домена), по умолчанию загружаются только первые 25 000 значений. Это число можно изменить в свойстве MaximumDbaEntitySize в файле excelusersettings.config, расположенном на компьютере, на котором установлена программа Excel. Этот файл расположен в каталоге C:\Users\\<пользователь\>\AppData\Local\Microsoft\Microsoft SQL Server\130\MasterDataServices\\.  
    >   
    >      Если количество значений для атрибута на основе домена превышает настройку свойства MaximumDbEntitySize, список значений не загружается.  
  
    > [!NOTE]  
    >  Если при загрузке разделенных текстом данных с помощью надстройки для Microsoft Excel в 32-разрядную версию Excel свойствам **Число ячеек для загрузки** и **Число ячеек для публикации** присвоено максимальное значение 1000, возникнет ошибка нехватки памяти. Для использования максимальных значений свойств **Число ячеек для загрузки** и **Число ячеек для публикации**необходимо использовать 64-разрядную версию Excel.  
  
## <a name="next-steps"></a>Следующие шаги  
 [Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор экспорта данных в Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Диалоговое окно «Фильтр» &#40; Надстройка MDS для Excel &#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Обзор импорта данных из Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  