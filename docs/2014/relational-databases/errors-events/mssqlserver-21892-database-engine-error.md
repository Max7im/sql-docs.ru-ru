---
title: MSSQLSERVER_21892 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a01f07cdfb20ed88a43dbda2b555e819ca725c0b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414323"
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
 `sp_validate_replica_hosts_as_publishers` выполняет запрос к текущей первичной реплике группы доступности, связанной с перенаправленным издателем, чтобы определить, на каких экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] размещены реплики-члены.  Если выполнить этот запрос не удается, возвращается ошибка 21892.  
  
 `sp_validate_replica_hosts_as_publishers` обычно вызывается при первом использовании временно связанного сервера, поэтому проблемы с подключением, вероятнее всего, в первую очередь проявятся при вызове `sp_validate_replica_hosts_as_publishers`. В отличие от `sp_validate_redirected_publisher`, связанный сервер, используемый `sp_validate_replica_hosts_as_publishers`, всегда использует учетные данные вызывающей стороны при соединении с любым из узлов реплик группы доступности.  
  
## <a name="user-action"></a>Действие пользователя  
 При запуске этой хранимой процедуры убедитесь, что имя входа, используемое при выполнении, действительно на всех репликах. У имени входа должны быть достаточные права на авторизацию для выполнения запросов к таблицам метаданных группы доступности, а также к таблицам метаданных подписки на реплике базы данных издателя.  
  
 Просмотрите исходное сообщение об ошибке, на которое указывает ссылка, чтобы определить причину ошибки и соответствующие действия по ее исправлению.  
  
  
