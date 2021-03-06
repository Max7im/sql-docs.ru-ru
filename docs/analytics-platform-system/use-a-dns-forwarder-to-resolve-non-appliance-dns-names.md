---
title: Использовать DNS-сервер пересылки в Analytics Platform System | Документы Microsoft»
description: Используйте DNS-сервер пересылки для разрешения имен DNS не является специализированным в Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2f707d4c681c695105daf23d5fc640279bb83658
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31544946"
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names-in-analytics-platform-system"></a>Использовать DNS-сервер пересылки для разрешения имен DNS не является специализированным в система платформы аналитики
DNS-сервер пересылки можно настроить на узлах доменных служб Active Directory (***appliance_domain *-AD01** и ***appliance_domain *-AD02**) вашего устройства Analytics Platform System, чтобы разрешить сценарии и приложения для доступа к внешним серверам.  
  
## <a name="ResolveDNS"></a>С помощью DNS-сервер пересылки  
Система платформы аналитики устройства настроена на запрещение разрешения имен DNS, серверов, которые не находятся в устройстве. Некоторые процессы, такие как Windows программного обеспечения Update Services (WSUS), потребуется доступ к серверам вне устройства. Для поддержки этого сценария использования системы DNS платформы Analytics можно настроить для поддержки пересылки внешнее имя, которое позволит Analytics Platform System узлов и виртуальных машин (ВМ) для использования внешнего DNS-серверы для разрешения имен вне устройства. Пользовательские конфигурации DNS-суффиксы не поддерживается, что означает, что необходимо использовать полные доменные имена для разрешения имени сервера не является специализированным.  
  
**Для создания DNS-сервер пересылки с графическим интерфейсом пользователя DNS**  
  
1.  Выполните вход на ***appliance_domain *-AD01** узла.  
  
2.  Откройте диспетчер DNS (**dnsmgmt.msc**).  
  
3.  Щелкните правой кнопкой мыши имя сервера и нажмите кнопку **свойства**.  
  
4.  На **Дополнительно** вкладки, снимите флажок **отключить рекурсию (и серверы пересылки)** , а затем щелкните **применить**.)  
  
5.  Нажмите кнопку **пересылки** и нажмите кнопку **изменить**.  
  
6.  Введите IP-адрес внешнего DNS-сервера, который будет предоставлять разрешения имен. Виртуальные машины и серверов (узлов) в устройстве будет соединения с внешними серверами с использованием полных доменных имен.  
  
7.  Повторите шаги 1 – 6 на ***appliance_domain *-AD02** узла  
  
**Создание DNS-сервер пересылки с помощью Windows PowerShell**  
  
1.  Выполните вход на ***appliance_domain *-AD01**узла.  
  
2.  Запустите следующий сценарий Windows PowerShell из ***appliance_domain *-AD01** узла. Перед выполнением сценария Windows PowerShell, замените IP-адреса DNS-серверов не является специализированным IP-адресов.  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  Выполните ту же команду на ***appliance_domain *-AD02** узла.  
  
## <a name="configuring-dns-resolution-for-wsus"></a>Настройка разрешения DNS для WSUS  
SQL Server PDW 2012 предоставляет встроенную обслуживания и исправления функциональность. SQL Server PDW использует Центр обновления Майкрософт и других обслуживания технологий Майкрософт. Чтобы включить обновление устройство должно находиться либо подключиться в репозиторий корпоративной WSUS или в репозитории открытого WSUS Microsoft.  
  
Для клиентов, которые решено настроить устройство искать обновления в WSUS репозитории открытого Microsoft следующие инструкции задать сведения о правильной конфигурации на устройстве.  
  
> [!NOTE]  
> Сетевому администратору клиента необходимо указать IP-адрес для корпоративной DNS-сервера, можно разрешать имена в **Microsoft.com**.  
  
1.  С помощью удаленного рабочего стола, войдите в систему виртуальной Машины VMM (<fabric domain>- VMM) с помощью учетной записи администратора домена структуры.  
  
2.  Откройте панель управления, нажмите кнопку **сеть и Интернет**, а затем нажмите кнопку **сетями и общим доступом**.  
  
3.  В списке соединений щелкните **VMSEthernet**, а затем нажмите кнопку **свойства**.  
  
4.  Выберите **Интернет протокола версии 4 (TCP/IPv4)**, а затем нажмите кнопку **свойства**.  
  
5.  В **Альтернативный DNS-сервер** добавьте IP-адрес, предоставленный администратором сети клиента.  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
