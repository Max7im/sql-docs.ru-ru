---
title: "MSSQLSERVER_21892 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3ce5f5c4d88232aee27695aae35bfcf55734497d
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver21892"></a>MSSQLSERVER_21892
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21892|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21892|  
|Текст сообщения|Невозможно запросить имена серверов реплик-членов в представлении sys.availability_replicas первичной реплики группы доступности, связанной с именем виртуальной сети " %s" : ошибка = %d, сообщение об ошибке = %s',|  
  
## <a name="explanation"></a>Объяснение  
**sp_validate_replica_hosts_as_publishers** выполняет запрос к текущей первичной реплике группы доступности, связанной с перенаправленным издателем, чтобы определить, на каких экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] размещены реплики-члены.  Если выполнить этот запрос не удается, возвращается ошибка 21892.  
  
Обычно **sp_validate_replica_hosts_as_publishers** вызывается при первом использовании временно связанного сервера, поэтому проблемы с подключением, если они есть, скорее всего проявятся именно при вызове **sp_validate_replica_hosts_as_publishers**. В отличие от **sp_validate_redirected_publisher**, **sp_validate_replica_hosts_as_publishers** использует связанный сервер, который всегда использует учетные данные вызывающей стороны для подключения к любому из узлов реплик группы доступности.  
  
## <a name="user-action"></a>Действие пользователя  
При запуске этой хранимой процедуры убедитесь, что имя входа, используемое при выполнении, действительно на всех репликах. У имени входа должны быть достаточные права на авторизацию для выполнения запросов к таблицам метаданных группы доступности, а также к таблицам метаданных подписки на реплике базы данных издателя.  
  
Просмотрите исходное сообщение об ошибке, на которое указывает ссылка, чтобы определить причину ошибки и соответствующие действия по ее исправлению.  
  
