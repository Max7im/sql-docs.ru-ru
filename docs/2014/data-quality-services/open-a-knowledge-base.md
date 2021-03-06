---
title: Открытие базы знаний | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.openkb.f1
ms.assetid: a5f010a5-b762-41c9-881b-bf0c192dca83
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bff4aba1e3b9095b2962165bc7a1b96d5ac4771f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151645"
---
# <a name="open-a-knowledge-base"></a>Открытие базы знаний
  В этом разделе описано, как открыть существующую базу знаний в [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) и подготовить ее для управления доменами, обнаружения знаний или добавления политики сопоставления.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Для открытия базы знаний она уже должна быть создана и либо опубликована (если ее создал другой пользователь), либо закрыта (если ее создали вы).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для открытия базы знаний необходима роль dqs_kb_editor или dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="Open"></a> Open a knowledge base  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Запуск клиентского приложения Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главной странице [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] нажмите кнопку **Открыть базу знаний**.  
  
3.  Выберите базу знаний в таблице. Домены и правила сопоставления в базе знаний будут отображаться на правой панели страницы.  
  
    > [!NOTE]  
    >  Операции над базой знаний вы можете выполнять, щелкнув базу знаний в таблице правой кнопкой мыши. Базу знаний вы можете открыть, сохранить ее под другим именем, разблокировать, отменить выполненную работу, переименовать ее или отобразить ее свойства.  
  
4.  В поле **Выбор действия**выберите действие, которое необходимо выполнить над базой знаний.  
  
    -   Выберите вариант **Управление доменами** , чтобы перейти на экраны, на которых можно изменить домены в базе знаний.  
  
    -   Выберите вариант **Обнаружение набора знаний** , чтобы запустить мастер, который позволяет проанализировать образец данных и заполнить домены базы знаний результатами анализа.  
  
    -   Выберите вариант **Политика сопоставления** , чтобы создать политику сопоставления и добавить ее в базу знаний.  
  
5.  Нажмите кнопку **Открыть**.  
  
    > [!NOTE]  
    >  Также вы можете открыть базу знаний, щелкнув ее правой кнопкой мыши и выбрав команду «Открыть». Другие команды в контекстном меню позволяют сохранить базу знаний под другим именем, разблокировать ее, отменить проведенную работу, переименовать ее или отобразить ее свойства.  
  
    > [!NOTE]  
    >  Если базу знаний не удается открыть, так как она заблокирована, см. раздел ниже.  
  
## <a name="open-a-recent-knowledge-base"></a>Открытие последних баз знаний  
 Пять последних открытых баз знаний отображаются в списке **Последние базы знаний** на домашней странице DQS. Это позволяет открывать базы знаний, с которыми недавно велась работа, без перехода на страницу **Открыть базу знаний** .  
  
-   Чтобы открыть базу знаний из списка «Последние», которая не заблокирована, щелкните стрелку вправо возле базы знаний и выберите действие, в котором следует открыть базу знаний.  
  
-   Чтобы открыть базу знаний из списка «Последние», заблокированную вами, щелкните стрелку вправо — и база знаний откроется в действии и на странице, указанных в скобках.  
  
-   Чтобы открыть базу знаний из списка «Последние», заблокированную не вами, свяжитесь с выполнившим блокировку пользователем и попросите его разблокировать базу знаний.  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После открытия базы знаний  
 После открытия базы знаний она переходит в состояние, указанное в столбце «Состояние» таблицы «База знаний». Для действий по обнаружению набора знаний и политикам сопоставления база знаний открывается на соответствующей странице мастера. Для действий по управлению доменами база знаний открывается на странице управления доменами. Дополнительные сведения см. в разделах [Обнаружение знаний](../../2014/data-quality-services/perform-knowledge-discovery.md), [Управление доменом](../../2014/data-quality-services/managing-a-domain.md) и [Создание политики сопоставления](../../2014/data-quality-services/create-a-matching-policy.md).  
  
##  <a name="Locked"></a> Если база знаний заблокирована  
 Значок блокировки в первом столбце сообщает, заблокирована ли база знаний. Имя заблокированной базы знаний отображается красным цветом. База знаний, которая изменяется определенным пользователем посредством действия базы знаний, отмечается как заблокированная. С заблокированной базой знаний не могут параллельно работать другие пользователи. Пользователь, работающий с базой знаний, может разблокировать ее, щелкнув базу знаний правой кнопкой мыши в таблице на странице «Открыть базу знаний» и выбрав пункт **Разблокировать**или опубликовав базу знаний. Когда курсор наведен на заблокированную базу знаний, службы DQS показывают, кто и когда ее заблокировал.  
  
##  <a name="State"></a> Состояние базы знаний  
 Поле «Состояние» указывает, на какой стадии действия находится база знаний. При открытии база знаний откроется на этой стадии.  
  
-   **\<Пусто>**. Поле "Состояние" для базы знаний пусто, если для публикации этой базы использовалась функция **Опубликовать** в действии "Управление доменами" и был выбран элемент **Да — опубликовать базу знаний и выйти**.  
  
-   **В работе**. Работа над базой знаний была сохранена посредством нажатия кнопки **Опубликовать** в действии «Управление доменами» и выбора элемента **Нет — сохранить работу в базе знаний и выйти**.  
  
-   **Управление доменами**. Для домена базы знаний были введены данные, но база знаний не была опубликована, и работа над ней продолжается в действии «Управление доменами». Действия с набором знаний недоступны. Это происходит в том случае, если была нажата кнопка **Закрыть** на экране **Управление доменами** .  
  
-   **Обнаружение — сопоставление**. База знаний была закрыта на странице **Управление базами знаний: сопоставление** База знаний заблокирована, и действия «Управление доменами» и «Сопоставление» недоступны.  
  
-   **Обнаружение — обнаружение**. База знаний была закрыта на странице **Управление базами знаний: анализ** База знаний заблокирована, и действие «Управление доменами» недоступно.  
  
-   **Обнаружение — управление значениями**. База знаний была закрыта на странице **Управление базами знаний: управление терминами доменов** База знаний заблокирована, и действие «Управление доменами» недоступно.  
  
-   **Политика сопоставления — политика сопоставления**. База знаний была закрыта на странице **Политика сопоставления — политика сопоставления** . База знаний заблокирована, и действия «Обнаружение набора знаний» и «Управление доменами» недоступны.  
  
-   **Политика сопоставления — результаты сопоставления**. База знаний была закрыта на странице **Политика сопоставления — результаты сопоставления** . База знаний заблокирована, и действия «Обнаружение набора знаний» и «Управление доменами» недоступны.  
  
  
