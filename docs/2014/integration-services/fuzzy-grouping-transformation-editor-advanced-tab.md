---
title: Нечеткое группирование преобразования, редактор (вкладка «Дополнительно») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7e8c12ad683e46838a88359170ea970f20c02828
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231524"
---
# <a name="fuzzy-grouping-transformation-editor-advanced-tab"></a>Редактор преобразования «Нечеткое группирование» (вкладка «Дополнительно»)
  На вкладке **Дополнительно** диалогового окна **Редактор преобразования «Нечеткое группирование»** можно определить входные и выходные столбцы, пороги подобия и разделители токенов.  
  
> [!NOTE]  
>  `Exhaustive` И `MaxMemoryUsage` свойства преобразования «Нечеткое группирование» недоступны в **редактор преобразования Нечеткое группирование**, однако его можно установить с помощью **расширенный редактор**. Дополнительные сведения об этих свойствах см. в подразделе «Преобразование "Нечеткое группирование"» раздела [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
 Дополнительные сведения о преобразовании «Нечеткое группирование» см. в разделе [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Имя входного ключевого столбца**  
 Укажите имя выходного столбца, содержащего уникальный идентификатор для каждой входной строки. `_key_in` Столбец имеет значение, однозначно определяющий каждую строку.  
  
 **Имя выходного ключевого столбца**  
 Укажите имя выходного столбца, содержащего уникальный идентификатор для канонической строки группы повторяющихся строк. Столбец `_key_out` соответствует значению `_key_in` канонической строки данных.  
  
 **Имя столбца порога подобия**  
 Укажите имя столбца, содержащего показатель подобия. Показатель подобия — значение от 0 до 1, представляющее собой степень подобия входной строки относительно канонической. Чем ближе к 1 коэффициент, тем более строка соответствует канонической.  
  
 **Порог подобия**  
 Установите порог подобия с помощью ползунка. Чем ближе порог к 1, тем большее сходство между собой должны иметь строки, считающиеся повторяющимися. Увеличение этого порога может повысить скорость нахождения совпадений, так как количество рассматриваемых потенциальных записей будет меньше.  
  
 **Разделители токенов**  
 В преобразовании имеется набор разделителей по умолчанию для разделения данных на лексемы. При необходимости можно добавить или удалить разделители в списке.  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Определение подобных строк данных с помощью преобразования "Нечеткое группирование"](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  