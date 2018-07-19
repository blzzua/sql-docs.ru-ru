---
title: Внутренние свойства элементов (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- intrinsic member properties [MDX]
ms.assetid: 84e6fe64-9b37-4e79-bedf-ae02e80bfce8
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9cbfcb8926d8d4b1ae71c5a3b6ed35c3beb7796c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236034"
---
# <a name="intrinsic-member-properties-mdx"></a>Внутренние свойства элементов (многомерные выражения)
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] предоставляет внутренние свойства элементов измерения, которые можно включить в запрос для возвращения дополнительных данных или метаданных для использования в пользовательском приложении или при исследовании в модели или структуре. Если используются клиентские средства SQL Server, внутренние свойства можно просматривать в среде SQL Server Management Studio (SSMS).  
  
 Внутренние свойства включают: `ID`, `KEY`, `KEYx` и `NAME`— это свойства, предоставляемые каждым элементом, на любом уровне. Можно также получить информацию о позиции, например `LEVEL_NUMBER` или `PARENT_UNIQUE_NAME`, среди прочего.  
  
 В зависимости от структуры запроса и от используемого для выполнения запроса клиентского приложения свойства элементов могут быть видны или не видны в результирующем наборе. Если для проверки или выполнения запросов используется среда SQL Server Management Studio, можно дважды щелкнуть элемент в результирующем наборе, чтобы открыть диалоговое окно свойств элемента, в котором показаны значения для каждого внутреннего свойства элемента.  
  
 Основные сведения об использовании и просмотре свойств элемента измерения см. в разделе [Просмотр свойств элементов служб SSAS в окне запроса MDX в SSMS](http://go.microsoft.com/fwlink/?LinkId=317362).  
  
> [!NOTE]  
>  Как поставщик, выполняющий требования раздела OLAP спецификации OLE DB, принятой в марте 1999 года (версия 2.6), службы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают внутренние свойства элементов, указанные в этом разделе.  
>   
>  Другие поставщики (не службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ) могут поддерживать дополнительные встроенные свойства элементов. Дополнительные сведения о внутренних свойствах элементов, поддерживаемых другими поставщиками, см. в документации по этим поставщикам.  
  
## <a name="types-of-member-properties"></a>Типы свойств элементов  
 Службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают два типа внутренних свойств элементов.  
  
 Свойства элементов, зависящие от контекста  
 Эти свойства элементов должны использоваться в контексте конкретной иерархии или уровня и передавать значения для каждого элемента заданного измерения или уровня.  
  
 Обратите внимание на то, как в следующем примере включен путь к `KEY` свойство: `MEMBER [Measures].[Parent Member Key] AS [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")`.  
  
 Свойства элементов, не зависящие от контекста  
 Эти свойства элементов нельзя использовать в контексте конкретного измерения или уровня, они возвращают значения для всех элементов оси.  
  
 Контекстно независимые свойства являются автономными и не содержат сведений о пути поиска включаемых файлов. Обратите внимание на то, как отсутствует измерение или уровень, заданный для `PARENT_UNIQUE_NAME` в следующем примере: `DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS`  
  
 Независимо от зависимости внутреннего свойства элемента от контекста, действуют следующие правила их использования.  
  
-   Можно указывать только те внутренние свойства элементов, которые связаны с элементами измерения, проецируемым на оси.  
  
-   В одном запросе можно одновременно обращаться к свойствам элементов как зависящим, так и не зависящим от контекста.  
  
-   Для обращения к свойству используется ключевое слово `PROPERTIES`.  
  
 Ниже описаны различные зависящие и не зависящим от контекста элементов как зависящим свойства доступны в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]и как использовать `PROPERTIES` ключевое слово со свойствами каждого типа.  
  
## <a name="context-sensitive-member-properties"></a>Свойства элементов, зависящие от контекста  
 Все элементы измерения и уровня поддерживают группу внутренних свойств, зависящих от контекста. Эти свойства перечислены в следующей таблице.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`ID`|Внутренний идентификатор элемента.|  
