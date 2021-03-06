---
title: "Функциональные возможности клиента ADOMD.NET | Документы Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: 0f5e16a1-dc2d-4c87-8551-985921bf069b
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 59d5086aaba3fbf1ebe8581031f30f3313a51938
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="adomdnet-client-functionality"></a>Функциональные возможности клиента ADOMD.NET
  Как и другие поставщики данных платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, ADOMD.NET выступает в качестве моста между приложением и источником данных. Однако ADOMD.NET отличается от остальных поставщиком данных платформы .NET Framework тем, что он работает с аналитическими данными. Для этого компонент ADOMD.NET обладает функциями, которые в значительной степени отличаются от функций других поставщиков данных платформы .NET Framework. ADOMD.NET позволяет получать не только данные, но и метаданные, а также изменять структуру источника аналитических данных.  
  
 **Получение метаданных**  
 Доступ к метаданным через наборы строк схемы или модели объектов дает приложению возможность больше узнать о тех данных, которые можно получить из источника данных. Доступны также такие данные, как типы каждого из ключевых показателей эффективности, измерения в кубе и параметры, необходимые модели интеллектуального анализа данных. Метаданных является наиболее важным для *динамическое* приложений, которые требуют ввод данных пользователем для определения типа, глубины и области данных, требуется получить. Это Query Analyzer, Microsoft Excel и другие средства запросов. Метаданные не так критично для *статических* приложений, выполняющих набор стандартных действий.  
  
 Дополнительные сведения: [получение метаданных из источника аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md).  
  
 **Извлечение данных**  
 Получение данных — это фактическое получение сведений, хранящихся в источнике данных. Получение данных является основной функцией «статических» приложений, которым известна его структура. Получение данных также является конечным результатом «динамических» приложений. Значение ключевого показателя эффективности в заданное время суток, количество велосипедов, проданных за последний час в каждом из магазинов, и факторы, влияющие на среднегодовую производительность сотрудников, — вот примеры данных, которые можно получить. Получение данных важно для любого приложения, выполняющего запросы.  
  
 Дополнительные сведения: [получение данных из источника аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md).  
  
 **Изменение структуры аналитических данных**  
 Компонент ADOMD.NET также может быть использован для физического изменения структуры хранилища аналитических данных. Хотя обычно это делается с помощью модели объектов AMO, компонент ADOMD.NET позволяет отправлять команды на языке сценариев служб Analysis Services (язык ASSL) для создания, изменения и удаления объектов на сервере.  
  
 Дополнительные сведения: [выполнение команд для аналитических источника данных](../../analysis-services/multidimensional-models-adomd-net-client/executing-commands-against-an-analytical-data-source.md), [разработку с помощью объектов AMO &#40; Объекты AMO &#41; ](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md), [Служб analysis Services, язык сценариев &#40; ASSL для XMLA &#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)  
  
 Извлечение метаданных, извлечение данных и изменение структуры данных происходит в определенной точке рабочего процесса обычного приложения ADOMD.NET.  
  
## <a name="typical-process-flow"></a>Типичная последовательность операций  
 При работе с аналитической базой данных стандартные приложения ADOMD.NET обычно выполняют один и тот же рабочий процесс.  
  
1.  Сначала при помощи объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> устанавливается соединение с базой данных. При открытии соединения объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> предоставляет доступ к метаданным о сервере, с которым установлено соединение. Динамические приложения обычно отображают часть этих сведений пользователю, чтобы он смог, например, выбрать куб, к которому будут выполняться запросы. Приложение может повторно использовать соединение, созданное на этом этапе, что приводит к снижению издержек.  
  
     Дополнительные сведения: [Establishing Connections in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)  
  
2.  После установления соединения динамическое приложение запрашивает с сервера другие специфичные метаданные. При создании статического приложения программист заранее знает, к каким объектам будет выполнять запросы приложение, что делает получение метаданных ненужным. Полученные метаданные могут быть использованы приложением или пользователем на следующем шаге.  
  
     Дополнительные сведения: [получение метаданных из источника аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
3.  Приложение выполняет команду на сервере. Целью выполнения команды может быть получение дополнительных метаданных, получение данных или изменение структуры базы данных. Для любой из этих задач приложение может либо использовать ранее определенный запрос, либо создать новый запрос на основе только что полученных данных.  
  
     Дополнительные сведения: [получение метаданных из источника аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md), [получение данных из источника аналитических данных](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md), [выполнение команд для аналитических источника данных](../../analysis-services/multidimensional-models-adomd-net-client/executing-commands-against-an-analytical-data-source.md)  
  
4.  Получив команду, сервер начинает возвращать клиенту данные или метаданные. Эти сведения можно просмотреть с помощью <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> объекта, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> объекта, или **System.XmlReader** объекта.  
  
 В следующем примере, чтобы проиллюстрировать этот стандартный рабочий процесс, содержится метод, который открывает соединение с базой данных, выполняет команду в известном кубе и извлекает результаты в набор ячеек. Затем набор ячеек возвращает строку, разделенную знаками табуляции, которая содержит заголовки столбцов, заголовки строк и данные ячеек.  
  
 [!code-cs[Adomd.NetClient#ReturnCommandUsingCellSet](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/adomd-net-client-functio_1.cs)]  
  
## <a name="see-also"></a>См. также  
 [Программирование клиента ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
