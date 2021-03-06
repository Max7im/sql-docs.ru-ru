---
title: Создание связанного отчета | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reports
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2fe56792237235d86a6ac59c8ac5e3e98c8f961f
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43265431"
---
# <a name="create-a-linked-report"></a>Создание связанного отчета
  Связанный отчет является элементом сервера отчетов, обеспечивающим точку доступа к существующему отчету. Концептуально связанный отчет можно сравнить с ярлыком, который используется для запуска программы или открытия файла.  
  
 Связанный отчет создается из существующего отчета и сохраняет определение оригинального отчета. Связанный отчет всегда наследует макет отчета и свойства источника данных у оригинального отчета. Все остальные свойства и настройки могут отличаться от свойств и настроек оригинального отчета, включая настройки безопасности, параметры, месторасположение, подписки и расписания.  
  
 Связанный отчет может быть создан в тех случаях, когда необходимо создать дополнительные версии существующего отчета. Например, можно использовать один отчет о региональных продажах для создания региональных отчетов для всех территорий продаж.  
  
 Хотя связанные отчеты обычно основаны на параметризованных отчетах, параметризованный отчет не является обязательным. Можно создавать связанные отчеты, когда необходимо развернуть существующий отчет с различными параметрами.  
  
### <a name="to-create-a-linked-report"></a>Создание связанного отчета  
  
1.  В диспетчере отчетов перейдите к папке с отчетом, с которым требуется установить связь, откройте меню параметров и выберите **Создать связанный отчет**.  
  
2.  Введите имя нового связанного отчета. При необходимости введите также описание.  
  
3.  Чтобы выбрать иную папку для отчета, щелкните **Изменить местоположение**. Щелкните папку, которую нужно использовать, или введите имя папки в поле **Местоположение** . [!INCLUDE[clickOK](../../includes/clickok-md.md)] Если не выбрана иная папка, то связанный отчет создается в текущей папке (где хранится отчет, на основе которого создается связанный отчет).  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Откроется связанный отчет.  
  
     Значок связанного отчета отличается от других элементов, управляемых сервером отчетов. Следующий значок указывает на связанный отчет:  
  
     ![Значок "Связанный отчет"](../../reporting-services/report-server/media/hlp-16linked.gif "Значок \"Связанный отчет\"")  
  
## <a name="see-also"></a>См. также:  
 [Открытие и закрытие отчетов (диспетчер отчетов)](../../reporting-services/reports/open-and-close-a-report-report-manager.md)   
 [Страница "Создание связанного отчета" (диспетчер отчетов)](http://msdn.microsoft.com/library/fefb46e8-6901-4d50-a3f8-7c49ad72e7b1)   
 [Страница "Выбор расположения элементов" (диспетчер отчетов)](http://msdn.microsoft.com/library/4a53a1a8-d1e1-47ef-b1fc-63352ece7d3c)   
 [Страница "Общие свойства", "Отчеты" (диспетчер отчетов)](http://msdn.microsoft.com/library/66c99d28-ab41-45f0-bf02-ed560293595d)   
 [Основные понятия служб Reporting Services (SSRS)](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [Диспетчер отчетов (службы SSRS в собственном режиме)](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)  
  
  
