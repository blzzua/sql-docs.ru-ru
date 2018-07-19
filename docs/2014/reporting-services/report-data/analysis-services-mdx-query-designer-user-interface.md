---
title: Пользовательский интерфейс конструктора запросов многомерных выражений для служб Analysis Services (построитель отчетов) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10012"
- sql12.rtp.rptdesigner.dataview.asquerydesigner.f1
helpviewer_keywords:
- MDX [Reporting Services], creating datasets
- query designers [Reporting Services]
ms.assetid: d9c7c0b3-fce4-4a65-b679-408273e6a925
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f322526680b3a91f2fcb7e93e3159f79b79793a6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323854"
---
# <a name="analysis-services-mdx-query-designer-user-interface"></a>Пользовательский интерфейс конструктора запросов многомерных выражений служб Analysis Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] предоставляют графические конструкторы запросов для построения запросов многомерных выражений (MDX) и выражений интеллектуального анализа данных (DMX) запрашивает [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] источника данных. Данный раздел посвящен конструктору запросов многомерных выражений. Дополнительные сведения о конструкторе запросов расширений интеллектуального анализа данных см. в разделе [тип соединения служб Analysis Services для расширений интеллектуального анализа данных &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md).  
  
 Графический конструктор запросов многомерных выражений имеет два режима: режим конструктора и режим запросов. В каждом режиме есть панель метаданных, из которой можно перетаскивать элементы с выбранного куба для построения запроса многомерных выражений, который извлекает данные в ходе обработки отчета.  
  
> [!IMPORTANT]  
>  При создании и выполнении запросов пользователи получают доступ к источникам данных. Следует предоставить минимальные разрешения на источники данных, например разрешение только на чтение.  
  
## <a name="graphical-mdx-query-designer-in-design-mode"></a>Графический конструктор запросов многомерных выражений: режим конструктора  
 При изменении запроса многомерных выражений для набора данных отчета графический конструктор запросов многомерных выражений откроется в режиме конструктора.  
  
 На следующем рисунке отмечены панели в режиме конструктора.  
  
 ![Конструктор запросов многомерных выражений служб Analysis Services, режим конструктора](../../analysis-services/media/rsqd-dsawas-mdx-designmode.gif "Конструктор запросов многомерных выражений служб Analysis Services, режим конструктора")  
  
 В следующей таблице перечисляются панели, доступные в этом режиме.  
  
|Панель|Компонент|  
|----------|--------------|  
|Кнопка "Выбрать куб" (**...**)|Отображает куб, выбранный в настоящий момент.|  
|Панель «Метаданные»|Отображает список мер в иерархическом порядке, ключевые показатели эффективности (KPIs) и измерения, определенные для выбранного куба.|  
|Панель «Вычисляемые элементы»|Отображает вычисляемые элементы, определенные на данный момент и доступные для использования в запросе.|  
|Панель «Фильтр»|Используется для выбора измерений и относящихся к ним иерархий для фильтрации данных источника и ограничения данных, возвращенных отчету.|  
|Панель «Данные»|Отображает заголовки столбцов для результирующего набора в ходе перетаскивания элементов с панели «Метаданные» и панели «Вычисляемые элементы». Автоматически обновляет результирующий набор, если выбрана кнопка **Автовыполнение** . , и делает это по-другому.|  
  
 Можно перетаскивать измерения, меры и ключевые показатели эффективности с панели «Метаданные», а вычисляемые элементы с панели «Вычисляемые элементы» на панель «Данные». На панели «Фильтр» можно выбрать измерения и относящиеся к ним иерархии, а также задать критерии фильтра для ограничения данных, доступных запросу. При выборе переключателя **Автовыполнение** (![Автоматическое выполнение запроса](../../analysis-services/media/rsqdicon-autoexecute.gif "Автоматическое выполнение запроса")) на панели инструментов конструктор запросов выполняет запрос каждый раз при помещении объекта метаданных на панель "Данные". Запрос можно выполнить вручную, нажав кнопку **Запуск** (![Выполнение запроса](../../analysis-services/media/rsqdicon-run.gif "Выполнение запроса")) на панели инструментов.  
  
 При создании запроса многомерных выражений в данном режиме следующие дополнительные свойства автоматически включаются в запрос:  
  
 **Свойства элемента** MEMBER_CAPTION, MEMBER_UNIQUE_NAME  
  
 **Свойства ячейки** VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS  
  
 Чтобы включить собственные дополнительные свойства, необходимо вручную изменить запрос многомерных выражений в режиме запроса.  
  
