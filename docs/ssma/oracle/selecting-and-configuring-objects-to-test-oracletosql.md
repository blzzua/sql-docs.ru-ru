---
title: Выбор и настройка объектов для теста (OracleToSQL) | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Selection of Objects to Test,Parameter Comparison Settings
ms.assetid: 29fb6542-5c1f-4b14-a822-87700beb7623
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 51688e76b4493b6f4fa5eda7712d1e60ac498c99
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="selecting-and-configuring-objects-to-test-oracletosql"></a>Выбор и настройка объектов для теста (OracleToSQL)
На этом этапе выберите объекты для тестирования и настроить параметры для сравнения процедуры и функции выходные параметры, а также возвращаемые значения функций.  
  
## <a name="selection-of-objects-to-test"></a>Выбор объектов для тестирования  
В дереве объектов Oracle, находится в левой части окна проверьте объекты, которые вы хотите запустить в процессе тестирования. Просмотреть весь список тестируемых объектов в [тестирование перенесенные объекты базы данных &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md) раздела.  
  
Если тест-инженер SSMA не поддерживает объекты, выбранные для тестирования, вы увидите ссылку с меткой **некоторые из выделенных объектов содержат ошибки** в дереве объектов. Щелкните эту ссылку для просмотра причины, почему не удается проверить эти объекты и снимите флажок не тот объект.  
  
С правой стороны можно просмотреть нескольких страниц **SQL** страницы показано определение текущего объекта. **Параметров** страницы перечислены параметры, если объект является хранимой процедуры или функции. **Свойства** страницы отображаются дополнительные характеристики объекта. См. в описании **сравнения параметра** и **значения вызовите** на следующих страницах.  
  
## <a name="parameter-comparison-settings"></a>Сравнение параметров  
Создание правила сравнения строк для выходных параметров и возвращаемых значений в **сравнения параметра** страницы. Можно внести следующие параметры.  
  
### <a name="use-during-test-comparisons"></a>Используется во время сравнения тестов  
Включите использование выбранного параметра в отличие от результатов теста.  
  
-   При выборе **True**, SSMA сравнит выходное значение этого параметра после выполнения процедуры в Oracle с соответствующим значением на сервере SQL Server.
  
-   При выборе**False**, параметр исключаются из результатов проверки.  
  
### <a name="use-custom-scale"></a>Использовать пользовательский масштаб  
Для параметров типа числовых данных можно задать пользовательский масштаб для сравнения.  
  
-   При выборе **True**, числовые значения будут округляться согласно **сравнение шкалы** значения перед сравнением.  
  
-   При выборе**False**, числовое сравнение будут точными.  
  
### <a name="comparing-scale"></a>Сравнение шкалы  
Доступными, только если **Используйте настраиваемый масштаб** включен режим **True**. Это точность числового сравнения.  
  
### <a name="date-time-comparing"></a>Сравнение времени в дату  
Определяет способ даты и времени выполняется сравнение значений.  
  
-   При выборе **сравнения всей Дата**, будет выполняться полное сравнение значений из обеих платформах.  
  
-   При выборе **сравнения только дата**, время часть будет игнорироваться.  
  
-   При выборе **сравнения только время**, дату часть будет игнорироваться.  
  
-   При выборе **игнорировать миллисекунд**, результаты будут сравниваться до секунд.  
  
-   При выборе **игнорировать дату и миллисекунд**, это приведет к появлению сравниваемых только часть времени и без учета дробных частей секунды.  
  
### <a name="ignore-strings-case"></a>Игнорировать регистр строк  
Определяет чувствительность к регистру сравнения.  
  
-   При выборе **True**, сравнение будет зависеть от регистра.  
  
-   При выборе **False**, то сравнение будет учитываться регистр.  
  
### <a name="ignore-trailing-spaces"></a>Без учета конечных пробелов  
Определяет, каким образом конечные пробелы при сравнении обрабатывать.  
  
-   При выборе **True**, сравниваемые строки будет усекаются справа перед сравнением.  
  
-   При выборе **False**, сравниваемых строк будет сохраняет конечные пробелы.  
  
## <a name="specify-input-values-for-procedures-and-functions-call-values"></a>Укажите входные значения для процедур и функций (вызов значения)  
Значения входных параметров можно указать на **значения вызовите** страницы. **Добавить вызов** кнопка добавляет новый вызов с пустой параметр значения. **Удалите вызовы** кнопка удаляет текущего вызова.  
  
## <a name="next-step"></a>Следующий шаг  
[Выбор и настройка затронутые объекты &#40; OracleToSQL &#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
## <a name="see-also"></a>См. также:  
[Тестирование миграции объектов базы данных &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
