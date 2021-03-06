---
title: "Объект базы данных (TMSL) | Документы Microsoft"
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
ms.assetid: ae5c046b-8242-4046-ae76-2c070503fd93
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e67dfe62b23e08a675fbb93833c9383091198629
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="database-object-tmsl"></a>Объект базы данных (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Определяет табличной базы данных на уровне совместимости 1200 или выше, на основе модели одного уровня. В этом разделе описываются определения объекта базы данных, предоставляя полезные данные для запросов, создания, изменения, удаления и выполнять задачи управления базами данных.  
  
> [!NOTE]  
>  В любом сценарии можно ссылаться только одна база данных во время. Для любого объекта, отличные от самой базы данных свойства базы данных необязателен, если указать модель. Имеется взаимно-однозначное сопоставление между моделью и базы данных, которая может использоваться для определения имени базы данных, если явно не указано.   
> Аналогичным образом вы можете оставить модель, задавая ее свойства в базе данных.  
  
## <a name="object-definition"></a>Определение объекта  
 Все объекты имеют общий набор свойств, включая имя, тип, описание, коллекцию свойств и заметки. **База данных** объекты также имеют следующие свойства.  
  
 уровень совместимости  
 В настоящее время допустимыми значениями являются 1200, 1400. Более низкими уровнями совместимости следует использовать механизм изменения в метаданных.  
  
 readwritemode  
 Перечисляет режим базы данных. Чаще всего чтобы база данных только для чтения в конфигурациях с высокой доступности и масштабируемости. Допустимые значения: readWrite,  
                только для чтения,  
                или readOnlyExclusive. В разделе [высокий уровень доступности и масштабируемость в службах Analysis Services](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md) и [переключения базы данных служб Analysis Services между режимами ReadOnly и ReadWrite](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md) Дополнительные сведения о при использовании этого свойства.  
  
## <a name="usage"></a>Использование  
 **База данных** объекты используются в почти для всех команд. В разделе [команд в табличной модели язык сценариев &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) список. Объект **базы данных** объект является потомком объекта сервера.  
  
 При создании, замена или изменение объекта базы данных, укажите все свойства чтения и записи определения объекта. Пропуск свойства чтения и записи, считается удаления.  
  
## <a name="partial-syntax"></a>Частичное синтаксис  
 Так как это определение объектов велико, перечислены только прямые свойства. **Модель** объект предоставляет большую часть определения базы данных. В разделе [модели объект &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md) для определения объекта.  
  
```  
    "database": {  
      "type": "object",  
      "properties": {  
        "name": {  
          "type": "string"  
        },  
        "id": {  
          "type": "string"  
        },  
        "description": {  
          "type": "string"  
        },  
        "compatibilityLevel": {  
          "type": "integer"  
        },  
        "readWriteMode": {  
          "enum": [  
            "readWrite",  
            "readOnly",  
            "readOnlyExclusive"  
          ]  
        },  
        "model": {  
          "type": "object",  
          ...  
        }  
    }  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Высокий уровень доступности и масштабируемость в службах Analysis Services](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)  
  
  
