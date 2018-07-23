---
title: Кэширование общих наборов данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c2d8c81a-da1e-4a8a-9845-fff9a0903d24
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 14558568086141ee23721e99d1180361638041ee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159995"
---
# <a name="cache-a-shared-dataset"></a>кэшировать общий набор данных
  Один из способов повышения производительности состоит в настройке свойств кэширования общего набора данных. При кэшировании общего набора данных копия результатов запроса сохраняется на указанный период времени. Первый пользователь, запрашивающий отчет, в котором используется общий набор данных, должен будет дождаться получения результатов запроса и завершения всех процессов обработки до просмотра отчета. Производительность работы последующих пользователей, запрашивающих тот же отчет в пределах времени кэширования, будет значительно повышена, поскольку запрос и обработка уже выполнены. Также можно указать расписание обновления кэша для выполнения запроса и кэширования результатов до истечения указанного периода кэширования.  
  
 Пользователи, выполняющие отчеты на основе общих наборов данных или планов обновления кэша, создают кэш запроса, и в обоих случаях доступность кэша зависит от параметров периода истечения кэша.  
  
 Существуют ограничения на типы общих наборов, которые можно кэшировать. Например, результаты запроса нельзя кэшировать, если данные зависят от идентификатора пользователя или если данные получаются с помощью токена безопасности пользователя, запросившего отчет. Дополнительные сведения см. в разделах [Общие наборы данных в кэше (службы SSRS)](cache-shared-datasets-ssrs.md) и [Кэширование отчетов (службы SSRS)](caching-reports-ssrs.md).  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a>Назначение момента для истечения срока действия кэшированного отчета  
  
1.  Запустите [диспетчер отчетов (службы SSRS в собственном режиме)](../report-manager-ssrs-native-mode.md).  
  
2.  В диспетчере отчетов перейдите к общему набору данных, для которого необходимо задать свойства кэширования, наведите на него курсор мыши и щелкните стрелку раскрывающегося списка.  
  
3.  В раскрывающемся меню выберите **Управление**.  
  
4.  В левом окне перейдите на вкладку **Кэширование**.  
  
    > [!NOTE]  
    >  При возникновении ошибки **Не сохранены учетные данные, используемые для выполнения общего набора данных**параметры кэширования для общего набора данных будут отключены. Необходимо изменить источник данных, хранящий учетные данные, или изменить общий набор данных для использования другого источника данных, хранящего учетные данные.  
  
5.  Выберите **Кэширование общего набора данных**.  
  
6.  Установите для параметра истечения срока действия кэша значение 30 минут. Также можно выбрать истечения срока действия кэша по указанному расписанию.  
  
7.  Нажмите кнопку **Применить**.  
  
## <a name="see-also"></a>См. также  
 [Управление общими наборами данных](../report-data/manage-shared-datasets.md)  
  
  