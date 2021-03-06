---
title: "Указание таблицы дат | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30841d1f-0c3b-4575-8f4a-27a1492e248c
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2520764fdd298dc63d6af5b2d44fd41bd67160ce
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="specify-mark-as-date-table-for-use-with-time-intelligence"></a>Указание таблицы дат для использования с логики операций со временем
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Для использования функции логики операций со временем в формулах DAX, необходимо указать таблицу дат и столбец уникальных идентификаторов (datetime) типа данных Date. После указания в таблице дат столбца в качестве уникального идентификатора можно создавать связи между столбцами таблицы дат и любых таблиц фактов.  
  
 При использовании функций логики операций со временем, применяются следующие правила:  
  
-   При использовании логики операций со временем в DAX никогда не указывайте столбец datetime из таблицы фактов. Всегда создавайте в модели отдельную таблицу дат, содержащую хотя бы один столбец datetime с типом данных Date и уникальными значениями.  
  
-   Убедитесь, что таблица дат содержит непрерывный диапазон дат.  
  
-   Столбец datetime в таблице дат должен иметь гранулярность по дням (без долей дня).  
  
-   Таблицу дат и столбец уникальных идентификаторов необходимо указывать в диалоговом окне **Пометить как таблицу дат** .  
  
-   Создайте связи между таблицами фактов и столбцами типа данных Date в таблице дат.  
  
#### <a name="to-specify-a-date-table-and-unique-identifier"></a>Указание таблицы дат и уникального идентификатора  
  
1.  В конструкторе моделей щелкните таблицу дат.  
  
2.  Откройте меню **Таблица** , выберите пункт **Дата**, а затем пункт **Пометить как таблицу дат**  
  
3.  В диалоговом окне **Пометить как таблицу дат** в списке **Дата** выберите столбец, который будет служить уникальным идентификатором. Этот столбец должен содержать уникальные значения и иметь тип данных Date. Пример:  
  
    |Дата|  
    |----------|  
    |7/1/2010 12:00:00 AM|  
    |7/2/2010 12:00:00 AM|  
    |7/3/2010 12:00:00 AM|  
    |7/4/2010 12:00:00 AM|  
    |7/5/2010 12:00:00 AM|  
  
4.  При необходимости создайте связи между таблицами фактов и таблицей дат.  
  
## <a name="see-also"></a>См. также:  
 [Вычисления](../../analysis-services/tabular-models/calculations-ssas-tabular.md)   
 [Функции логики операций со временем (DAX)](http://msdn.microsoft.com/en-us/91df278d-4b28-40c1-a572-cdb91f081517)  
  
  
