---
title: Создание диаграмм и графиков с помощью SQL и R (Пошаговое руководство) | Документы Microsoft
ms.date: 11/10/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: e7c40d76a585e021fac13094a524e32ff4da0a45
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="create-graphs-and-plots-using-sql-and-r-walkthrough"></a>Создание диаграмм и графиков с помощью SQL и R (Пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой части пошагового руководства вы узнаете способы создания диаграмм и карт с помощью R с данными SQL Server. Создание простых гистограмм, чтобы получить некоторый практический опыт и затем разрабатывать более сложные построения карты.

### <a name="create-a-histogram"></a>Создать гистограмму

1. Создайте первую диаграмму с помощью функции [rxHistogram](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource) .  Функция rxHistogram предоставляет функциональность, аналогичную, в пакеты R с открытым кодом, но можно запустить в контексте удаленного выполнения.

    ```R
    # Plot fare amount on SQL Server and return the plot
    start.time <- proc.time()
    rxHistogram(~fare_amount, data = inDataSource, title = "Fare Amount Histogram")
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2), " seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate plot.", sep=""))
    ```

2. Изображение возвращается в графическом устройстве R вашей среды разработки.  Например, в RStudio откройте окно **Plot** (График).  В [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]открывается отдельное графическое окно.

    ![использование rxHistogram для построения диаграммы сумм оплаты](media/rsql-e2e-rxhistogramresult.png "использование rxHistogram для построения диаграммы сумм оплаты")

    > [!NOTE]
    > Диаграммы выглядят иначе?
    >  
    > Причина этого заключается в _inDataSource_ использует только первые 1000 строк. Упорядочение строк с помощью предложения TOP является недетерминированным отсутствует предложение ORDER BY, поэтому предполагается, что данные и полученный граф может различаться.
    > Конкретно это изображение было создано с использованием приблизительно 10 000 строк данных. Мы рекомендуем поэкспериментировать с разным числом строк, чтобы получить разные графики, и обратить внимание на то, как долго возвращаются результаты в вашей среде.

### <a name="create-a-map-plot"></a>Создать диаграмму карты

Как правило серверы баз данных заблокировать доступ к Интернету. Это может оказаться неудобным при использовании пакетов R, которые нужно загрузить карты или других изображений для создания графиков. Однако имеется обходной путь, который могут оказаться полезными при разработке приложения. По сути создать представление карты на стороне клиента и затем наложения на карте точек, которые хранятся в таблице SQL Server в виде атрибутов.

1. Определите функцию, которая создает объект R построения. Пользовательская функция *mapPlot* создает точечную диаграмму, использует расположения раскладки такси, а затем число и которые запущены от каждого расположения. Она использует пакеты **ggplot2** и  **ggmap** , которые уже должны быть установлены и загружены.

    ```R
    mapPlot <- function(inDataSource, googMap){
        library(ggmap)
        library(mapproj)
        ds <- rxImport(inDataSource)
        p <- ggmap(googMap)+
        geom_point(aes(x = pickup_longitude, y =pickup_latitude ), data=ds, alpha =.5,
    color="darkred", size = 1.5)
        return(list(myplot=p))
    }
    ```

    + *MapPlot* функция принимает два аргумента: существующего объекта данных, которые вы определили ранее с помощью RxSqlServerData и представления карты, переданные от клиента.
    + В строке, начинающейся с *доменных служб Active Directory* переменной rxImport, используемой для загрузки в памяти данных из источника данных ранее созданный *inDataSource*. (Этот источник данных содержит только 1000 строк, если вы хотите создать схему с большим количеством точек данных, можно заменить другой источник данных.)
    + При использовании **открытой** функций R, данные должны быть загружены в блоки данных в локальной памяти. Тем не менее, путем вызова [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) функции, можно выполнить в памяти контекста удаленных вычислений.

2. Измените контекст вычислений локальную и загружать библиотеки, необходимые для создания карты.

    ```R
    rxSetComputeContext("local")
    library(ggmap)
    library(mapproj)
    gc <- geocode("Times Square", source = "google")
    googMap <- get_googlemap(center = as.numeric(gc), zoom = 12, maptype = 'roadmap', color = 'color');
    ```

    + В переменной `gc` хранится набор координат площади Таймс-сквер в Нью-Йорке.

    + Строка, начинающаяся с `googmap` , создает карту с указанными координатами в центре.

3. Перейдите в контексте вычислений SQL Server и отображения результатов, заключив функции построения в [rxExec](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxexec) как показано ниже. Функция rxExec является частью **RevoScaleR** пакета и поддерживает выполнение произвольного функций R в контексте удаленных вычислений.

    ```R
    rxSetComputeContext(sqlcc)
    myplots <- rxExec(mapPlot, inDataSource, googMap, timesToRun = 1)
    plot(myplots[[1]][["myplot"]]);
    ````

    + Данные карты в `googMap` передается в качестве аргумента в функцию выполняемый удаленно *mapPlot*. Поскольку карт были созданы в локальной среде, они должны быть переданы функции для создания графика в контексте SQL Server.

    + Если в строке, начинающейся с `plot` запусков, готовый для просмотра данных сериализуется обратно в локальной среде R, чтобы можно было просматривать в клиентском приложении R.

    > [!NOTE]
    > Если вы используете SQL Server в виртуальной машине Azure, может появиться ошибка на этом этапе. Это, так как по код R в Azure правило брандмауэра по умолчанию блокирует доступ к сети. Дополнительные сведения по устранению этой ошибки см. в разделе [Установка служб R на виртуальной Машине Azure](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md).

4. На следующем рисунке показана итоговая диаграмма. Места посадки обозначены на карте красными точками. Образ может выглядеть иначе, в зависимости от того, сколько расположения в источнике данных, которая использовалась.

    ![отображение диаграммы поездок в такси с помощью пользовательской функции R](media/rsql-e2e-mapplot.png "отображение диаграммы поездок в такси с помощью пользовательской функции R")

## <a name="next-lesson"></a>Следующее занятие

[Создание компонентов данных, с помощью R и SQL](/walkthrough-create-data-features.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Сведение данных с помощью R](/walkthrough-view-and-summarize-data-using-r.md)
