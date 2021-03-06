---
title: "Управление соединениями и сеансами (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- statefulness [XML for Analysis]
- statelessness [XML for Analysis]
- XML for Analysis, sessions
- states [XML for Analysis]
- XMLA, sessions
- sessions [XML for Analysis]
ms.assetid: b83bb3ff-09be-4fda-9d1d-6248e04ffb21
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 761618d7a0d651fb24257e03c5fcb261fde051c6
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="managing-connections-and-sessions-xmla"></a>Управление соединениями и сеансами (XMLA)
  *Пользуясь* — это условие, в течение которого сервер сохраняет идентификатор и контекст клиента между вызовами методов. *Отсутствие поддержки состояния* — это условие, в течение которого сервер не запоминает идентификатор и контекст клиента после завершения вызова метода.  
  
 Чтобы обеспечить контроль изменений состояния, XML для аналитики (XMLA) поддерживает *сеансы* , которые позволяют выполнить ряд инструкций друг с другом. Примером такого ряда инструкций служит создание вычисляемого элемента, который должен использоваться в последующих запросах.  
  
 В целом поведение сеансов в XMLA соответствует описанию, приведенному в спецификации OLE DB 2.6.  
  
-   Сеансы определяют область контекста команд и транзакций.  
  
-   В контексте одного сеанса могут выполняться несколько команд.  
  
-   Поддержка транзакций в контексте XMLA обеспечивается специфический для поставщика команды, отправляемые с [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) метод.  
  
 XMLA определяет способ поддержки сеансов в веб-среде, похожий на тот, который используется в протоколе DAV для реализации блокировки в слабосвязанной среде. Эта реализация соответствует протоколу DAV в том, что поставщик может закрывать сеансы по различным причинам (например, из-за ошибки времени ожидания или соединения). В случае поддержки сеансов веб-службы должны знать об этом и быть готовыми к обработке прерванных наборов команд, которые необходимо перезапускать.  
  
 В спецификации протокола SOAP консорциума World Wide Web (W3C) рекомендуется использовать заголовки SOAP для построения новых протоколов поверх сообщений SOAP. В приведенной далее таблице перечислены элементы и атрибуты заголовков SOAP, которые XMLA определяет для запуска, ведения и закрытия сеанса.  
  
|Заголовок SOAP|Описание|  
|-----------------|-----------------|  
|BeginSession|Этот заголовок запрашивает у поставщика создание нового сеанса. В ответ поставщик должен создать новый сеанс и возвратить его идентификатор, как часть заголовка Session в ответе SOAP.|  
|SessionId|Область значения содержит идентификатор сеанса, который необходимо использовать в каждом вызове метода в течение сеанса. В ответе SOAP поставщик отправляет этот тег, а клиент также должен отправлять этот атрибут с каждым элементом заголовка Session.|  
|Session|Этот заголовок должен использоваться для каждого вызова метода в рамках данного сеанса, а на панели значения заголовка должен быть указан идентификатор сеанса.|  
|EndSession|Используйте этот заголовок для завершения сеанса. Идентификатор сеанса необходимо указывать в области значения.|  
  
> [!NOTE]  
>  Наличие идентификатора сеанса не гарантирует того, что сеанс остается допустимым. Если время сеанса истекает (например, если истекло его время ожидания или потеряно соединение), поставщик может завершить и выполнить откат действий, выполнявшихся во время сеанса. В результате все последующие вызовы методов, отправленные клиентом с идентификатором сеанса, завершатся ошибкой, сигнализирующей, что сеанс недопустим. Клиент должен обработать это условие и быть готовым повторно отправить вызовы метода сеанса с самого начала.  
  
## <a name="legacy-code-example"></a>Пример кода прежних версий  
 В следующем примере показано, как поддерживаются сеансы.  
  
1.  Чтобы начать сеанс, добавьте заголовок BeginSession в SOAP в исходящий от клиента вызов метода XMLA. Первоначально область значения остается пустой, поскольку идентификатор сеанса пока не известен.  
  
    ```  
    <SOAP-ENV:Envelope  
       xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
       SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
       <SOAP-ENV:Header>  
          <XA:BeginSession  
             xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
             xsi:type="xsd:int"  
             mustUnderstand="1"/>  
       </SOAP-ENV:Header>  
       <SOAP-ENV:Body>  
          ...<!-- Discover or Execute call goes here.-->  
       </SOAP-ENV:Body>  
    </SOAP-ENV:Envelope>  
    ```  
  
2.  Сообщение ответа SOAP от поставщика включает идентификатор сеанса в возвращаемой области заголовка, с помощью тега заголовка XMLA \<SessionId >.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
3.  В каждый вызов метода в рамках этого сеанса необходимо добавлять заголовок Session, содержащий идентификатор сеанса, который возвратил поставщик.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
4.  По завершении сеанса, \<EndSession > используется тег, содержащий связанное значение идентификатора сеанса.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:EndSession  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          xsi:type="xsd:int"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
## <a name="see-also"></a>См. также  
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
