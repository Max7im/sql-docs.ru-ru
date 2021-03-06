---
title: Справочник по API экземпляра SQL Server Express LocalDB | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: localdb
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 980b4c3de096cb9eaed8243a57c0f32a579206b8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32939479"
---
# <a name="sql-server-express-localdb-reference---instance-apis"></a>SQL Server Express LocalDB - Справочник по API-интерфейсов экземпляра
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Традиционно экземпляры SQL Server, устанавливаемые на один компьютер, разделены физически, то есть каждый из них должен быть установлен или удален отдельно, каждый из них имеет отдельный набор двоичных файлов и выполняется в отдельном процессе службы. Имя экземпляра SQL Server используется для указания того, с каким экземпляром SQL Server пользователь хочет установить соединение.  
  
 В API экземпляра SQL Server Express LocalDB используется упрощенная, «легкая» модель экземпляров. Хотя отдельные экземпляры LocalDB разделены на диске и в реестре, они используют тот же набор общих двоичных файлов LocalDB. Кроме того, LocalDB не использует службы; экземпляры LocalDB запускаются по запросу через вызовы API экземпляра LocalDB. В LocalDB имя экземпляра используется для указания того, с какими экземплярами LocalDB пользователь хочет работать.  
  
 Экземпляр LocalDB всегда принадлежит одному пользователю и является видимым и доступным только из контекста этого пользователя, за исключением случаев, когда включено совместное использование.  
  
 Хотя технически экземпляры LocalDB не идентичны традиционным экземплярам SQL Server, цели, для которых они используются, схожи. Они называются *экземпляров* чтобы подчеркнуть эту схожесть и сделать их более понятными для пользователей SQL Server.  
  
 LocalDB поддерживает два вида экземпляров: автоматические экземпляры (AI) и именованные экземпляры (NI). Идентификатор для экземпляра LocalDB — это имя экземпляра.  
  
## <a name="automatic-localdb-instances"></a>Автоматические экземпляры LocalDB  
 Автоматические экземпляры LocalDB являются «общими»; они автоматически создаются и управляются для пользователей и могут использоваться любым приложением. Один автоматический экземпляр LocalDB существует для каждой версии LocalDB, установленной на компьютере пользователя.  
  
 Автоматические экземпляры LocalDB обеспечивают гладкое управление экземплярами. Пользователю не нужно создавать экземпляр. Это позволяет пользователям легко устанавливать приложения и выполнять миграцию на другие компьютеры. Если на целевом компьютере установлена заданная версия LocalDB, на нем также будет доступен автоматический экземпляр LocalDB.  
  
### <a name="automatic-instance-management"></a>Автоматическое управление экземплярами  
 Пользователю не нужно создавать автоматический экземпляр LocalDB. Если на целевом компьютере установлена заданная версия LocalDB, автоматический экземпляр LocalDB будет создан в фоновом режиме при первом использовании экземпляра. С точки зрения клиента автоматический экземпляр всегда будет доступен, если присутствуют двоичные файлы LocalDB.  
  
 Другие операции управления экземплярами, такие, как удаление или включение и отключение совместного использования, также доступны для автоматических экземпляров. При удалении автоматического экземпляра, фактически, происходит его перезапуск. При следующей операции запуска он будет создан повторно. Удаление автоматического экземпляра может потребоваться при повреждении системных баз данных.  
  
### <a name="automatic-instance-naming-rules"></a>Правила именования автоматических экземпляров  
 Автоматические экземпляры LocalDB имеют специальный шаблон имен экземпляров, принадлежащий зарезервированному пространству имен. Он необходим для предотвращения конфликтов имен с именованными экземплярами LocalDB.  
  
 Имя автоматического экземпляра — это номер версии базового выпуска LocalDB в начале которого стоит символ «v». Имя выглядит как символ «v» и два числа, разделенные точкой; например v11.0 или V12.00.  
  
 Примеры недопустимых имен автоматических экземпляров:  
  
-   11.0 (отсутствует символ «v» в начале)  
  
-   v11 (отсутствует точка и второй номер версии)  
  
-   v11. (отсутствует второй номер версии)  
  
-   V11.0.1.2 (номер версии состоит более чем из двух частей)  
  
## <a name="named-localdb-instances"></a>Именованные экземпляры LocalDB  
 Именованные экземпляры LocalDB являются «закрытыми». Они принадлежат одному приложению, которое отвечает за создание и управление ими. Именованные экземпляры LocalDB обеспечивают изоляцию и повышают производительность.  
  
### <a name="named-instance-creation"></a>Создание именованных экземпляров  
 Пользователь может создавать именованные экземпляры явно, посредством API управления LocalDB или скрыто, посредством файла app.config для управляемого приложения. Управляемое приложение также может использовать API.  
  
 Каждый именованный экземпляр имеет соответствующую версию LocalDB; то есть он указывает на конкретный набор двоичных файлов LocalDB. Версия для именованного экземпляра устанавливается в процессе создания экземпляра.  
  
