---
title: Служба Microsoft курсора для OLE DB | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: acb0604f051aa532e0f1d0081972a49d037d3181
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272923"
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>Служба Microsoft курсора для OLE DB
При выборе клиентский курсор, или задать **CursorLocation** свойства **adUseClient**, вы вызываете служба курсора для OLE DB. Также может отображаться ссылки на «Обработчик курсора клиента», который является по сути то же самое в контексте ADO. Эта служба дополняет функции поддержки курсора поставщиков данных. В результате способен воспринимать относительно однообразного функции из всех поставщиков данных.  
  
 Служба курсора для OLE DB делает доступными динамических свойств и расширяет поведение определенных методов. Например **оптимизировать** динамических свойств позволяет создавать временные индексы для упрощения определенных операций, таких как **найти** метод.  
  
 Службы курсора включает поддержку пакетного обновления во всех случаях. Также имитирует более производительные типов курсора, таких как динамические курсоры, когда поставщик данных может поддерживать только меньшими возможностями курсоров, такие как статические курсоры.  
  
## <a name="see-also"></a>См. также  
 [Службы Microsoft курсора для OLE DB (ADO компонент службы)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
