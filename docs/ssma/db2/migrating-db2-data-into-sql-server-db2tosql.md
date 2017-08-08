---
title: "Миграция данных DB2 в SQL Server (DB2ToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 86cbd39f-6dac-409a-9ce1-7dd54403f84b
caps.latest.revision: 5
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 392deeac6aeb1791322723367def8f2e3e6464e8
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="migrating-db2-data-into-sql-server-db2tosql"></a>Перенос данных DB2 в SQL Server (DB2ToSQL)
После успешной синхронизации преобразованные объекты с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], можно выполнить перенос данных из DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
> [!IMPORTANT]  
> Если механизм, используемый модуль переноса данных стороне сервера, затем, перед переносом данных, необходимо установить SSMA для пакета расширения DB2 и поставщиков DB2 на компьютере, на котором выполняется SSMA. Также должна выполняться служба агента SQL Server. Дополнительные сведения о том, как установить пакет расширения см. в разделе [Установка SSMA компонентов на сервере SQL Server](http://msdn.microsoft.com/en-us/cf2b724b-4ca7-470a-8dd7-fa95b1e060a4)  
  
## <a name="setting-migration-options"></a>Настройка параметров миграции  
Перед переносом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], проверьте параметры миграции проекта в **параметры проекта** диалоговое окно.  
  
-   В этом диалоговом окне можно задать параметры, такие как размер пакета миграции, блокировка таблицы, ограничения проверки, обработки значений null и обработки значений идентификаторов. Дополнительные сведения о миграции параметров проекта см. в разделе [параметры проекта (миграция)](http://msdn.microsoft.com/en-us/48aaa8e6-a9cb-487d-9ba5-fc3f1c4786ae).  
  
-   **Модуль переноса** в **параметры проекта** диалоговом дает пользователю возможность выполнения процесса миграции с использованием двух типов данных миграции ядер:  
  
    1.  Модуль переноса данных стороны клиента  
  
    2.  Модуль переноса данных стороне сервера  
  
**Миграцию данных клиента:**  
  
-   Чтобы начать перенос данных на стороне клиента, выберите **модуль переноса данных стороны клиента** в диалоговом окне **параметры проекта** диалоговое окно.  
  
-   В **параметры проекта**, **модуль переноса данных стороны клиента** был установлен.  
  
    > [!NOTE]  
    > **Модуль переноса данных клиентского** находится внутри SSMA приложения и, соответственно, не зависит от доступности пакета расширения.  
  
**Миграция данных стороне сервера.**  
  
-   Во время переноса данных стороне сервера средство поиска находится в целевой базе данных. Он устанавливается с помощью пакета расширения. Дополнительные сведения о том, как установить пакет расширения см. в разделе [Установка SSMA компонентов на сервере SQL Server](http://msdn.microsoft.com/en-us/cf2b724b-4ca7-470a-8dd7-fa95b1e060a4)  
  
-   Чтобы начать миграцию на стороне сервера, выберите **модуль переноса данных стороне сервера** в диалоговом окне **параметры проекта** диалоговое окно.  
  
## <a name="migrating-data-to-sql-server"></a>Перенос данных в SQL Server  
Миграция данных является операцией массовой загрузки, которая перемещает строки данных из таблиц DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] таблиц в транзакции. Число строк, загруженных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в одной транзакции, настроенному в параметрах проекта.  
  
Для просмотра сообщений о миграции, убедитесь, что отображается область вывода. В противном случае — из **представление** последовательно выберите пункты **вывода**.  
  
**Для переноса данных**  
  
1.  Проверьте выполнение следующих условий.  
  
    -   Поставщики DB2 устанавливаются на компьютере, на котором выполняется SSMA.  
  
    -   Вы синхронизировали преобразованные объекты с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных.  
  
2.  Выберите объекты, которые содержат данные, которые требуется перенести в обозревателе метаданных DB2:  
  
    -   Чтобы выполнить миграцию данных для всех схем, установите флажок рядом с **схемы**.  
  
    -   Перенос данных или исключив некоторые из отдельных таблиц, сначала разверните схемы, разверните **таблиц**и затем установите или снимите флажок рядом с таблицей.  
  
3.  Для переноса данных, возникают два варианта:  
  
    **Миграцию данных клиента:**  
  
    -   Для выполнения **миграцию данных клиента**выберите **модуль переноса данных стороны клиента** в диалоговом окне **параметры проекта** диалоговое окно.  
  
    **Миграция данных стороне сервера.**  
  
    -   Прежде чем выполнять перенос данных на стороне сервера, обеспечения:  
  
        1.  SSMA для пакета расширения DB2 устанавливается на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
        2.  Служба агента SQL Server выполняется на экземпляре SQL Server.  
  
    -   Для выполнения **миграцию данных Server**выберите **модуль переноса данных стороне сервера** в диалоговом окне **параметры проекта** диалоговое окно.  
  
4.  Щелкните правой кнопкой мыши **схемы** в обозреватель метаданных DB2, а затем выберите **переноса данных**. Можно также перенести данные для отдельных объектов и категории объектов: щелкните правой кнопкой мыши объект или ее родительскую папку; Выберите **переноса данных** параметр.  
  
    > [!NOTE]  
    > SSMA для DB2 пакет расширения не установлены ли на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]и если **модуль переноса данных стороне сервера** выбран, то во время миграции данных в целевую базу данных, обнаружена следующая ошибка: "SSMA переноса данных компоненты не найдены на сервере SQL Server, перенос данных на сервере будет невозможно. Проверьте, правильно ли установлен пакет расширений ". Нажмите кнопку **отменить** завершить перенос данных.  
  
5.  В **подключение к DB2** диалоговое окно, введите учетные данные подключения и нажмите кнопку **Connect**. Дополнительные сведения о подключении к DB2 см. в разделе [подключение к базе данных DB2 &#40; DB2ToSQL &#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md)  
  
    Для подключения к целевой базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], введите учетные данные соединения в **подключение к SQL Server** диалоговое окно и нажмите кнопку **Connect**. Дополнительные сведения о подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], в разделе [подключение к SQL Server](http://msdn.microsoft.com/en-us/b59803cb-3cc6-41cc-8553-faf90851410e)  
  
    Сообщения будут отображаться в **вывода** области. По завершении миграции, **отчет о миграции данных** отображается. Если перемещение данных, щелкните строку, которая содержит ошибки и нажмите кнопку **сведения**. По окончании работы с отчетом щелкните **закрыть**. Дополнительные сведения об отчете о переносе данных см. в разделе [(SSMA Common) отчет о миграции данных](http://msdn.microsoft.com/en-us/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> При использовании выпуска SQL Express в целевой базе данных допускается только клиентских данных миграцию и миграцию данных сервера не поддерживается.  
  
## <a name="see-also"></a>См. также:  
[Перенос данных DB2 в SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
