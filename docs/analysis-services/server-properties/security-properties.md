---
title: "Свойства безопасности | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- security [Analysis Services], properties
- SecurityPackageList property
- BuiltinAdminsAreServerAdmins property
- DisableClientImpersonation property
- ErrorMessageMode property
- RequiredProtectionLevel property
- ServiceAccountIsServerAdmin property
- RequireClientAuthentication property
ms.assetid: 2fc7fe10-0cbb-49ac-aa8c-8ec3f7a7705f
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0233cd9c2e9eff5cc776b921e092206524546a52
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="security-properties"></a>Свойства безопасности
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера безопасности, перечисленные в следующей таблице. Дополнительные сведения о дополнительных свойствах сервера и их настройке см. в разделе [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Область применения:** многомерный и табличный режим сервера  
  
## <a name="properties"></a>Свойства  
 **RequireClientAuthentication**  
 Логическое свойство, указывает, требуется ли проверка подлинности клиента.  
  
 Значение по умолчанию True означает, что проверка подлинности необходима.  
  
 **SecurityPackageList**  
 Строковое свойство, содержащее разделенный запятыми список пакетов SSPI, при помощи которых сервер проверяет подлинность клиентов.  
  
 **DisableClientImpersonation**  
 Логическое свойство, указывает, отключено ли олицетворение клиента (например, хранимые процедуры).  
  
 Значение по умолчанию False означает, что олицетворение клиента включено.  
  
 **BuiltinAdminsAreServerAdmins**  
 Логическое свойство, указывает, являются ли члены группы администраторов локального компьютера администраторами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 **ServiceAccountIsServerAdmin**  
 Логическое свойство, указывает, является ли учетная запись службы администратором сервера.  
  
 Значение по умолчанию True означает, что учетная запись службы является администратором сервера.  
  
 **ErrorMessageMode**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **DataProtection\ RequiredProtectionLevel**  
 Целочисленное 32-разрядное свойство со знаком, определяющее требуемый уровень защиты для всех запросов клиентов. Возможные значения этого свойства перечислены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*0*|Нет, допускается открытый текст.|  
|*1*|Значение по умолчанию. Открытый текст не регистрируется.|  
|*2*|Допускается подписанный открытый текст (более слабая защита, чем шифрование).|  
  
 **AdministrativeDataProtection\ RequiredProtectionLevel**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  