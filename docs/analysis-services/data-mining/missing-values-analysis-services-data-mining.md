---
title: "Отсутствующие значения (службы Analysis Services — Интеллектуальный анализ данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [data mining]
- MISSING_VALUE_SUBSTITUTION
- MissingValueSubstitution property
- MISSING_VALUE_SUBSTITUTION parameter
- null values [Analysis Services]
- coding [Data Mining]
ms.assetid: 2b34abdc-7ed4-4ec1-8780-052a704d6dbe
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 78f57e86acdbcf9292e462854c97ebf4c91f79b1
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="missing-values-analysis-services---data-mining"></a>Отсутствующие значения (службы Analysis Services — интеллектуальный анализ данных)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Правильная обработка  *отсутствующих значений* является важной частью эффективного моделирования. В этом разделе объясняется, что такое отсутствующие значения, и описываются функции [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для работы с отсутствующими значениями при построении структур и моделей интеллектуального анализа данных.  
  
## <a name="definition-of-missing-values-in-data-mining"></a>Определение отсутствующих значений в интеллектуальном анализе данных  
 Отсутствующее значение может указывать на различные обстоятельства. Возможно, поле неприменимо, не произошло событие или данные не были доступными. Может быть, человек, заполнявший данные, не знал правильного значения или не заботился о заполнении этого поля.  
  
 Однако имеется много сценариев интеллектуального анализа данных, в которых недостающие значения предоставляют важную информацию. Значение отсутствующего значения в значительной степени зависит от контекста. Например, отсутствующее значение даты в списке счетов-фактур значительно отличается от отсутствующей даты в столбце, указывающем дату найма работника. Обычно в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] недостающие значения рассматриваются как информативные, а вероятности определяются таким образом, чтобы недостающие значения включались в вычисления. Это позволяет обеспечить сбалансированность моделей и не слишком большой объем существующих вариантов.  
  
 Таким образом, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляет два совершенно разных механизма для управления и расчета отсутствующих значений. Первый метод заключается в управлении обработкой значений NULL на уровне структуры интеллектуального анализа данных. При использовании второго метода реализация каждого алгоритма имеет свои отличия, но в целом этот метод определяет порядок обработки и подсчета отсутствующих значений в моделях, которые разрешают значения NULL.  
  
## <a name="specifying-handling-of-nulls"></a>Задание обработки значений NULL  
 В источнике данных отсутствующие значения могут быть представлены различными способами: как значения NULL, пустые ячейки в электронной таблице, как значение с кодом N/A или другим кодом либо как искусственное значение, например 9999. Однако для целей интеллектуального анализа данных отсутствующими считаются только значения NULL. Если данные содержат значения заполнителя вместо значений NULL, они могут повлиять на результаты модели, так что их необходимо по возможности заменить значениями NULL или ввести правильные значения. Предусмотрен набор средств, которые могут использоваться для логического вывода и заполнения требуемых значений, например преобразование «Уточняющий запрос» или задача «Профайлер данных» в службах SQL Server Integration Services, а также средство «Заполнение по примеру», предоставляемое в надстройках интеллектуального анализа данных для Excel.  
  
 Если моделируемая задача требует, чтобы какой-то столбец не мог ни при каких обстоятельствах содержать отсутствующие значения, то при определении структуры интеллектуального анализа данных для столбца необходимо применить флаг модели **NOT_NULL** . Этот флаг указывает, что обработка должна окончиться неудачей, если в некотором варианте будет отсутствовать соответствующее значение. Если при обработке модели возникнет эта ошибка, можно зарегистрировать эту ошибку в журнале и предпринять шаги по исправлению данных, предоставляемых для модели.  
  
