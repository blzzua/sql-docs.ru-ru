---
title: "Грамматика формальных фигуры | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f9eb99feba381701f7e590add3906cd0285b2720
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="formal-shape-grammar"></a>Грамматика формальных фигуры
Это формальная Грамматика для создания любой команды фигуры:  
  
-   Необходимые условия грамматической являются текстовыми строками, угловые скобки («<>»).  
  
-   Необязательные условия разделяются квадратные скобки («[]»).  
  
-   Альтернативные варианты обозначаются косая черта ("&#124;»).  
  
-   Повторяющийся альтернативы обозначены кнопку с многоточием («...»).  
  
-   *Альфа-канал* указывает строку буквы алфавита.  
  
-   *Цифра* указывает строку чисел.  
  
-   *Цифр Юникода* указывает строки знаков Юникода.  
  
 Другие термины являются литералами.  
  
|Термин|Определение|  
|----------|----------------|  
|\<Команда фигуры >|ФИГУРЫ [\<exp таблицы > [[AS] \<псевдонима >]] [\<действие фигуры >]|  
|\<exp таблицы >|{\<текст для команды поставщика >} &#124;<br /><br /> (\<фигуры command >) &#124;<br /><br /> Таблица \<кавычки name > &#124;<br /><br /> \<заключенный в кавычки имя >|  
|\<Действие фигуры >|ДОБАВЛЕНИЕ \<списка для полей псевдоним > &#124;<br /><br /> ВЫЧИСЛЕНИЙ \<списка для полей псевдоним > [BY \<список полей >]|  
|\<aliased-field-list>|\<aliased-field> [, \<aliased-field...>]|  
|\<aliased-field>|\<field-exp> [[AS] \<alias>]|  
|\<field-exp>|(\<exp отношения >) &#124;<br /><br /> \<вычислить exp > &#124;<br /><br /> \<Статистическая функция exp > &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp> [[AS] \<alias>]<br /><br /> ССЫЛКА \<список условного связь->|  
|\<relation-cond-list>|\<отношение условного > [, \<отношения условного >...]|  
|\<отношение условного >|\<Имя поля > TO \<дочерние ссылки >|  
|\<child-ref>|\<Имя поля > &#124;<br /><br /> ПАРАМЕТР \<param ref >|  
|\<PARAM ref >|\<число >|  
|\<Список полей >|\<Имя поля > [, \<имя поля >]|  
|\<aggregate-exp>|SUM (\<указанием поле name >) &#124;<br /><br /> AVG (\<указанием поле name >) &#124;<br /><br /> MIN (\<указанием поле name >) &#124;<br /><br /> MAX (\<указанием поле name >) &#124;<br /><br /> COUNT (\<указанием псевдонима > &#124; \<полное имя >) &#124;<br /><br /> STDEV (\<указанием поле name >) &#124;<br /><br /> ANY(\<qualified-field-name>)|  
|\<calculated-exp>|Калькулятор (\<выражение >)|  
|\<qualified-field-name>|\<alias>.[\<alias>...]\<field-name>|  
|\<псевдонима >|\<заключенный в кавычки имя >|  
|\<Имя поля >|\<quoted-name> [[AS] \<alias>]|  
|\<заключенный в кавычки имя >|"\<строка >» &#124;<br /><br /> "\<строка >" &#124;<br /><br /> [\<string>] &#124;<br /><br /> \<имя >|  
|\<qualified-name>|псевдонимы [.alias]|  
|\<имя >|альфа-канал [альфа &#124; цифра &#124; _ &#124; # &#124;: &#124;...]|  
|\<число >|цифра [цифрой...]|  
|\<new-exp>|НОВЫЙ \<тип поля > [(\<номер > [, \<номер >])]|  
|\<Тип поля >|Тип данных OLE DB или ADO.|  
|\<string>|Юникод char [Юникода char...]|  
|\<выражение >|Visual Basic для приложений выражения операнды которых являются другие столбцы не CALC в той же строке.|  
  
## <a name="see-also"></a>См. также  
 [Доступ к строк в иерархических записей](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Общие сведения о формирования данных](../../../ado/guide/data/data-shaping-overview.md)   
 [Для формирования данных службы необходимых поставщиков](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Предложение APPEND фигуры](../../../ado/guide/data/shape-append-clause.md)   
 [Команды фигуры в целом](../../../ado/guide/data/shape-commands-in-general.md)   
 [Предложение COMPUTE фигуры](../../../ado/guide/data/shape-compute-clause.md)   
 [Функции Visual Basic для приложений](../../../ado/guide/data/visual-basic-for-applications-functions.md)
