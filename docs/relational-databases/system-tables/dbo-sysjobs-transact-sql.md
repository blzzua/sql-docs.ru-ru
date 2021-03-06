---
title: "dbo.sysjobs (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysjobs
- sysjobs_TSQL
- dbo.sysjobs
- dbo.sysjobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobs system table
ms.assetid: e244a6a5-54c2-47a6-8039-dd1852b0ae59
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 37562aba8f3582eb58ece88dcad8ca72e080db18
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="dbosysjobs-transact-sql"></a>dbo.sysjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Хранит сведения для каждого задания, назначенного к выполнению агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Уникальный идентификатор задания.|  
|**originating_server_id**|**int**|Идентификатор сервера, от которого поступило задание.|  
|**name**|**sysname**|Имя задания.|  
|**включен**|**tinyint**|Показывает, разрешено ли задание к выполнению.|  
|**Описание**|**nvarchar(512)**|Описание задания.|  
|**start_step_id**|**int**|Идентификатор шага задания, с которого должно начаться выполнение.|  
|**category_id**|**int**|Идентификатор категории задания.|  
|**owner_sid**|**varbinary(85)**|Номер идентификатора защиты (SID) владельца задания.|  
|**notify_level_eventlog**|**int**|**Битовая маска** , указывающее, при каких обстоятельствах событие уведомления должно записываться в журнал приложений Microsoft Windows:<br /><br /> **0** = никогда<br /><br /> **1** = при успешном завершении задания<br /><br /> **2** = при ошибке задания<br /><br /> **3** = каждый раз по завершении задания (вне зависимости от результата выполнения)|  
|**notify_level_email**|**int**|Битовая маска, указывающая, при каких обстоятельствах должно быть отправлено электронное письмо с уведомлением при завершении задания.<br /><br /> **0** = никогда<br /><br /> **1** = при успешном завершении задания<br /><br /> **2** = при ошибке задания<br /><br /> **3** = каждый раз по завершении задания (вне зависимости от результата выполнения)|  
|**notify_level_netsend**|**int**|Битовая маска, указывающая, при каких обстоятельствах должно быть отправлено сетевое сообщение при завершении задания.<br /><br /> **0** = никогда<br /><br /> **1** = при успешном завершении задания<br /><br /> **2** = при ошибке задания<br /><br /> **3** = каждый раз по завершении задания (вне зависимости от результата выполнения)|  
|**notify_level_page**|**int**|Битовая маска, указывающая, при каких обстоятельствах должна быть отправлена страница при завершении задания.<br /><br /> **0** = никогда<br /><br /> **1** = при успешном завершении задания<br /><br /> **2** = при ошибке задания<br /><br /> **3** = каждый раз по завершении задания (вне зависимости от результата выполнения)|  
|**notify_email_operator_id**|**int**|Имя адреса электронной почты уведомляемого оператора.|  
|**notify_netsend_operator_id**|**int**|Идентификатор компьютера или пользователя, используемый при отправке сетевых сообщений.|  
|**notify_page_operator_id**|**int**|Идентификатор компьютера или пользователя, используемый при отправке страницы.|  
|**delete_level**|**int**|**Битовая маска** , указывающее, при каких обстоятельствах задание должно удаляться при завершении выполнения задания:<br /><br /> **0** = никогда<br /><br /> **1** = при успешном завершении задания<br /><br /> **2** = при ошибке задания<br /><br /> **3** = каждый раз по завершении задания (вне зависимости от результата выполнения)|  
|**date_created**|**datetime**|Дата создания задания.|  
|**date_modified**|**datetime**|Дата последнего изменения задания.|  
|**version_number**|**int**|Версия задания.|  
  
  
