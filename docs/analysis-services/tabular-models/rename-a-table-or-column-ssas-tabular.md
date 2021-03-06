---
title: "Переименование таблицы или столбца | Документы Microsoft"
ms.custom: 
ms.date: 05/22/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.renametableorcolumn.f1
ms.assetid: 88061a39-c5aa-403d-a52b-7fdb365fc235
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bf8d925f0ffe72eab343ebf8af82030a21c0a9b0
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="rename-a-table-or-column"></a>Переименование таблицы или столбца 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Имя таблицы можно изменить во время импорта, указав **Понятное имя** на странице **Выбор таблиц и представлений** **мастера импорта таблиц**. Имена таблицы и столбцов также можно изменить, если данные импортируются с помощью запроса на странице **Указание SQL-запроса** **мастера импорта таблиц**.  
  
 После добавления данных в модель имя (или название) таблицы появляется на вкладке таблицы в нижней части конструктора моделей. Имя таблицы можно заменить более подходящим. После добавления данных в модель можно также переименовать столбец. Переименование столбца может оказаться полезным в том случае, если данные были импортированы из нескольких источников и необходимо сделать так, чтобы столбцы в разных таблицах имели легко различимые имена.  
  
### <a name="to-rename-a-table"></a>Переименование таблицы  
  
1.  В конструкторе моделей щелкните правой кнопкой мыши вкладку с таблицей, которую необходимо переименовать, и выберите команду **Переименовать**.  
  
2.  Введите новое имя.  
  
    > [!NOTE]  
    >  Другие свойства таблицы, включая сведения о соединении и сопоставления столбцов, можно изменить в диалоговом окне **Изменение свойств таблицы** . Однако изменить имя в этом диалоговом окне нельзя.  
  
### <a name="to-rename-a-column"></a>Переименование столбца  
  
1.  В конструкторе моделей дважды щелкните заголовок столбца, который необходимо переименовать, либо щелкните его правой кнопкой мыши и выберите в контекстном меню пункт **Переименовать столбец** .  
  
2.  Введите новое имя.  
  
## <a name="naming-requirements-for-columns-and-tables"></a>Требования к именам для столбцов и таблиц  
 Следующие слова и символы не могут быть использованы в именах таблиц и столбцов.  
  
-   Начальные и конечные пробелы  
  
-   Управляющие символы  
  
-   Следующие символы (недопустимые в именах объектов служб Analysis Services): .,;':/\\*|?&%$!+=()[]{}<>  
  
-   Зарезервированные ключевые слова служб Analysis Services, включая функциональные имена и операторы многомерных выражений (MDX) и выражений интеллектуального анализа (DMX).  
  
## <a name="effect-of-renaming-on-existing-tables-columns-and-calculations"></a>Влияние переименования на существующие таблицы, столбцы и вычисления  
 При каждом переименовании таблицы изменяется имя объекта базовой таблицы, которая может содержать много столбцов или измерений. Столбцы в таблице и все связи, в которых участвуют таблицы, необходимо обновить для использования нового имени в своих определениях. В большинстве случаев обновление происходит автоматически.
  
 Вычисления, использующие переименованную таблицу или столбцы из переименованной таблицы, также должны быть обновлены, и данные, получаемые из этих вычислений необходимо обновление и повторное вычисление. В зависимости от числа таблиц и вычислений, которых коснулось это изменение, выполнение этой операции может занять определенное время. Поэтому лучше всего переименовывать таблицы во время операции импорта или до начала построения сложных связей или вычислений.  
  
## <a name="see-also"></a>См. также  
 [Таблицы и столбцы](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)   
 [Импорт из Power Pivot](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)   
 [Импорт из служб Analysis Services](../../analysis-services/tabular-models/import-from-analysis-services-ssas-tabular.md)  
  
  
