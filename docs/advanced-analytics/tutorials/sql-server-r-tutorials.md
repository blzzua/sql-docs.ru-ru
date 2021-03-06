---
title: Учебники по SQL Server R | Документы Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 08/29/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 34fee91978a27e38fca6092a98596c701cfd32eb
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="sql-server-r-tutorials"></a>Учебники по SQL Server R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье список учебники и образцы, демонстрирующие использование R с SQL Server 2016 или 2017 г. SQL Server. Эти образцы и демонстрационные материалы Вы узнаете:

+ Выполнение R из T-SQL
+ Каковы удаленных и локальных вычислительных контекстов, и как можно выполнять код R, с помощью имени компьютера SQL Server
+ Создание программы-оболочки код R в хранимой процедуре
+ Оптимизация кода R в рабочей среде SQL
+ Реальные сценарии для внедрения в приложениях машинного обучения

Сведения о требованиях и установки см. в разделе [необходимых компонентов](#bkmk_Prerequisites).

## <a name="bkmk_sqltutorials"></a>Учебники R

Если не указано иное, учебники были разработаны для служб R SQL Server 2016 и требуется для работы в службах SQL Server 2017 г машины обучения без значительных изменений.

Все учебники предусматривают широкое использование компонентах из пакета RevoScaleR для SQL Server контекстов вычислений.

+ [Глубокое погружение обработки и анализа данных с помощью R и SQL Server](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)

  Узнайте, как использовать функции RevoScaleR пакетов. Перемещение данных между R и SQL Server и коммутатор вычислений контекстов в соответствии с конкретной задачей. Создание моделей и графики и перемещать их между среды разработки и сервером базы данных.

  **Аудитория:** для специалистов по анализу данных или разработчиков, знакомых с языком R, и включает дополнительные сведения о расширенных пакетов R и функций в Microsoft R компанией Revolution Analytics.

  **Требования:** базовые знания R. Доступ к серверу с SQL Server R Services или службы обучения машины с R. В разделе справки по установке, [необходимых компонентов](#bkmk_Prerequisites).

+ [Аналитика в базе данных R для разработчиков SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md)

  Построение и развертывание законченное решение R, используя только [!INCLUDE[tsql](../../includes/tsql-md.md)] средства.

  Основное внимание уделяется перемещения решения в производственной среде. Вы узнаете, как включить код на языке R в хранимую процедуру, сохранить модель R в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выполнять параметризованные вызовы модели R для составления прогнозов.

  **Аудитория:** для разработчиков SQL, разработчики приложений или SQL-специалистов, осуществляющих поддержку решений R и хотите узнать, как развертывание моделей R в SQL Server.

  **Требования:** среда R не требуется. Содержит все кода R, и вы можете создавать законченное решение, только с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и знакомые бизнес-аналитики и средств разработки SQL. Однако полезно базовые знания о R.

  Необходимо иметь доступ к SQL Server с помощью языка r. установлен и включен. В разделе справки по установке, [необходимых компонентов](#bkmk_Prerequisites).

+ [Краткое руководство: Использование R в T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)

  Это краткое руководство охватывает базовый синтаксис для использования R в [!INCLUDE[tsql](../../includes/tsql-md.md)].

  Узнайте, как вызов среды выполнения R из T-SQL, перенос функций R в SQL-кода и выполнение хранимой процедуры, которая сохраняет выходные данные R и R-модели в таблицу SQL.

  **Аудитория:** для пользователей, которые не знакомы с функцией и хотите изучить основы вызов R из хранимой процедуры.

  **Требования:** не знает о R или необходимые SQL. Тем не менее требуется SQL Server Management Studio или другой клиент, можно подключиться к базе данных и выполнить T-SQL. Мы рекомендуем бесплатный [MSSQL расширения для Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) Если вы не знакомы с запросами T-SQL.

  Также необходимо иметь доступ к серверу с SQL Server R Services или службы обучения машины с помощью R уже включен. В разделе справки по установке, [необходимых компонентов](#bkmk_Prerequisites).

+ [Пошаговое руководство по обработке и анализу данных](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

  Демонстрирует процесс обработки и анализа данных от начала до конца, в процессе получения данных и сохранить его в SQL Server, анализ данных с помощью R и построения диаграмм.

  Вы узнаете, как переместить графики между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и R и сравнить конструируются в T-SQL с функциями r. Наконец, вы узнаете, как использовать прогнозной модели в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для массовой оценки и оценки одной строки.

  **Аудитория:** для тех, кто уже знаком с R и средств разработчика, например SQL Server Management Studio.

  **Требования:** должны иметь доступ к среду разработки R и знать, как запускать команды R. Использование PowerShell требуется для загрузки набора данных такси Нью-Йорк. Необходимо иметь доступ к серверу с SQL Server R Services или службы обучения машины с помощью R уже включен. В разделе справки по установке, [необходимых компонентов](#bkmk_Prerequisites).

## <a name ="bkmk_samples"></a>Образцы продуктов

Эти образцы, демонстрационные материалы и обеспечиваются с помощью команды разработчиков SQL Server для выделения нескольких способов, можно использовать внедренные аналитика в реальных приложениях.

+ [Создать прогнозную модель с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

  Узнайте, как использовать машинного обучения для прогнозирования будущих внаем, что позволяет бизнес-планом и персонал будущих требований бизнеса ski аренды.

+ [Выполнение клиента кластеризации с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/)

  Используйте неконтролируемого обучения сегмент клиентам на основе данных продаж.

## <a name="bkmk_Prerequisites"></a>Предварительные требования

Чтобы использовать эти учебники и примеры, необходимо установить одну из следующих серверных продуктов:

+ Службы R SQL Server 2016 (в базе данных)
  
  Поддерживает R. не забудьте установить машинного обучения функции, а затем включить внешние скрипты.

+ SQL Server 2017 г машины обучения Services (в базе данных)
  
  Поддерживает R или Python. Необходимо выбрать машинного обучения, функции и язык для установки и затем включить внешние сценарии.

После запуска программы установки SQL Server, не забывайте следующие важные действия:

+ Включение возможности выполнения внешнего сценария, выполнив `sp_configure 'external scripts enabled', 1`
+ Перезагрузите сервер
+ Убедитесь в наличии необходимых разрешений на службу, которая обращается к внешней среде выполнения
+ Убедитесь в наличии необходимых разрешений для подключения к серверу для чтения данных, а также для создания объектов базы данных, необходимые для образца вашей учетной записи пользователя Windows или имя входа SQL

Если возникли трудности, см. статью для некоторых распространенных проблем: [Устранение неполадок службы машины обучения](../machine-learning-troubleshooting-faq.md)