## <a name="calculation-of-the-missing-state"></a>Расчет отсутствующего состояния  
 В рассматриваемом алгоритме интеллектуального анализа данных недостающие значения являются информативными. В таблицах вариантов состояние **Missing** рассматривается как допустимое состояние, подобно любому другому состоянию. Кроме того, в модели интеллектуального анализа данных могут использоваться другие значения для прогнозирования того, является ли некоторое значение недостающим. Иными словами, тот факт, что некоторое значение отсутствует, не является ошибкой.  
  
 При создании модели интеллектуального анализа данных для всех дискретных столбцов модели автоматически добавляется состояние **Missing** . Например, если входной столбец для представления пола [Gender] содержит два возможных значения, Male (мужской) и Female (женский), то автоматически добавляется третье значение для представления значения **Missing** , а гистограмма, показывающая распределение всех значений для этого столбца, всегда включает данные о количестве вариантов со значениями **Missing** . Если в столбце Gender отсутствуют недостающие значения, то гистограмма показывает, что состояние Missing обнаружено в 0 вариантах.  
  
 Включение состояния **Missing** по умолчанию имеет смысл, если есть основание полагать, что в данных могут отсутствовать примеры всех возможных значений, но не должно быть так, чтобы модель исключала данную вероятность лишь потому, что в данных нет соответствующего примера. Например, даже если данные о сбыте, относящиеся к какому-то магазину, показали, что все клиенты, приобретавшие определенный продукт, оказались женщинами, то вряд ли следует создавать модель, которая прогнозирует, что данный продукт могут приобретать только женщины. Вместо этого в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] добавляется заполнитель для дополнительного неизвестного значения, называемый **Missing**, который становится основой способа учета других возможных состояний.  
  
 Например, в следующей таблице показано распределение значений для узла (All) в модели дерева решений, созданной для занятия «Покупатель велосипеда». В сценарии, рассматриваемом в этом примере, столбец [Bike Buyer] представляет собой прогнозируемый атрибут, где 1 обозначает «Да», а 0 — «Нет».  
  
|Значение|Варианты|  
|-----------|-----------|  
|0|9296|  
|1|9098|  
|Missing|0|  
  
 Это распределение показывает, что приблизительно половина клиентов приобрела велосипед, а другая половина — нет. Этот конкретный набор данных является очень качественным, поэтому для каждого варианта в столбце [Bike Buyer] предусмотрено значение, а количество значений, помеченных как **Missing** (отсутствует), равно 0. Однако если в некотором случае в столбце [Bike Buyer] будет обнаружено значение NULL, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] будут рассматривать эту строку как случай со значением **Missing** .  
  
 Если входные данные представляют собой непрерывный столбец, то в данной модели два возможных состояния для атрибута были бы сведены в таблицу: **Existing** и **Missing**. Иными словами, столбец либо содержит значение с некоторым числовым типом данных, либо не содержит никакого значения. Для вариантов, в которых значение имеется, в этой модели вычисляется среднее, стандартное отклонение и другие значимые статистические показатели. Для вариантов, в которых значение отсутствует, в этой модели предоставляются данные о количестве значений **Missing** , а также корректируются прогнозы соответствующим образом. Применяемый метод корректировки прогнозов зависит от алгоритма и рассматривается в следующем разделе.  
  
> [!NOTE]  
>  Что касается атрибутов во вложенной таблице, недостающие значения там не являются информативными. Например, если некоторый клиент не приобрел определенный продукт, то во вложенной таблице **Products** будет отсутствовать строка, соответствующая этому продукту, а в модели интеллектуального анализа данных не появится атрибут, относящийся к отсутствующему продукту. Но если интерес представляют клиенты, которые не приобрели определенные продукты, то можно создать модель, предусматривающую фильтрацию по критерию отсутствия продуктов во вложенной таблице, используя инструкцию NOT EXISTS в фильтре модели. Дополнительные сведения см. в разделе [Применение фильтра к модели интеллектуального анализа данных](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md).  
  
## <a name="adjusting-probability-for-missing-states"></a>Корректировка вероятности для отсутствующих состояний  
 Кроме подсчета значений службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] вычисляют вероятность любого значения по всему набору данных. Это касается и значения **Missing** . Например, в следующей таблице показана вероятность, относящаяся к вариантам в предыдущем примере.  
  
|Значение|Варианты|Вероятность|  
|-----------|-----------|-----------------|  
|0|9296|50.55%|  
|1|9098|49.42%|  
|Missing|0|0.03%|  
  
 Может показаться странным, что вычисленная вероятность появления значения **Missing** равна 0,03 %, хотя число таких случаев равно 0. На самом деле такое поведение предусмотрено изначально и позволяет обеспечить разумную обработку моделью неизвестных значений.  
  
 Обычно вероятность рассчитывается как количество благоприятных вариантов, деленное на количество всех возможных вариантов. В этом примере алгоритм вычисляет сумму количества вариантов, соответствующих определенному условию ([Bike Buyer] = 1 или [Bike Buyer] = 0), после чего полученное значение делится на общее количество строк. Однако чтобы учесть варианты **Missing** , к количеству всех возможных вариантов добавляется 1. В результате вероятность неизвестного варианта больше не равна нулю, но составляет очень небольшую величину, которая указывает, что это состояние просто маловероятно, но возможно.  
  
 Добавление небольшого значения **Missing** не приводит к изменению результата прогноза, однако позволяет усовершенствовать моделирование в сценариях, где данные с предысторией не содержат все возможные исходы.  
  
