---
title: Что&#39;новые возможности служб SQL Server Machine Learning | Документы Microsoft
ms.date: 03/17/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 07c21de29f41826d1314f92f77fd9277f84cb0e7
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Новые возможности служб SQL Server машины обучения 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Возможности обучения машины будут добавлены к SQL Server в каждом выпуске как мы продолжаем развернуть, расширить и улучшить интеграцию платформы данных и обработки и анализа данных, анализа и защищено обучения, который вы хотите реализовать по данным. 

## <a name="new-in-sql-server-2017"></a>Новые возможности SQL Server 2017 г.

Этот выпуск добавлена поддержка Python и отрасли алгоритмов машинного обучения. Переименован в соответствии с новой областью 2017 г. SQL Server помечен появлением **обучения машины службы (в базе данных) для SQL Server**, благодаря поддержке языка Python и R. 

Этот выпуск также появился **обучения машины сервера SQL Server (автономный)**, полностью независим от SQL Server для рабочих нагрузок R и Python, которые вы хотите запустить на выделенной системы. С автономным сервером можно распространять и масштабирования решения R или Python без использования SQL Server.

| Выпуск | Обновления компонентов |
|---------|---------------|
| CU 4 | Пакет обновления и исправления ошибок, но это не новая функция объявлений. |
| CU 3 | Python модели сериализации в revoscalepy, с помощью [rx_serialize_model функция](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model).<br/><br/>[Оценки собственного](sql-native-scoring.md) плюс усовершенствования [оценки в реальном времени](real-time-scoring.md). С оценки в базе данных, пропускная способность — миллиона строк в секунду, с помощью R-модели. В этом обновлении оценки в реальном времени и оценки собственного обеспечивают более высокую производительность в одной строки и массовой оценки. Собственный оценки использует функцию T-SQL для быстрой оценки может выполняться в любом выпуске SQL Server, даже в Linux. Функция требует без установки R или дополнительной настройки. Это означает обучения модели в другом месте, сохраните его в SQL Server и затем выполнять количественную оценку без вызова R. Дополнительные сведения о методологиях оценки см. в разделе [выполнении оценки в реальном времени или собственного оценки](r/how-to-do-realtime-scoring.md). |
| CU 2 | Пакет обновления и исправления ошибок, но это не новая функция объявлений. |
| CU 1 | В revoscalepy, добавляет rx_create_col_info для возвращения сведений о схеме из источника данных SQL Server, аналогично [rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo) для R. <br/><br/>Усовершенствования [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) для поддержки параллельных сценариях с использованием `RxLocalParallel` контекста вычислений.|
| Начальный выпуск |[**Интеграция Python для аналитики в базе данных**](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/) <br/><br/>[Revoscalepy](python/what-is-revoscalepy.md) пакет является эквивалентом Python RevoScaleR. Можно создавать модели Python для линейной и логистической регрессии, деревья принятия решений, повышенных деревьев и случайные леса, все параллельно и способны выполнялась в контекстах удаленных вычислений. Данный пакет поддерживает использование нескольких источников данных и контекстах удаленных вычислений. Специалист по анализу данных или разработчик могут выполнять код Python на удаленный экземпляр SQL Server, для просмотра данных или моделей создаются без перемещения данных. <br/><br/>[Microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) пакет является эквивалентом Python MicrosoftML R-пакет.<br/><br/>T-SQL и Python интеграция через [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Может вызывать любой код Python, с помощью этой хранимой процедуры. Эта инфраструктура безопасности обеспечивает развертывание корпоративного уровня Python моделей и сценариев, которые могут вызываться из приложения с помощью простой хранимой процедуры. Повышение производительности достигается путем потоковой передачи данных из SQL в процессы Python и параллелизации кольцо MPI. <br/><br/>T-SQL можно использовать [PREDICT](../t-sql/queries/predict-transact-sql.md) функцию для выполнения [оценки собственного](sql-native-scoring.md) на предварительно обученной модели, которая ранее была сохранена в требуемый двоичный формат.|
| Начальный выпуск | [**MicrosoftML (R)** ](using-the-microsoftml-package.md) содержит состояние современных машинного обучения алгоритмы и преобразование данных, может быть контекстах удаленных вычислений масштабированный или запускаться в. Алгоритмы включают настраиваемые глубоких нейронных сетей, деревья принятия решений быстрого и леса принятия решений, линейной регрессии и логистической регрессии. |
| Начальный выпуск | [**Предварительно обученной модели** ](r/install-pretrained-models-sql-server.md) для распознавания изображений и анализ мнений положительные отрицательные. Эти модели используются для создания прогнозов на ваших данных. |
| Начальный выпуск | [**Пакет управления**](r/r-package-management-for-sql-server-r-services.md), включая следующие основные особенности: роли, чтобы помочь Администратору управлять пакетами и назначение разрешений для установки пакетов, базы данных [создать ВНЕШНЮЮ БИБЛИОТЕКУ](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) инструкции T-SQL, Справка администраторов баз данных управлять пакетами, без необходимости знать R и R богатый набор функций в [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) для установки, удаление или перечисление пакетов, принадлежащих пользователям. |
| Начальный выпуск | [**Ввода в эксплуатацию через mrsdeploy** ](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package) для развертывания и размещения R-сценария веб-службы. Применяется только для сценария R (эквивалента Python). Предназначен для параметра server (автономный), чтобы избежать конкуренции ресурсов с другими операциями SQL Server. |


## <a name="new-in-sql-server-2016"></a>Новые возможности SQL Server 2016

Этой машины выпуске появилась в SQL Server с помощью функциональных возможностей обучения **служб R SQL Server 2016**, подсистема аналитики в базе данных для сценария обработки R на данных, находящихся в экземпляр ядра СУБД.

Кроме того **SQL Server 2016 R Server (изолированный)** был выпущен как способ установки R Server на сервере Windows. Первоначально программа установки SQL Server содержит единственный способ установки R Server для Windows. В последующих выпусках разработчики и специалисты по анализу данных, желавшим R Server для Windows использовать другой автономный установщик для достижения общей цели. Изолированный сервер в SQL Server является функциональным эквивалентом автономная Серверная система [Microsoft R Server для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

| Выпуск |Обновления компонентов |
|---------|----------------|
| CU | [**В реальном времени оценки** ](real-time-scoring.md) использует собственные библиотеки C++ для чтения модели, хранящихся в оптимизированный двоичный формат и создавать прогнозы без необходимости вызывать среду выполнения R. В результате оценки операции гораздо быстрее. С помощью оценки в реальном времени, можно выполнить хранимую процедуру или выполнять оценки из кода R в реальном времени. В реальном времени оценки может также использоваться для SQL Server 2016, если экземпляр обновляется до последней версии [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]. |
| Начальный выпуск | [**Интеграция R для аналитики в базе данных**](r/sql-server-r-services.md). <br/><br/> R-пакетов R вызывающей функции в T-SQL и наоборот. Функции RevoScaleR обеспечения аналитики R в масштабе, фрагментация на компоненты, согласование данных и управление распределенная обработка и статистическая обработка результатов. В службах SQL Server 2016 R (в базе данных) подсистема RevoScaleR интегрирован с экземпляром компонента database engine, brining данные и аналитика вместе в один и тот же контекст обработки. <br/><br/>Интеграция T-SQL и R через [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Может вызывать любой код R, с помощью этой хранимой процедуры. Эта инфраструктура безопасности обеспечивает развертывание корпоративного уровня Rn моделей и сценариев, которые могут вызываться из приложения с помощью простой хранимой процедуры. Повышение производительности достигается путем потоковой передачи данных из SQL в процессы R и параллелизации кольцо MPI. <br/><br/>T-SQL можно использовать [PREDICT](../t-sql/queries/predict-transact-sql.md) функцию для выполнения [оценки собственного](sql-native-scoring.md) на предварительно обученной модели, которая ранее была сохранена в требуемый двоичный формат.|

## <a name="linux-support-roadmap"></a>Стратегия поддержка Linux

Машинное обучение с помощью R или Python в базе данных в настоящее время не поддерживается в SQL Server в Linux. Найдите объявления в более поздней версии.

Однако в Linux могут выполнять [оценки собственного](sql-native-scoring.md) с помощью функции ПРОГНОЗИРОВАНИЯ T-SQL. Оценки собственного позволяет оценки из предварительно обученные модели очень быстро, без вызова или даже требования среды выполнения R. Это означает, что SQL Server в Linux можно использовать для создания прогнозов очень быстро, для обслуживания клиентских приложений.

## <a name="next-steps"></a>Следующие шаги

+ [Установка служб SQL Server 2017 г машинного обучения (в базе данных)](install/sql-machine-learning-services-windows-install.md)
+ [Машины обучения учебники и примеры](tutorials/machine-learning-services-tutorials.md)
