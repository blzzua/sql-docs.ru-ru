---
title: "Массовый импорт данных больших объектов с помощью поставщика больших наборов строк OPENROWSET | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: import-export
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SINGLE_NCLOB option
- bulk rowset providers [SQL Server]
- bulk importing [SQL Server], data formats
- OPENROWSET function, bulk importing large data
- SINGLE_CLOB option
- data formats [SQL Server], large-object data
- large data, bulk imports
- SINGLE_BLOB option
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5cb73567a88cbdc4402a178fe7ec28f79cccca95
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="bulk-import-large-object-data-with-openrowset-bulk-rowset-provider"></a>Массовый импорт данных больших объектов с помощью поставщика больших наборов строк OPENROWSET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Поставщик больших наборов строк OPENROWSET в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет выполнять массовый импорт файла данных как большого объекта данных.  
  
 Поставщик больших наборов строк OPENROWSET поддерживает следующие типы больших объектов данных: **varbinary**(max) или **image**, **varchar**(max) или **text**и **nvarchar**(max) или **ntext**.  
  
> [!NOTE]  
>  Типы данных **image**, **text** и **ntext** считаются устаревшими.  
  
 В предложении OPENROWSET BULK поддерживаются три параметра для импорта содержимого файла данных в виде однострочного набора строк с одним столбцом. Вместо файла форматирования можно указать один из данных параметров для больших объектов. Это следующие параметры:  
  
 SINGLE_BLOB  
 Считывает содержимое файла *data_file* в одну строку и возвращает его в виде набора строк, состоящего из одного столбца типа **varbinary(max)**.  
  
 SINGLE_CLOB  
 Считывает содержимое указанного файла данных в виде символов и возвращает его в виде набора строк, состоящего из одной строки и одного столбца типа **varchar(max)**, с параметрами сортировки текущей базы данных; это может быть, например, текстовый документ или документ [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word.  
  
 SINGLE_NCLOB  
 Считывает содержимое указанного файла данных в кодировке Юникод и возвращает содержимое в виде набора строк, состоящего из одной строки и одного столбца типа **varchar(max)**, с параметрами сортировки текущей базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Массовый импорт данных при помощи инструкции BULK INSERT или OPENROWSET(BULK...) (SQL Server)](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)   
 [Программа bcp](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)  
  
  
