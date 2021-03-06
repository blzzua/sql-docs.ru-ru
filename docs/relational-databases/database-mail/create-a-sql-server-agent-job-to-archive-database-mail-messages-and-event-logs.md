---
title: Создание задания агента SQL Server по архивации сообщений и журналов событий компонента Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: database-mail
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- archiving mail messages and attachments [SQL Server]
- removing mail messages and attachements
- Database Mail [SQL Server], archiving
- saving mail messages and attachments
ms.assetid: 8f8f0fba-f750-4533-9b76-a9cdbcdc3b14
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8823296f7fd9a64fdc0d5b978a22e89e8b415d37
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs"></a>Создание задания агента SQL Server по архивации сообщений компонента Database Mail и журналов событий базы данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Копии сообщений компонента Database Mail и их вложения хранятся в таблицах **msdb** , расположенных в журнале событий компонента Database Mail. Может возникнуть потребность периодического уменьшения объема ненужных таблиц и архивных сообщений и событий. Представленные ниже процедуры используются для создания задания агента SQL Server для автоматизации указанного процесса.  
  
-   **Перед началом работы:**  , [Необходимые компоненты](#Prerequisites), [Рекомендации](#Recommendations), [Разрешения](#Permissions)  
  
-   **To Archive Database Mail messages and logs using :**  [SQL Server Agent](#Process_Overview)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Необходимые компоненты  
 Новые таблицы для хранения архивных данных могут быть расположены в специальной архивной базе данных. Кроме того, строки можно экспортировать в текстовый файл.  
   
###  <a name="Recommendations"></a> Рекомендации  
 В случае сбоя задания в процессе работы, возможно, понадобится провести дополнительную проверку и отправить уведомления операторам.  
  
  
###  <a name="Permissions"></a> Разрешения  
 Чтобы выполнить хранимые процедуры, описанные в данном разделе, пользователь должен быть членом предопределенной роли сервера **sysadmin** .  
  
  
###  <a name="Process_Overview"></a> Общие сведения о процессе  
  
-   Первая процедура, которая создает задание с именем «Archive Database Mail», состоит из следующих действий.  
  
    1.  Скопируйте все сообщения из таблиц компонента Database Mail в новую таблицу с именем прошлого месяца в формате **DBMailArchive_***<год_месяц>*.  
  
    2.  Скопируйте вложения, прикрепленные к сообщениям, скопированным на первом шаге из таблиц компонента Database Mail, в новую таблицу с именем прошлого месяца в формате **DBMailArchive_Attachments_***<год_месяц>*.  
  
    3.  Скопируйте из журналов событий компонента Database Mail события, имеющие отношение к сообщениям, скопированным на первом шаге, из таблиц компонента Database Mail в новую таблицу с именем прошлого месяца в формате **DBMailArchive_Log_***<год_месяц>*.  
  
    4.  Удаление всех скопированных элементов из таблиц компонента Database Mail.  
  
    5.  Удаление всех событий, связанных со скопированными элементами, хранящихся в журнале событий компонента Database Mail.  
  
-   Планирование задания для периодического выполнения.  
  
  
## <a name="to-create-a-sql-server-agent-job"></a>Создание задания агента SQL Server  
  
1.  В обозревателе объектов разверните узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , правой кнопкой мыши щелкните элемент **Задания**и выберите команду **Создать задание**.  
  
2.  В диалоговом окне **Создание задания** в поле **Имя** введите **Archive Database Mail**.  
  
3.  В окне **Владелец** подтвердите принадлежность владельца к предопределенной роли сервера **sysadmin** .  
  
4.  В окне **Категория** выберите **Обслуживание базы данных**.  
  
5.  В поле **Описание** введите **Archive Database Mail messages**, а затем выберите вкладку **Шаги**.  
  
 [Обзор](#Process_Overview)  
  
## <a name="to-create-a-step-to-archive-the-database-mail-messages"></a>Создание шага по архивации сообщений компонента Database Mail  
  
1.  На странице **Шаги** нажмите кнопку **Создать**.  
  
2.  В текстовое поле **Имя шага** введите **Copy Database Mail Items**.  
  
3.  В поле **Тип** выберите **Скрипт Transact-SQL (T-SQL)**.  
  
4.  В поле **База данных** выберите **msdb**.  
  
5.  Чтобы создать таблицу с именем прошлого месяца, в которой будут храниться все строки данных за предыдущие месяцы, в окне **Команда** введите представленную ниже инструкцию:  
  
    ```sql  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_' + @LastMonth + '] FROM sysmail_allitems WHERE send_request_date < ''' + @CopyDate +'''';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  Нажмите кнопку **ОК** , чтобы сохранить шаг.  
  
 [Обзор](#Process_Overview)  
  
## <a name="to-create-a-step-to-archive-the-database-mail-attachments"></a>Создание шага по архивации вложений компонента Database Mail  
  
1.  На странице **Шаги** нажмите кнопку **Создать**.  
  
2.  В текстовое поле **Имя шага** введите **Copy Database Mail Attachments**.  
  
3.  В поле **Тип** выберите **Скрипт Transact-SQL (T-SQL)**.  
  
4.  В поле **База данных** выберите **msdb**.  
  
5.  Чтобы создать таблицу с именем прошлого месяца, в которой будут храниться все вложения, связанные с сообщениями, скопированными на предыдущем шаге, в окне **Команда** введите представленную ниже инструкцию:  
  
    ```sql  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Attachments_' + @LastMonth + '] FROM sysmail_attachments   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  Нажмите кнопку **ОК** , чтобы сохранить шаг.  
  
 [Обзор](#Process_Overview)  
  
## <a name="to-create-a-step-to-archive-the-database-mail-log"></a>Создание шага по архивации журнала компонента Database Mail  
  
1.  На странице **Шаги** нажмите кнопку **Создать**.  
  
2.  В текстовом поле **Имя шага** введите **Copy Database Mail Log**.  
  
3.  В поле **Тип** выберите **Скрипт Transact-SQL (T-SQL)**.  
  
4.  В поле **База данных** выберите **msdb**.  
  
5.  Чтобы создать таблицу с именем прошлого месяца, в которой будут храниться все записи журнала, связанные с сообщениями, скопированными на предыдущих шагах, в окне **Команда** введите представленную ниже инструкцию:  
  
    ```sql  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Log_' + @LastMonth + '] FROM sysmail_Event_Log   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  Нажмите кнопку **ОК** , чтобы сохранить шаг.  
  
 [Обзор](#Process_Overview)  
  
## <a name="to-create-a-step-to-remove-the-archived-rows-from-database-mail"></a>Создание шага по удалению архивных строк из компонента Database Mail  
  
1.  На странице **Шаги** нажмите кнопку **Создать**.  
  
2.  В текстовом поле **Имя шага** введите **Remove rows from Database Mail**.  
  
3.  В поле **Тип** выберите **Скрипт Transact-SQL (T-SQL)**.  
  
4.  В поле **База данных** выберите **msdb**.  
  
5.  Чтобы удалить из таблиц компонента Database Mail строки, созданные ранее начала текущего месяца, в окне **Команда** введите представленную ниже инструкцию:  
  
    ```sql  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @CopyDate ;  
    ```  
  
6.  Нажмите кнопку **ОК** , чтобы сохранить шаг.  
  
 [Обзор](#Process_Overview)  
  
## <a name="to-create-a-step-to-remove-the-archived-items-from-database-mail-event-log"></a>Создание шага по удалению архивных элементов из журнала событий компонента Database Mail  
  
1.  На странице **Шаги** нажмите кнопку **Создать**.  
  
2.  В текстовом поле **Имя шага** введите **Remove rows from Database Mail event log**.  
  
3.  В поле **Тип** выберите **Скрипт Transact-SQL (T-SQL)**.  
  
4.  Чтобы удалить из журнала событий компонента Database Mail строки, созданные ранее начала текущего месяца, в окне **Команда** введите представленную ниже инструкцию:  
  
    ```sql  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_log_sp @logged_before = @CopyDate ;  
    ```  
  
5.  Нажмите кнопку **ОК** , чтобы сохранить шаг.  
  
 [Обзор](#Process_Overview)  
  
## <a name="to-schedule-the-job-to-run-periodically"></a>Планирование периодического выполнения задания  
  
1.  В диалоговом окне **Создание задания** выберите **Расписания**.  
  
2.  На странице **Расписания** нажмите кнопку **Создать**.  
  
3.  В текстовое поле **Имя** введите **Archive Database Mail**.  
  
4.  В окне **Тип расписания** выберите **Циклический**.  
  
5.  В области **Периодичность** задайте параметр выполнения периодического задания, например, первое число каждого месяца.  
  
6.  В области **Сколько раз в день** выберите **Выполняется один раз в \<время>**.  
  
7.  Убедитесь, что другие параметры настроены правильно, и сохраните расписание, нажав кнопку **OK** .  
  
8.  Нажмите кнопку **ОК** , чтобы сохранить задание.  
  
 [Обзор](#Process_Overview)  
  
  
