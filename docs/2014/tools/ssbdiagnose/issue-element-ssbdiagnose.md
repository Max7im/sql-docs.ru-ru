---
title: Элемент Issue (ssbdiagnose) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 39b279a22da8c75573aa0cad2dc50d7f85e46a74
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175206"
---
# <a name="issue-element-ssbdiagnose"></a>Элемент Issue (программа ssbdiagnose)
  Сообщает о проблеме, обнаруженной программой **ssbdiagnose** . В выходном XML-файле программы **ssbdiagnose** для каждой из обнаруженных проблем присутствует один элемент Issue.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## <a name="element-attributes"></a>Атрибуты элемента  
  
|attribute|Описание|  
|---------------|-----------------|  
|`type`|Определяет категорию проблемы, о которой сообщает элемент Issue:<br /><br /> **"Diagnosis"** . Сообщает о проблеме, обнаруженной во время анализа конфигурации компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] .<br /><br /> **Problem** . Сообщает о проблеме, в результате которой программе **ssbdiagnose** не удалось завершить анализ. Устраните проблему и снова запустите программу **ssbdiagnose**.<br /><br /> **Event** . Сообщает о событии приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , обнаруженном во время выполнения проверки **-RUNTIME** . События включаются в отчет, только если указан параметр **-SHOWEVENTS** .|  
|`code`|Определяет номер ошибки для сообщения.|  
|`server`|Определяет экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , в котором обнаружена проблема. Если проблема произошла в экземпляре по умолчанию, то в атрибуте server будет указано только имя компьютера. Если проблема произошла в именованном экземпляре, то атрибут server будет иметь значение в формате «ИмяКомпьютера\ИмяЭкземпляра».|  
|`database`|Определяет имя базы данных, в которой обнаружена проблема.|  
|`object`|Определяет имя объекта, в котором обнаружена проблема. Если неполадка произошла на уровне экземпляра или базы данных, то в атрибуте object повторяется имя экземпляра или базы данных.|  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|`string`, длина не ограничена.|  
|**Value**|Возвращает текст сообщения об ошибке.|  
|**Наличие**|Один раз для каждой ошибки.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DiagnosticInformation &#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)|  
|**Дочерние элементы**|None|  
  
## <a name="example"></a>Пример  
 Следующий элемент сообщает об ошибке с номером 1102 для базы данных, в которой отсутствует главный ключ. Ошибка была обнаружена во время анализа конфигурации компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] .  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## <a name="see-also"></a>См. также  
 [Программа ssbdiagnose (компонент Service Broker)](ssbdiagnose-utility-service-broker.md)  
  
  
