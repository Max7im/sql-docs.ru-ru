---
title: Восстановление из PowerPivot | Документация Майкрософт
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
- sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 65f585fe2a6ac0046cebd99878f6e2bf8c5a5061
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250867"
---
# <a name="restore-from-powerpivot"></a>Восстановление из PowerPivot
  Можно использовать функцию «Восстановление из PowerPivot» в SQL Server Management Studio для создания новой базы данных на основе табличной модели на экземпляре служб Analysis Services (выполняемых в табличном режиме) или восстановления в существующую базу данных из книги PowerPivot (XLSX).  
  
> [!NOTE]  
>  Шаблон проекта «Импорт из PowerPivot» в SQL Server Data Tools предоставляет аналогичную функциональность. Дополнительные сведения см. в разделе [Импорт из PowerPivot &#40;табличные службы SSAS&#41;](import-from-power-pivot-ssas-tabular.md).  
  
 При использовании восстановления из PowerPivot следует учитывать следующее.  
  
-   Чтобы использовать восстановление из PowerPivot, необходимо выполнить вход от имени члена роли администратора сервера для экземпляра служб Analysis Services.  
  
-   Учетная запись службы для экземпляра служб Analysis Services должна иметь права на чтение файла книги, из которой производится восстановление.  
  
-   По умолчанию при восстановлении базы данных из PowerPivot свойство «Сведения об олицетворении источника данных» для базы данных на основе табличной модели имеет значение «По умолчанию», что указывает на учетную запись службы для экземпляра служб Analysis Services. Рекомендуется изменить учетные данные олицетворения на учетную запись Windows в свойствах базы данных. Дополнительные сведения см. в разделе [Олицетворение (табличные службы SSAS)](impersonation-ssas-tabular.md).  
  
-   Данные в модели данных PowerPivot копируются в существующую или новую базу данных на основе табличной модели на экземпляре служб Analysis Services. Если книга PowerPivot содержит связанные таблицы, они воссоздаются в виде таблиц без источника данных, аналогично таблицам, созданным с использованием вставки в новую таблицу.  
  
### <a name="to-restore-from-powerpivot"></a>Восстановление из PowerPivot  
  
1.  В среде SSMS, в экземпляре Active Directory, в который производится восстановление, щелкните правой кнопкой мыши пункт **Базы данных**и выберите пункт **Восстановление из PowerPivot**.  
  
2.  В диалоговом окне **Восстановление из PowerPivot** в разделе **Источник восстановления**в области **Файл резервной копии**нажмите кнопку **Обзор**и выберите файл ABF или XLSX для восстановления из него.  
  
3.  В поле **Цель восстановления**области **Восстановление базы данных**введите имя новой или существующей базы данных. Если имя не указано, будет использовано имя книги.  
  
4.  В поле **Место хранения**нажмите кнопку **Обзор**и выберите расположение для хранения базы данных.  
  
5.  В области **Параметры**оставьте флажок **Включить сведения о безопасности** . При восстановлении из книги PowerPivot этот параметр не действует.  
  
## <a name="see-also"></a>См. также  
 [Базы данных табличной модели &#40;табличные службы SSAS&#41;](tabular-model-databases-ssas-tabular.md)   
 [Импорт из PowerPivot &#40;табличные службы SSAS&#41;](import-from-power-pivot-ssas-tabular.md)  
  
  