|`Key`|Значение ключа элемента в исходном типе данных. Параметр MEMBER_KEY сохранен в целях обратной совместимости.  Параметр MEMBER_KEY имеет то же самое значение, что и KEY0 для несоставного ключа, и имеет значение NULL для составных ключей.|  
|`KEYx`|Ключ для элемента, где x — это начинающийся с нуля порядковый номер ключа. Значение KEY0 доступно для составных и несоставных ключей, но в основном используется для составных ключей.<br /><br /> Для составных ключей KEY0, KEY1, KEY2 и т. д. совместно образуют составной ключ. Можно использовать каждый из них независимо в запросе для возврата части составного ключа. Например, если указать значение KEY0, то будет возвращена первая часть составного ключа, а при указании значения KEY1 — следующая часть составного ключа, и т. д.<br /><br /> Если ключ не является составным, то значение KEY0 эквивалентно `Key`.<br /><br /> Обратите внимание, что `KEYx` может использоваться как в контексте, так и без контекста. По этой причине оно приведено в обоих списках.<br /><br /> Пример использования этого свойства элемента см. в статье [A Simple MDX Tidbit: Key0, Key1, Key2](http://go.microsoft.com/fwlink/?LinkId=317364)(О простой инструкции многомерного выражения: Key0, Key1, Key2).|  
|`Name`|Имя элемента.|  
  
### <a name="properties-syntax-for-context-sensitive-properties"></a>Синтаксис ключевого слова PROPERTIES для свойств, зависящих от контекста  
 Данные свойства элементов используются в контексте конкретного измерения или уровня и передают значения для каждого элемента заданного измерения или уровня.  
  
 Для свойств элемента измерения перед именем свойства указывается имя измерения, к которому относится свойство. Правильный синтаксис показан в следующем примере.  
  
 `DIMENSION PROPERTIES Dimension.Property_name`  
  
 Имя свойства элемента уровня может быть предварено только именем уровня или (для дополнительного уточнения) как именем измерения, так и и именем уровня. Правильный синтаксис показан в следующем примере.  
  
 `DIMENSION PROPERTIES [Dimension.]Level.Property_name`  
  
 Необходимо вернуть список имен всех указанных элементов в измерении `[Sales]` . Чтобы получить список этих имен, в запрос многомерных выражений включена следующая инструкция:  
  
 `DIMENSION PROPERTIES [Sales].Name`  
  
## <a name="non-context-sensitive-member-properties"></a>Свойства элементов, не зависящие от контекста  
 Все элементы поддерживают группу внутренних свойств элементов, одинаковых вне зависимости от контекста. Эти свойства несут дополнительные сведения, используемые приложениями для создания более удобной пользовательской среды.  
  
 В следующей таблице перечислены внутренние свойства, которые поддерживаются службами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]и не зависят от контекста.  
  
