---
title: Определить нужный номер SKU базы данных Azure SQL для вашей локальной базы данных (Data Migration Assistant) | Документация Майкрософт
description: Узнайте, как использовать помощник по миграции данных для выявления справа номер SKU базы данных SQL Azure для вашей локальной базы данных
ms.custom: ''
ms.date: 08/29/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 84601b6a556df64d3708fd749af06be8e753048d
ms.sourcegitcommit: 010755e6719d0cb89acb34d03c9511c608dd6c36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2018
ms.locfileid: "43240152"
---
# <a name="identify-the-right-azure-sql-database-sku-for-your-on-premises-database"></a>Определить нужный номер SKU базы данных Azure SQL для базы данных на предприятии

Задачу миграции баз данных в облако — это сложная и требует много времени, включающие большое количество переменных. Выбрав целевой базы данных прямо в Azure и SKU для базы данных может оказаться сложной задачей. Наша цель с Database Migration Assistant (DMA) — Чтобы решить эти задачи и сделать возможности миграции базы данных, простой и эффективный.

Эта статья посвящена главным образом функция рекомендации DMA в номер SKU базы данных SQL Azure, которая позволяет определить минимальный рекомендуемый номер SKU базы данных SQL Azure на основе счетчиков производительности, собранных с компьютеров, на котором размещены ваши базы данных. Этот компонент предоставляет рекомендации, связанные с цены на уровень, уровень вычислений и максимальный объем данных, а также оценочная стоимость в месяц. Он также предлагает возможность подготавливать всех баз данных в Azure в пакетном режиме.

> [!NOTE] 
> Эта функция сейчас доступна только через интерфейс командной строки (CLI). Поддержка этой функции через пользовательский интерфейс DMA будут добавляться в предстоящем выпуске.

> [!IMPORTANT]
> SKU рекомендации для базы данных SQL Azure в настоящее время доступны для миграции из SQL Server 2016 или более поздней версии.

Приведенные ниже инструкции помогут определить рекомендации номер SKU базы данных SQL Azure и подготовка связанных баз данных в Azure, с помощью Data Migration Assistant.

## <a name="prerequisites"></a>предварительные требования

Скачать помощник по миграции базы данных версии 4.0 или более поздней версии, а затем установить его. Если у вас уже есть средство установки, закройте и снова откройте его, и вам будет предложено обновить средство.

## <a name="collect-performance-counters"></a>Сбор данных счетчиков производительности

Для сбора данных счетчиков производительности для баз данных является первым шагом в процессе. Можно собирать данные счетчиков производительности, выполнив команду PowerShell на компьютере, на котором размещены ваши базы данных. DMA предоставляет копию этого файла PowerShell, но можно также использовать свой собственный метод для записи счетчиков производительности с компьютера.

Не требуется для выполнения этой задачи для каждой базы данных по отдельности. Счетчики производительности, собранные с компьютера можно рекомендовать SKU для всех баз данных, подключенного к компьютеру.

> [!IMPORTANT]
> Компьютер, из которого при выполнении этой команды требуются права администратора к компьютеру с размещенной баз данных.

1. Убедитесь, что файл PowerShell, необходимые для сбора данных счетчиков производительности устанавливается в папке DMA.

    ![Файл PowerShell, показанный в папке DMA](../dma/media/dma-sku-recommend-data-collection-file.png)

2. Запустите сценарий PowerShell со следующими аргументами:
    - **ComputerName**: имя компьютера, на котором размещаются базы данных.
    - **OutputFilePath**: путь к файлу в выходных данных для сохранения собранных счетчиков.
    - **CollectionTimeInSeconds**: количество времени, во время которого вы хотите собирать данные счетчиков производительности.
      Сохранять данные счетчиков производительности в течение 40 минут получить осмысленные рекомендацию. Длительный срок, записи, тем точнее рекомендация будет.
    - **DbConnectionString**: подключение к строкой, указывающей на базе данных master, размещенной на компьютере, с которого вы будете собирать данные счетчиков производительности.
     
    Ниже приведен образец вызова.

    ```
    .\SkuRecommendationDataCollectionScript.ps1
     -ComputerName Foobar1
     -OutputFilePath D:\counters2.csv
     -CollectionTimeInSeconds 10
     -DbConnectionString "Server=localhost;Initial Catalog=master;Integrated Security=SSPI;"
    ```
    
    После выполнения команды, процесс будет выводить файл со счетчиками производительности в указанном расположении. Этот файл можно использовать в качестве входных данных для команды рекомендация SKU в следующем разделе.

## <a name="use-the-dma-cli-to-get-sku-recommendations"></a>Использовать интерфейс командной строки DMA для получения рекомендаций SKU

Используйте выходной файл счетчики производительности из предыдущего шага как входные данные для этого шага. DMA предоставит рекомендации для базы данных SQL Azure цены на уровень, уровень вычислений и максимальный размер данных для каждой базы данных на компьютере. DMA будет также отобразится расчетная Месячная стоимость для каждой базы данных.

Выполните dmacmd.exe со следующими аргументами:

- **/ Action = SkuRecommendation**: Введите этот аргумент для выполнения оценки SKU.
- **/ SkuRecommendationInputDataFilePath**: путь к файлу счетчика собираются в предыдущем разделе.
- **/ SkuRecommendationTsvOutputResultsFilePath**: путь для записи выходных данных в формате TSV.
- **/ SkuRecommendationJsonOutputResultsFilePath**: путь для записи выходных данных в формате JSON.
- **/ SkuRecommendationHtmlResultsFilePath**: путь для записи выходных данных в формате HTML.

