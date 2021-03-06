---
title: "Рекомендации и ограничения XML-массовой загрузки (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
ms.assetid: c5885d14-c7c1-47b3-a389-455e99a7ece1
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e5d719e03cc033606ca339633d0b13cf01c3b6a2
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="guidelines-and-limitations-of-xml-bulk-load-sqlxml-40"></a>Правила и ограничения массовой загрузки XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Использование массовой загрузки XML требует понимания следующих рекомендаций и ограничений.  
  
-   Встроенные схемы не поддерживаются.  
  
     Если в исходном XML-документе содержится встроенная схема, при массовой загрузке XML она не учитывается. Для массовой загрузки XML нужно задать схему сопоставления, внешнюю по отношению к XML-данным. Нельзя задать схему сопоставления для узла с помощью **xmlns = «x: schema»** атрибута.  
  
-   Проверяется правильность формата XML-документа, но сам документ не проверяется.  
  
     При массовой загрузке производится проверка XML-документа, чтобы определить правильность формата, то есть убедиться, что конструкции XML соответствуют требованиям рекомендации консорциума W3C по языку XML 1.0. Если формат документа содержит ошибки, массовая загрузка XML прекращается и возвращает ошибку. Единственное исключение — когда документ является фрагментом (например, когда у него не один корневой элемент), в этом случае массовая загрузка XML загружает документ.  
  
     Массовая загрузка XML не проверяет документ на соответствие какой-либо схеме DTD или XML-Data, которую содержит или на которую ссылается файл XML-данных. Кроме того, массовая загрузка XML-данных не проверяет файл XML-данных на соответствие переданной схеме сопоставления.  
  
-   Никакая информация из пролога XML-документа не учитывается.  
  
     Массовая загрузка XML пропускает все данные до и после \<корневой > элемент в XML-документе. В частности, массовая загрузка XML не учитывает никаких XML-деклараций, внутренних определений DTD, ссылок на внешние DTD, комментариев и тому подобное.  
  
