---
title: "Компоненты-шаблоны и проверка достоверности содержимого | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wildcard components [XML]
- content validation [XML]
ms.assetid: ffa7d974-3645-446c-8425-f0b22b6b060a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 48b9aa7f4ed8182d094b5240481b32b12c6f4d6a
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="wildcard-components-and-content-validation"></a>Компоненты-шаблоны и проверка достоверности содержимого
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Компоненты-шаблоны используются для увеличения гибкости в том, в чем это разрешено для модели содержимого. Эти компоненты поддерживаются в языке XSD следующими способами.  
  
-   Компоненты-шаблоны элемента. Они представлены элементом **\<<xsd:any>**.  
  
-   Компоненты-шаблоны атрибута. Они представлены элементом **\<<xsd:anyAttribute>**.  
  
 Оба элемента-шаблона — **\<xsd:any>** и **\<xsd:anyAttribute>** — поддерживают использование атрибута **processContents**. Это позволяет задать значение, указывающее, как приложения XML обрабатывают проверку правильности содержимого документа, связанную с этими элементами символа-шаблона. Они являются различными значениями, и их действие заключается в следующем.  
  
-   Значение **strict** указывает, что содержимое полностью подтверждено.  
  
-   Значение **skip** указывает, что содержимое не подтверждено.  
  
-   Значение **lax** указывает, что только элементы и атрибуты, для которых определения схемы являются доступными, будут подтверждены.  
  
## <a name="lax-validation-and-xsanytype-elements"></a>Нестрогая проверка и элементы xs:anyType  
 В спецификации XML-схемы для элементов типа **anyType** используется **нестрогая** проверка. Поскольку в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] нестрогая проверка не поддерживалась, к элементам **anyType**применялась строгая проверка. Начиная с версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], предоставляется поддержка нестрогой проверки. Содержимое элементов типа **anyType** будет осуществляться при помощи нестрогой проверки.  
  
 Следующий пример демонстрирует использование нестрогой проверки. Элемент `e` схемы принадлежит типу **anyType** . В примере создаются типизированные переменные **xml** и демонстрируется нестрогая проверка элемента типа **anyType** .  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="http://ns">  
   <element name="e" type="anyType"/>  
   <element name="a" type="byte"/>  
   <element name="b" type="string"/>  
 </schema>'  
GO  
```  
  
 Выполнение следующего примера завершится без ошибок, поскольку успешно завершается проверка `<e>` :  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><b>data</b></e>'  
GO  
```  
  
 Следующий пример завершается успешно. Экземпляр принимается, несмотря на то, что элементы `<c>` в схеме не определены.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><c>Wrong</c><b>data</b></e>'  
GO  
```  
  
 В следующем примере экземпляр XML отклонен, потому что определение элемента `<a>` не допускает строковых значений.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>Wrong</a><b>data</b></e>'  
SELECT @var  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Требования и ограничения для коллекций XML-схем на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
