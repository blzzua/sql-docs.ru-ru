---
title: Элемент Session (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Session Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.session
- http://schemas.microsoft.com/analysisservices/2003/engine#Session
- urn:schemas-microsoft-com:xml-analysis#Session
helpviewer_keywords:
- Session element
ms.assetid: 884ed090-968e-41d3-97e5-6d12787467da
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c033153f19ce1456b0558a95a85ad6caab778be5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="session-element-xmla"></a>Элемент Session (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Использует заголовок SOAP в сообщении SOAP-запроса, чтобы идентифицировать существующий явный сеанс на экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <Session  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Description|  
|---------------|-----------------|  
|SessionId|Необходимый атрибут типа **String** , идентифицирующий используемый сеанс. Для определения сеанса службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используют идентификатор GUID.|  
  
## <a name="remarks"></a>Remarks  
 **Сеанса** элемент заголовка определяет существующий, явно запущенный сеанс на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Элемент **Session** является частью заголовка SOAP для следующих типов сообщений.  
  
-   Ответ SOAP, который содержит [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) элемент заголовка SOAP.  
  
-   SOAP-запрос на идентификацию сеанса, в которой будет выполняться [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод.  
  
 Идентификатор сеанса не гарантирует того, что сеанс остается допустимым. У сеанса, заданного в элементе **Session** , может истечь срок действия. Например, срок действия сеанса может истечь, если будет превышено время ожидания или произойдет отключение соединения, связанного с этим сеансом. Если время сеанса истекает и он становится недействительным, служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] завершает сеанс и выполняет откат текущих транзакций. Все SOAP-сообщения, отправленные с идентификатором недействительного сеанса, возвращают ошибку SOAP, указывающую, что заданный сеанс не найден.  
  
 Если **сеанса** элемент не отправляются как часть запроса SOAP, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр неявно начинает сеанс в течение **Discover** или **Execute** метод, а после его завершения завершает данный сеанс после завершения вызова метода.  
  
## <a name="see-also"></a>См. также:  
 [Элемент EndSession &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Управление &#40; соединений и сеансов XML для Аналитики &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
