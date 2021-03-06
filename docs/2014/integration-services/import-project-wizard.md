---
title: Мастер импорта проекта | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.importprojectwizard.f1
ms.assetid: 9247ad6c-4bd1-43ab-b347-583181cb9917
caps.latest.revision: 9
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e25fd5e0d0142d7e29f14fc1691c979bac24149
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314144"
---
# <a name="import-project-wizard"></a>Мастер импорта проектов
  Мастер импорта проектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] служит для создания нового проекта служб Integration Services на основе существующего проекта. Можно импортировать проекты, уже развернутые в каталоге служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , или проекты из файла развертывания проекта (расширение ISPAC).  
  
### <a name="to-create-a-project-based-on-a-project-in-ispac-file-or-in-catalog"></a>Создание проекта на основе проекта в файле ISPAC или в каталоге  
  
1.  Выберите меню **Файл**, **Создать**, а затем «Проект».  
  
2.  Разверните узел **Бизнес-аналитика**и выберите **Службы Integration Services**.  
  
3.  На средней панели выберите **Мастер импорта служб Integration Services** , введите **имя** для решения, проекта, затем введите **папку** для проекта и нажмите кнопку **ОК**.  
  
     Должен открыться **Мастер импорта проекта служб Integration Services**. Мастер создаст новый проект служб Integration Services на основе существующего проекта.  
  
4.  Нажмите кнопку **Далее** , на странице **Введение** , чтобы перейти на страницу **Выбор источника данных** .  
  
5.  Укажите, должен ли проект импортироваться из файла ISPAC или из каталога.  
  
    -   Если был выбран режим **Файл развертывания проекта** , то укажите путь к файлу ISPAC.  
  
    -   Если был выбран **Каталог служб Integration Services** , то введите имя экземпляра сервера базы данных, в котором содержится каталог, а также путь к проекту в каталоге.  
  
6.  Нажмите кнопку **Далее** , на странице **Выбор источника** , чтобы перейти на страницу **Просмотр** . Проверьте отображаемую на странице информацию об операции импорта, которую выполнит мастер.  
  
7.  Нажмите кнопку **Импорт** , чтобы создать новый проект служб Integration Services на основе существующего выбранного проекта.  
  
8.  На странице **Результаты** должны быть отображены результаты выполнения операции импорта, выполненной мастером. Нажмите кнопку **Сохранить отчет** , чтобы сохранить отчет в XML-файле.  
  
9. Нажмите кнопку **Закрыть** , чтобы закрыть мастер.  
  
  
