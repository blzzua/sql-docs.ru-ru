---
title: Диалоговое окно "Свойства набора данных" — "Запрос" (построитель отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10024"
ms.assetid: 75432318-0b00-4797-917c-0a2e74f9d951
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 547a93b4d82a2d799d9d13835d1ce910ba1114c3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160105"
---
# <a name="dataset-properties-dialog-box-query-report-builder"></a>Диалоговое окно «Свойства набора данных» — «Запрос» (построитель отчетов)
  Выберите **Запрос** в диалоговом окне **Свойства набора данных** , чтобы выбрать общий набор данных на сервере отчетов или создать внедренный набор данных. Для внедренного набора данных необходимо выбрать источник данных и создать запрос.  
  
 Диалоговое окно **Свойства набора данных** содержит следующие элементы.  
  
-   [Диалоговое окно "Свойства набора данных" — "Параметры" (построитель отчетов)](../dataset-properties-dialog-box-parameters-report-builder.md)  
  
-   [Диалоговое окно "Свойства набора данных" — "Поля" (построитель отчетов)](../dataset-properties-dialog-box-fields-report-builder.md)  
  
-   [Диалоговое окно "Свойства набора данных" — "Настройки" (построитель отчетов)](dataset-properties-dialog-box-options-report-builder.md)  
  
-   [Диалоговое окно "Свойства набора данных" — "Фильтры" (построитель отчетов)](../dataset-properties-dialog-box-filters-report-builder.md)  
  
 Дополнительные сведения см. в разделе [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Параметры  
 **Название**  
 Введите имя набора данных. Это имя не должно совпадать ни с одним именем области данных или группы в данном отчете.  
  
 **Использовать общий набор данных**  
 Выберите этот параметр, чтобы использовать стандартный набор данных с сервера отчетов.  
  
 **Обзор**  
 Перейдите в папку на сервере отчетов или сайте SharePoint и выберите общий набор данных (RSD).  
  
 **Использовать в отчете внедренный набор данных**  
 Выберите этот параметр, чтобы создать набор данных, используемый только в данном отчете.  
  
 **Источник данных**  
 Выберите источник данных, на котором основывается этот набор данных. Чтобы создать новый источник данных, нажмите кнопку **Создать**.  
  
 **Тип запроса**  
 Выберите тип команды или запрос для этого набора данных. Выберите **Текст** , чтобы запустить запрос и получить данные из базы данных. Выберите **Таблица** , чтобы выбрать все поля таблицы с помощью функции **TableDirect** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Выберите **Хранимая процедура** , чтобы выполнить хранимую процедуру по имени. Поле**Текст** выбирается по умолчанию и используется для большинства запросов. Чтобы изменить выбранный запрос к источнику данных, нажмите кнопку **Конструктор запросов**.  
  
> [!NOTE]  
>  Не все типы запросов поддерживаются всеми источниками данных. Например, тип **Таблица** поддерживается только источниками данных типа **OLE DB** и **ODBC**.  
  
 **Запрос**  
 Появляется при выборе параметра типа команды **Текст** . Введите запрос или импортируйте существующий запрос, нажав кнопку **Импорт**. Чтобы изменить выражение, нажмите кнопку **Выражение** (*fx*).  
  
> [!NOTE]  
>  Если запрос был построен с помощью конструктора, текст запроса появляется в этом поле.  
  
 **Имя таблицы**  
 Введите имя таблицы, которая будет использоваться в качестве набора данных. Этот параметр появляется при выборе параметра **Таблица**.  
  
 **Выберите или введите имя хранимой процедуры**  
 Выберите или введите имя хранимой процедуры, которую нужно использовать. Чтобы изменить выражение, нажмите кнопку **Выражение** (*fx*). Этот параметр появляется при выборе параметра типа команды «Хранимая процедура».  
  
 **Время ожидания (сек)**  
 Введите время ожидания запроса в секундах. Значение по умолчанию — 30 секунд. Значение параметра **Истечение времени ожидания** должно быть пустым или положительным числом. Если значение не задано, время ожидания запроса не ограничивается.  
  
 **Обновление полей**  
 Выполните команду запроса, чтобы обновить список полей в диалоговом окне [Свойства набора данных — страница "Поля"](../dataset-properties-dialog-box-fields-report-builder.md) .  
  
## <a name="see-also"></a>См. также  
 [Добавление данных в отчет &#40;построитель отчетов и службы SSRS&#41;](report-datasets-ssrs.md)   
 [Справка построителя отчетов для диалоговых окон, панелей и мастеров](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Конструкторы запросов (построитель отчетов)](../query-designers-report-builder.md)  
  
  