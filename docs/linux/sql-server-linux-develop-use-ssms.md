---
title: "Управление SQL Server в Linux с помощью SSMS | Документы Microsoft"
description: "Этого учебника показано, как использовать SQL Server Management Studio в Windows для подключения к SQL Server под управлением Linux."
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
ms.assetid: 30cc4564-f389-4707-9b25-8ba782cc5150
ms.workload: On Demand
ms.openlocfilehash: 442d57154222fdb06ba26ad7858eb783103e93cd
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="use-sql-server-management-studio-ssms-on-windows-to-manage-sql-server-on-linux"></a>Использование SQL Server Management Studio (SSMS) в Windows для управления SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье показано, как использовать [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) для подключения к 2017 г. SQL Server в Linux. SSMS — это приложение Windows, поэтому SSMS следует использовать при наличии компьютером Windows, можно подключиться к удаленному экземпляру SQL Server в Linux.

После успешного подключения, выполняется простой запрос Transact-SQL (T-SQL), чтобы проверить связь с базой данных.

## <a name="install-the-newest-version-of-sql-server-management-studio"></a>Установите последнюю версию SQL Server Management Studio

При работе с SQL Server, следует всегда использовать последнюю версию служб SQL Server Management Studio (SSMS). Последнюю версию SSMS постоянно обновляется и оптимизированы и в настоящее время работает с SQL Server 2017 в Linux. Чтобы загрузить и установить последнюю версию, в разделе [загрузка SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Быть в курсе событий, последняя версия SSMS предлагает при наличии доступного для загрузки новой версии. 

## <a name="connect-to-sql-server-on-linux"></a>Подключение к SQL Server в Linux

Ниже показано, как подключиться к 2017 г. SQL Server в Linux с помощью SSMS.

1. Запустите SSMS, введя **Microsoft SQL Server Management Studio** поле поиска в Windows и нажмите кнопку классического приложения.

    ![Среда SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/ssms.png)

2. В **соединение с сервером** окно, введите следующие сведения (если SSMS уже запущен, щелкните **Connect > Database Engine** для открытия **соединение с сервером** окна):

   | Настройка | Описание |
   |-----|-----|
   | **Тип сервера** | Значение по умолчанию — компонент database engine; не изменяйте это значение. |
   | **Имя сервера** | Введите имя целевом компьютере Linux SQL Server или его IP-адрес. |
   | **Проверка подлинности** | SQL Server 2017 г. в Linux, используйте **проверки подлинности SQL Server**. |
   | **Имя входа** | Введите имя пользователя, имеющего доступ к базе данных на сервере (например, значение по умолчанию **SA** учетную запись, созданную во время установки). |
   | **Пароль** | Введите пароль для указанного пользователя (для **SA** учетной записи, вы создали это во время установки). |

    ![SQL Server Management Studio: Подключиться к базе данных SQL server](./media/sql-server-linux-develop-use-ssms/connect.png)

3. Нажмите кнопку **Соединить**.

    > [!TIP]
    > Если произойдет сбой подключения, сначала попробуйте узнать проблему по сообщению об ошибке. Затем ознакомьтесь с [рекомендациями по устранению неполадок с подключением](sql-server-linux-troubleshooting-guide.md#connection).
 
5. После успешного подключения к вашей Sever SQL, **обозревателя объектов** и теперь имеют доступ к базе данных для выполнения задач администрирования или запроса данных.
 
     ![Обозреватель объектов](./media/sql-server-linux-develop-use-ssms/object-explorer.png)
     
## <a name="run-sample-queries"></a>Запустите образцы запросов

После подключения к серверу можно подключиться к базе данных и выполнение образца запроса. Если вы новичок в написании запросов, см. раздел [написание инструкций Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md).

1. Определите базу данных для выполнения запроса. Это может быть создан в новую базу данных [учебник по Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md). Или это может быть **AdventureWorks** образца базы данных, которые [загружаются и восстановить](sql-server-linux-migrate-restore-database.md).
2. В **обозревателя объектов**, перейдите в целевую базу данных на сервере.
2. Щелкните правой кнопкой мыши базу данных, а затем выберите **новый запрос**:

    ![Новый запрос. Подключиться к базе данных SQL server: SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/new-query.png)

3. В окне запроса будет напишите запрос Transact-SQL для выборки данных из одной из таблиц. В следующем примере выбираются данные из **Production.Product** таблицу **AdventureWorks** базы данных.

        SELECT TOP 10 Name, ProductNumber
        FROM Production.Product
        ORDER BY Name ASC

4. Нажмите кнопку **Execute** кнопки:

    ![Успешно. Подключиться к базе данных SQL server: SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/execute-query.png)

## <a name="next-steps"></a>Следующие шаги

В дополнении к запросам можно использовать инструкции T-SQL для создания и управления базами данных.

Если вы не знакомы с T-SQL, см. раздел [учебника: написание инструкций Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md) и [Справочник по Transact-SQL (компонент Database Engine)](https://msdn.microsoft.com/library/bb510741.aspx).

Дополнительные сведения о том, как с помощью среды SSMS см. в разделе [использовать SQL Server Management Studio](https://msdn.microsoft.com/library/ms174173.aspx).
