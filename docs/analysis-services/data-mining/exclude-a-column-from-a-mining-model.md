---
title: "Исключить столбец из модели интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
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
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d9e175dde4ca78636c909b20e3898ee582f1adb9
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="exclude-a-column-from-a-mining-model"></a>исключить столбец из модели интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
При создании новой модели интеллектуального анализа данных может отсутствовать необходимость использовать все столбцы, существующие в структуре интеллектуального анализа данных, на которой основывается модель. Например, если вы добавили столбец имен заказчиков для детализации, который не требуется использовать при моделировании. Или же может потребоваться создать несколько копий столбца с различной дискретизацией так, чтобы только одна из таких копий использовалась в каждой модели, а остальные пропускались. Также можно избирательно добавлять входные столбцы в некоторые модели для того, чтобы увидеть, как добавленные переменные повлияют на выходной столбец.  
  
 Не требуется создавать новую структуру интеллектуального анализа данных для каждой комбинации столбцов. Вместо этого можно просто отметить столбцы, которые не будут использоваться в конкретной модели.  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>Исключение столбца из модели интеллектуального анализа данных  
  
1.  На вкладке **Модели интеллектуального анализа данных** конструктора интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]выберите ячейку, которая соответствует столбцу, который необходимо исключить, под соответствующей моделью интеллектуального анализа данных.  
  
2.  Выберите пункт **Пропустить** из раскрывающегося списка.  
  
## <a name="see-also"></a>См. также  
 [Задачи модели интеллектуального анализа данных и инструкции](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
