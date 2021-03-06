---
title: "Определения объектов в табличной модели язык сценариев (TMSL) | Документы Microsoft"
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
ms.assetid: 486f0507-cec6-4672-b947-0bb61d1cbc46
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f03fce7d1159e6fe7d34024e7cf63167024b752b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="tmsl-reference---tabular-objects"></a>Ссылка TMSL - табличных объектов
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Приложения, создание, использование и администрирование табличных баз данных или, подключитесь к экземпляру SQL Sever 2016 Analysis Services в табличном режиме, могут использовать табличной модели языка скриптов (TMSL) для команд и представления объектов в формате JSON.  
  
 В этой статье приведены основные объекты схемы TMSL, используемых в скриптах, созданных SQL Server Management Studio, SQL Server Data Tools (SSDT) и объекты AMO PowerShell.  
  
 Определения объектов в формате JSON и используются в TMSL команды Create, Alter и удалить. В разделе [команд в табличной модели язык сценариев &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) список команд.  
  
## <a name="main-objects"></a>Основные объекты  
 В следующей таблице приведен список наиболее часто используемых объектов в сценарии TMSL.  
  
|||  
|-|-|  
|[Объект базы данных &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|Определяет табличной базы данных на уровне совместимости 1200 или выше, на основе модели одного уровня.|  
|[Объект модели &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|Определяет табличной модели на уровне совместимости 1200 или выше.|  
|[Объект источника данных &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|Определяет соединение с источником данных, используемые при импорте, чтобы загрузить модель или запросы к серверу при использовании модели в режиме DirectQuery.|  
|[Объект Tables &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|Указывает таблицы модели.|  
|[Объект секций &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|Определяет хранилище строк таблицы, а также вычисляемые таблицы.|  
|[Объект связи &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|Определяет связи между таблицами.|  
|[Объект роли &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|Определяет разрешения, членство и фильтры безопасности, управляющие доступом к данным и операциям.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