### <a name="graphical-mdx-query-designer-toolbar-in-design-mode"></a>Панель инструментов графического конструктора запросов многомерных выражений в режиме конструктора  
 Панель инструментов конструктора запросов содержит кнопки, которые помогают создавать запросы многомерных выражений с помощью графического интерфейса. В следующей таблице перечислены кнопки и их функции.  
  
|Кнопка|Описание|  
|------------|-----------------|  
|**Редактировать как текст**|Не включено для данного типа источника данных.|  
|**Импорт**|Импортировать существующий запрос из файла определения отчета (RDL), расположенного в файловой системе. Дополнительные сведения см. в разделе [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Переключение в режим запросов многомерных выражений](../../analysis-services/media/rsqdicon-commandtypemdx.gif "Переключение в режим запросов многомерных выражений")|Перейти к многомерному выражению командного типа.|  
|![Переключение в режим DMX-запросов](../media/rsqdicon-commandtypedmx.gif "Переключение в режим DMX-запросов")|Перейти к расширению интеллектуального анализа данных командного типа.|  
|![Обновление результирующих данных](../../analysis-services/media/rsqdicon-refresh.gif "Обновление результирующих данных")|Обновление метаданных из источника данных.|  
|![Добавить вычисляемый элемент](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "добавить вычисляемый элемент")|Отображение диалогового окна **Построитель вычисляемых элементов** .|  
|![Переключатель для просмотра пустых ячеек](../../analysis-services/media/rsqdicon-showemptycells.gif "Переключатель для просмотра пустых ячеек")|Переключение между отображением и скрытием пустых ячеек на панели «Данные». (Это эквивалентно использованию предложения NON EMPTY в многомерном выражении).|  
|![Автоматическое выполнение запроса](../../analysis-services/media/rsqdicon-autoexecute.gif "Автоматическое выполнение запроса")|Автоматически выполнять запрос и отображать результат при каждом изменении. Результаты отображаются в панели «Данные».|  
|![Кнопка "Показать агрегаты"](../../analysis-services/media/rsqdicon-showaggregations.gif "Кнопка \"Показать агрегаты\"")|Показать статистические выражения на панели «Данные».|  
|![Удалить](../../analysis-services/media/rsqdicon-delete.gif "удалить")|Удалить выбранный на панель «Данные» столбец из запроса.|  
|![Значок диалогового окна "Параметры запроса"](../../analysis-services/media/iconqueryparameter.gif "Значок диалогового окна \"Параметры запроса\"")|Отображает диалоговое окно **Параметры запроса** . При указании значений для параметра запроса автоматически создается аналогичный параметр отчета с тем же именем. В качестве значения для параметра запроса устанавливается выражение, ссылающееся на параметр отчета.|  
|![Кнопка "Подготовить запрос"](../../analysis-services/media/rsqdicon-preparequery.gif "Кнопка \"Подготовить запрос\"")|Подготовить запрос.|  
|![Выполнить запрос](../../analysis-services/media/rsqdicon-run.gif "Выполнить запрос")|Выполнить запрос и показать результаты на панели «Данные».|  
|![Отмена запроса](../../analysis-services/media/rsqdicon-cancel.gif "Отмена запроса")|Отмена запроса.|  
|![Переключение в режим конструктора](../../analysis-services/media/rsqdicon-designmode.gif "Переключение в режим конструктора")|Переключение между режимом конструктора и режимом запроса.|  
  
