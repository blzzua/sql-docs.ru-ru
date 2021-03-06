---
title: "sys.sp_cdc_enable_db (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
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
- sp_cdc_enable_db_TSQL
- sp_cdc_enable_db
- sys.sp_cdc_enable_db
- sys.sp_cdc_enable_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_enable_db
- change data capture [SQL Server], enabling databases
- sp_cdc_enable_db
ms.assetid: 176d83b3-493d-43cd-800e-aa123c3bdf17
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b4dfd41cd9ae452fb3ce7924e215372de7768bb
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sysspcdcenabledb-transact-sql"></a>sys.sp_cdc_enable_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Включает систему отслеживания измененных данных для текущей базы данных. Эту процедуру необходимо выполнить в базе данных, чтобы для таблиц в этой базе можно было включить систему отслеживания измененных данных. Система отслеживания измененных данных регистрирует действия по вставке, обновлению и удалению, применяемые к таблицам, для которых включена система, предоставляя сведения об операциях изменения в легко обрабатываемом реляционном формате. Данные столбца, зеркально копирующего структуру столбцов отслеживаемой исходной таблицы, регистрируются для измененных строк вместе с метаданными, необходимыми для применения изменений к целевой среде.  
  
> [!IMPORTANT]  
>  Система отслеживания измененных данных доступна не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_enable_db  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Измененных данных не может быть включен для [системных баз данных](../../relational-databases/databases/system-databases.md) или базы данных распространителя.  
  
 Процедура sys.sp_cdc_enable_db создает объекты отслеживания измененных данных, действующие в области базы данных, включая таблицы метаданных и триггеры DDL. Он также создает схему cdc и пользователя базы данных cdc и устанавливает для записи базы данных в столбец is_cdc_enabled [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представление 1 каталога.  
  
## <a name="permissions"></a>Permissions  
 Требует членства в предопределенной роли сервера sysadmin.  
  
## <a name="examples"></a>Примеры  
 В следующем примере включается система отслеживания измененных данных.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_enable_db;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.sp_cdc_disable_db &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md)  
  
  
