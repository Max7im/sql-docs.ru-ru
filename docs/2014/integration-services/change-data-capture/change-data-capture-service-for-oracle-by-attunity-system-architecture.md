---
title: Архитектура системы Change Data Capture Service для Oracle от Attunity | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1db6c737-3c60-4066-a0a3-3611e1c83e4e
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f12b56a22e5a69aa38ee6a899814dc0eeb2c3b96
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312074"
---
# <a name="change-data-capture-service-for-oracle-by-attunity-system-architecture"></a>Архитектура службы системы отслеживания измененных данных для Oracle компании Attunity
  Служба CDC Service для Oracle отслеживает изменения выбранных таблиц из одной или нескольких исходных баз данных Oracle и записывает сведения о них в базы данных CDC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , расположенные в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . На следующей диаграмме показаны компоненты, составляющие службу CDC Service для Oracle.  
  
 ![Архитектура службы](../media/service-architecture.gif "Архитектура службы")  
  
 На рисунке показано использование четырех платформ. Во многих случаях эти платформы могут дублировать друг друга, однако на диаграмме представлен стандартный вариант использования. Например, часто бывает целесообразно, чтобы Oracle и базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполнялись на разных компьютерах, а не совместно с платформой службы Oracle CDC Service или платформой, с которой запускается служба CDC Service. На этом рисунке показаны следующие платформы:  
  
-   Служба Oracle CDC Service. Это может быть любой поддерживаемый компьютер с ОС Windows, где установлена и запущена служба Oracle CDC Service. Эта платформа может также представлять собой узел в отказоустойчивом кластере Microsoft (конфигурации высокого уровня доступности описаны далее в этом документе).  
  
-   База данных Oracle. Это может быть любой компьютер, на котором работает поддерживаемая версия базы данных Oracle. Сюда входят любые компьютеры, работающие под управлением ОС Windows, Linux или любой другой операционной системы, поддерживаемой версией установленной базы данных Oracle. Следует отметить, что на диаграмме показано несколько таких платформ, поскольку одна служба Oracle CDC Service может отслеживать изменения в нескольких исходных базах данных Oracle.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: это может быть любой компьютер, на котором работает база данных-получатель [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (поддерживаемый номер SKU [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]). Служба Oracle CDC Service поддерживает один целевой экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , где хранятся таблицы изменений и конфигурация службы. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Платформы может также представлять собой кластеризованный экземпляр [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] или Зеркалированный экземпляр [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью **AlwaysOn** функции.  
  
-   Конструктор Oracle CDC. Это может быть любой поддерживаемый компьютер с ОС Windows, который может осуществлять доступ к базе данных-источнику Oracle и базе данных-получателю [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 В следующей таблице описаны компоненты, которые выполняются на четырех платформах, указанных выше.  
  
|Компонент/Описание|Компонент включает в себя следующее:|  
|----------------------------|----------------------------|  
|Служба Oracle CDC Service. Это служба Windows, где выполняются действия по отслеживанию измененных данных.|Экземпляр Oracle CDC. Подпроцесс службы Oracle CDC Service, который обрабатывает действия по отслеживанию измененных данных для одной исходной базы данных Oracle (на одну исходную базу данных Oracle приходится один экземпляр Oracle CDC).<br /><br /> Средство чтения журнала Oracle. Читает журналы транзакций Oracle с помощью клиента Oracle.<br /><br /> Клиент Oracle. Клиент Oracle Instant Client, используемый для связи с Oracle. Это обязательный компонент, который нужно получить у Oracle и установить до установки службы Oracle CDC Service.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] : Изменение записывает зафиксированные изменения, внесенные в отслеживаемые таблицы Oracle, чтобы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]таблицы изменений. Этот компонент также поддерживает состояние отслеживания в целевой базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Клиент ODBC: Клиент Microsoft Native Client для [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Это обязательный компонент, который нужно получить у Microsoft и установить до установки службы Oracle CDC Service.|  
|Конфигурация службы Oracle CDC Service. Это оснастка консоли управления (MMC), которая создает службу Windows и настраивает ее конфигурацию.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL ADO.NET клиент, поставляемый с версии 4 платформы .NET framework.|  
|База данных Oracle. База данных-источник Oracle, в которой отслеживаются изменения выбранных таблиц.|Средство анализа журналов. Компонент Oracle, с помощью которого читаются журналы транзакций Oracle.<br /><br /> Журнал транзакций. Активные и архивированные журналы операций повтора Oracle, используемые Oracle для отката транзакций и восстановления после сбоев (в этом случае база данных Oracle должна работать в режиме ARCHIVELOG).|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Экземпляр: A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра, где размещаются базы данных CDC. Это может быть кластеризованный [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляр (отказоустойчивый кластер) или зеркальной базы данных (AlwaysOn).|База данных MSXDBCDC. База данных, в которой хранятся сведения о службе CDC Service, работающей с этим экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Здесь также хранятся сведения об экземплярах Oracle CDC, обрабатываемых каждой службой CDC Service. Эта база данных создается в ходе процесса создания службы CDC Service.<br /><br /> Базы данных CDC. Базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , в которых хранятся изменения одной из баз данных-источников Oracle. В базах данных CDC обеспечена возможность работы CDC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , поэтому у них есть таблицы и функции CDC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , облегчающие прием данных об изменениях, получаемых из Oracle.|  
|Конструктор Oracle CDC. Оснастка консоли управления (MMC), которая позволяет создавать экземпляры Oracle CDC. Используется для выбора таблиц и столбцов, в которых будут отслеживаться изменения, указания данных подключения к Oracle и управления жизненным циклом экземпляров CDC.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL ADO.NET клиент, поставляемый с версии 4 платформы .NET framework.<br /><br /> Клиент Oracle. Клиент Oracle Instant Client, используемый для связи с Oracle. Это обязательный компонент, который нужно получить у Oracle и установить до установки службы Oracle CDC Service.|  
  
 Служба Oracle CDC Service и ее дочерние экземпляры Oracle CDC могут обмениваться данными только с исходной базой (базами) данных Oracle и целевым экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве клиентов. Они не занимаются активным прослушиванием какого-либо сетевого или иного протокола. Служба Oracle CDC Service отслеживает изменения конфигурации баз данных CDC и обновляет свою работу с учетом обновленной конфигурации.  
  
  
