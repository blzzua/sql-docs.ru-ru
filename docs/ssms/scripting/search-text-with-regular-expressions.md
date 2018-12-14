---
title: Поиск текста с помощью регулярных выражений | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.regularexpressionbuilder
helpviewer_keywords:
- regular expressions [SQL Server Management Studio]
- Query Editor [SQL Server Management Studio], regular expression searches
- searches [SQL Server Management Studio], regular expressions
ms.assetid: a057690c-d118-4159-8e4d-2ed5ccfe79d3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 58a824164a694239faeb5dbfc9ce18ba260f518f
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52538790"
---
# <a name="search-text-with-regular-expressions"></a>Поиск текста с помощью регулярных выражений
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Регулярные выражения представляют компактный и гибкий формат записи условий для поиска и замены в тексте по шаблону. Определенный набор регулярных выражений может быть использован в поле **Найти** диалогового окна [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **среды** .  
  
#### <a name="to-find-using-regular-expressions"></a>Выполнение поиска с помощью регулярных выражений  
  
1.  Чтобы включить использование регулярных выражений в поле **Найти** во время операций **Быстрый поиск**, **Найти в файлах**, **Быстрая замена**или **Заменить в файлах** , выберите параметр **Использовать** в разделе **Параметры поиска**и выберите **Регулярные выражения**.  
  
2.  В этом случае становится доступной треугольная кнопка **Список ссылок** , расположенная рядом с полем **Найти** . Нажмите кнопку для просмотра списка наиболее часто используемых регулярных выражений. При выборе любого элемента в построителе выражений он автоматически вставляется в поле **Найти** .  
  
> [!NOTE]  
>  Выражения, используемые в поле **Найти** , имеют некоторые синтаксические отличия от регулярных выражений, используемых в программировании на платформе [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Например, в режиме **Найти и заменить**фигурные скобки {} используются в выражениях с тегами. Например, выражение «zo{1}» отвечает всем вхождениям «zo», за которыми следует тег 1, как, например, «Alonzo1» или «Gonzo1». В рамках платформы .NET Framework фигурные скобки {} используются в качестве квантификаторов. Таким образом, выражение «zo{1}» отвечает всем вхождениям символа «z», за которым следует только 1 символ «o», как в слове «zone», но не как в «zoo».  
  
 В следующей таблице описываются регулярные выражения, доступные в поле **Справочный список**.  
  
|Выражение|Синтаксис|Описание|  
|----------------|------------|-----------------|  
|Любой символ|.|Совпадает с любым одиночным символом, кроме символа новой строки.|  
|Ноль или более|*|Совпадает с нулем или большим числом вхождений предыдущего выражения, создавая все возможные совпадения.|  
|Один или более|+|Совпадает с одним и больше вхождений предыдущего выражения.|  
|Начало строки|^|Совпадает с вхождением, только если оно находится в начале строки текста, в котором производится поиск.|  
|Конец строки|$|Совпадает с вхождением, только если оно находится в конце строки текста, в котором производится поиск.|  
|Начало слова|\<|Совпадает с вхождением, только если оно является началом слова в тексте.|  
|Конец слова|>|Совпадает с вхождением, только если оно является концом слова в тексте.|  
|Символ новой строки|\n|Совпадает с символом новой строки, не зависящим от платформы. Вставляет символ новой строки в выражение замены.|  
|Любой символ из набора|[]|Совпадает с любым из символов внутри квадратных скобок ([ ]). Чтобы указать диапазон символов, начальный и конечный символ следует вводить через тире (—), например: [a—z].|  
|Любой символ, не входящий в набор|[^...]|Совпадает с любым символом, не перечисленным в наборе символов после символа ^.|  
|либо|&#124;|Совпадает с выражением до или после символа OR (&#124;). В основном используется в группах. Например, строка "(хвойный&#124;лиственный) лес" совпадает со строками "хвойный лес" и "лиственный лес".|  
|ESC|\|Совпадает с символом после обратной косой черты (\\) в качестве литерала. Это позволяет искать символы, имеющие специальное значение в регулярных выражениях, таких как { или ^. Например, \\^ ищет символ ^.|  
|Выражение, заключенное в теги|{}|Совпадает со строкой, заключенной в фигурные скобки.|  
|Идентификатор C/C++|:i|Совпадает с выражением ([a-zA-Z_$][a-zA-Z0-9_$]*).|  
|Строка в кавычках|:q|Совпадает с выражением (("[^"]*")&#124;('[^']\*')).|  
|Пробел или символ табуляции|:b|Совпадает с пробелами или символами табуляции.|  
|Целочисленный|:z|Совпадает с выражением ([0-9]+).|  
  
 **Справочный список** содержит неполный список регулярных выражений, допустимых в операциях **Найти и заменить**. Любые из перечисленных ниже регулярных выражений также могут быть использованы в поле **Найти** .  
  
|Выражение|Синтаксис|Описание|  
|----------------|------------|-----------------|  
|Минимум — ноль или больше|@|Совпадает с нулем или большим числом вхождений предыдущего выражения, совпадая с минимальным числом символов.|  
|Минимум — один или больше|#|Совпадает с одним или большим числом вхождений предыдущего выражения, совпадая с минимальным числом символов.|  
|Повтор n раз|^n|Совпадает с числом n вхождений предыдущего выражения. Например, [0-9]^4 совпадет с любым четырехзначным числом.|  
|Группирование|()|Группирует вложенное выражение.|  
|n-й текст, заключенный в теги|\n|В выражении **Поиск и замена** показывает, что текст должен совпадать с n-м текстом, заключенным в теги, где n — это число в диапазоне от 1 до 9.<br /><br /> В выражении **Замена** \0 вставляет текст совпадения полностью.|  
|Выравнивание по правому краю|\\(w,n)|В выражении **Замена** выравнивает по правому краю n-е выражение, заключенное в теги, в поле шириной, по крайней мере, *w* символов.|  
|Выравнивание по левому краю|\\(-w,n)|В выражении **Замена** выравнивает по левому краю n-е выражение, заключенное в теги, в поле шириной, по крайней мере, *w* символов.|  
|Предотвращение совпадения|~(Х)|Предотвращает совпадение, когда X появляется в этом месте выражения. Например, «прав~(да)» совпадает со словами «правый» и «правота», но не со словом «правда».|  
|Буквенно-цифровой символ|:a|Совпадает с выражением ([a-zA-Z0-9]).|  
|Буква|:c|Совпадает с выражением ([a-zA-Z]).|  
|Десятичная цифра|:d|Совпадает с выражением ([0-9]).|  
|Шестнадцатеричная цифра|:h|Совпадает с выражением ([0-9a-fA-F]+).|  
|Рациональное число|:n|Совпадает с выражением (([0-9]+.[0-9]*)&#124;([0-9]\*.[0-9]+)&#124;([0-9]+)).|  
|Строка букв|:w|Совпадает с выражением ([a-zA-Z]+).|  
|ESC|\e|Юникод U+001В.|  
|Спецсимвол Bell|\g|Юникод U+0007.|  
|Отмена|\h|Юникод U+0008.|  
|Вкладка|\t|Совпадает с символом табуляции, код Юникода U + 0009.|  
|символьный формат Юникода|\x#### или \u####|Совпадает с символом, который соответствует значению #### в шестнадцатеричных цифрах в Юникоде. Символ, не входящий в основное многоязычное поле (суррогатный), можно указать с помощью элементов кода ISO 10646 или двух элементов кода Юникод, дающих значение суррогатной пары.|  
  
 В следующей таблице приведен синтаксис для совпадений по стандартным свойствам символов Юникода. Двухсимвольные сокращения идентичны перечисленным в базе данных свойств символов Юникода. Они могут быть указаны как часть кодировки. Например, выражение [:Nd:Nl:No] совпадает с любым типом цифр.  
  
|Выражение|Синтаксис|Описание|  
|----------------|------------|-----------------|  
|Буква в верхнем регистре|:Lu|Совпадает с любой буквой в верхнем регистре. Например, «:Luнига» совпадает со строкой «Книга», но не «книга».|  
|Буква в нижнем регистре|:Ll|Совпадает с одной прописной буквой. Например, «:Llнига», наоборот, совпадает со строкой «книга», но не «Книга».|  
|Заглавная буква|:Lt|Совпадает со строкой из одной заглавной и одной прописной буквы, например «Нж» или «Дз».|  
|Буква-модификатор|:Lm|Совпадает со знаками пунктуации, например запятыми, знаками ударений, двойными штрихами, используемыми для обозначения модификации предыдущей буквы.|  
|Другая буква|:Lo|Совпадает с другими буквами, например готическая буква «asha».|  
|Десятичная цифра|:Nd|Совпадает с десятичными цифрами от 0 до 9 и их эквивалентами полной ширины.|  
|Цифра, обозначаемая буквой|:Nl|Совпадает с цифрами, обозначаемыми при помощи букв (например римские цифры или идеографический ноль).|  
|Другая цифра|:No|Совпадает с другими цифрами, например старая курсивная единица.|  
|Открывающая пунктуация|:Ps|Совпадает с открывающей пунктуацией, например открывающиеся круглые или фигурные скобки.|  
|Закрывающая пунктуация|:Pe|Совпадает с закрывающей пунктуацией, например закрывающиеся круглые или фигурные скобки.|  
|Открывающие кавычки|:Pi|Совпадает со знаком открывающих двойных кавычек.|  
|Закрывающие кавычки|:Pf|Совпадает с одиночными кавычками или знаком закрывающих двойных кавычек.|  
|Тире|:Pd|Совпадает со знаком тире.|  
|Соединительная пунктуация|:Pc|Совпадает с символом подчеркивания или знаком выделения подчеркиванием.|  
|Другая пунктуация|:Po|Совпадает с (,), ?, ", !, @, #, %, &, *, \\, (:), (;), ', and /.|  
|Пробел|:Zs|Совпадает с пробелами.|  
|Разделитель строк|:Zl|Соответствует символу Юникода U+2028.|  
|Разделитель абзацев|:Zp|Соответствует символу Юникода U+2029.|  
|Знак, отличный от пробельного|:Mn|Совпадает со всеми знаками, отличными от пробельных.|  
|Объединяющий знак|:Mc|Совпадает с объединяющими знаками.|  
|Закрывающий знак|:Me|Совпадает с закрывающими знаками.|  
|Математический символ|:Sm|Совпадает со знаками +, =, ~, &#124;, \< и >.|  
|Символ валют|:Sc|Совпадает со знаком $ и остальными символами валют.|  
|Символ-модификатор|:Sk|Совпадает с символами-модификаторами, например двойным, одинарным диакритическим ударением и знаком долготы над гласными.|  
|Другие символы|:So|Совпадает с другими символами, например знаком авторских прав, знаком абзаца и знаком градуса.|  
|Другие управляющие символы|:Cc|Совпадает с концом строки.|  
|Другие символы форматирования|:Cf|Совпадает с управляющими символами форматирования, например двунаправленными управляющими символами.|  
|Суррогат|:Cs|Совпадает с половиной суррогатной пары.|  
|Символы личного пользования|:Co|Совпадает с символами из индивидуальной области.|  
|Другие не присвоенные символы|:Cn|Символы, не имеющие соответствия символам Юникода.|  
  
 В дополнение к стандартным свойствам символов Юникода в качестве набора символов могут быть объявлены следующие дополнительные свойства.  
  
|Выражение|Синтаксис|Описание|  
|----------------|------------|-----------------|  
|Коэффициент альфа|:Al|Совпадает с одним любым символом. Например, «:Alда» совпадает со словами «правда», «вода» и «сдача».|  
|Числовой|:Nu|Совпадает с любым числом или цифрой.|  
|Пунктуация|:Pu|Совпадает с любым знаком пунктуации, например ?, @, ' и т. д.|  
|Пробельная область|:Wh|Совпадает со всеми типами пробелов, включая публицистический и идеографический пробелы.|  
|Двунаправленный текст|:Bi|Совпадает со всеми символами скриптов с записью справа налево, например арабский или иврит.|  
|Символы Хангула (Hangul)|:Ha|Совпадает с корейскими символами Хангула и сочетающимися символами Джамоса (Jamos).|  
|Хирагана|:Hi|Совпадает с символами хираганы.|  
|Катакана|:Ka|Совпадает с символами катаканы.|  
|Идеографические символы / символы Хань / символы Кандзи|:Id|Совпадает со всеми идеографическими символами, например символами Хань и Кандзи.|  
  
## <a name="see-also"></a>См. также:  
 [Поиск и замена](../../relational-databases/scripting/search-and-replace.md)   
 [Поиск текста с символами-шаблонами](../../relational-databases/scripting/search-text-with-wildcards.md)  
  
  