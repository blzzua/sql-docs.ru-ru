---
title: "sys.http_endpoints (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.http_endpoints
- http_endpoints
- sys.http_endpoints_TSQL
- http_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.http_endpoints catalog view
ms.assetid: 16f59695-ecd9-457e-8874-055af63f8ea7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: af5140f2389501a10a9228c2e133441f072c2efc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syshttpendpoints-transact-sql"></a>sys.http_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит строку для всех конечных точек, созданных на сервере, который работает по протоколу HTTP.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**< унаследованные столбцы >**||Наследует столбцы из [sys.endpoints &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**сайт**|**nvarchar(128)**|Имя сервера для веб-сайта, заданное в параметре SITE.|  
|**url_path**|**nvarchar(4000)**|Часть URL-адреса, содержащая только путь к данной конечной точке HTTP, как указано в параметре PATH. |  
|**is_clear_port_enabled**|**bit**|1 = очистка порта разрешена с помощью параметра PORT = CLEAR.|  
|**CLEAR_PORT**|**int**|Номер порта, указанный в параметре CLEAR PORT.<br /><br /> NULL = номер не указан.|  
|**is_ssl_port_enabled**|**bit**|1 = порт SSL разрешен с помощью параметра PORT = SSL.|  
|**SSL_PORT**|**int**|Номер порта, указанный в параметре SSL PORT.<br /><br /> NULL = номер не указан.|  
|**is_anonymous_enabled**|**bit**|1 = анонимный доступ разрешен с помощью параметра AUTHENTICATION = ANONYMOUS.|  
|**is_basic_auth_enabled**|**bit**|1 = обычная проверка подлинности включена с помощью параметра AUTHENTICATION = BASIC.|  
|**is_digest_auth_enabled**|**bit**|1 = дайджест-проверка подлинности включена с помощью параметра AUTHENTICATION = DIGEST.|  
|**is_kerberos_auth_enabled**|**bit**|1 = встроенная проверка подлинности включена с помощью параметра AUTHENTICATION = KERBEROS.|  
|**is_ntlm_auth_enabled**|**bit**|1 = встроенная проверка подлинности включена с помощью параметра AUTHENTICATION = NTLM.|  
|**is_integrated_auth_enabled**|**bit**|1 = встроенная проверка подлинности включена с помощью параметра AUTHENTICATION = INTEGRATED.|  
|**authorization_realm**|**nvarchar(128)**|Указание, которое возвращается клиенту как часть оклика при дайджест-проверке подлинности. Значение параметра AUTH REALM.<br /><br /> NULL, если значение не указано или если дайджест-проверка подлинности не включена.|  
|**default_logon_domain**|**nvarchar(128)**|Домен имени входа по умолчанию, если включена обычная проверка подлинности. Значение параметр DEFAULT LOGON DOMAIN.<br /><br /> NULL, если значение не указано или если обычная проверка подлинности не включена.|  
|**is_compression_enabled**|**bit**|1 = COMPRESSION = ENABLED параметр задан.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога конечных точек &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
