---
title: "Планирование выполнения пакета служб SSIS в Azure | Документы Майкрософт"
ms.date: 01/16/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4724d7a306e59e05d17f466643146d868f372a7f
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="schedule-the-execution-of-an-ssis-package-on-azure"></a>Планирование выполнения пакета служб SSIS в Azure
Вы можете запланировать выполнение пакетов, хранящихся в базе данных каталога SSISDB на сервере базы данных SQL Azure, выбрав один из следующих вариантов планирования:
-   [Агент SQL Server](#agent)
-   [Задания обработки эластичных баз данных SQL](#elastic)
-   [Операция хранимой процедуры SQL Server для фабрики данных Azure](#sproc)

## <a name="agent"></a> Планирование пакета с помощью агента SQL Server

### <a name="prerequisite---create-a-linked-server"></a>Необходимое условие — создание связанного сервера

Прежде чем использовать агент SQL Server в локальной среде для планирования выполнения пакетов, хранящихся на сервере базы данных SQL Azure, нужно добавить сервер базы данных SQL Database в локальный SQL Server в качестве связанного сервера.

1.  **Настройка связанного сервера**

    ```sql
    -- Add the SSISDB database on your Azure SQL Database as a linked server to your SQL Server on premises
    EXEC sp_addlinkedserver
        @server='myLinkedServer', -- Name your linked server
        @srvproduct='',     
        @provider='sqlncli', -- Use SQL Server native client
        @datasrc='<server_name>.database.windows.net', -- Add your Azure SQL Database server endpoint
        @location=‘’,
        @provstr=‘’,
        @catalog='SSISDB'  -- Add SSISDB as the initial catalog
    ```

2.  **Настройка учетных данных связанного сервера**

    ```sql
    -- Add your Azure SQL DB server admin credentials
    EXEC sp_addlinkedsrvlogin
        @rmtsrvname = 'myLinkedServer’,
        @useself = 'false’,
        @rmtuser = 'myUsername', -- Add your server admin username
        @rmtpassword = 'myPassword' -- Add your server admin password
    ```

3.  **Настройка параметров связанного сервера**

    ```sql
    EXEC sp_serveroption 'myLinkedServer', 'rpc out', true;
    ```

Дополнительные сведения см. в разделах [Создание связанных серверов](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md) и [Связанные серверы](../../relational-databases/linked-servers/linked-servers-database-engine.md).

### <a name="create-a-sql-server-agent-job"></a>Создание задания агента SQL Server

Чтобы запланировать выполнение пакета с помощью локального агента SQL Server, создайте задание с шагом, на котором вызываются хранимые процедуры каталога служб SSIS `[catalog].[create_execution]` и затем `[catalog].[start_execution]`. Дополнительные сведения см. в разделе [Пакеты служб из заданий агента SQL Server](../packages/sql-server-agent-jobs-for-packages.md).

1.  В SQL Server Management Studio установите подключение к базе данных SQL Server в локальной среде, в которой требуется создать задание.

2.  Щелкните правой кнопкой мыши узел **Агент SQL Server**, выберите **Создать** и затем **Задание**, чтобы открыть диалоговое окно **Создание задания**.

3.  В диалоговом окне **Создание задания** перейдите на страницу **Шаги** и выберите команду **Создать**, чтобы открыть диалоговое окно **Создание шага задания**.

4.  В диалоговом окне **Создание шага задания** выберите `SSISDB` в поле **База данных**.

5.  В поле **Команда** введите скрипт Transact-SQL, аналогичный приведенному в следующем примере:

    ```sql
    -- T-SQL script to create and start SSIS package execution using SSISDB stored procedures
    DECLARE @return_value int, @exe_id bigint 

    EXEC @return_value = [YourLinkedServer].[SSISDB].[catalog].[create_execution] 
        @folder_name=N'folderName', @project_name=N'projectName', 
        @package_name=N'packageName', @use32bitruntime=0, @runincluster=1, @useanyworker=1,
        @execution_id=@exe_id OUTPUT 

    EXEC [YourLinkedServer].[SSISDB].[catalog].[set_execution_parameter_value] @exe_id,
        @object_type=50, @parameter_name=N'SYNCHRONIZED', @parameter_value=1

    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution] @execution_id=@exe_id
    ```

6.  Завершите настройку и планирование задания.

## <a name="elastic"></a> Планирование пакета с использованием заданий обработки эластичных баз данных SQL

Дополнительные сведения о заданиях обработки эластичных баз данных SQL см. в разделе [Управление облачными базами данных с горизонтальным масштабированием](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).

### <a name="prerequisites"></a>предварительные требования

Прежде чем использовать задания обработки эластичных баз данных для планирования пакетов SSIS, хранящихся в каталоге базы данных SSISDB на сервере базы данных SQL Azure, необходимо выполнить следующие действия:

1.  Установить и настроить компоненты для заданий обработки эластичных баз данных. Дополнительные сведения см. в разделе [Общие сведения об установке заданий обработки эластичных баз данных](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-service-installation).

2. Создать учетные данные уровня базы данных, которые задания смогут использовать для отправки команд в базу данных каталога SSIS. Дополнительные сведения см. в разделе [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

### <a name="create-an-elastic-job"></a>Создание задания обработки эластичных баз данных

Чтобы создать задание, используйте скрипт Transact-SQL, аналогичный приведенному в следующем примере:

```sql
-- Create Elastic Jobs target group 
EXEC jobs.sp_add_target_group 'TargetGroup' 

-- Add Elastic Jobs target group member 
EXEC jobs.sp_add_target_group_member @target_group_name='TargetGroup', 
    @target_type='SqlDatabase', @server_name='YourSQLDBServer.database.windows.net',
    @database_name='SSISDB' 

-- Add a job to schedule SSIS package execution
EXEC jobs.sp_add_job @job_name='ExecutePackageJob', @description='Description', 
    @schedule_interval_type='Minutes', @schedule_interval_count=60

-- Add a job step to create/start SSIS package execution using SSISDB catalog stored procedures
EXEC jobs.sp_add_jobstep @job_name='ExecutePackageJob', 
    @command=N'DECLARE @exe_id bigint 
        EXEC [SSISDB].[catalog].[create_execution]
            @folder_name=N''folderName'', @project_name=N''projectName'',
            @package_name=N''packageName'', @use32bitruntime=0,
            @runinscaleout=1, @useanyworker=1, 
            @execution_id=@exe_id OUTPUT         
        EXEC [SSISDB].[catalog].[start_execution] @exe_id, @retry_count=0', 
    @credential_name='YourDBScopedCredentials', 
    @target_group_name='TargetGroup' 

-- Enable the job schedule 
EXEC jobs.sp_update_job @job_name='ExecutePackageJob', @enabled=1, 
    @schedule_interval_type='Minutes', @schedule_interval_count=60 
```

## <a name="sproc"></a> Планирование пакета с использованием операции хранимой процедуры SQL Server для фабрики данных Azure

Сведения о планировании пакета SSIS с помощью операции хранимой процедуры в фабрике данных Azure см. в следующих статьях:

-   для фабрики данных версии 2: [Вызов пакета SSIS с помощью операции хранимой процедуры в фабрике данных Azure](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-stored-procedure-activity);

-   для фабрики данных версии 1: [Вызов пакета SSIS с помощью операции хранимой процедуры в фабрике данных Azure](https://docs.microsoft.com/azure/data-factory/v1/how-to-invoke-ssis-package-stored-procedure-activity).

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения об агенте SQL Server см. в разделе [Пакеты служб из заданий агента SQL Server](../packages/sql-server-agent-jobs-for-packages.md).

Дополнительные сведения о заданиях обработки эластичных баз данных SQL см. в разделе [Управление облачными базами данных с горизонтальным масштабированием](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).
