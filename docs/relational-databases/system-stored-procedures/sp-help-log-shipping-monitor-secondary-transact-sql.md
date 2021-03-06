---
title: "sp_help_log_shipping_monitor_secondary (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_monitor_secondary
- sp_help_log_shipping_monitor_secondary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor_secondary
ms.assetid: 3ac091ea-c9a8-4c05-a0b6-1ccf4e001339
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 80c3f736037a763b1cda3ee37c92b443ecd07e87
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sphelplogshippingmonitorsecondary-transact-sql"></a>sp_help_log_shipping_monitor_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает из таблиц мониторинга информацию о базе данных-получателе.  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_log_shipping_monitor_secondary  
[ @secondary_server = ] 'secondary_server',  
[ @secondary_database = ] 'secondary_database'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@secondary_server =** ] '*secondary_server*'  
 Имя сервера-получателя. *сервер_получатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@secondary_database =** ] "*secondary_database*"  
 Имя базы данных-получателя. *secondary_database* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Столбец|Описание|  
|------------|-----------------|  
|**secondary_server**|Имя экземпляра-получателя [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журналов.|  
|**secondary_database**|Имя базы данных-получателя в конфигурации доставки журналов.|  
|**secondary_id**|Идентификатор сервера-получателя в конфигурации доставки журналов.|  
|**primary_server**|Имя первичного экземпляра компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журнала.|  
|**primary_database**|Имя базы данных-источника в конфигурации доставки журналов.|  
|**restore_threshold**|Время (в минутах), которое может пройти между операциями восстановления, прежде чем сформируется предупреждение.|  
|**threshold_alert**|Предупреждение, создаваемое при истечении порогового срока восстановления.|  
|**threshold_alert_enabled**|Этот аргумент определяет, активированы ли предупреждения об истечении порогового срока восстановления.<br /><br /> 1 = включено.<br /><br /> 0 = отключено.|  
|**last_copied_file**|Имя последнего файла резервной копии, скопированного на сервер-получатель.|  
|**last_copied_date**|Дата и время последней операции копирования на сервер-получатель.|  
|**last_copied_date_utc**|Дата и время последней операции копирования на сервер-получатель по времени в формате UTC.|  
|**last_restored_file**|Имя файла последней резервной копии, восстановленной в базу данных-получатель.|  
|**last_restored_date**|Дата и время последней операции восстановления в базе данных-получателе.|  
|**last_restored_date_utc**|Дата и время последней операции восстановления в базу данных-получатель по времени в формате UTC.|  
|**history_retention_period**|Время (в минутах) хранения истории доставки журналов для конкретной базы данных-получателя; по истечении этого времени записи удаляются.|  
  
## <a name="remarks"></a>Remarks  
 **sp_help_log_shipping_monitor_secondary** должна запускаться из **master** базы данных на сервере мониторинга.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру.  
  
## <a name="see-also"></a>См. также:  
 [О доставке журналов &#40; SQL Server &#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
