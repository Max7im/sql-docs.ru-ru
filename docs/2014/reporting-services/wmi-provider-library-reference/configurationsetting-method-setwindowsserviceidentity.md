---
title: Метод SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
caps.latest.revision: 19
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bc53a516da25d81c1532ea1418b4f846f37597ef
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37268460"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserverconfigurationsetting"></a>Метод SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting)
  Обеспечивает запуск службы Windows сервера отчетов в качестве заданного пользователя Windows, а также предоставляет этой учетной записи достаточные разрешения, необходимые для работы сервера отчетов.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *UseBuiltInAccount*  
 Показывает, является ли указанная учетная запись встроенной учетной записью Windows.  
  
 *Учетная запись*  
 Учетная запись Windows, которая используется для запуска службы Windows, имеет формат «ДОМЕН\псевдоним».  
  
 *Пароль*  
 Пароль для учетной записи.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Примечания  
 Когда *UseBuiltInAccount* параметр имеет значение `true` и сервер отчетов работает под управлением Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] или Windows XP, то значения параметров *имя*, *домена*, и *пароль* учитываются и используется учетная запись локальной системы.  
  
 Когда *UseBuiltInAccount* параметр имеет значение `true` и сервер отчетов работает в Windows Server 2003, *домена* и *пароль* свойства игнорируется, а поле имени должно быть значение «» или «Builtin\System» или «Builtin\LocalService».  
  
 Метод SetWindowsServiceIdentity задает разрешения для файлов и папок в установочном каталоге сервера отчетов.  
  
 Учетная запись, указанная в *учетной записи* параметр требует `LogonAsService` прав в Windows. Метод предоставляет эти права указанной учетной записи.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
