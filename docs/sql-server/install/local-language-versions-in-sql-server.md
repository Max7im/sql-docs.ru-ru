---
title: "Версии SQL Server на разных языках | Документация Майкрософт"
ms.custom: 
ms.date: 08/23/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20b99363-0490-4aa3-9a3d-262f827d81e8
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 59bccb3bef14b779a017567211148096d2cb6c35
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="local-language-versions-in-sql-server"></a>Версии SQL Server на местных языках
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает все языки, поддерживаемые операционными системами Windows.  
  
## <a name="cross-language-support"></a>Поддержка версий на разных языках  
  
-   Английская версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживается на всех локализованных версиях операционных систем.  
  
-   Локализованные версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются в локализованных операционных системах с соответствующими языками или в версиях поддерживаемых операционных систем для английского языка с пакетом многоязыкового пользовательского интерфейса Windows (MUI). Дополнительные сведения см. в разделе [Configure Operating System to Support Localized Versions](../../sql-server/install/local-language-versions-in-sql-server.md#BK_ConfigureOS).  
  
-   Локализованные версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут быть обновлены только до локализованных версий на том же языке. Они не могут быть обновлены до версии на английском языке.  
  
-   Локализованные версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут быть также установлены параллельно с англоязычными экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="BK_ConfigureOS"></a> Configure Operating System to Support Localized Versions  
 Локализованные версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются в английских версиях поддерживаемых операционных систем с помощью пакета многоязыкового пользовательского интерфейса Windows.  
  
 Однако перед установкой локализованной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на сервер, работающий под управлением англоязычной версии операционной системы с установленным пакетом многоязыкового пользовательского интерфейса, в котором выбран другой язык, необходимо проверить некоторые настройки операционной системы. Необходимо убедиться, что следующие настройки операционной системы соответствуют языку локализации устанавливаемой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Настройки пользовательского интерфейса операционной системы  
  
-   Пользовательские настройки локали операционной системы  
  
-   Настройки локали системы  
  
 Если настройки не соответствуют языку локализации устанавливаемой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используйте следующие процедуры, чтобы правильно установить эти параметры операционной системы.  
  
> [!CAUTION]  
>  Установка нескольких экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с разными языками на одном компьютере не поддерживается.  
  
#### <a name="to-change-the-operating-system-user-interface-setting"></a>Изменение настройки пользовательского интерфейса операционной системы  
  
1.  При необходимости установите интерфейс MUI операционной системы, соответствующий локализованным версиям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  На панели управления откройте **Язык и региональные стандарты**.  
  
3.  На закладке **Языки** на панели **Язык, используемый в меню и диалоговых окнах**выберите значение из раскрывающегося списка.  
  
     Этот параметр влияет на язык интерфейса пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поэтому он должен совпадать с версией локализации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  Нажмите кнопку **Применить** , чтобы подтвердить изменения, а затем **ОК** , чтобы закрыть окно.  
  
#### <a name="to-change-the-operating-system-user-locale-setting"></a>Изменение настройки локали операционной системы  
  
1.  При необходимости установите интерфейс MUI операционной системы, соответствующий локализованным версиям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  На панели управления откройте **Язык и региональные стандарты**.  
  
3.  На вкладке **Региональные параметры** выберите значение из раскрывающегося списка в области **Языковые стандарты и форматы**.  
  
     Этот параметр повлияет на форматирование данных, характерное для страны.  
  
4.  Нажмите кнопку **Применить** , чтобы подтвердить изменения, а затем **ОК** , чтобы закрыть окно.  
  
#### <a name="to-change-the-system-locale-setting"></a>Изменение настройки локали системы  
  
1.  При необходимости установите интерфейс MUI операционной системы, соответствующий локализованным версиям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  На панели управления откройте **Язык и региональные стандарты**.  
  
3.  На вкладке **Дополнительно** в области **Язык программ, не поддерживающих Юникод**выберите значение из раскрывающегося списка.  
  
     Эта настройка дает возможность программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выбрать наилучшие параметры сортировки по умолчанию для установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
4.  Нажмите кнопку **Применить** , чтобы подтвердить изменения, а затем **ОК** , чтобы закрыть окно.  
  
## <a name="see-also"></a>См. также:  
 [Требования к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [Установка SQL Server](../../database-engine/install-windows/install-sql-server.md)  
  
  