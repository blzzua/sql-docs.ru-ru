---
title: "Заметки XSD (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, annotations listed
- XSD schemas [SQLXML], annotations
ms.assetid: c62a6785-8d66-40a2-9c5d-80c73d600a3b
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5bbef29a71c90646f4d3b9b6a225089c98fb1692
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="xsd-annotations-sqlxml-40"></a>Заметки XSD (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
В таблице перечисляются заметки XSD, введенные в версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и проводится их сравнение с заметками XDR, введенными в версии [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
|Заметка XSD|Описание|Ссылка на раздел|Заметка XDR|  
|--------------------|-----------------|----------------|--------------------|  
|**sql:encode**|Позволяет запросить URI-ссылку, когда элемент или атрибут XML сопоставлен с BLOB-столбцом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С помощью этой URI-ссылки можно потом возвратить данные типа BLOB.|[Запрос URL-ссылки на данные BLOB с помощью sql: encode &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|**url-encode**|  
|**sql:guid**|Позволяет указать, нужно ли использовать значение идентификатора GUID, созданное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или значение, заданное в диаграмме обновления для данного столбца.|[Использование заметок sql:identity и sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Не поддерживается|  
|**sql:hide**|Прячет элемент или атрибут, заданные в схеме результирующего XML-документа.|[Скрытие элементов и атрибутов с помощью sql:hide](../../relational-databases/sqlxml-annotated-xsd-schemas-using/hiding-elements-and-attributes-by-using-sql-hide.md)|Не поддерживается|  
|**SQL: IDENTITY**|Может быть задан для любого узла, сопоставляемого со столбцом типа IDENTITY. Значение, заданное для этой аннотации, определяет, каким образом будет изменяться соответствующий столбец типа IDENTITY в базе данных.|[Использование заметок sql:identity и sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Не поддерживается|  
|**sql:inverse**|Указывает диаграмме обновления следует Инвертировать ее интерпретацию связи родитель потомок, который был указан с помощью  **\<SQL: Relationship >**.|[Указание sql:inverse атрибут для SQL: Relationship &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|Не поддерживается|  
|**sql:is-constant**|Создает XML-элемент, который не сопоставлен ни с одной из таблиц. Этот элемент появляется в выходных данных запроса.|[Создание постоянных элементов при помощи sql: — константы &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|То же|  
|**sql:key-fields**|Позволяет задавать определения столбцов, которые служат уникальными идентификаторами строк в таблице.|[Определение ключевых столбцов с помощью SQL: Key-поля &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|То же|  
|**sql:limit-field**<br /><br /> **sql:limit-value**|Позволяет ограничить значения, возвращаемые на основе ограничения значений.|[Фильтрация значений при помощи SQL: Limit-поля и SQL: Limit-значение &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/filtering-values-using-sql-limit-field-and-sql-limit-value-sqlxml-4-0.md)|То же|  
|**sql:mapped**|Позволяет исключать элементы схемы из результата.|[Исключение элементов схемы из результирующего XML-документа при помощи sql: сопоставленный &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|**map-field**|  
|**sql:max-depth**|Позволяет указать глубину рекурсивных связей, заданных в схеме.|[Задание глубины рекурсивных связей с использованием sql:max-depth](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|Не поддерживается|  
|**sql:overflow-field**|Определяет столбец базы данных, в котором содержатся данные переполнения.|[Получение невостребованных данных при помощи SQL: Overflow-поле &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/retrieving-unconsumed-data-using-the-sql-overflow-field-sqlxml-4-0.md)|То же|  
|**sql:prefix**|Создает допустимые XML ID, IDREF и IDREFS. Предваряет значения ID, IDREF и IDREFS строкой.|[Создание допустимый идентификатор, IDREF и IDREFS атрибуты типа с помощью SQL: prefix &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|То же|  
|**sql:relationship**|Определяет связи между XML-элементами. **Родительского**, **дочерних**, **родительский ключ**, и **дочерний ключ** атрибуты используются для установления связи.|[Указание связей при помощи SQL: Relationship &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|Имена атрибутов отличаются:<br /><br /> **key-relation**<br /><br /> **внешние отношения**<br /><br /> **key**<br /><br /> **foreign-key**|  
|**sql:use-cdata**|Позволяет задавать использование разделов CDATA для определенных элементов XML-документа.|[Создание разделов CDATA с использованием SQL: USE-cdata &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|То же|  
  
> [!NOTE]  
>  Собственный XSD **targetNamespace** атрибут заменяет **target-namespace** заметку, которая была введена в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] схеме сопоставления XDR.  
  
## <a name="see-also"></a>См. также  
 [Указание целевого пространства имен с помощью атрибута targetNamespace &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  
