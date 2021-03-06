---
title: "Просмотр свойств куба и измерения | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: dda922b8-6d75-4662-b09e-8a317c6a1c70
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: d0913972ef2ca0b1c40c0e23d3d189a6149809cf
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="lesson-2-4---reviewing-cube-and-dimension-properties"></a>Занятие 2-4 - свойств Просмотр куба и измерения
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

После определения свойств куба можно просмотреть результаты в конструкторе кубов. В следующей задаче предстоит просмотреть структуру куба проекта [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.  
  
### <a name="to-review-cube-and-dimension-properties-in-cube-designer"></a>Просмотр свойств куба и измерений в конструкторе кубов  
  
1.  Чтобы открыть конструктор кубов, в обозревателе решений в узле **Кубы** дважды щелкните куб **Учебник по службам Analysis Services** .  
  
2.  Чтобы просмотреть определенные меры,на панели **Меры** вкладки **Структура куба** конструктора кубов раскройте группу мер **Internet Sales** .  
  
    Можно изменить порядок отображения этих мер, перетаскивая их и выстраивая в желаемой последовательности. Такой порядок влияет на очередность использования этих мер определенными клиентскими приложениями. Эта группа мер и каждая содержащаяся в ней мера имеют свойства, которые можно изменять в окне свойств.  
  
3.  На панели **Измерения** вкладки **Структура куба** конструктора кубов просмотрите измерения куба [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.  
  
    Обратите внимание, что в кубе [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial доступно пять измерений, хотя на уровне базы данных было создано только три измерения, что отражено в обозревателе решений. Куб имеет больше измерений, чем база данных, потому что измерение Date в базе данных служит основой для трех отдельных измерений куба, связанных с датами. Эти измерения основаны на разных связанных с датами фактах из таблицы фактов. Эти измерения даты называются также *ролевыми измерениями*. Три измерения даты куба дают пользователям возможность разделить куб по трем отдельным фактам, связанным с каждой продажей: дате заказа товара, сроку выполнения заказа и дате отгрузки заказа. Повторно используя одно измерение базы данных для нескольких измерений куба, службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] упрощают управление измерениями, используют меньше места на диске и уменьшают общее время обработки данных.  
  
4.  На панели **Измерения** вкладки **Структура куба** раскройте измерение **Customer**, а затем нажмите кнопку **Изменить Customer** , чтобы открыть это измерение в конструкторе измерений.  
  
    Конструктор измерений содержит следующие вкладки: **Структура измерения**, **Связи атрибутов**, **Переводы**и **Браузер**. Обратите внимание, что вкладка **Структура измерения** содержит три панели: **Атрибуты**, **Иерархии**и **Представление источника данных**. Атрибуты, содержащиеся в измерении, отображаются на панели **Атрибуты** . Дополнительные сведения см. в разделах [Справочник по свойствам атрибута измерения](../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md), [Создание пользовательских иерархий](../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)и [Определение связей атрибутов](../analysis-services/multidimensional-models/attribute-relationships-define.md).  
  
5.  Чтобы переключиться к конструктору кубов, щелкните правой кнопкой мыши **Учебник по службам Analysis Services** в узле **Кубы** в обозревателе решений и выберите пункт **Конструктор представлений**.  
  
6.  В конструкторе кубов перейдите на вкладку **Использование измерений** .  
  
    В этом представлении куба [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial показаны измерения куба, используемые группой мер Internet Sales. Также можно определить тип связи между каждым измерением и каждой группой мер, в которой оно используется.  
  
7.  Перейдите на вкладку **Секции** .  
  
    Мастер кубов определяет единственную секцию для куба с использованием режима хранения результатов многомерной интерактивной аналитической обработки данных (MOLAP) без статистических выражений. Для обработки MOLAP все данные конечного уровня и все статистические выражения хранятся в кубе, чтобы обеспечить максимальную производительность. Статистические выражения представляют собой предварительно вычисленные сводные данные, которые содержат ответы на еще не заданные вопросы, что позволяет сократить время до получения ответа на запрос. На вкладке **Секции** можно определять дополнительные секции, параметры хранения и настройки обратной записи. Дополнительные сведения см. в разделе [Секции (службы Analysis Services — многомерные данные)](../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md), [Агрегаты и статистические схемы](../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
8.  Перейдите на вкладку **Браузер** .  
  
    Обратите внимание, что куб нельзя просмотреть, поскольку он еще не был развернут на экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. На данном этапе куб в проекте [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial представляет собой лишь определение куба, его можно развернуть на любом экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Во время развертывания и обработки куба создаются определенные объекты в экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , которые затем заполняются данными из базовых источников данных.  
  
9. В обозревателе решений щелкните правой кнопкой мыши **Учебник по службам Analysis Services** в узле **Кубы** и выберите пункт **Просмотр кода**. Возможно, потребуется подождать.  
  
    XML-код для куба "Учебник по [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] " отображается на вкладке **[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.cube [XML]** . Это фактический код, используемый для создания куба в экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в процессе развертывания. Дополнительные сведения см. в разделе [Просмотр XML-кода проекта служб Analysis Services (среда SSDT)](../analysis-services/multidimensional-models/view-the-xml-for-an-analysis-services-project-ssdt.md).  
  
10. Закройте вкладку XML-кода.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Развертывание проекта служб Analysis Services](../analysis-services/lesson-2-5-deploying-an-analysis-services-project.md)  
  
## <a name="see-also"></a>См. также  
[Просмотр данных измерения в конструкторе измерений](../analysis-services/multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md)  
  
  
  