-   При наличии схемы сопоставления, задающей связь «первичный ключ — внешний ключ» между двумя таблицами (например, между таблицами Customer и CustOrder), таблица, содержащая первичный ключ, должна описываться в схеме первой. Таблица с внешним ключевым столбцом должна располагаться после нее. Это обусловлено тем, что порядок, в котором таблицы идентифицируются в схеме является порядок, используемый для их загрузки в базе данных. Например, следующая схема XDR вызовет ошибку, когда он используется в Массовая загрузка XML, так как  **\<порядок >** элемент описан раньше  **\<клиента >** элемент. Столбец CustomerID в таблице CustOrder представляет собой внешний ключевой столбец, ссылающийся на первичный ключевой столбец CustomerID в таблице Cust.  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
        <ElementType name="Order" sql:relation="CustOrder" >  
          <AttributeType name="OrderID" />  
          <AttributeType name="CustomerID" />  
          <attribute type="OrderID" />  
          <attribute type="CustomerID" />  
        </ElementType>  
  
       <ElementType name="CustomerID" dt:type="int" />  
       <ElementType name="CompanyName" dt:type="string" />  
       <ElementType name="City" dt:type="string" />  
  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
       <ElementType name="Customers" sql:relation="Cust"   
                         sql:overflow-field="OverflowColumn"  >  
          <element type="CustomerID" sql:field="CustomerID" />  
          <element type="CompanyName" sql:field="CompanyName" />  
          <element type="City" sql:field="City" />  
          <element type="Order" >   
               <sql:relationship  
                   key-relation="Cust"  
                    key="CustomerID"  
                    foreign-key="CustomerID"  
                    foreign-relation="CustOrder" />  
          </element>  
       </ElementType>  
    </Schema>  
    ```  
  
-   Если схема не задает столбцы переполнения с помощью **SQL: Overflow-поле** заметки, Массовая загрузка XML пропускает любые данные, присутствующие в XML-документе, но не описаны в схеме сопоставления.  
  
     Массовая загрузка XML применяет заданную схему сопоставления каждый раз, как в потоке XML-данных попадаются известные теги. Данные, которые присутствуют в XML-документе, но не описаны в схеме, пропускаются. Например, предположим, имеется схема сопоставления, которое описывает  **\<клиента >** элемента. XML-файл данных имеет  **\<AllCustomers >** корневой тег (который не описаны в схеме), который включает все  **\<клиента >** элементов:  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
      <Customer>...</Customer>  
       ...  
    </AllCustomers>  
    ```  
  
     В этом случае Массовая загрузка XML пропускает  **\<AllCustomers >** элемент и начинает сопоставление  **\<клиента >** элемента. Массовая загрузка XML пропускает все элементы, не описанные в схеме, но присутствующие в XML-документе.  
  
     Рассмотрим другой исходный XML-данных файл, содержащий  **\<порядок >** элементов. Эти элементы не описаны в схеме сопоставления.  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      ...  
    </AllCustomers>  
    ```  
  
     Массовая загрузка XML пропускает эти  **\<порядок >** элементов. Но если вы используете **SQL: Overflow-поле**заметки в схеме, чтобы определить столбец как столбец переполнения, Массовая загрузка XML сохранит все неиспользованные данные в этом столбце.  
  
-   Разделы CDATA и ссылки на сущности для сохранения их в базе данных преобразуются в эквивалентные строки.  
  
     В этом примере раздел CDATA содержит значение для  **\<Город >** элемента. Массовая загрузка XML извлекает строковое значение («NY»), прежде чем он вставляет  **\<Город >** элемент в базу данных.  
  
    ```  
    <City><![CDATA[NY]]> </City>  
    ```  
  
     Массовая загрузка XML не сохраняет ссылки на сущности.  
  
-   Если в схеме сопоставления задано значение по умолчанию для атрибута и в исходных XML-данных этот атрибут отсутствует, при массовой загрузке XML будет использовано значение по умолчанию.  
  
     Следующий образец схемы XDR назначается значение по умолчанию для **HireDate** атрибута:  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
  
       <ElementType name="Customers" sql:relation="Cust3" >  
          <AttributeType name="CustomerID" dt:type="int"  />  
          <AttributeType name="HireDate"  default="2000-01-01" />  
          <AttributeType name="Salary"   />  
  
          <attribute type="CustomerID" sql:field="CustomerID" />  
          <attribute type="HireDate"   sql:field="HireDate"  />  
          <attribute type="Salary"     sql:field="Salary"    />  
       </ElementType>  
    </Schema>  
    ```  
  
     В этом XML-данных **HireDate** второй отсутствует атрибут  **\<клиентов >** элемента. При массовой загрузке XML второй  **\<клиентов >** элемент в базу данных, используется значение по умолчанию, который указан в схеме.  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1" HireDate="1999-01-01" Salary="10000" />  
      <Customers CustomerID="2" Salary="10000" />  
    </ROOT>  
    ```  
  
-   **Заметки SQL: URL-encode** заметка не поддерживается:  
  
     Нельзя задать во вводных XML-данных URL-адрес и ждать, что массовая загрузка XML прочтет данные, находящиеся по этому адресу.  
  
     Создаются таблицы, заданные в схеме сопоставления (база данных должна существовать). Если один или несколько таблиц в базе данных уже существует, свойство SGDropTables определяет эти таблицы должен быть удален и создан повторно.  
  
-   Если задано свойство SchemaGen (например, SchemaGen = true), создаются таблицы, которые определены в схеме сопоставления. Но SchemaGen не создает никаких ограничений (например, ограничение PRIMARY KEY/FOREIGN KEY) для следующих таблиц с одним исключением: Если узлов XML, которые составляют первичный ключ в отношении определяются как имеющие тип XML ID (то есть **тип = «xsd:ID»** для XSD) и свойство SGUseID имеет значение True для SchemaGen, а затем не только первичные ключи создаются из узлов типа ID, но связи первичного и внешнего ключа создаются из связей в схеме сопоставления.  
  
-   SchemaGen не использует аспекты схемы XSD и расширения для создания реляционной [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] схемы.  
  
-   Если задано свойство SchemaGen (например, SchemaGen = true) для массовой загрузки XML только таблицы (и не одноименные представления), которые задаются обновляются.  
  
-   SchemaGen предоставляет только базовую функциональность для создания реляционной схемы из аннотированного XSD. При необходимости пользователь должен изменить созданные таблицы вручную.  
  
-   Если существует более одного связь между таблицами, SchemaGen пытается создать одну связь, который содержит все ключи, между двумя таблицами. Это ограничение может вызвать ошибку [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
-   При массовой загрузке XML-данных в базу по меньшей мере один атрибут или дочерний элемент в схеме сопоставления должен быть сопоставлен со столбцом базы данных.  
  
-   Если при массовой загрузке XML происходит вставка значений дат, эти значения должны быть заданы в формате (-)CCYY-MM-DD((+-)TZ). Это стандартный формат даты в XSD.  
  
-   Некоторые флаги свойств несовместимы друг с другом. Например, Массовая загрузка не поддерживает **Ignoreduplicatekeys = true** вместе с **Keepidentity = false**. Когда **Keepidentity = false**, Массовая загрузка происходит ожидание создания сервером значений ключа. Таблицы должны иметь **УДОСТОВЕРЕНИЕ** ограничение по ключу. Сервер не создает повторяющиеся ключи, что означает, что нет необходимости для **Ignoreduplicatekeys** будет присвоено **true**. **Ignoreduplicatekeys** должно быть присвоено **true** только при передаче значений первичного ключа из входящих данных в таблицу, содержащую строки, существует вероятность конфликта значений первичного ключа.  
  
  
