---
title: Вычисление политики управления на основе политик по расписанию | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 760c52393015b6b4481048a04a5a04a3f2fe8f0e
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808740"
---
# <a name="evaluate-a-policy-based-management-policy-on-a-schedule"></a>Вычисление политики управления на основе политик по расписанию
  В этом разделе описывается вычисление политики управления на основе политик по расписанию в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Вычисление политики по расписанию с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-on-a-schedule"></a>Вычисление политики по расписанию  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, содержащий расписание политики, которую нужно вычислить.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Щелкните знак «плюс», чтобы развернуть папку **Политики** .  
  
5.  Щелкните правой кнопкой мыши политику, расписание которой нужно вычислить, и выберите пункт **Свойства**.  
  
6.  В диалоговом окне **Открытие политики —***имя_политики* в списке **Режим оценки** выберите значение **По расписанию**.  
  
7.  В разделе **Расписание**нажмите кнопку **Выбрать** , чтобы указать существующее расписание, или кнопку **Создать** , чтобы создать новое расписание.  
  
8.  После завершения нажмите кнопку **ОК**.  
  
  
