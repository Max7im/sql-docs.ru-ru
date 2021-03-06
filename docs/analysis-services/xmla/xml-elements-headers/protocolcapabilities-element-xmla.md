---
title: Элемент ProtocolCapabilities (XML для Аналитики) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 85ddeb22fac03e5ae7f66521ac3ca8a46e210fe7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38021199"
---
# <a name="protocolcapabilities-element-xmla"></a>Элемент ProtocolCapabilities (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Использует заголовок SOAP в сообщении SOAP-запроса для определения возможностей протокола между экземпляром служб Analysis Services и клиентским приложением.  
  
 **Пространство имен** `http://schemas.microsoft.com/analysisservices/2003/engine`  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <ProtocolCapabilities xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
         <Capability>...</Capability>  
      </ProtocolCapabilities>  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Возможность](../../../analysis-services/xmla/xml-elements-properties/capability-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 **ProtocolCapabilities** элемент позволяет клиентским приложениям согласовать возможности протокола, например двоичного XML или поддержки сжатия, с [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр в любое время. Согласование протокола включает следующие шаги.  
  
1.  Клиентское приложение определяет возможности своего протокола с помощью отправки запроса SOAP, включающего элемент **ProtocolCapabilities** , как часть заголовка SOAP.  
  
2.  Экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] получает и обрабатывает запрос SOAP.  
  
3.  Если [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр имеет те же возможности протокола, который запросил, он отправляет ответ SOAP, включающий тот же **ProtocolCapabilities** элемент присутствовал в запросе SOAP, и была протокол успешно согласован. В противном случае возможности протокола не согласуются и экземпляр возвращает ошибку SOAP.  
  
 После успешного согласования возможностей протокола, как долго клиентское приложение и [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используйте экземпляр определенного протокола зависит от того, является ли сеанс явным или неявным:  
  
-   Явный сеанс — это приложения, создается с помощью [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) элемент заголовка. В явном сеансе протокол используется, пока клиентское приложение не отправит новый элемент **ProtocolCapabilities** или не завершится сеанс.  
  
-   Неявный сеанс создается экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и не задается явно клиентским приложением при приеме запроса SOAP. В неявном сеансе согласованный протокол используется только до завершения запроса SOAP.  
  
 Возможности протокола не обязательно согласовывать явно. То есть клиентскому приложению не обязательно включать элемент **ProtocolCapabilities** , как часть запроса. Если запрос SOAP не включает **ProtocolCapabilities** элемент, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр отвечает, используя тот же формат запроса SOAP.  
  
## <a name="see-also"></a>См. также
 [Управление соединениями и сеансами &#40;XML для Аналитики&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
