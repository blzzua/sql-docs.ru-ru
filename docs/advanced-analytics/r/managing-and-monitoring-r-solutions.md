---
title: Управление и мониторинг машины обучению | Документы Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 07/26/2016
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 8fa8eabdb5556f8b46ef46e22d077be43d574687
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="managing-and-monitoring-machine-learning-solutions"></a>Управление и мониторинг машины обучению
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описаны возможности обучения SQL Server Machine Services, которые важны для администраторов баз данных, которым необходимо начать работу с решений R и Python.

**Применяется к:** служб R SQL Server 2016, SQL Server 2017 г машинного обучения служб

## <a name="security"></a>безопасность

Администраторы базы данных необходимо предоставить доступ к данным, не только специалистам по анализу данных, но различным разработчикам отчетов, бизнес-аналитикам и потребителям бизнес-данных. Интеграция R (и теперь Python) в SQL Server предоставляет множество преимуществ администратору базы данных, который поддерживает роль обработки и анализа данных.

+ Архитектура [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] защищает ваши базы данных и изолирует сеансы кода R от экземпляра базы данных.

+ Можно указать, кто может выполнять сценарии R, чтобы данные, используемые в заданиях R, контролировались ролями безопасности, определенными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

+ Администратор базы данных, роли можно использовать для управления установкой пакетов R и выполнение скриптов R и Python.

Дополнительные сведения см. в разделах:

+ [Вопросы безопасности для среды выполнения R в SQL Server](../../advanced-analytics/r/security-considerations-for-the-r-runtime-in-sql-server.md)

+ [Общие сведения о безопасности R](../r/security-overview-sql-server-r.md)

+ [Общие сведения о безопасности Python](../python/security-overview-sql-server-python-services.md)

+ [Установка пакетов R и управление ими](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)

## <a name="configuration-and-management"></a>Настройка и управление

Администраторам баз данных необходимо интегрировать конкурирующие проекты и приоритеты в единую точку контакта: сервер базы данных. Они должны поддерживать аналитика при поддержании работоспособности хранилищ данных оперативной и создания отчетов. Интеграция машинного обучения с помощью SQL Server предоставляет множество преимуществ администратору базы данных, который выступает в все более важную роль в развертывании эффективная инфраструктура для обработки и анализа данных.

+ Сеансы R и Python выполняются в отдельном процессе, чтобы сервер продолжал работать как обычно, даже если среда выполнения внешнего сценария имеет проблемы.

+ Недостаточно привилегий физического учетных записей, используются для хранения и изолировать действия внешнего скрипта.

+ Администратор базы данных можно использовать стандартные средства управления SQL Server ресурсов для управления объемом ресурсов, выделяемых для среды выполнения R, чтобы предотвратить на общую производительность сервера негативное влияние масштабных вычислений.

Дополнительные сведения см. в разделах:

+ [Управление ресурсами для служб R](../r/resource-governance-for-r-services.md)

+ [Настройка и управление расширений углубленной аналитики](../r/configure-and-manage-advanced-analytics-extensions.md)