## <a name="graphical-mdx-query-designer-in-query-mode"></a>Графический конструктор запросов многомерных выражений: режим запроса  
 Для переключения графического конструктора запросов в режим **запроса** нажмите кнопку **Режим конструктора** на панели инструментов.  
  
 На следующем рисунке показаны метки панелей режима запроса.  
  
 ![Конструктор запросов многомерных выражений для служб Analysis Services, режим запроса](../../analysis-services/media/rsqd-dsawas-mdx-querymode.gif "Конструктор запросов многомерных выражений для служб Analysis Services, режим запроса")  
  
 В следующей таблице перечисляются панели, доступные в этом режиме.  
  
|Панель|Компонент|  
|----------|--------------|  
|Кнопка "Выбрать куб" (**...**)|Отображает куб, выбранный в настоящий момент.|  
|Панель Метаданные/Функции/Шаблоны|Отображает меры в иерархическом списке, ключевые показатели эффективности и измерения, определенные для выбранного куба.|  
|Панель запросов|Отображает текст запроса.|  
|Панель результатов|Отображает результаты выполнения запроса.|  
  
 Панель «Метаданные» содержит вкладки **Метаданные**, **Функции**и **Шаблоны**. Можно перетащить измерения, иерархии, ключевые показатели эффективности и меры с вкладки **Метаданные** на панель запросов многомерных выражений. Функции можно перетащить с вкладки **Функции** на панель запросов многомерных выражений. Шаблоны многомерных выражений можно добавить на панель запросов многомерных выражений с вкладки **Шаблоны** . После выполнения запроса на панели результатов отображаются результаты запроса многомерных выражений.  
  
 Запрос многомерных выражений по умолчанию, сформированный в режиме конструктора, можно расширить, включив дополнительные свойства элементов и ячеек. После выполнения запроса следующие значения не будут отражены в результирующем наборе. Однако данные значения передаются службам [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и могут быть использованы в отчете. Дополнительные сведения см. в разделе «Использование расширенных свойств поля для базы данных служб Analysis Services (службы SSRS)».  
  
### <a name="graphical-query-designer-toolbar-in-query-mode"></a>Панель инструментов графического конструктора запросов многомерных выражений в режиме запроса  
 Панель инструментов конструктора запросов содержит кнопки, которые помогают создавать запросы многомерных выражений с помощью графического интерфейса.  
  
 Кнопки на панели инструментов в режиме конструктора ничем не отличаются от кнопок в режиме запроса, однако в режиме запроса недоступны следующие кнопки.  
  
-   **Редактировать как текст**  
  
-   **Добавить вычисляемый элемент** (![добавить вычисляемый элемент](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "добавить вычисляемый элемент"))  
  
-   **Показывать пустые ячейки** (![Переключатель для просмотра пустых ячеек](../../analysis-services/media/rsqdicon-showemptycells.gif "Переключатель для просмотра пустых ячеек"))  
  
-   **Автоматическое выполнение** (![Автоматическое выполнение запроса](../../analysis-services/media/rsqdicon-autoexecute.gif "Автоматическое выполнение запроса"))  
  
-   **Показать агрегаты** (![Кнопка "Показать агрегаты"](../../analysis-services/media/rsqdicon-showaggregations.gif "Кнопка \"Показать агрегаты\""))  
  
## <a name="see-also"></a>См. также  
 [Определение параметров в конструкторе запросов многомерных Выражений для служб Analysis Services &#40;построитель отчетов и службы SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md)   
 [Создание общего или внедренного набора данных (построитель отчетов и службы SSRS)](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Тип служб Analysis Services соединение для расширения интеллектуального анализа данных &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md)   
 [Файл конфигурации RSReportDesigner](../report-server/rsreportdesigner-configuration-file.md)   
 [Тип соединения служб Analysis Services для запросов многомерных выражений (службы SSRS)](analysis-services-connection-type-for-mdx-ssrs.md)  
  
  