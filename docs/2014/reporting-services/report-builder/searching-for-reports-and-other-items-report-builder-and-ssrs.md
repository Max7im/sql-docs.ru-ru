---
title: Поиск отчетов и других элементов (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6a586659-5c2b-453b-8f40-a3a469277b17
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: eafc6aa4bfbd9df7ca6fbc33b2475cc96ebc62f3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198796"
---
# <a name="searching-for-reports-and-other-items-report-builder--and-ssrs"></a>Поиск отчетов и других элементов (построитель отчетов и службы SSRS)
  Можно использовать диспетчер отчетов для поиска на сервере отчетов заданных элементов по имени или описанию. Можно искать опубликованные отчеты, модели отчетов, папки, общие источники данных и ресурсы. Нельзя искать расписания, владельцев, назначения ролей, определенные моментальные снимки в журнале отчета или в подписках. Поиск выполняется в базе данных сервера отчетов, в которой хранятся элементы.  
  
> [!NOTE]  
>  Выполнение поиска системного файла не вернет результаты поиска для элементов, управляемых сервером отчетов.  
  
-   Чтобы начать поиск элементов в диспетчере отчетов, введите строку поиска в текстовом поле **Поиск** вверху страницы. Поиски начинаются с высшего узла иерархии папок и затем следуют через каждую ветку. Если отсутствует разрешение на доступ к определенной ветке, то эта ветка пропускается. Это относится к папкам «Мои отчеты», принадлежащим другим пользователям и другим папкам, которые обычно не доступны. Только отчеты и элементы, на которые есть разрешение просмотра, включаются в результаты поиска.  
  
-   Чтобы найти элемент по имени или описанию, укажите весь текст или часть текста, с которым нужно совпадение. В строке поиска регистр букв не учитывается. Нельзя использовать операторы поиска, такие как символы плюс (+) или минус (-), для требования или исключения критерия поиска.  
  
-   Для поиска определенного текста в отчете используется панель инструментов, расположенная в верхней части отчета.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Поиск и просмотр отчетов в диспетчере отчетов (построитель отчетов и службы SSRS)](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)   
 [Использование папки "Мои отчеты" (построитель отчетов и службы SSRS)](using-my-reports-report-builder-and-ssrs.md)   
 [Поиск, просмотр отчетов и управление ими (построитель отчетов и службы SSRS)](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Открытие и закрытие отчетов (диспетчер отчетов)](../reports/open-and-close-a-report-report-manager.md)  
  
  
