---
title: Определение формата текста (текстовый файл драйвер) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- text format [ODBC]
- text file driver [ODBC], text format
ms.assetid: 3af46dad-52cc-4d5c-a27e-6315d65a74e6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4b8d87785ccb63796698e164b36728301d3c35e5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904879"
---
# <a name="defining-text-format-text-file-driver"></a>Определение формата текста (текстовый файл драйвер)
При использовании драйвера текста можно использовать **Определение текстового формата** для определения формата столбцов в выбранном файле используется диалоговое окно. Это диалоговое окно позволяет указать схемы для каждой таблицы данных. Эта информация записывается в файл Schema.ini в каталоге источника данных. Для каждого каталога источника данных текст создается отдельный файл Schema.ini.  
  
> [!NOTE]  
>  Один и тот же формат файлов по умолчанию применяется для всех новых таблиц данных в текст. Все файлы, созданные инструкцией CREATE TABLE наследуют эти же по умолчанию формат значения, которые устанавливаются путем выбора значения формата файла в **Определение текстового формата** диалоговое окно с \<по умолчанию > выбранным в **Таблиц** списка. Текстовый драйвер не изменяет формат существующего текстового файла в соответствии с форматом, определенные в этом диалоговом окне, но возвращает ошибку, если он использует формат, например при попытке получения данных из текстового файла.  
  
 Следующие параметры доступны в **Определение текстового формата** диалоговое окно:  
  
|Параметр|Сведения|  
|------------|-----------------|  
|**Добавить**|Добавляет столбец, используя значения из **тип данных**, **имя**, и **ширина** из диалогового окна, и если применимо, разделитель компонентов даты значение из Schema.ini.|  
|**Символы**|**ANSI** или **OEM**. OEM указывает набор символов, не удовлетворяющую стандарту ANSI. По умолчанию используется OEM Если формат элемента, выбранного в **таблиц** списка не было определено ранее с данным диалоговым окном.|  
|**Заголовок с именами столбцов**|Указывает, будут ли использоваться в качестве имен столбцов столбцы из первой строки выбранной таблицы. Либо **TRUE** или **FALSE**. По умолчанию используется значение FALSE, если формат элемента, выбранного в **таблиц** списка не было определено ранее с данным диалоговым окном.|  
|**Столбцы**|Список имен столбцов для каждого столбца в выбранной таблице. Порядок столбцов соответствует порядку столбцов в таблице. Этот список доступен в том случае, если файл был выбран в **таблиц** списка.|  
|**Тип данных**|Может быть бит, БАЙТОВ, CHAR, валюты, даты, число с плавающей запятой, целое число со знаком, LONGCHAR, SHORT или один. Типы данных даты можно в следующих форматах: «дд ммм гг», «мм дд гг», «ммм дд гг», «гггг мм дд» или «гггг мм дд». «мм» обозначает номера названия месяца. «МММ» обозначает буквы месяцев.|  
|**разделитель**|Определяет символ пользовательский разделитель, используемый для разделения столбцов. Если задан **разделители** выбран формат. Разделитель может быть только один символ, а двойные кавычки ("") не может использоваться в качестве разделителя. (Разделитель не может быть указан в шестнадцатеричном или десятичном формате.)|  
|**Формат**|С разделителями или фиксированной длины. Если с разделителями, указывает тип разделителя: специальный символ (пользовательский), табуляции или запятыми (CSV). По умолчанию используется **CSV с разделителями** Если формат элемента, выбранного в **таблиц** списка не было определено ранее с данным диалоговым окном.<br /><br /> Если **формат** является фиксированной длины и **заголовок с именами столбцов** имеет значение TRUE, первая строка должна быть с разделителями запятыми.|  
|**Прогноз**|Автоматически создает значения данных столбца тип, имя и ширина столбцов в выбранной таблице путем сканирования содержимого таблицы в соответствии с **формат** поле выделения. Включить, если в качестве разделителя в формате таблицы. Все ранее определенные столбцы в **столбцы** списка удаляются и заменяются новыми записями. Если **заголовок с именами столбцов** — не выбран, имена столбцов создаются автоматически как «F1», «F2» и т. д. Значение по умолчанию не отображается в **тип данных** поле.<br /><br /> Эта функция работает только на столбцы, которые являются превышает 64 513 байт.|  
|**Изменение**|Изменяет выбранного столбца, используя значения в **тип данных**, **имя**, и **ширина**.|  
|**Название**|Отображает имя выбранного столбца. Можно использовать для указания нового имени существующего или нового столбца.<br /><br /> Если **заголовок с именами столбцов** имеет значение TRUE, в столбце имя отображается учитывается.|  
|**Удалить**|Удаление выбранного столбца.|  
|**Строк для просмотра**|Число строк, программа установки или драйвер при настройке столбцов и типов данных столбцов на основе существующих данных.<br /><br /> Можно ввести число от 1 до 32767 для числа строк для сканирования. По умолчанию используется значение 25, если формат элемента, выбранного в **таблиц** списка не было определено ранее с данным диалоговым окном. (Число за пределами ограничение будет возвращена ошибка.)|  
|**Таблицы**|Содержит список всех файлов в каталоге, выбранного в **Установка текстового** диалоговое окно, соответствующих списку расширений, указанных.<br /><br /> При \<по умолчанию > выбран, и одно из следующих равно "true", значения атрибутов таблицы в **таблиц** группы записываются в файл Schema.ini (никаких других записей Schema.ini соприкасающиеся):<br /><br /> -Уже не Schema.ini в указанном каталоге.<br />-Файл Schema.ini существует, но нет раздела в файл Schema.ini для одного из текстовых файлов (с определенным расширением) в каталоге.<br />-В разделе в текстовый файл существует в Schema.ini, но текст является пустым.<br /><br /> Когда \<по умолчанию > выбран, **столбцы** группа отключена.|  
|**Ширина**|Для столбцов типа CHAR и LONGCHAR можно изменить ширину столбца. Ширина по умолчанию имеет значение 1, если формат элемента, выбранного в **таблиц** списка не было определено ранее с данным диалоговым окном.<br /><br /> Для других типов данных ширина элемента управления будет отключена, а значение не отображается.|
