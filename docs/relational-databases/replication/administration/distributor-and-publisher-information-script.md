---
title: "Скрипт вывода сведений о распространителе и издателе | Документация Майкрософт"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Publishers [SQL Server replication], information scripts
- Distributors [SQL Server replication], information scripts
ms.assetid: 8622db47-c223-48fa-87ff-0b4362cd069a
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: abc4df76c4d01e9a36fa66885dc91f8e0d2b35e1
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="distributor-and-publisher-information-script"></a>Скрипт вывода сведений о распространителе и издателе
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Этот скрипт использует системные таблицы и хранимые процедуры репликации, позволяющие получить ответы на часто задаваемые вопросы об объектах на распространителе и издателе. Скрипт может использоваться «как есть», а также может служить основой для пользовательских скриптов. Для выполнения в вашей среде, возможно, потребуется внести в скрипт два изменения:  
  
-   Изменить строку `use AdventureWorks2012` для использования имени вашей базы данных публикации.  
  
-   Удалить комментарии (`--`) из строки `exec sp_helparticle @publication='<PublicationName>'` и заменить \<PublicationName> именем публикации.  
  
```  
--********** Execute at the Distributor in the master database **********--  
  
USE master;  
go  
  
--Is the current server a Distributor?  
--Is the distribution database installed?  
--Are there other Publishers using this Distributor?  
EXEC sp_get_distributor  
  
--Is the current server a Distributor?  
SELECT is_distributor FROM sys.servers WHERE name='repl_distributor' AND data_source=@@servername;  
  
--Which databases on the Distributor are distribution databases?  
SELECT name FROM sys.databases WHERE is_distributor = 1  
  
--What are the Distributor and distribution database properties?  
EXEC sp_helpdistributor;  
EXEC sp_helpdistributiondb;  
EXEC sp_helpdistpublisher;  
  
--********** Execute at the Publisher in the master database **********--  
  
--Which databases are published for replication and what type of replication?  
EXEC sp_helpreplicationdboption;  
  
--Which databases are published using snapshot replication or transactional replication?  
SELECT name as tran_published_db FROM sys.databases WHERE is_published = 1;  
--Which databases are published using merge replication?  
SELECT name as merge_published_db FROM sys.databases WHERE is_merge_published = 1;  
  
--What are the properties for Subscribers that subscribe to publications at this Publisher?  
EXEC sp_helpsubscriberinfo;  
  
--********** Execute at the Publisher in the publication database **********--  
  
USE AdventureWorks2012;  
go  
  
--What are the snapshot and transactional publications in this database?   
EXEC sp_helppublication;  
--What are the articles in snapshot and transactional publications in this database?  
--REMOVE COMMENTS FROM NEXT LINE AND REPLACE <PublicationName> with the name of a publication  
--EXEC sp_helparticle @publication='<PublicationName>';  
  
--What are the merge publications in this database?   
EXEC sp_helpmergepublication;  
--What are the articles in merge publications in this database?  
EXEC sp_helpmergearticle; -- to return information on articles for a single publication, specify @publication='<PublicationName>'  
  
--Which objects in the database are published?  
SELECT name AS published_object, schema_id, is_published AS is_tran_published, is_merge_published, is_schema_published  
FROM sys.tables WHERE is_published = 1 or is_merge_published = 1 or is_schema_published = 1  
UNION  
SELECT name AS published_object, schema_id, 0, 0, is_schema_published  
FROM sys.procedures WHERE is_schema_published = 1  
UNION  
SELECT name AS published_object, schema_id, 0, 0, is_schema_published  
FROM sys.views WHERE is_schema_published = 1;  
  
--Which columns are published in snapshot or transactional publications in this database?  
SELECT object_name(object_id) AS tran_published_table, name AS published_column FROM sys.columns WHERE is_replicated = 1;  
  
--Which columns are published in merge publications in this database?  
SELECT object_name(object_id) AS merge_published_table, name AS published_column FROM sys.columns WHERE is_merge_published = 1;  
```  
  
## <a name="see-also"></a>См. также:  
 [Вопросы, часто задаваемые администраторам репликации](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)   
 [sp_get_distributor (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-get-distributor-transact-sql.md)   
 [sp_helparticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helpdistributiondb (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [sp_helpdistpublisher (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [sp_helpdistributor (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpmergearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [sp_helpmergepublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [sp_helppublication (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [sp_helpreplicationdboption (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helpreplicationdboption-transact-sql.md)   
 [sp_helpsubscriberinfo (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.procedures (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md)   
 [sys.servers (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-servers-transact-sql.md)   
 [sys.tables (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.views (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-views-transact-sql.md)  
  
  
