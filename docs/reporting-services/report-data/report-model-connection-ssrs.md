---
title: "Отчетов соединение с моделью (SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da880fb8-13cc-4d5f-b992-91ed0ec3ca7d
caps.latest.revision: 11
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2ea71172fab75f76e398f1d5469c0c825670f65c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="report-model-connection-ssrs"></a>Соединение с моделью отчета (службы SSRS)
  Для включения данных из модели отчета необходимо использовать в качестве источника данных набор данных на основе модели отчета. В отличие от других источников данных отчета, для модели отчета не существует модуля обработки данных. В построителе отчетов необходимо перейти на сервер отчетов и выбрать модель. В конструкторе отчетов можно указать URL-адрес для модели отчета.  
  
 Используйте сведения в этом разделе для создания источника данных. Пошаговые инструкции см. в разделе [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Строка подключения  
 При использовании модели отчета в качестве источника данных строка соединения не нужна. Для соединения с моделью отчета перейдите на сервер отчетов или сайт SharePoint и выберите опубликованную модель. На сайте SharePoint имена файлов моделей отчета имеют расширение SMDL.  
  
 Дополнительные примеры строк соединения см. в разделе [Подключения к данным, источники данных и строки подключения в построителе отчетов](http://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34).  
  
  
##  <a name="Credentials"></a> Учетные данные  
 Учетные данные необходимы для запуска запросов, локального предварительного просмотра отчетов, а также для предварительного просмотра отчетов на сервере отчетов.  
  
 После публикации отчета может понадобиться изменить учетные данные источника данных, чтобы разрешения, необходимые для получения данных при запуске отчета на сервере отчетов, были допустимыми.  
  
 Дополнительные сведения см. в разделе [Указание учетных данных в построителе отчетов](http://msdn.microsoft.com/library/7412ce68-aece-41c0-8c37-76a0e54b6b53).  
  
  
##  <a name="Query"></a> Запросы  
 Чтобы интерактивно указать для запроса сущности, поля и фильтры используйте конструктор запросов к модели отчета. Сущности и поля модели становятся коллекцией полей набора данных, отображаемой в области данных отчета.  
  
  
##  <a name="Parameters"></a> Параметры  
 Чтобы добавить параметр отчета, создайте фильтр с запросом в конструкторе запросов модели отчета.  
  
 Параметры отчета создаются со значениями свойств по умолчанию, которые, возможно, потребуется изменить. По умолчанию все параметры отчета имеют тип данных **Текст**. Если базовые данные имеют другой тип, необходимо изменить тип данных параметра.  
  
 Дополнительные сведения см. в разделе [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
  
##  <a name="Remarks"></a> Замечания  
 Этот поставщик данных поддерживает не все режимы доставки отчетов. Доставка отчетов с помощью управляемых данными подписок для этого модуля обработки данных не предусмотрена. Дополнительные сведения см. в разделе [Использование внешнего источника данных для данных подписчика (управляемая данными подписка)](../../reporting-services/subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).  
  
  
##  <a name="HowTo"></a> Инструкции  
 В этом разделе содержатся пошаговые инструкции по работе с подключениями к данным, источниками данных и наборами данных.  
  
 [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Создание общего или внедренного набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Добавление фильтра для набора данных &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="Related"></a> См. также  
 В этих разделах документации содержатся подробные сведения о данных отчетов, а также методические сведения об определении, настройке и использовании элементов отчетов, связанных с данными.  
  
 [Наборы данных отчетов (службы SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)  
 Предоставляет общие сведения о доступе к данным отчета.  
  
 [Подключения к данным, источники данных и строки подключения в построителе отчетов](http://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34)  
 Предоставляет сведения о подключениях к данным и источникам данных.  
  
 [Отчет внедренные наборы данных и общие наборы данных &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Предоставляет сведения об общих и внедренных наборах данных.  
  
 [Коллекция полей набора данных &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 Предоставляет сведения о коллекции полей набора данных, создаваемой запросом.  
  
 [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md), см. в документации к [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в [электронной документации](http://go.microsoft.com/fwlink/?linkid=121312) по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 Предоставляет подробные сведения о поддержке платформ и версий для каждого модуля обработки данных.  
  
  
## <a name="see-also"></a>См. также  
 [Поиск, просмотр отчетов и управление ими (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Параметры отчета &#40; Построитель отчетов и конструктор отчетов &#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Фильтр, группы и сортировка данных &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Выражения &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  