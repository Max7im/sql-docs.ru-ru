---
title: Визуализация данных SQL Server с помощью R (SQL и R глубокое погружение) | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 923b8201b6948a93f0994306269c0d3338f54c2d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31202316"
---
#  <a name="visualize-sql-server-data-using-r-sql-and-r-deep-dive"></a>Визуализация данных SQL Server с помощью R (SQL и R глубокое погружение)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Расширенные пакеты в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] включают несколько функций, которые оптимизированы для масштабируемости и параллельной обработки. Обычно эти функции начинаются с префикса **rx** или **Rx**.

В этом пошаговом руководстве используется **rxHistogram** функции, чтобы просмотреть распределение значений в _creditLine_ столбца по половому признаку.

## <a name="visualize-data-using-rxhistogram"></a>Визуализация данных с помощью rxHistogram

1. Используйте следующий код R, чтобы вызвать функцию [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) и передать формулу и источник данных. Сначала эту операцию можно выполнить локально, чтобы оценить результаты и продолжительность.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Сама по себе функция **rxHistogram** вызывает функцию [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) , которая включена в пакет **RevoScaleR** . **rxCube** выводит один список (или кадра данных) содержит один столбец для каждой переменной, указанным в формуле, плюс количество столбец.
    
2. Теперь, задайте для контекста вычислений удаленный компьютер SQL Server и запустите **rxHistogram** еще раз.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
 
3. Результаты будут такими же, поскольку вы используете тот же источник данных; однако вычисления выполняются на компьютере с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Затем результаты возвращаются на локальную рабочую станцию для построения графика.
   
![Результаты в виде гистограммы](media/rsql-sue-histogramresults.jpg "Результаты в виде гистограммы")

4. Можно также вызвать **rxCube** функцией и передавать результаты для отображения на диаграмме функции R.  Например, в следующем примере функция **rxCube** используется для вычисления среднего значения *fraudRisk* для каждого сочетания значений *numTrans* и *numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Чтобы указать группы, используемые для вычисления средних значений по группам, используйте нотацию `F()` . В этом примере `F(numTrans):F(numIntlTrans)` указывает, что целых чисел в переменные `_numTrans` и `numIntlTrans` должны рассматриваться как категориальные переменные уровня для каждого целочисленное значение.
  
    Поскольку низкий и высокий уровни уже было добавлено к источнику данных `sqlFraudDS` (с помощью `colInfo` параметра), уровни, автоматически используются в гистограмме.
  
5. Значение по умолчанию возвращает значение **rxCube** — *rxCube объекта*, представляющий перекрестные таблицы. Однако при помощи функции [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) можно преобразовать результаты в кадр данных, который можно легко использовать в одной из стандартных функций формирования диаграмм языка R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    **RxCube** функция включает необязательный аргумент, *returnDataFrame* = **TRUE**, что можно использовать, чтобы преобразовать результаты в кадр данных напрямую. Например:
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Однако выходные данные функции **rxResultsDF** более понятны, и в них сохраняются имена исходных столбцов.
  
6. Наконец, выполните следующий код для создания тепловой карты с помощью `levelplot` функции из **решетки** пакет, который входит в состав все R распределения.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Результаты**
  
    ![Результаты в виде точечной диаграммы](media/rsql-sue-scatterplotresults.jpg "Результаты в виде точечной диаграммы")
  
Даже выполнив такой быстрый анализ, можно заметить, что риск мошенничества растет с увеличением как числа обычных транзакций, так и числа международных транзакций.

Дополнительные сведения о **rxCube** функции и перекрестным см в разделе [сводок по данным с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-step"></a>Следующий шаг

[Создание моделей R с помощью данных SQL Server](../../advanced-analytics/tutorials/deepdive-create-models.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание и выполнение скриптов R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
