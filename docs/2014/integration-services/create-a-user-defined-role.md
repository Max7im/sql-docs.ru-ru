---
title: Создание определяемой пользователем роли | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c4128993-2333-48c7-84b1-e51cdcea393d
caps.latest.revision: 5
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fcd15f49067a9c6a1091f98e6b361ab11baf2a0b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295124"
---
# <a name="create-a-user-defined-role"></a>Создание пользовательской роли
    
### <a name="to-create-a-user-defined-role"></a>Создание пользовательской роли  
  
1.  Откройте [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Щелкните **обозреватель объектов** в меню **Вид** .  
  
3.  На панели инструментов обозревателя объектов нажмите кнопку **Соединить**и выберите **Компонент Database Engine**.  
  
4.  В диалоговом окне **Соединение с сервером** введите имя сервера и выберите режим проверки подлинности. Можно использовать точку (.), (local), или `localhost` для указания локального сервера.  
  
5.  Нажмите кнопку **Соединить**.  
  
6.  Последовательно разверните узлы «Базы данных», «Системные базы данных», «msdb», «Безопасность» и «Роли».  
  
7.  В узле "Роли" щелкните правой кнопкой мыши элемент "Роли базы данных" и выберите **Создать роль базы данных**.  
  
8.  На странице «Общие» введите имя и при необходимости укажите владельца, схемы владельца и членов роли.  
  
9. При необходимости нажмите кнопку **Разрешения** и настройте разрешения объекта.  
  
10. При необходимости нажмите кнопку **Расширенные свойства** и настройте расширенные свойства.  
  
11. Нажмите кнопку **ОК**.  
  
  
