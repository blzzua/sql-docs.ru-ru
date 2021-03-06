---
title: "Восстановление базы данных SQL Server в Docker | Документы Microsoft"
description: "Этот учебник показывает способ восстановления резервной копии базы данных SQL Server в новый контейнер Linux Docker."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: ea1aa01f3917c0d6ee4423861a3bf4fb985f53fa
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="restore-a-sql-server-database-in-a-linux-docker-container"></a>Восстановление базы данных SQL Server в контейнер Linux Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Этот учебник посвящен перемещения и восстановления файла резервной копии SQL Server в Linux 2017 г. SQL Server образ контейнера, запущенного на Docker.

> [!div class="checklist"]
> * По запросу и запустите последний образ контейнера Linux 2017 г. SQL Server.
> * Скопируйте файл базы данных World Wide Importers в контейнер.
> * Восстановите базу данных в контейнере.
> * Выполните инструкции Transact-SQL для просмотра и изменения базы данных.
> * Создайте резервную копию базы данных.

## <a name="prerequisites"></a>предварительные требования

* Подсистема docker 1.8 + для какого-либо поддерживается дистрибутив Linux или Docker для Mac и Windows. Дополнительные сведения см. в разделе [установить Docker](https://docs.docker.com/engine/installation/).
* Минимум 2 ГБ места на диске
* Минимум 2 ГБ ОЗУ
* [Требования к системе для SQL Server в Linux](sql-server-linux-setup.md#system).

## <a name="pull-and-run-the-container-image"></a>По запросу, а затем запускать образ контейнера

1. Откройте терминал bash на Linux или Mac или сеанс PowerShell с повышенными правами в Windows.

1. Образ контейнера Linux 2017 г. SQL Server по запросу из Docker Hub.

    ```bash
    sudo docker pull microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker pull microsoft/mssql-server-linux:2017-latest
    ```

    > [!TIP]
    > В этом учебнике примеров команд docker заданы для команд bash (Linux или Mac) и PowerShell (Windows).

1. Чтобы запустить образ контейнера с помощью Docker, можно использовать следующую команду:

    ```bash
    sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
       --name 'sql1' -p 1401:1433 \
       -v sql1data:/var/opt/mssql \
       -d microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
       --name "sql1" -p 1401:1433 `
       -v sql1data:/var/opt/mssql `
       -d microsoft/mssql-server-linux:2017-latest
    ```

    Эта команда создает контейнер 2017 г. SQL Server с выпуска Developer edition (по умолчанию). Порт SQL Server **1433** предоставляется на узле в качестве порта **1401**. Необязательный `-v sql1data:/var/opt/mssql` параметр создает контейнер томов данных с именем **sql1ddata**. Используется для хранения данных, созданный на сервере SQL Server.

   > [!NOTE]
   > Процесс запуска выпусков SQL Server производства в контейнерах немного отличается. Дополнительные сведения см. в разделе [запуска производства образы контейнеров](sql-server-linux-configure-docker.md#production). Если вы используете те же имена контейнеров и порты, пошаговым руководством по-прежнему работает с контейнерами в рабочей среде.

1. Чтобы просмотреть в контейнеры Docker, используйте `docker ps` команды.

    ```bash
    sudo docker ps -a
    ```

    ```PowerShell
    docker ps -a
    ```
 
1. Если **состояние** столбце отображается состояние **копирование**, затем SQL Server работает в контейнере и прослушивается порт, указанный в **ПОРТЫ** столбца. Если **состояние** столбца отображается контейнер к SQL Server **завершил работу**, см. [Устранение неполадок конфигурации руководства](sql-server-linux-configure-docker.md#troubleshooting).

   ```
   $ sudo docker ps -a

   CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
   941e1bdf8e1d        microsoft/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour    0.0.0.0:1401->1433/tcp   sql1
   ```

## <a name="change-the-sa-password"></a>Измените пароль учетной записи SA

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="copy-a-backup-file-into-the-container"></a>Скопируйте файл резервной копии в контейнер

В этом учебнике используется [образца базы данных Wide World Importers](../sample/world-wide-importers/wide-world-importers-documentation.md). Для загрузки и скопируйте файл резервной копии базы данных Wide World Importers контейнера SQL Server, выполните следующие действия.

1. Во-первых, используйте **docker exec** создать папку резервного копирования. Следующая команда создает **/var/opt/mssql/** каталог в контейнере SQL Server.

   ```bash
   sudo docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

   ```PowerShell
   docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

1. Затем загрузить [WideWorldImporters Full.bak](https://github.com/Microsoft/sql-server-samples/releases/tag/wide-world-importers-v1.0) файла на хост-компьютер. Следующие команды, перейдите в папку home, пользователей и загружает файл резервной копии как **wwi.bak**.

   ```bash
   cd ~
   curl -L -o wwi.bak 'https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak'
   ```

   ```PowerShell
   curl -OutFile "wwi.bak" "https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak"
   ```

1. Используйте **docker cp** для копирования файла резервной копии в контейнер в **/var/opt/mssql/backup** каталога.

   ```bash
   sudo docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

   ```PowerShell
   docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

## <a name="restore-the-database"></a>Восстановление базы данных

Файл резервной копии теперь находится внутри контейнера. Перед восстановлением резервной копии, важно знать логических имен файлов и типов файлов в резервной копии. Следующие команды Transact-SQL проверки резервной копии и выполнить восстановление с помощью **sqlcmd** в контейнере.

> [!TIP]
> В этом учебнике используется **sqlcmd** внутри контейнера, так как контейнер поставляется с предварительно установлено это средство. Тем не менее, можно выполнять также инструкции Transact-SQL с другими клиентами средств вне контейнера, таких как [кода Visual Studio](sql-server-linux-develop-use-vscode.md) или [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md). Чтобы подключиться, используйте порт узла, который был сопоставлен порт 1433 в контейнере. В этом примере это **localhost, 1401** на хост-компьютере и **Host_IP_Address 1401** удаленно.

1. Запустите **sqlcmd** внутри контейнера, в список логических имен файлов и путей внутри резервной копии. Это делается с **RESTORE FILELISTONLY** инструкции Transact-SQL.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost \
      -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'RESTORE FILELISTONLY FROM DISK = "/var/opt/mssql/backup/wwi.bak"' \
      | tr -s ' ' | cut -d ' ' -f 1-2
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost `
      -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "RESTORE FILELISTONLY FROM DISK = '/var/opt/mssql/backup/wwi.bak'"
   ```

   Вы увидите результат, аналогичный приведенному ниже:

   ```
   LogicalName   PhysicalName
   ------------------------------------------
   WWI_Primary   D:\Data\WideWorldImporters.mdf
   WWI_UserData   D:\Data\WideWorldImporters_UserData.ndf
   WWI_Log   E:\Log\WideWorldImporters.ldf
   WWI_InMemory_Data_1   D:\Data\WideWorldImporters_InMemory_Data_1
   ```

1. Вызовите **RESTORE DATABASE** команду, чтобы восстановить базу данных внутри контейнера. Укажите новые пути для каждого файла на предыдущем шаге.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'RESTORE DATABASE WideWorldImporters FROM DISK = "/var/opt/mssql/backup/wwi.bak" WITH MOVE "WWI_Primary" TO "/var/opt/mssql/data/WideWorldImporters.mdf", MOVE "WWI_UserData" TO "/var/opt/mssql/data/WideWorldImporters_userdata.ndf", MOVE "WWI_Log" TO "/var/opt/mssql/data/WideWorldImporters.ldf", MOVE "WWI_InMemory_Data_1" TO "/var/opt/mssql/data/WideWorldImporters_InMemory_Data_1"'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "RESTORE DATABASE WideWorldImporters FROM DISK = '/var/opt/mssql/backup/wwi.bak' WITH MOVE 'WWI_Primary' TO '/var/opt/mssql/data/WideWorldImporters.mdf', MOVE 'WWI_UserData' TO '/var/opt/mssql/data/WideWorldImporters_userdata.ndf', MOVE 'WWI_Log' TO '/var/opt/mssql/data/WideWorldImporters.ldf', MOVE 'WWI_InMemory_Data_1' TO '/var/opt/mssql/data/WideWorldImporters_InMemory_Data_1'"
   ```

   Вы увидите результат, аналогичный приведенному ниже:

   ```
   Processed 1464 pages for database 'WideWorldImporters', file 'WWI_Primary' on file 1.
   Processed 53096 pages for database 'WideWorldImporters', file 'WWI_UserData' on file 1.
   Processed 33 pages for database 'WideWorldImporters', file 'WWI_Log' on file 1.
   Processed 3862 pages for database 'WideWorldImporters', file 'WWI_InMemory_Data_1' on file 1.
   Converting database 'WideWorldImporters' from version 852 to the current version 869.
   Database 'WideWorldImporters' running the upgrade step from version 852 to version 853.
   Database 'WideWorldImporters' running the upgrade step from version 853 to version 854.
   Database 'WideWorldImporters' running the upgrade step from version 854 to version 855.
   Database 'WideWorldImporters' running the upgrade step from version 855 to version 856.
   Database 'WideWorldImporters' running the upgrade step from version 856 to version 857.
   Database 'WideWorldImporters' running the upgrade step from version 857 to version 858.
   Database 'WideWorldImporters' running the upgrade step from version 858 to version 859.
   Database 'WideWorldImporters' running the upgrade step from version 859 to version 860.
   Database 'WideWorldImporters' running the upgrade step from version 860 to version 861.
   Database 'WideWorldImporters' running the upgrade step from version 861 to version 862.
   Database 'WideWorldImporters' running the upgrade step from version 862 to version 863.
   Database 'WideWorldImporters' running the upgrade step from version 863 to version 864.
   Database 'WideWorldImporters' running the upgrade step from version 864 to version 865.
   Database 'WideWorldImporters' running the upgrade step from version 865 to version 866.
   Database 'WideWorldImporters' running the upgrade step from version 866 to version 867.
   Database 'WideWorldImporters' running the upgrade step from version 867 to version 868.
   Database 'WideWorldImporters' running the upgrade step from version 868 to version 869.
   RESTORE DATABASE successfully processed 58455 pages in 18.069 seconds (25.273 MB/sec).
   ```

## <a name="verify-the-restored-database"></a>Проверка восстановленной базы данных

Выполните следующий запрос, чтобы отобразить список имен баз данных в контейнере:

```bash
sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
   -Q 'SELECT Name FROM sys.Databases'
```

```PowerShell
docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
   -Q "SELECT Name FROM sys.Databases"
```

Вы увидите **WideWorldImporters** в список баз данных.

## <a name="make-a-change"></a>Изменить

Следующие шаги внести изменения в базе данных.

1. Выполните запрос, чтобы просмотреть 10 верхних элементов в **Warehouse.StockItems** таблицы.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT TOP 10 StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems ORDER BY StockItemID'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT TOP 10 StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems ORDER BY StockItemID"
   ```

   Вы увидите список имена и идентификаторы элементов:

   ```
   StockItemID StockItemName
   ----------- -----------------
             1 USB missile launcher (Green)
             2 USB rocket launcher (Gray)
             3 Office cube periscope (Black)
             4 USB food flash drive - sushi roll
             5 USB food flash drive - hamburger
             6 USB food flash drive - hot dog
             7 USB food flash drive - pizza slice
             8 USB food flash drive - dim sum 10 drive variety pack
             9 USB food flash drive - banana
            10 USB food flash drive - chocolate bar
   ```

1. Обновите Описание первого элемента со следующими **обновление** инструкции:

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'UPDATE WideWorldImporters.Warehouse.StockItems SET StockItemName="USB missile launcher (Dark Green)" WHERE StockItemID=1; SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "UPDATE WideWorldImporters.Warehouse.StockItems SET StockItemName='USB missile launcher (Dark Green)' WHERE StockItemID=1; SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   Вы увидите выходные данные, аналогичные следующим текстом:

   ```
   (1 rows affected)
   StockItemID StockItemName
   ----------- ------------------------------------
             1 USB missile launcher (Dark Green)
   ```

## <a name="create-a-new-backup"></a>Создание резервной копии

После восстановления базы данных в контейнер может также потребоваться регулярно создавать резервные копии баз данных внутри запущенного контейнера. Действия выполните той же модели, к предыдущим шагам, но в обратном порядке.

1. Используйте **резервной копии базы данных** команды Transact-SQL для создания резервной копии базы данных в контейнере. Данный учебник создает новый файл резервной копии, **wwi_2.bak**, в созданном ранее **/var/opt/mssql/backup** каталога.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q "BACKUP DATABASE [WideWorldImporters] TO DISK = N'/var/opt/mssql/backup/wwi_2.bak' WITH NOFORMAT, NOINIT, NAME = 'WideWorldImporters-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "BACKUP DATABASE [WideWorldImporters] TO DISK = N'/var/opt/mssql/backup/wwi_2.bak' WITH NOFORMAT, NOINIT, NAME = 'WideWorldImporters-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
   ```

   Вы увидите результат, аналогичный приведенному ниже:

   ```
   10 percent processed.
   20 percent processed.
   30 percent processed.
   40 percent processed.
   50 percent processed.
   60 percent processed.
   70 percent processed.
   Processed 1200 pages for database 'WideWorldImporters', file 'WWI_Primary' on file 1.
   Processed 53096 pages for database 'WideWorldImporters', file 'WWI_UserData' on file 1.
   80 percent processed.
   Processed 3865 pages for database 'WideWorldImporters', file 'WWI_InMemory_Data_1' on file 1.
   Processed 938 pages for database 'WideWorldImporters', file 'WWI_Log' on file 1.
   100 percent processed.
   BACKUP DATABASE successfully processed 59099 pages in 25.056 seconds (18.427 MB/sec).
   ```

1. Скопируйте файл резервной копии из контейнера, а также на хост-компьютере.

   ```bash
   cd ~
   sudo docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls -l wwi*
   ```

   ```PowerShell
   cd ~
   docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls -l wwi*
   ```

## <a name="use-the-persisted-data"></a>Использовать сохраненные данные

Кроме подсчета резервные копии баз данных для защиты данных, можно также использовать контейнеры томов данных. В начале этого учебника создан **sql1** контейнер с `-v sql1data:/var/opt/mssql` параметра. **Sql1data** контейнер томов данных сохраняется **/var/opt/mssql** данных даже после удаления контейнера. Следующие шаги полностью удалить **sql1** контейнера, а затем создать новый контейнер **sql2**, с материализованных данных.

1. Остановить **sql1** контейнера.

   ```bash
   sudo docker stop sql1
   ```

   ```PowerShell
   docker stop sql1
   ```

1. Удалите контейнер. Это действие не удаляет ранее созданный **sql1data** контейнер томов данных и сохраненные данные в нем.

   ```bash
   sudo docker rm sql1
   ```

   ```PowerShell
   docker rm sql1
   ```

1. Создайте контейнер, **sql2**и повторно использовать **sql1data** контейнер томов данных.

    ```bash
    sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
       --name 'sql2' -e 'MSSQL_PID=Developer' -p 1401:1433 \
       -v sql1data:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
       --name "sql2" -e "MSSQL_PID=Developer" -p 1401:1433 `
       -v sql1data:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
    ```

1. Базы данных Wide World Importers теперь находится в новый контейнер. Выполните запрос для проверки предыдущего внесенные изменения.

   ```bash
   sudo docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   > [!NOTE]
   > Пароль учетной записи SA не пароль, указанный для **sql2** контейнера, `MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>`. Все данные SQL Server была восстановлена из **sql1**, включая измененные пароли из ранее в этом учебнике. В действительности из-за восстановления данных в /var/opt/mssql игнорируются некоторые параметры следующим образом. По этой причине, что пароль указан `<YourNewStrong!Passw0rd>` как показано ниже.

## <a name="next-steps"></a>Следующие шаги

В этом учебнике вы узнали, как для резервного копирования базы данных в Windows и переместите его на сервер Linux, под управлением SQL Server, RC2 2017 г. Узнать, как для:
> [!div class="checklist"]
> * Создание образов контейнеров Linux 2017 г. SQL Server.
> * Скопируйте резервные копии баз данных SQL Server в контейнер.
> * Выполнять инструкции Transact-SQL внутри контейнера с **sqlcmd**.
> * Создание и извлеките файлы резервных копий из контейнера.
> * Использование контейнеров томов с данными в Docker для сохранения данных SQL Server.

Далее необходимо Проверьте другие конфигурации Docker и устранения неполадок:

> [!div class="nextstepaction"]
>[Руководство по конфигурации для SQL Server 2017 г. для Docker](sql-server-linux-configure-docker.md)
