---
title: "Объект связи (TMSL) | Документы Microsoft"
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
ms.assetid: 7588565f-ea34-4402-8be9-331188bdb8c2
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c41594e9e4ef5776a4e170ba3d9895d5799e9bd7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="relationships-object-tmsl"></a>Объект связи (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Определяет связь между исходной и целевой таблицы, с возможностью указать количество элементов и направление фильтры запросов и безопасности.  
  
## <a name="object-definition"></a>Определение объекта  
 Все объекты имеют общий набор свойств, включая имя, тип, описание, коллекцию свойств и заметки. **Связь** объекты также имеют следующие свойства.  
  
 isActive  
 Логическое значение, указывающее, помечена ли связь как активным или неактивным. Активная связь автоматически используется для фильтрации в таблицах. Неактивная связь может использоваться явным образом в вычислениях DAX с применением функции USERELATIONSHIP.  
  
 crossFilteringBehavior  
 Указывает, как связи влияют на фильтрацию данных. В разделе [двунаправленные кросс-фильтры для табличных моделей в SQL Server 2016 Analysis Services](../../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md) для получения дополнительной информации. Допустимы следующие значения:  
  
-   Значением OneDirection (1) — строк, выбранных в поле «Кому» конце связи автоматически профильтрует результаты сканирования таблицы в «От» конце связи.  
  
-   BothDirections (2) - фильтры на каждом конце связи автоматически профильтруют другой таблицы.  
  
-   Автоматический (3) - обработчик анализа связей и выберите один из вариантов поведения с помощью эвристики.  
  
 joinOnDateBehavior  
 При объединении двух столбцов даты и времени указывает, идет ли объединение по дате и времени или только по дате.  
  
-   Присоединиться к DateAndTime (1) — при объединении двух столбцов, в дате и времени.  
  
-   (2) при объединении двух столбцов, DatePartOnly соединения только по дате.  
  
 relyOnReferentialIntegrity  
 Не используется — зарезервировано для будущего использования.  
  
 отношениями securityFilteringBehavior  
 Перечисление, указывающее, как связи влияют на фильтрацию данных при вычислении выражения безопасности уровня строк. Допустимы следующие значения:  
  
-   Значением OneDirection (1) — строк, выбранных в поле «Кому» конце связи автоматически профильтрует результаты сканирования таблицы в «От» конце связи.  
  
-   BothDirections (2) - фильтры на каждом конце связи автоматически профильтруют другой таблицы.  
  
## <a name="usage"></a>Использование  
 Связи объектов используются в [Alter команда &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [Создать команду &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [CreateOrReplace команда &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), и [удалить команду &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md).  
  
 При создании, замена или изменение связи объекта, укажите все свойства чтения и записи определения объекта. Пропуск свойства чтения и записи, считается удаления.  
  
## <a name="full-syntax"></a>Полное описание синтаксиса  
 Ниже приведено представление схемы объекта связи.  
  
```  
"relationships": {  
          "type": "array",  
          "items": {  
            "anyOf": [  
              {  
                "description": "SingleColumnRelationship object of Tabular Object Model (TOM)",  
                "type": "object",  
                "properties": {  
                  "name": {  
                    "type": "string"  
                  },  
                  "isActive": {  
                    "type": "boolean"  
                  },  
                  "type": {  
                    "enum": [  
                      "singleColumn"  
                    ]  
                  },  
                  "crossFilteringBehavior": {  
                    "enum": [  
                      "oneDirection",  
                      "bothDirections",  
                      "automatic"  
                    ]  
                  },  
                  "joinOnDateBehavior": {  
                    "enum": [  
                      "dateAndTime",  
                      "datePartOnly"  
                    ]  
                  },  
                  "relyOnReferentialIntegrity": {  
                    "type": "boolean"  
                  },  
                  "securityFilteringBehavior": {  
                    "enum": [  
                      "oneDirection",  
                      "bothDirections"  
                    ]  
                  },  
                  "fromCardinality": {  
                    "enum": [  
                      "none",  
                      "one",  
                      "many"  
                    ]  
                  },  
                  "toCardinality": {  
                    "enum": [  
                      "none",  
                      "one",  
                      "many"  
                    ]  
                  },  
                  "fromColumn": {  
                    "type": "string"  
                  },  
                  "fromTable": {  
                    "type": "string"  
                  },  
                  "toColumn": {  
                    "type": "string"  
                  },  
                  "toTable": {  
                    "type": "string"  
                  },  
                  "annotations": {  
                    "type": "array",  
                    "items": {  
                      "description": "Annotation object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "name": {  
                          "type": "string"  
                        },  
                        "value": {  
                          "anyOf": [  
                            {  
                              "type": "string"  
                            },  
                            {  
                              "type": "array",  
                              "items": {  
                                "type": "string"  
                              }  
                            }  
                          ]  
                        }  
                      },  
                      "additionalProperties": false  
                    }  
                  }  
                },  
                "additionalProperties": false  
              }  
            ]  
          }  
        }  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Создание связей](../../integration-services/data-flow/transformations/create-relationships.md)  
  
  
