---
title: Создание сборки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
caps.latest.revision: 26
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a7dcaae61cdfa6466f8f7194b4f93977ec2e7d97
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37353352"
---
# <a name="creating-an-assembly"></a>Создание сборки
  Управляемые объекты базы данных, например хранимые процедуры или триггеры, компилируются и развертываются в единицах, называемых сборками. Управляемые DLL-сборки должны регистрироваться в [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] прежде чем можно будет использовать возможности этой сборки. Для регистрации сборки в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используется инструкция CREATE ASSEMBLY. В этом разделе описывается регистрация сборки с помощью инструкции CREATE ASSEMBLY и способы указания параметров безопасности для сборки.  
  
## <a name="the-create-assembly-statement"></a>Инструкция CREATE ASSEMBLY  
 Инструкция CREATE ASSEMBLY используется для создания сборки в базе данных. Например:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Предложение FROM задает путь к создаваемой сборке. Путь может указываться в формате UNC или быть локальным физическим путем к файлу.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не дает возможность регистрировать различные версии сборок с одинаковыми именами, культурой и открытыми ключами.  
  
 Можно создавать сборки, ссылающиеся на другие сборки. При создании сборки в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] также создает сборки ссылается сборка корневого уровня, в том случае, если эти сборки уже не созданы в базе данных.  
  
 Пользователям базы данных или ролям пользователей предоставляются разрешения на создание в базе данных сборок, владельцами которых они будут. Чтобы создавать сборки, пользователь или роль базы данных должны иметь разрешение CREATE ASSEMBLY.  
  
 Сборка может успешно ссылаться на другие сборки только при следующих условиях.  
  
-   Владельцем сборки, которую вызывает или на которую ссылается пользователь или роль, является этот пользователь или роль.  
  
-   Сборка, которая вызывается или на которую указывает ссылка, была создана в этой базе данных.  
  
## <a name="specifying-security-when-creating-assemblies"></a>Уровни безопасности при создании сборки  
 При создании сборки в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных, можно указать один из трех различных уровней безопасности, в котором может выполняться код: `SAFE`, `EXTERNAL_ACCESS`, или `UNSAFE`. При вызове инструкции `CREATE ASSEMBLY` в коде сборки выполняются определенные проверки, в результате которых сборка может быть не зарегистрирована на сервере. Дополнительные сведения см. в разделе образца Impersonation на [CodePlex](http://msftengprodsamples.codeplex.com/).  
  
 `SAFE` является набором разрешений по умолчанию и работает в большинстве сценариев. Чтобы задать определенный уровень безопасности, измените синтаксис инструкции CREATE ASSEMBLY следующим образом.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 Также можно создать сборку с разрешением `SAFE`, просто опустив третью строку приведенного выше кода.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Если код сборки запускается с набором разрешений `SAFE`, он может только выполнять вычисления и получать доступ на сервере с помощью внутрипроцессного управляемого поставщика.  
  
### <a name="creating-externalaccess-and-unsafe-assemblies"></a>Создание сборок EXTERNAL_ACCESS и UNSAFE  
 Сборка `EXTERNAL_ACCESS` предназначена для сценариев, в которых коду требуется получить доступ к ресурсам, внешним по отношению к серверу, например к файлам, сети, реестру или переменным среды. Каждый раз, когда сервер получает доступ к внешним ресурсам, он олицетворяет контекст безопасности пользователя, вызывающего управляемый код.  
  
 Разрешение кода `UNSAFE` предназначено для тех случаев, когда сборка не проверялась на безопасность или нуждается в дополнительном доступе к ресурсам, на которые существуют ограничения, например к API-интерфейсу [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32.  
  
 Чтобы создать сборку `EXTERNAL_ACCESS` или `UNSAFE` в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], необходимо, чтобы выполнялось одно из двух следующих условий.  
  
1.  Сборка должна иметь строгое имя, подписанное обычной подписью или кодом Authenticode с сертификатом. Это строгое имя (или удостоверение) создается в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как ассиметричный ключ (или сертификат) и имеет соответствующую учетную запись с разрешением `EXTERNAL ACCESS ASSEMBLY` (для сборок внешнего доступа) или `UNSAFE ASSEMBLY` (для небезопасных сборок).  
  
2.  Владелец базы данных (DBO) имеет `EXTERNAL ACCESS ASSEMBLY` (для `EXTERNAL ACCESS` сборок) или `UNSAFE ASSEMBLY` (для `UNSAFE` сборок) разрешение и база данных имеет [свойство базы данных TRUSTWORTHY](../../security/trustworthy-database-property.md) присвоено `ON`.  
  
 Два приведенных выше условия также проверяются при загрузке сборки (которая включает выполнение). Чтобы загрузить сборку, должно выполняться хотя бы одно условие.  
  
 Мы рекомендуем [свойство базы данных TRUSTWORTHY](../../security/trustworthy-database-property.md) в базе данных не будет присвоено `ON` только для запуска common language runtime (CLR) кода в серверный процесс. Вместо этого рекомендуется создать асимметричный ключ из файла сборки в главной базе данных. Необходимо создать имя входа, сопоставляемое с этим асимметричным ключом, которому будет предоставлено разрешение `EXTERNAL ACCESS ASSEMBLY` или `UNSAFE ASSEMBLY`.  
  
 Следующие [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции перед выполнением инструкции CREATE ASSEMBLY.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  Необходимо создать новое имя входа для сопоставления с асимметричным ключом. Это имя входа используется только для предоставления разрешений и не должно сопоставляться с пользователем или использоваться в приложении.  
  
 Для создания сборки `EXTERNAL ACCESS` создатель должен иметь разрешение `EXTERNAL ACCESS`. Оно задается при создании сборки.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 Следующие [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции перед выполнением инструкции CREATE ASSEMBLY.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 Чтобы указать, что сборка загружается с разрешением `UNSAFE`, необходимо задать набор разрешений `UNSAFE` при загрузке сборки на сервер.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 Дополнительные сведения о разрешениях для каждого параметра см. в разделе [безопасность интеграции CLR](../security/clr-integration-security.md).  
  
## <a name="see-also"></a>См. также  
 [Управление сборками интеграции со средой CLR](managing-clr-integration-assemblies.md)   
 [Изменение сборки](altering-an-assembly.md)   
 [При удалении сборки](dropping-an-assembly.md)   
 [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md)   
 [Свойство базы данных TRUSTWORTHY](../../security/trustworthy-database-property.md)   
 [Частично доверенный вызывающий код](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
  
  
