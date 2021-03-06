---
title: Определение упорядочивания для измерения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 622dc698bfcae76297e208015a7c257feadd6b5d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293564"
---
# <a name="define-the-ordering-for-a-dimension"></a>Определение упорядочивания для измерения
  Добавьте расширение упорядочивания атрибутов к кубу или измерению, чтобы указать, как упорядочиваются элементы атрибута. Элементы можно упорядочивать по имени или ключу атрибута, либо по имени или ключу другого атрибута (основанному на связи атрибута). По умолчанию элементы упорядочиваются по имени. Это расширение изменяет `OrderBy` и `OrderByAttributeID` параметры свойств для атрибутов в измерении.  
  
 Чтобы добавить упорядочивание атрибутов, используйте мастер бизнес-аналитики и выберите параметр **Задать сортировку атрибута** на странице **Выбор расширения** . После этого мастер отобразит шаги, позволяющие выбрать измерение, к которому необходимо применить упорядочивание атрибутов, и указать способ упорядочивания атрибутов для выбранного измерения.  
  
## <a name="selecting-a-dimension"></a>Выбор измерения  
 На первой странице **Определение порядка атрибутов** мастера указывается измерение, к которому необходимо применить упорядочивание атрибутов. Добавление расширения упорядочивания атрибутов к этому выбранному измерению приведет к изменению измерения. Эти изменения будут наследоваться всеми кубами, включающими выбранное измерение.  
  
## <a name="specifying-ordering"></a>Указание упорядочивания  
 На второй странице **Определение порядка атрибутов** мастера указывается, как будут упорядочиваться все атрибуты в измерении.  
  
 В столбце **Атрибут сортировки** можно изменить атрибут, используемый для выполнения упорядочивания. Если атрибут, который вы хотите использовать для упорядочивания элементов не находится в списке, прокрутите список вниз и выберите  **\<создать атрибут... >** открыть **выберите столбец** диалоговое окно, где вы можете Выберите столбец в таблице измерения. При выборе столбца с использованием диалогового окна **Выбор столбца** создается дополнительный атрибут, с помощью которого необходимо упорядочивать элементы атрибута.  
  
 В столбце **Критерии** после этого можно выбрать, необходимо ли упорядочивать элементы атрибута по **Key** или **Name**.  
  
  