### <a name="named-instance-naming-rules"></a>Правила именования именованных экземпляров  
 Имя экземпляра LocalDB может состоять всего 128 символов (ограничение накладывается **sysname** тип данных). Это существенно отличается от традиционных имен экземпляров SQL Server, которые ограничены именами NetBIOS из 16 ASCII-символов. Это различие связано тем, что LocalDB обрабатывает базы данных как файлы, и, соответственно, применяет к ним файловую семантику. Это дает пользователям большую свободу при выборе имен.  
  
 Имя экземпляра LocalDB может содержать любые символы Юникода, допустимые в компоненте имени файла. Недопустимые знаки в компоненте имени файла, обычно содержат следующие символы: символы ASCII/Юникода 1 до 31, а также кавычек ("«), меньше (\<), больше (>), вертикальная черта (|), backspace (\b), символ табуляции (\t), двоеточие (:), звездочка (*) вопросительный знак (?), обратной косой черты (\\) и косая черта (/). Обратите внимание, что символ null (\0) допускается, потому что он используется для завершения строк; все, что находится после первого символа null не будет учитываться.  
  
> [!NOTE]  
>  Список недопустимых символов зависит от операционной системы и может измениться в последующих выпусках.  
  
 Начальные и конечные пробелы в именах экземпляров не учитываются и будут усечены.  
  
 Чтобы избежать конфликтов, с именем LocalDB имен экземпляров не может иметь именем, соответствующим шаблону именования автоматических экземпляров, как описано выше в «Автоматический экземпляр именование правила.» Сбой при создании именованного экземпляра с именем, соответствующим шаблону именования автоматических экземпляров, фактически создает экземпляр по умолчанию.  
  
## <a name="sql-server-express-localdb-reference-topics"></a>Справочные разделы по SQL Server Express LocalDB  
 [Заголовок и сведения о версии SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
 Содержит сведения из файла заголовка и разделы реестра для поиска API экземпляра LocalDB.  
  
 [Программа командной строки SqlLocalDB.exe](../../relational-databases/express-localdb-instance-apis/command-line-management-tool-sqllocaldb-exe.md)  
 Описывает программу SqlLocalDB.exe, средство для управления экземплярами LocalDB из командной строки.  
  
 [Функция LocalDBCreateInstance](../../relational-databases/express-localdb-instance-apis/localdbcreateinstance-function.md)  
 Описывает функцию создания нового экземпляра LocalDB.  
  
 [Функция LocalDBDeleteInstance](../../relational-databases/express-localdb-instance-apis/localdbdeleteinstance-function.md)  
 Описывает функцию удаления экземпляра LocalDB.  
  
 [Функция LocalDBFormatMessage](../../relational-databases/express-localdb-instance-apis/localdbformatmessage-function.md)  
 Описывает функцию возврата локализованного описания ошибки LocalDB.  
  
 [Функция LocalDBGetInstanceInfo](../../relational-databases/express-localdb-instance-apis/localdbgetinstanceinfo-function.md)  
 Описывает функцию получения сведений об экземпляре LocalDB, например, существует ли он, сведения о его версии, запущен ли он и т.п.  
  
 [Функция LocalDBGetInstances](../../relational-databases/express-localdb-instance-apis/localdbgetinstances-function.md)  
 Описывает функцию возврата всех экземпляров LocalDB с указанной версией.  
  
 [Функция LocalDBGetVersionsInfo](../../relational-databases/express-localdb-instance-apis/localdbgetversioninfo-function.md)  
 Описывает функцию возврата сведений об определенной версии LocalDB.  
  
 [Функция LocalDBGetVersions](../../relational-databases/express-localdb-instance-apis/localdbgetversions-function.md)  
 Описывает функцию возврата всех версий LocalDB, доступных на компьютере.  
  
 [Функция LocalDBShareInstance](../../relational-databases/express-localdb-instance-apis/localdbshareinstance-function.md)  
 Описывает функцию включения для совместного использования заданного экземпляра LocalDB.  
  
 [Функция LocalDBStartInstance](../../relational-databases/express-localdb-instance-apis/localdbstartinstance-function.md)  
 Описывает функцию запуска указанного экземпляра LocalDB.  
  
 [Функция LocalDBStartTracing](../../relational-databases/express-localdb-instance-apis/localdbstarttracing-function.md)  
 Описывает функцию включения трассировки API для пользователя.  
  
 [Функция LocalDBStopInstance](../../relational-databases/express-localdb-instance-apis/localdbstopinstance-function.md)  
 Описывает функцию остановки указанного экземпляра LocalDB.  
  
 [Функция LocalDBStopTracing](../../relational-databases/express-localdb-instance-apis/localdbstoptracing-function.md)  
 Описывает функцию отключения трассировки API для пользователя.  
  
 [Функция LocalDBUnshareInstance](../../relational-databases/express-localdb-instance-apis/localdbunshareinstance-function.md)  
 Описывает функцию остановки совместного использования указанного экземпляра LocalDB.  
  
  
