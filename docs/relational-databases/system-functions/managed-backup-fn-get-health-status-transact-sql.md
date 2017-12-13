---
title: "managed_backup.fn_get_health_status (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_get_health_status_TSQL
- smart_admin.fn_get_health_status_TSQL
- smart_admin.fn_get_health_status
- fn_get_health_status
dev_langs: TSQL
helpviewer_keywords:
- smart_admin.fn_get_health_status
- fn_get_health_status
ms.assetid: b376711d-444a-4b5e-b483-8df323b4e31f
caps.latest.revision: "12"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 25675b2dc83e5251b381bf95af353deb647d563a
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="managedbackupfngethealthstatus-transact-sql"></a>managed_backup.fn_get_health_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Возвращает таблицу, состоящую из 0, одной или более строк объединенного числа ошибок, указанных расширенными событиями в течение заданного периода времени.  
  
 Эта функция используется для отчета о состоянии работоспособности служб в Smart Admin.  В настоящее время [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] поддерживается в Smart Admin. Поэтому возвращаемые ошибки связаны с [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```tsql  
managed_backup.fn_get_health_status([@begin_time = ] 'time_1' , [ @end_time = ] 'time_2')  
```  
  
##  <a name="Arguments"></a> Аргументы  
 [@begin_time]  
 Начало периода времени, для которого вычисляется общее количество ошибок.  @begin_time Тип параметра — DATETIME. Значение по умолчанию — NULL. Если значение равно NULL, функция будет обрабатывать все события, возникшие за 30 минут до текущего времени.  
  
 [ @end_time]  
 Конец периода времени, для которого вычисляется общее количество ошибок. @end_time Тип параметра — DATETIME со значением по умолчанию NULL. Если значение равно NULL, функция будет обрабатывать расширенные события до текущего времени.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|number_of_storage_connectivity_errors|int|Количество ошибок подключения, когда программа устанавливает соединение с учетной записью хранения Windows Azure.|  
|number_of_sql_errors|int|Число ошибок, возвращаемых при подключении программы к компоненту SQL Server Engine.|  
|number_of_invalid_credential_errors|int|Число ошибок, возвращаемых, когда программа пытается выполнить проверку подлинности с использованием учетных данных SQL.|  
|number_of_other_errors|int|Количество ошибок в других категориях, помимо обмена данными, SQL или учетных данных.|  
|number_of_corrupted_or_deleted_backups|int|Число удаленных или поврежденных файлов резервных копий.|  
|number_of_backup_loops|int|Число сканирований агентом резервного копирования всех баз данных, настроенных с помощью [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
|number_of_retention_loops|int|Количество сканирований баз данных, выполняемых для оценки заданного срока хранения.|  
  
## <a name="best-practices"></a>Рекомендации  
 Эти суммарные значения можно использовать для контроля состояния работоспособности системы. Например, если столбец number_of_retention_loops получает значение 0 за 30 минут, то, возможно, управление хранением работает слишком долго или неправильно. Ненулевые столбцы ошибок могут означать неполадки, и для обнаружения проблемы следует ознакомиться с журналами расширенных событий. Кроме того, используйте хранимую процедуру **managed_backup.sp_get_backup_diagnostics** для получения списка расширенных событий, чтобы найти сведения об ошибке.  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Требуется **ВЫБЕРИТЕ** разрешений на функцию.  
  
## <a name="examples"></a>Примеры  
  
-   В следующем примере возвращается объединенное число ошибок за последние 30 минут времени выполнения.  
  
    ```  
    SELECT *  
    FROM managed_backup.fn_get_health_status(NULL, NULL)  
  
    ```  
  
-   В следующем примере возвращается объединенное число ошибок за текущую неделю.  
  
    ```  
    Use msdb  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
    SELECT *  
    FROM managed_backup.fn_get_health_status(@startofweek, @endofweek)  
  
    ```  
  
  