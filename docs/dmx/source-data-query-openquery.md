---
title: OPENQUERY (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- OPENQUERY
dev_langs:
- DMX
helpviewer_keywords:
- OPENQUERY statement
ms.assetid: fe57f3a3-a8e6-402c-995e-bd2fe28a7a7c
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6e8c250b96c2da83e6dd34263ccddeb622a67050
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;запрос источника данных&gt; -OPENQUERY
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Заменяет запрос источника данных запросом существующего источника данных. Инструкции INSERT, SELECT FROM PREDICTION JOIN и SELECT FROM NATURAL PREDICTION JOIN поддерживают **OPENQUERY**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OPENQUERY(<named datasource>, <query syntax>)  
```  
  
## <a name="arguments"></a>Аргументы  
 *именованный источник данных*  
 Источник данных, который существует в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базы данных.  
  
 *синтаксис запроса*  
 Синтаксис запроса, возвращающего набор строк.  
  
## <a name="remarks"></a>Remarks  
 **OPENQUERY** обеспечивает более безопасный способ доступа к внешним данным путем поддержки разрешений источника данных. Так как строка соединения хранится в источнике данных, администраторы могут использовать свойства источника данных для управления доступом к данным. Дополнительные сведения об источниках данных см. в разделе [поддерживаемые источники данных &#40; Службы SSAS — многомерные &#41; ](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md).  
  
 Список источников данных, доступных на сервере с помощью запроса можно получить **MDSCHEMA_INPUT_DATASOURCES** набора строк схемы. Дополнительные сведения об использовании **MDSCHEMA_INPUT_DATASOURCES**, в разделе [набор строк MDSCHEMA_INPUT_DATASOURCES](../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md).  
  
 Кроме того, список источников данных в текущей базе данных служб Analysis Services можно получить с помощью следующего DMX-запроса:  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется источник данных myDS, предварительно, уже определен в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базы данных для создания подключения к [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] базы данных и запрос **vTargetMail** представления.  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>См. также:  
 [&#60; запросом источника данных &#62;](../dmx/source-data-query.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции управления данными](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