> [!NOTE]  
>  Столбцы в наборе строк схемы MEMBERS поддерживают внутренние свойства элементов, перечисленные в следующей таблице. Дополнительные сведения о `MEMBERS` набора строк схемы, см. в разделе [набор строк MDSCHEMA_MEMBERS](../../schema-rowsets/ole-db-olap/mdschema-members-rowset.md).  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`CATALOG_NAME`|Имя куба, которому принадлежит элемент.|  
|`CHILDREN_CARDINALITY`|Количество потомков элемента. Значение этого свойства может быть приблизительным, поэтому не стоит рассчитывать на него для определения точного числа. Поставщики должны возвращать возможное наивернейшее приблизительное значение.|  
|`CUSTOM_ROLLUP`|Пользовательское выражение элемента.|  
|`CUSTOM_ROLLUP_PROPERTIES`|Пользовательские свойства элемента.|  
|`DESCRIPTION`|Понятное описание элемента.|  
|`DIMENSION_UNIQUE_NAME`|Уникальное имя измерения, которому принадлежит элемент. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`HIERARCHY_UNIQUE_NAME`|Уникальное имя иерархии. Если элемент принадлежит нескольким иерархиям, свойство содержит строку для каждой из этих иерархий. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`IS_DATAMEMBER`|Логическое значение, указывающее, является ли элемент элементом данных.|  
|`IS_PLACEHOLDERMEMBER`|Логическое значение, указывающее, является ли элемент заполнителем.|  
|`KEYx`|Ключ для элемента, где x — это начинающийся с нуля порядковый номер ключа. Значение KEY0 доступно для составных и несоставных ключей.<br /><br /> Если ключ не является составным, то значение KEY0 эквивалентно `Key`.<br /><br /> Для составных ключей KEY0, KEY1, KEY2 и т. д. совместно образуют составной ключ. Можно ссылаться на каждый из них независимо в запросе для возврата части составного ключа. Например, если указать значение KEY0, то будет возвращена первая часть составного ключа, а при указании значения KEY1 — следующая часть составного ключа, и т. д.<br /><br /> Обратите внимание, что `KEYx` может использоваться как в контексте, так и без контекста. По этой причине оно приведено в обоих списках.<br /><br /> Пример использования этого свойства элемента см. в статье [A Simple MDX Tidbit: Key0, Key1, Key2](http://go.microsoft.com/fwlink/?LinkId=317364)(О простой инструкции многомерного выражения: Key0, Key1, Key2).|  
|`LCID` *x*|Перевод заголовка элемента в шестнадцатеричное значение локали, где *x* — шестнадцатеричное значение локали (например, LCID1009 для канадского английского). Доступно, только если перевод имеет столбец заголовков, привязанный к источнику данных.|  
|`LEVEL_NUMBER`|Расстояние от элемента до корня иерархии. Корневой уровень является нулевым.|  
|`LEVEL_UNIQUE_NAME`|Уникальное имя уровня, которому принадлежит элемент. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`MEMBER_CAPTION`|Метка или заголовок, связанный с элементом. Заголовок используется главным образом при отображении элемента. Если заголовок отсутствует, запрос возвращает `MEMBER_NAME`.|  
|`MEMBER_KEY`|Значение ключа элемента в исходном типе данных. Параметр MEMBER_KEY сохранен в целях обратной совместимости.  Параметр MEMBER_KEY имеет то же самое значение, что и KEY0 для несоставного ключа, и имеет значение NULL для составных ключей.|  
|`MEMBER_NAME`|Имя элемента.|  
|`MEMBER_TYPE`|Тип элемента. Это свойство может принимать одно из следующих значений: <br />**MDMEMBER_TYPE_REGULAR**<br />**MDMEMBER_TYPE_ALL**<br />**MDMEMBER_TYPE_FORMULA**<br />**MDMEMBER_TYPE_MEASURE**<br />**MDMEMBER_TYPE_UNKNOWN**<br /><br /> <br /><br /> Значение MDMEMBER_TYPE_FORMULA имеет больший приоритет, чем MDMEMBER_TYPE_MEASURE. Таким образом, если в измерении мер есть формула (вычисляемый) элемент `MEMBER_TYPE` свойство для вычисляемого элемента будет MDMEMBER_TYPE_FORMULA.|  
|`MEMBER_UNIQUE_NAME`|Уникальное имя элемента. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`MEMBER_VALUE`|Значение элемента в исходном типе данных.|  
|`PARENT_COUNT`|Количество родительских элементов данного элемента.|  
|`PARENT_LEVEL`|Расстояние от родительского элемента данного элемента до корневого уровня иерархии. Корневой уровень является нулевым.|  
|`PARENT_UNIQUE_NAME`|Уникальное имя родителя элемента. Для любых элементов на корневом уровне возвращается значение `NULL`. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`SKIPPED_LEVELS`|Количество пропущенных уровней элемента.|  
|`UNARY_OPERATOR`|Унарный оператор элемента.|  
|`UNIQUE_NAME`|Полное имя элемента в следующем формате: [dimension].[level].[key6.]|  
  
### <a name="properties-syntax-for-non-context-sensitive-properties"></a>Синтаксис ключевого слова PROPERTIES для свойств, не зависящих от контекста  
 Используйте следующий синтаксис для указания свойства элемента, зависящему нечувствительные к контексту с помощью `PROPERTIES` ключевое слово:  
  
 `DIMENSION PROPERTIES Property`  
  
 Обратите внимание, что такой синтаксис не позволяет указывать для этого свойства измерение или уровень, поскольку внутреннее контекстно-независимое свойство элемента применяется ко всем элементам оси.  
  
 Например, инструкция многомерных Выражений, `DESCRIPTION` внутреннего свойства элемента будет иметь следующий синтаксис:  
  
 `DIMENSION PROPERTIES DESCRIPTION`  
  
 Инструкция возвращает описание каждого элемента в оси измерения. Если добавить в качестве квалификатора свойства измерение или уровень, например *Dimension*`.DESCRIPTION` или *Level*`.DESCRIPTION`, то инструкция будет недопустимой.  
  
### <a name="example"></a>Пример  
 В следующих примерах показаны запросы многомерных выражений, которые возвращают внутренние свойства.  
  
 **Пример 1. Использование контекстно зависимых встроенных свойств в запросе**  
  
 В следующем примере возвращается родительский ID, ключ и имя для каждой категории продукта. Обратите внимание, что свойства доступны в виде мер. Это позволяет просматривать свойства в наборе ячеек при выполнении запроса, а не в диалоге свойств элемента в среде SSMS. Можно выполнить запрос наподобие этого для получения метаданных элемента из куба, который уже развернут.  
  
```  
WITH  
MEMBER [Measures].[Parent Member ID] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("ID")  
MEMBER [Measures].[Parent Member Key] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")  
MEMBER [Measures].[Parent Member Name] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("Name")  
SELECT  
 {[Measures].[Parent Member ID], [Measures].[Parent Member Key], [Measures].[Parent Member Name] } on COLUMNS,   
 [Product].[Product Categories].AllMembers on ROWS  
FROM [Adventure Works]  
```  
  
 **Пример 2. Встроенные свойства, не зависящие от контекста**  
  
 В следующем примере представлен полный список внутренних свойств, которые не зависят от контекста. После выполнения запроса в среде SSMS щелкните отдельные элементы для просмотра свойств в диалоговом окне свойств элементов.  
  
```  
SELECT [Measures].[Sales Amount Quota] on COLUMNS,  
[Employee].[Employees].members  
DIMENSION PROPERTIES  
 CATALOG_NAME ,   
 CHILDREN_CARDINALITY ,  
 CUSTOM_ROLLUP ,   
 CUSTOM_ROLLUP_PROPERTIES ,   
 DESCRIPTION ,   
 DIMENSION_UNIQUE_NAME ,   
 HIERARCHY_UNIQUE_NAME ,  
 IS_DATAMEMBER ,   
 IS_PLACEHOLDERMEMBER ,   
 KEY0 ,  
 LCID ,  
 LEVEL_NUMBER ,  
 LEVEL_UNIQUE_NAME ,  
 MEMBER_CAPTION ,   
 MEMBER_KEY ,   
 MEMBER_NAME ,   
 MEMBER_TYPE ,  
 MEMBER_UNIQUE_NAME ,   
 MEMBER_VALUE ,   
 PARENT_COUNT ,   
 PARENT_LEVEL ,   
 PARENT_UNIQUE_NAME ,  
 SKIPPED_LEVELS ,   
 UNARY_OPERATOR ,   
 UNIQUE_NAME    
 ON ROWS  
FROM [Adventure Works]  
WHERE [Employee].[Employee Department].[Department].&[Sales]  
```  
  
 **Пример 3. Возвращение свойств элемента как данных в результирующем наборе**  
  
 Следующий пример возвращает переведенный заголовок элемента категории продукта в измерении Product куба Adventure Works для указанной локали.  
  
```  
WITH   
MEMBER Measures.CategoryCaption AS Product.Category.CurrentMember.MEMBER_CAPTION  
MEMBER Measures.SpanishCategoryCaption AS Product.Category.CurrentMember.Properties("LCID3082")  
MEMBER Measures.FrenchCategoryCaption AS Product.Category.CurrentMember.Properties("LCID1036")  
SELECT   
{ Measures.CategoryCaption, Measures.SpanishCategoryCaption, Measures.FrenchCategoryCaption } ON 0  
,[Product].[Category].MEMBERS ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [PeriodsToDate &#40;многомерных Выражений&#41;](/sql/mdx/periodstodate-mdx)   
 [Дочерние элементы &#40;многомерных Выражений&#41;](/sql/mdx/children-mdx)   
 [Hierarchize &#40;многомерных Выражений&#41;](/sql/mdx/hierarchize-mdx)   
 [Число &#40;задать&#41; &#40;многомерных Выражений&#41;](/sql/mdx/count-set-mdx)   
 [Фильтр &#40;многомерных Выражений&#41;](/sql/mdx/filter-mdx)   
 [AddCalculatedMembers &#40;многомерных Выражений&#41;](/sql/mdx/addcalculatedmembers-mdx)   
 [DrilldownLevel &#40;многомерных Выражений&#41;](/sql/mdx/drilldownlevel-mdx)   
 [Свойства &#40;многомерных Выражений&#41;](/sql/mdx/properties-mdx)   
 [PrevMember &#40;многомерных Выражений&#41;](/sql/mdx/prevmember-mdx)   
 [Использование свойств элементов &#40;многомерных Выражений&#41;](mdx-member-properties.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](/sql/mdx/mdx-function-reference-mdx)  
  
  