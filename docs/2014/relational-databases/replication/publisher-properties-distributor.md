---
title: Свойства издателя — распространитель | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distpubproperties.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: ab6ada76-0f99-43fe-b524-baac7b1bc483
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 721b2030285f50ca2f7a1212b8589ebcb05957cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164125"
---
# <a name="publisher-properties---distributor"></a>Свойства издателя — распространитель
  Диалоговое окно **Свойства издателя** позволяет просматривать и изменять свойства, относящиеся к связи между издателем и его распространителем.  
  
## <a name="options"></a>Параметры  
 **Соединение агента с издателем**  
 Укажите контекст, в котором следующие агенты выполняют соединения распространителя с издателем.  
  
-   Агент чтения очереди для публикаций транзакций, допускающих подписки, обновляемые посредством очередей.  
  
-   Агент моментальных снимков и агент чтения журнала для публикаций Oracle.  
  
 Выберите **Выполнять олицетворение учетной записи процесса агента** для соединения с издателем при помощи контекста учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой работают эти агенты, или выберите **Проверка подлинности SQL Server**и введите **Имя входа** и **Пароль**. Рекомендуется выбрать **Выполнять олицетворение учетной записи процесса агента**. Дополнительные сведения о безопасности агента см. в статье [Модель безопасности агента репликации](security/replication-agent-security-model.md).  
  
 Учетные записи Windows, с которыми работают эти агенты, задаются в мастере создания публикаций. Эти учетные записи могут быть изменены двумя способами.  
  
-   В диалоговом окне **Свойства распространителя** для агента чтения очереди.  
  
-   В диалоговом окне **Свойства публикации** для агента моментальных снимков и агента чтения журнала.  
  
 **Разное**  
 Свойства **Тип издателя** и **Имя базы данных распространителя** доступны только для чтения. Свойство **Папка моментальных снимков по умолчанию** может быть изменено. Дополнительные сведения о папке моментальных снимков см. в статье [Организация безопасности папки моментальных снимков](security/secure-the-snapshot-folder.md).  
  
## <a name="see-also"></a>См. также  
 [Create a Publication](publish/create-a-publication.md)   
 [Просмотр и изменение свойств издателя и распространителя](view-and-modify-distributor-and-publisher-properties.md)   
 [Справочник по свойствам (репликация)](properties-reference-replication.md)  
  
  
