---
title: 'Задача 4: Экспорт результатов действия в файл Excel сопоставления | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 13fcd1b697be6ad7aeebd933da1059955dc0649f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37179003"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a>Задача 4. Экспорт результатов действия сопоставления в файл Excel
  В этой задаче вы экспортируете результаты операции сопоставления в файл Excel.  
  
1.  В **Экспорт** выберите **файл Excel** для **конечный тип**.  
  
2.  Выберите **результаты выживания** параметр. В процессе сохранения службы DQS определяют выжившую запись для каждого кластера, на основе **правило выживания** вы выбрали.  
  
3.  Нажмите кнопку **Обзор** и перейдите к папке, где вы хотите сохранить выходной файл.  
  
4.  Тип **Cleansed and Matched Suppliers.xls** имя и нажмите кнопку **откройте**.  
  
5.  Убедитесь, что **Сводная запись** выбран для **правило выживания**. Если вы выбрали этот параметр, сводная запись для каждого кластера используется для вывода из кластера. Другие параметры для правила сохранения перечислены ниже.  
  
    1.  **Наиболее полная запись:** Выжившей записью считается запись с большим количеством заполненных полей.  
  
    2.  **Самая длинная запись:** Выжившей записью считается запись с наибольшим количеством терминов в исходных полях.  
  
    3.  **Наиболее полная и самая длинная запись:** Выжившую запись считается запись с наибольшим количеством заполненных полей, а также имеет максимальным количеством терминов в каждом поле.  
  
     ![Экспорт результатов со страницы совпадения](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "Экспорт результатов со страницы совпадения")  
  
6.  Нажмите кнопку **Экспорт** для экспорта результатов в файл Excel.  
  
7.  Нажмите кнопку **закрыть** закрыть **Экспорт сопоставления** диалоговое окно.  
  
8.  Нажмите кнопку **Готово** для завершения операции сопоставления.  
  
9. Откройте **Cleansed and Matched Suppliers.xlsx** файл и убедитесь, что вы не видите никаких повторений (SupplierID).  
  
 Вы получили данные поставщика, которые были очищены и сопоставлены для удаления повторяющихся значений.  
  
## <a name="next-step"></a>Следующий шаг  
 [Урок 4. Хранение данных поставщика в MDS](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)  
  
  
