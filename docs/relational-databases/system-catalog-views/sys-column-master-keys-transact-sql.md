---
title: "sys.column_master_keys (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- column_master_key_definitions_TSQL
- column_master_key_definitions
- sys.column_master_key_definitions_TSQL
- sys.column_master_key_definitions
- column_master_keys_TSQL
- column_master_keys
- sys.column_master_keys_TSQL
- sys.column_master_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_key_definitions catalog view
- sys.column_master_keys catalog view
ms.assetid: fbec2efa-5fe9-4121-9b34-60497b0b2aca
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e22e052d88c339828e0a7e5d6f5803bc04b30925
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syscolumnmasterkeys-transact-sql"></a>sys.column_master_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого главного ключа базы данных, добавленные с помощью [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) инструкции. Каждая строка представляет одного главного ключа столбца (CMK).  
    
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя CMK.|  
|**column_master_key_id**|**int**|Идентификатор главного ключа столбца.|  
|**create_date**|**datetime**|Дата создания главного ключа столбца.|  
|**modify_date**|**datetime**|Дата последнего изменения главного ключа столбца.|  
|**key_store_provider_name**|**sysname**|Имя поставщика хранилища главного ключа столбца, которое содержит CMK. Допустимые значения:<br /><br /> MSSQL_CERTIFICATE_STORE — Если хранилища главных ключей столбцов в хранилище сертификатов.<br /><br /> Определяемые пользователем значение, если хранилище главного ключа столбца пользовательского типа.|  
|**key_path**|**nvarchar(4000)**|Путь конкретного хранилища главного ключа столбца ключа. Формат пути зависит от типа хранилища главного ключа столбца. Пример<br /><br /> `'CurrentUser/Personal/'<thumbprint>`<br /><br /> Для хранилища главного ключа настраиваемый столбец, разработчик отвечает за определение какой путь к разделу — пользовательские столбца хранилища главного ключа.|  
  
## <a name="permissions"></a>Permissions  
 Требуется **VIEW ANY COLUMN MASTER KEY** разрешение.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Постоянное шифрование (компонент Database Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
  
  
