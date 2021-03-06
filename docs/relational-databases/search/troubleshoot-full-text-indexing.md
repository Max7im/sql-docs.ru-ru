---
title: Устранение неполадок полнотекстового индексирования | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.component: search
ms.reviewer: ''
ms.suite: sql
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- indexes [full-text search]
- troubleshooting [SQL Server], full-text search
- troubleshooting [full-text search]
ms.assetid: 964c43a8-5019-4179-82aa-63cd0ef592ef
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: eb095aa9aa4492be44aa5077a33699b2d014486e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43072087"
---
# <a name="troubleshoot-full-text-indexing"></a>Устранение неполадок полнотекстового индексирования
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
     
##  <a name="failure"></a> Устранение неполадок при неудачном завершении полнотекстового индексирования  
 При заполнении или обслуживании полнотекстового индекса полнотекстовый индексатор по изложенным ниже причинам может пропустить одну или несколько строк. Данные ошибки на уровне строк не препятствуют завершению заполнения. Индексатор просто пропускает эти строки, что означает, что их содержимое останется недосягаемым для запросов.  
  
 Ошибки индексирования могут возникать в следующих случаях.  
  
-   Индексатор не смог найти или загрузить фильтр либо средство разбиения по словам. Данная ошибка может возникать, если строка таблицы содержит формат документа или содержимое на языке, не зарегистрированном в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данная ошибка также может возникать, если зарегистрированный компонент средства разбиения по словам или фильтрации не подписан либо не прошел проверку подписи при загрузке.  
  
-   Возникает ошибка в компоненте, например в средстве разбиения по словам или фильтре, возвращаемая индексатору. Это может происходить, если индексируемый документ поврежден и фильтр не может извлечь из него текст. Это также может происходить, если компонент вследствие ограничения памяти, установленного в узле управляющей программы полнотекстовой фильтрации (fdhost.exe), не может обработать содержимое одной строки, превышающее определенный размер.  
  
 Подробное описание причин каждой ошибки на уровне строк регистрируется в журнале сканирования. Итоговое количество ошибок определяется после полного или добавочного заполнения.  
  
 Существуют и другие ошибки, которые могут повлиять на индексирование как таковое и препятствовать завершению заполнения:  
  
-   Размер полнотекстового индекса превышает ограничение на количество строк, которые могут находиться в полнотекстовом каталоге.  
  
-   Кластеризованный индекс или индекс полнотекстового ключа в индексируемой таблице изменяется, удаляется или перестраивается.  
  
-   Сбой оборудования или повреждение жесткого диска, вызывающее повреждение полнотекстового каталога.  
  
-   Файловая группа, содержащая таблицу, в которой выполняется полнотекстовое индексирование, становится вне сети или доступной только для чтения.  
  
 По окончании любой большой операции заполнения полнотекстового индекса или в случае обнаружения незавершенной операции заполнения изучите журнал сканирования.  
  
### <a name="unsigned-components"></a>Неподписанные компоненты  
 По умолчанию полнотекстовый индексатор требует, чтобы загружаемые им фильтры и средства разбиения по словам были подписаны. Если они не подписаны, что иногда случается при установке пользовательских компонентов, необходимо настроить полнотекстовый индексатор так, чтобы он пропускал проверку подписей.  
  
> [!IMPORTANT]  
>  Игнорирование проверки подписей снижает защищенность экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Рекомендуется подписывать все самостоятельно внедряемые компоненты либо контролировать наличие подписей у всех приобретаемых компонентов. Дополнительные сведения о подписании компонентов см. в разделе [sp_fulltext_service (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md).  
  
  
##  <a name="state"></a> Полнотекстовый индекс в несогласованном состоянии после восстановления журнала транзакций  
 При восстановлении журнала транзакций базы данных может появиться предупреждение о том, что полнотекстовый индекс находится в рассогласованном состоянии. Причина заключается в том, что этот полнотекстовый индекс в таблице был изменен после резервного копирования базы данных. Чтобы привести полнотекстовый индекс в согласованное состояние, необходимо выполнить в таблице полное заполнение (сканирование). Дополнительные сведения см. в разделе [Заполнение полнотекстовых индексов](../../relational-databases/search/populate-full-text-indexes.md).  
  
  
## <a name="see-also"></a>См. также:  
 [ALTER FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [Заполнение полнотекстовых индексов](../../relational-databases/search/populate-full-text-indexes.md)  
  
  
