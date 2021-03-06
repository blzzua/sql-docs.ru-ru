---
title: "Обновить команды (TMSL) | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 97ff6ba8-c236-4ba6-8220-b0fcb9e1dc5c
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 77bef111f20a6ccc72347b8e02bd967ef2d316b4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="refresh-command-tmsl"></a>Обновить команды (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Обрабатывает объекты в текущей базе данных.   
**Обновить** всегда выполняется в параллельном режиме, если можно регулировать с помощью [последовательности команд &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/sequence-command-tmsl.md).  
  
 Во время операции обновления данных можно переопределить некоторые свойства некоторых объектов:  
  
-   Изменение **QueryDefinition** свойство **секции** объекта для импорта данных с помощью выражения фильтра на лету.  
  
-   Укажите учетные данные источника данных как часть **обновление** в команду **ConnectionString** свойство **источник данных** объекта. Этот подход может быть более безопасны, как учетные данные предоставляются и используются временно в течение операции, а не хранятся.  
  
 Примеры в этом разделе показано, эти переопределения свойств.  
  
> [!NOTE]  
>  В отличие от многомерной обработки нет обработки ошибок для обработки табличных данных без специальной обработки.  

  
## <a name="request"></a>Запрос  
 **Обновить** принимает определение типа параметра и объекту.  
  
```  
    {  
        "refresh": {  
            "description": "Parameters of Refresh command of Analysis Services JSON API",  
            "properties": {  
            "type": {  
                "enum": [  
                "full",  
                "clearValues",  
                "calculate",  
                "dataOnly",  
                "automatic",  
                "add",  
                "defragment"  
                ]  
            },  
            "objects": {  
. . .   
```  
  
 **Тип** параметр задает область для операции обработки.  
  
||||  
|-|-|-|  
|**Тип обновления.**|**Применяется к**|**Описание**|  
|переполненные|Базы данных,<br />Таблицы,<br />Секция|Обновить данные и пересчитать все зависимые объекты для всех секций в указанной секции, таблице или базе данных. Для вычисления секции пересчитать раздел и все его зависимости.|  
|clearValues|Базы данных,<br />Таблицы,<br />Секция|Очистка значений в этом объекте и всех его зависимых элементах.|  
|вычисления|Базы данных,<br />Таблицы,<br />Секция|Пересчитать этот объект и все зависимые ресурсы только при необходимости. Это значение не приводит к принудительному повторному вычислению, за исключением временных формул.|  
|dataOnly|Базы данных,<br />Таблицы,<br />Секция|Обновление данных в этом объекте и очистка его зависимых элементов.|  
|automatic|Базы данных,<br />Таблицы,<br />Секция|Если объект необходимо обновить и пересчитать, обновить и пересчитать объект и все его зависимости. Применяется, если секция находится в состоянии, отличном от "Готово".|  
|add|Секция|Добавление данных в эту секцию и пересчет всех зависимых элементов. Эта команда может применяться только к обычным секциям, а не для вычисления секций.|  
|Дефрагментация|Базы данных,<br />Table|Дефрагментировать данные в указанной таблице. По мере добавления или удаления данных из таблицы словари для каждого столбца могут заполниться значениями, которых на самом деле больше не существует в столбцах. Параметр дефрагментации приведет к очистке более не используемых значений в словарях.|  
  
 Вы можете обновить следующие объекты:  
  
 [Объект базы данных &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md) Обработки базы данных.  
  
```  
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200"  
      }  
    ]  
  }  
}  
```  
  
 [Объект Tables &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) Обработать одну таблицу.  
  
```  
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "Date"  
      }  
    ]  
  }  
}  
```  
  
 [Объект секций &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md) Обработки одной секции в пределах таблицы.  
  
```  
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "FactSalesQuota",  
        "partition": "FactSalesQuota"  
      },  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "FactSalesQuota",  
        "partition": "FactSalesQuota - 2011"  
      }  
    ]  
  }  
}  
```  
  
## <a name="response"></a>Ответ  
 Возвращает пустой результирующий после успешного завершения команды. В противном случае возвращается исключение XML для Аналитики.  
  
## <a name="examples"></a>Примеры  
 Переопределять оба **ConnectionString** и определение секции запроса.  
  
```  
{   
    "refresh": {   
        "type": "data",   
        "objects": [   
            {   
                "database": "tmtestdb",   
                "table": "sales"   
            },   
            {   
                "database": "tmtestdb",   
                "table": "customer"   
            }   
        ],   
        "overrides": [   
            {   
                "dataSources": [ // Bindings for Data Sources   
                    {   
                        "object": {   
                            "database": "tmtestdb",   
                            "dataSource": "contoso"   
                        },   
                        "dataSource": {   
                        "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=contoso;Integrated Security=SSPI;Persist Security Info=false"   
"   
                        }   
                    }   
                ],   
                "partitions": [ // Bindings for Partitions   
                    {   
                        "object": {   
                            "database": "tmtestdb",   
                            "table": "sales",   
                            "partition": "2015"   
                        },   
                        "partition": {   
                            "source": {   
                                "query": [  
                                     "SELECT sales.salesamount, customer.customername FROM sales",  
                                     "JOIN customer on custKey = sales.custkey",  
                                     "JOIN date on date.DateKey = customer.OrderDate",  
                                     "WHERE date.CalendarYear='2015'"  
                                  ],  
                            }   
                        }   
                    }   
                ]   
            }   
        ]   
    }   
}   
```  
  
 Переопределяет определенной области путем задания для параметра типа **dataOnly** обновления метаданных остается без изменений.  
  
```  
{   
        "refresh" : {   
            "type" : "dataOnly",   
            "objects" : [   
                {   
                    "database" : "TMTestDB",   
                    "table" : "Customer"   
                },   
                {   
                    "database" : "TMTestDB",   
                    "table" : "Sales"   
                }   
            ],   
            "overrides" : [{   
                "scope" : {   
                    "database" : "TMTestDB",   
                    "table" : "Sales"   
                },   
                "dataSources" : [{   
                    "originalObject" : {   
                        "dataSource" : "SqlServer sqlcldb2 AS_foodmart_2000"   
                    },   
                    "connectionString" : "Provider=SQLNCLI11;Data Source=sqlcldb2;Initial Catalog=AS_foodmart_2000;Integrated Security=SSPI;Persist Security Info=false"   
                }]   
            }]   
        }   
    }   
```  
  
## <a name="usage-endpoints"></a>Использование (конечные точки)  
 Этот элемент команды используется в инструкции [выполнить метод &#40; XML для Аналитики &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова через конечную точку XML для Аналитики, предоставляемых одним из следующих способов:  
  
-   Как окно XMLA в SQL Server Management Studio (SSMS)  
  
-   В качестве входного файла для **invoke-ascmd** командлет PowerShell  
  
-   В качестве входных данных для задачи служб SSIS или заданием агента SQL Server  
  
 Готовый сценарий для этой команды можно создать в среде SSMS.  Например, можно щелкнуть **сценарий** для обработки диалоговым окном.  
  
 [ \[MS-SSAS-T\]: Менное сервера служб Analysis Services табличной (SQL Server технические Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) документ содержит раздел 3.1.5.2.2, в котором описывается структура команд JSON табличных метаданных и объектов. В настоящее время этот документ охватывает команды и возможности, которые еще не реализована в сценарии TMSL. См. в разделе ([языке скриптов табличных моделей &#40; TMSL &#41; Ссылки](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) для дополнительной информации о том, что поддерживается.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Параметры обработки и параметры &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)  
  
  