> [!NOTE]  
>  Поставщики интеллектуального анализа данных различаются способами обработки недостающих значений. Например, некоторые поставщики исходят из предположения, что недостающие данные во вложенном столбце являются разреженным представлением, а наличие недостающих данных в невложенном столбце определяется случайным распределением.  
  
 Если достоверно известно, что в данных определены все исходы и нужно исключить возможность корректировки вероятностей, необходимо задать флаг модели NOT_NULL для соответствующего столбца в структуре интеллектуального анализа данных.  
  
> [!NOTE]  
>  Каждый алгоритм, включая пользовательские алгоритмы, которые могут быть получены из подключаемого модуля стороннего разработчика, может обрабатывать отсутствующие значения по-разному.  
  
### <a name="special-handling-of-missing-values-in-decision-tree-models"></a>Специальная обработка недостающих значений в моделях дерева принятия решений  
 В алгоритме дерева принятия решений (Майкрософт) вероятности недостающих значений вычисляются иначе по сравнению с другими алгоритмами. Алгоритм дерева принятия решений не просто прибавляет 1 к общему количеству вариантов, а использует немного другую формулу для корректировки с учетом состояний **Missing** .  
  
 В модели дерева принятия решений вероятность состояния **Missing** рассчитывается следующим образом:  
  
 ВероятностьСостояния = (АприорнаяВероятностьУзла)* (НесущееМножествоСостояния + 1) / (НесущееМножествоУзла + ВсегоСостояний).  
  
Алгоритм дерева принятия решений предоставляет возможность проведения дополнительной корректировки, что в алгоритме компенсировать присутствие фильтров на модели, которая может вызвать исключение многих состояний для исключения во время обучения.  
  
 В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]предусмотрено, что если некоторое состояние присутствует во время обучения, но при этом обнаруживается, что это состояние в определенном узле имеет нулевое несущее множество, то выполняется стандартная корректировка. Однако, если состояние ни разу не обнаружено во время обучения, алгоритм задает его вероятность равной нулю. Эта корректировка применяется не только к состоянию **Missing** , но и к состояниям, которые существуют в обучающих данных, но имеют нулевое несущее множество в результате фильтрации модели.  
  
 Эта дополнительная корректировка приводит к тому, что вступает в силу следующая формула.  
  
 StateProbability = 0.0, если это состояние имеет нулевое несущее множество в обучающем наборе  
  
 ELSE ВероятностьСостояния = (АприорнаяВероятностьУзла)* (НесущееМножествоСостояния + 1) / (НесущееМножествоУзла + ВсегоСостоянийСНенулевымНесущимМножеством)  
  
 Результатом применения этой корректировки является поддержание стабильности дерева.  
  
## <a name="related-tasks"></a>Связанные задачи  
 В следующих разделах приведены дополнительные сведения об обращении с отсутствующими значениями.  
  
|Задания|Ссылки|  
|-----------|-----------|  
|Добавление флагов к отдельным столбцам модели для управления обработкой отсутствующих значений|[Просмотр или изменение модели флаги &#40; интеллектуального анализа данных &#41;](../../analysis-services/data-mining/view-or-change-modeling-flags-data-mining.md)|  
|Установка свойств модели интеллектуального анализа данных для управления обработкой отсутствующих значений|[Изменение свойств модели интеллектуального анализа данных](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)|  
|Задание флагов модели в расширениях интеллектуального анализа данных|[Флаги моделирования &#40; расширений интеллектуального анализа данных &#41;](../../dmx/modeling-flags-dmx.md)|  
|Изменение способа обработки структурой интеллектуального анализа данных отсутствующих значений|[Изменить свойства структуры интеллектуального анализа данных](../../analysis-services/data-mining/change-the-properties-of-a-mining-structure.md)|  
  
## <a name="see-also"></a>См. также  
 [Содержимое модели интеллектуального анализа данных &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)   
 [Моделирование флаги &#40; интеллектуального анализа данных &#41;](../../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
  
