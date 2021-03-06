---
title: Установка и управление ими машины обучения пакетов в SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 02/19/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 9b2bf101674d6733c137324c9e5581647251726b
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="installing-and-managing-machine-learning-packages-in-sql-server"></a>Установка и управление ими машины обучения пакетов в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Этой статье описывается, как установить новые пакеты R или Python в 2017 г. SQL Server и SQL Server 2016. Здесь также описываются ограничения на пакеты, которые можно установить на SQL Server.

## <a name="overview-of-package-management-methods-and-requirements"></a>Обзор способов управления пакета и требований

В отличие от обычной разработки R или Python пакетов, используемый сервером SQL Server необходимо установить в папку в административный контроль. Существует множество преимуществ для хранения пакетов в одном месте.

+ Администратор сервера может отслеживать Добавление новых файлов и библиотек на сервере и управлять ростом файлы, используемые в библиотеках пакета. 
+ Пакеты можно легко совместно несколькими пользователями базы данных, в отличие от установки нескольких копий того же пакета в библиотек пользователей.
+ Можно установить только пакеты, защищенные, утвержденных, для защиты сервера и его операций.

Тем не менее эти ограничения означает некоторые изменения в способ работы специалистов по анализу данных и аналитики:

+ Как правило требуется административный доступ к серверу. В SQL Server 2017 г администратор базы данных роли можно использовать для предоставления определенным пользователям возможность устанавливать пакеты для личного использования, но по-прежнему администратор должен включить эту функцию.
+ Многие серверы не имеют доступа к Интернету. Установка пакетов для этих компьютеров не требует некоторых дополнительных подготовки.
+ Пакеты устанавливаются в библиотеку экземпляра. Пакеты не могут использоваться совместно экземпляров.
+ Пользователи не смогут запускать любой пакет, установленного в библиотеке пользователя.

## <a name="package-installation-guides-for-r-or-python"></a>Руководства по установке пакета для R или Python

Обратитесь к следующим статьям подробные инструкции о том, как установить новые пакеты R или Python. 

### <a name="install-new-r-packages"></a>Установка нового R-пакетов

+ [Установка дополнительных пакетов R в SQL Server](install-additional-r-packages-on-sql-server.md)

    Пакеты R можно установить на SQL Server 2016 или 2017 г., от имени администратора, с помощью средств R.

    Можно также установить пакеты R с удаленного клиента R где R Server 9.0.2 или более поздней.

    Можно также установить пакеты R в SQL Server 2017 г. с помощью инструкции DDL.

### <a name="install-new-python-packages"></a>Установить новые пакеты Python

+ [Установка новых пакетов Python в SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="prerequisites"></a>предварительные требования

Перед загрузкой или установкой любого нового пакета, ознакомьтесь с требованиями к:

+ Убедитесь в том, что версия Windows пакета: [получение правильный пакет версии и формат](#packageVersion)

+ Определите все зависимости пакета и выяснить их совместимости со средой SQL Server.

+ Проверьте версию R или совместимость версий Python. Пакет должен быть совместим с версии R или Python, который работает в SQL Server.

+ Разрешения. Определите наличие права на установку пакета. Чтобы установить библиотеку экземпляр, требуется административный доступ к компьютеру под управлением SQL Server. Если нет административного доступа к компьютеру SQL Server, найти администратором базы данных, помогающие при установке пакета.

    В 2017 г. SQL Server можно установить пакеты R с удаленного клиента, если пакет управления работает на сервере, и вы являетесь владельцем базы данных или членом роли пакета управления.

+ Рассмотрим риски и преимущества установке определенного пакета в среде SQL Server. Проверьте, содержит ли пакет (или все пакеты, которые необходимы) функции, которые были бы заблокированы в SQL Server или с помощью политики. Многие пакеты R и Python — очень плохо подходит для зафиксированного среды SQL Server. Проблемы могут включать:

    - Пакеты, которые обращаются к сети
    - Пакеты, которые требуют Java и других платформ, обычно не используется в среде SQL Server
    - Пакеты, которые требуют доступа с повышенными привилегиями файловой системы
    - Пакет используется для веб-разработки или другие задачи, которые не выигрывают, выполнив в SQL Server.

## <a name="installation-on-servers-with-no-internet-access"></a>Установка на серверах без доступа к Интернету

Как правило серверы, на которых размещены рабочие базы данных запрещают подключение к Интернету. Для установки новых пакетов R или Python в таких средах требуется подготовить все пакеты и их зависимости заранее и скопируйте файлы в папку на сервере для использования в установке.

1. Определите все зависимости пакета. 
2. Проверьте, установлены ли необходимые пакеты на сервере. Если пакет установлен, проверьте правильность версии.
3. Загрузите пакет и все зависимости на отдельный компьютер.
4. Переместите файлы в папку, доступную на сервере.
5. Выполните команду поддерживаемой установки или DDL-инструкции для установки пакета в библиотеку экземпляра.

Определение всех зависимостей может быть сложной задачей. Для R, мы рекомендуем использовать [miniCRAN](create-a-local-package-repository-using-minicran.md) Подготовка репозиторием автономный пакет.

Аналогичным образом для Python, необходимо подготовить все зависимости и сохраните их локально. Не забудьте использовать двоичные файлы совместимых с Windows и WHL формат.
