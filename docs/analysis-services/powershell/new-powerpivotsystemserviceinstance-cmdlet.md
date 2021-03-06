---
title: Командлет New-PowerPivotSystemServiceInstance | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4fbffee39fc5cb77ac70c1caaa2556361c162fea
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028075"
---
# <a name="new-powerpivotsystemserviceinstance-cmdlet"></a>Командлет «New-PowerPivotSystemServiceInstance»
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Добавляет новый экземпляр системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на сервер приложений.  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
New-PowerPivotSystemServiceInstance [[-ParentService] <PowerPivotMidTierServicePipeBind>] [-SystemServiceInstanceName <string>] [-Provision] [<CommonParameters>]  
```  
  
## <a name="description"></a>Описание  
 Командлет New-PowerPivotSystemServiceInstance подготавливает новый объект PowerPivotSystemService на уровне фермы после того, как вы установили [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint на локальном сервере приложений с помощью программы установки SQL Server. На каждом сервере приложений можно указать только один экземпляр службы.  Если служба уже указана, выполнить этот командлет нельзя.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-parentservice-powerpivotmidtierservicepipebind"></a>-ParentService \<PowerPivotMidTierServicePipeBind >  
 Указывает идентификатор GUID родительского объекта системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме. В этом выпуске допускается только один родительский объект. Команда Get-PowerPivotSystemService используется для получения объекта службы или его идентификатора GUID.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-systemserviceinstancename-string"></a>-SystemServiceInstanceName \<строка >  
 Указывает имя, идентифицирующее этот объект.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|1|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="provision-switchparameter"></a>Подготовка к работе [\<SwitchParameter >]  
 Делает службу доступной на SharePoint. Допустимые значения — $true или $false.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="commonparameters"></a>\<Общие параметры >  
 Этот командлет поддерживает общие параметры: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer и OutVariable. Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|Нет.|  
|Выходные данные|Нет.|  
  
## <a name="example-1"></a>Пример 1  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -Provision:$true  
```  
  
 В этом примере показана наиболее распространенная форма командлета. Командлет регистрирует в ферме системную службу [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на локальном сервере приложений.  
  
## <a name="example-2"></a>Пример 2  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -SystemServiceInstanceName "MyPSSInstance" -provision:$false  
```  
  
 В этом примере задается имя для экземпляра системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] без его подготовки. Если имя не задано, будет использовано имя по умолчанию — экземпляр системной службы служб SQL Server Analysis Services. Создание пользовательского имени для службы не является обязательным. Службу можно именовать для поддержки сценариев проверки, либо если имеется пользовательское средство или скрипт, который провизионирует экземпляр на последующих этапах.  
  
  
