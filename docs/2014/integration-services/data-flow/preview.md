---
title: Предварительный просмотр | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 551494c4-9e27-4592-9200-c6bf19e80c9a
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fa7f94ad690362189b29c7e86e34519d1a937bc1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281600"
---
# <a name="preview"></a>Предварительный просмотр
  В диалоговом окне **Предварительный просмотр** можно просмотреть данные, извлекаемые источником SAP BW.  
  
> [!IMPORTANT]  
>  Параметр **Предварительный просмотр** , доступный на странице **Диспетчер соединений** **Редактора источника SAP BW**, непосредственно извлекает данные. Если настроить SAP Netweaver BW для извлечения только тех данных, которые изменились со времени предыдущего сеанса извлечения, то при выборе параметра **Предварительный просмотр** просматриваемые данные будут исключены из следующего сеанса извлечения.  
  
 Для получения дополнительных сведений о компоненте источника SAP BW для [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. раздел [Источник SAP BW](sap-bw-source.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
> [!IMPORTANT]  
>  Для извлечения данных из SAP Netweaver BW требуется дополнительная лицензия SAP. Обратитесь к SAP, чтобы уточнить требования.  
  
 **Открытие диалогового окна «Предварительный просмотр»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий источник SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните источник SAP BW.  
  
3.  В **Редакторе источника SAP BW**щелкните **Диспетчер соединений** , чтобы открыть страницу редактора **Диспетчер соединений** .  
  
4.  Настройте источник SAP BW.  
  
5.  После настройки источника SAP BW на странице **Диспетчер соединений** щелкните **Предварительный просмотр** для предварительного просмотра данных в диалоговом окне **Предварительный просмотр** .  
  
    > [!NOTE]  
    >  При щелчке **Предварительный просмотр** также открывается диалоговое окно **Журнал запросов** . Дополнительные сведения об этом диалоговом окне см. в разделе [Request Log](request-log.md).  
  
## <a name="options"></a>Параметры  
 В диалоговом окне **Предварительный просмотр** отображаются строки, запрошенные в системе SAP Netweaver BW. Отображаемые столбцы — это столбцы, определенные в исходных данных.  
  
 В этом диалоговом окне отсутствуют другие параметры.  
  
## <a name="see-also"></a>См. также  
 [Редактор источника SAP BW &#40;страницы диспетчера соединений&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Справка F1 по Microsoft Connector 1.1 для SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