Кроме того необходимо выбрать одну из следующих аргументов:
- Предотвратить обновление цены
    - **/ SkuRecommendationPreventPriceRefresh**: предотвращает обновление цены. Используйте, если выполняется в автономном режиме.
- Получите последние цены 
    - **/ SkuRecommendationCurrencyCode**: валюты, в которой отображаются цены (например) «ДОЛЛ. США»).
    - **/ SkuRecommendationOfferName**: предложение имя (например) "MS-AZR - 0003 P»). Дополнительные сведения см. в разделе [сведения о предложении Microsoft Azure](https://azure.microsoft.com/support/legal/offer-details/) страницы.
    - **/ SkuRecommendationRegionName**: области имя (например) «WestUS»).
    - **/ SkuRecommendationSubscriptionId**: идентификатор подписки.
    - **/ AzureAuthenticationTenantId**: проверка подлинности клиента.
    - **/ AzureAuthenticationClientId**: идентификатор клиента приложения AAD, используемый для проверки подлинности.
    - Один из следующих режимов проверки подлинности:
        - Интерактивно
            - **AzureAuthenticationInteractiveAuthentication**: задано значение true для всплывающего окна проверки подлинности.
        - На основе сертификатов
            - **AzureAuthenticationCertificateStoreLocation**: значение в расположении хранилища сертификатов (например) «CurrentUser»).
            - **AzureAuthenticationCertificateThumbprint**: задается для отпечатка сертификата.
        - На основе маркера
            - **AzureAuthenticationToken**: значение маркера сертификата.

Ниже приведены некоторые вызовы образец.

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationInteractiveAuthentication=true
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
```

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true
```

TSV выходной файл будет содержать столбцы, которые отображаются на следующем рисунке:

   ![Файл PowerShell, показанный в папке DMA](../dma/media/dma-tsv-file-column.png)

Описание каждого столбца.

- **Имя базы данных** — имя базы данных.
- **MetricName** — ли метрики был выполнен.
- **MetricType** -уровня базы данных SQL Azure рекомендуется использовать.
- **MetricValue** -рекомендуется база данных Azure SQL SKU.
- **SQLMiEquivalentCores** -Если вы решили перейти к управляемому экземпляру Azure SQL Database, можно использовать это значение для числа ядер.
- **IsTierRecommended** -предпринимаем Минимальное рекомендуемое SKU для каждого уровня. Затем мы применяем эвристику для определения правильного уровня для базы данных. 
- **ExclusionReasons** -это значение пустым, если рекомендуем использовать уровень. Для каждого уровня, не рекомендуется мы предоставляем причин, почему он не используется.
- **AppliedRules** -короткий нотации правил, которые были применены.

Рекомендуемое значение — минимальный номер SKU, необходимые для запросов для запуска в Azure с помощью Доля успешных попыток, аналогичную локальных баз данных. Например если Рекомендуемый минимальный номер SKU уровня "стандартный" S4, а затем выбрав S3 или ниже будет запросы истечения времени ожидания или не могут быть выполнены.

HTML-файл, содержащий эту информацию в графическом формате. Входные данные подписки Azure, Выбор ценовой категории, вычисления уровня и максимальный размер данных для баз данных и создания скрипта для подготовки баз данных можно использовать HTML-файл. Этот сценарий может выполняться с помощью PowerShell.

## <a name="provision-your-databases-to-azure"></a>Подготовка баз данных в Azure
С помощью нескольких щелчков можно использовать рекомендации из предыдущего шага, на целевой подготовку баз данных в Azure, к которому можно перенести базы данных. Также можно внести изменения с рекомендациями, обновив файл HTML следующим образом.

1. Откройте HTML-файл и введите следующие сведения:
    - **Идентификатор подписки** — идентификатор подписки, к которому вы хотите подготовить базы данных подписки Azure.
    - **Регион** — регион, в котором для подготовки баз данных. Убедитесь, что выбор области поддерживает ваша подписка.
    - **Группа ресурсов** — группа ресурсов, к которому вы хотите развернуть базы данных. Введите группу ресурсов, что существует.
    - **Имя сервера** — базы данных SQL server для баз данных, развернутых. Если ввести имя сервера, который не существует, он будет создан.
    - **Администратор Username\Password** — имя входа администратора сервера и пароль.

2. Рекомендации для каждой базы данных, просмотреть и изменить ценовую категорию, вычислительные уровень и максимальный объем данных при необходимости. Не забудьте отменить выбор всех баз данных, которые вы не хотите в настоящее время подготовки.

3. Выберите **формирование скрипта подготовки**, сохраните сценарий и затем выполнить его в PowerShell.

    Этот процесс следует создать все базы данных, выбранного на странице HTML.

Можно выполнить все действия в этом процессе на одном компьютере, или можно выполнить их на нескольких компьютерах, чтобы определить номер SKU рекомендации в масштабе. DMA делает более простое и масштабируемое возможности, поддерживая все эти действия с помощью интерфейса командной строки. Опять же поддержка этой функции через пользовательский интерфейс DMA будут доступны в этом году.

## <a name="next-steps"></a>Следующие шаги
- Скачайте последнюю версию [Data Migration Assistant](https://aka.ms/get-dma).
- См. в статье [запустите помощник по миграции данных из командной строки](https://docs.microsoft.com/sql/dma/dma-commandline?view=sql-server-2017) полный список команд для выполнения DMA из интерфейса командной строки.
