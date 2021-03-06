---
title: Объединение данных (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f570016f39dab2b62276dc3b64ad2c135b05460d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197444"
---
# <a name="combine-data-mds-add-in-for-excel"></a>Объединение данных (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]объедините данные из двух листов, чтобы сравнить их перед публикацией. В этой процедуре данные из двух таблиц объединяются в одну. Затем можно выполнить сравнения и определить, какие данные (если имеются) следует опубликовать в репозитории MDS.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Необходимо иметь лист, содержащий данные, управляемые MDS. Дополнительные сведения см. в разделе [загрузки данных из MDS в Excel](export-data-to-excel-from-master-data-services.md).  
  
-   Необходимо иметь лист, содержащий данные, которые нужно объединить с данными, управляемыми MDS. Этот лист должен иметь строку заголовка.  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a>Объединение неуправляемых данных на листе, управляемом MDS  
  
1.  На листе, содержащем данные, управляемые MDS, в группе **Публикация и проверка** нажмите кнопку **Объединить данные**.  
  
2.  В диалоговом окне **Объединение данных** рядом с текстовым полем **Диапазон для объединения с данными MDS** щелкните значок. Диалоговое окно свернется.  
  
3.  Щелкните лист, содержащий данные, которые нужно объединить.  
  
4.  Выделите все ячейки на листе, которые нужно объединить, включая строку заголовка.  
  
5.  В диалоговом окне **Объединение данных** щелкните значок. Диалоговое окно раскроется.  
  
6.  Для столбца, указанного для сущности MDS, выберите столбец в поле **Соответствующий столбец**. Соответствующие столбцы нужны не для всех столбцов MDS.  
  
7.  Нажмите кнопку **Объединить**. Появится столбец **SOURCE** , указывающий, берутся ли данные из MDS или внешнего источника.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   Сведения об определении подобия между данными, управляемыми MDS, и внешними данными см. в разделе [Сопоставление схожих данных (надстройка MDS для Excel)](match-similar-data-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>См. также  
 [Загрузка данных &#40;надстройка MDS для Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Сопоставление качества данных в надстройке MDS для Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  
