---
title: "Шаг 5: Проверка учебного пакета занятия 4 | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 68e4545ee2eae96664007a8dc69c9953c0351107
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-4-5---testing-the-lesson-4-tutorial-package"></a>Занятие 4-5-Проверка учебного пакета занятия 4
На стадии выполнения произойдет ошибка поиска соответствия при работе преобразования «Уточняющий запрос» для Currency Key в поврежденном файле Currency_BAD.txt. Так как вывод ошибок преобразования «Уточняющий запрос» для Currency Key настроен на перенаправление строк новому адресату «неудачные обращения», операция не завершится ошибкой, и пакет будет успешно выполнен. Все ошибочные строки будут записаны в файл ErrorOutput.txt.  
  
В этой задаче требуется проверить измененную конфигурацию вывода ошибок, запустив пакет на выполнение. После успешного выполнения пакета проверьте содержимое файла ErrorOutput.txt.  
  
> [!NOTE]  
> Если нет необходимости накапливать ошибочные строки в файле ErrorOutput.txt, нужно вручную очистить содержимое файла между выполнениями пакета.  
  
## <a name="checking-the-package-layout"></a>Проверка макета пакета  
Перед проверкой пакета нужно проверить, что поток управления и данных в пакете занятия 4 содержит объекты, показанные на следующих диаграммах. Поток управления должен быть таким же, как и поток управления в занятиях 2 — 4.  
  
**Поток управления**  
  
![Поток в пакете управления](../integration-services/media/task4lesson2control.gif "поток в пакете управления")  
  
**Поток данных**  
  
![Поток данных в пакете](../integration-services/media/task5lesson5data.gif "потока данных в пакете")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>Выполнение учебного пакета занятия 4  
  
1.  В меню **Отладка** выберите команду **Начать отладку**.  
  
2.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
### <a name="to-verify-the-contents-of-the-erroroutputtxt-file"></a>Проверка содержимого файла ErrorOutput.txt  
  
-   Откройте файл ErrorOutput.txt в приложении «Блокнот» или другом текстовом редакторе. Порядок столбцов по умолчанию: AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription.  
  
    Обратите внимание, что все строки файла содержат несовпадающие значения в столбце CurrencyID, значение столбца ErrorCode равно -1071607778, значение столбца ErrorColumn равно 0 и значение столбца ErrorDescription равно «В результате уточняющего запроса для строки не обнаружено соответствия». Значение столбца ErrorColumn равно 0, поскольку ошибка не является специфической для данного столбца. Это неудавшаяся операция уточняющего запроса. .  
  
  
  
