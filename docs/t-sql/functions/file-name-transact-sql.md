---
title: "FILE_NAME (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILE_NAME_TSQL
- FILE_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- viewing file names
- file names [SQL Server], FILE_NAME
- IDs [SQL Server], files
- file IDs [SQL Server]
- names [SQL Server], files
- displaying file names
- identification numbers [SQL Server], files
- FILE_NAME function
- logical file names [SQL Server]
ms.assetid: 68b298aa-ce47-4af5-b59f-9a1b46d48326
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 35b7f2b516227e00af629cadb5c1dccadad2b092
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="filename-transact-sql"></a>FILE_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает логическое имя файла, соответствующее указанному идентификатору (ID) файла.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
FILE_NAME ( file_id )   
```  
  
## <a name="arguments"></a>Аргументы  
 *file_id*  
 Идентификатор файла, для которого необходимо вернуть имя файла. Аргумент *file_id* имеет тип **int**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Remarks  
 Аргумент *file_ID* соответствует столбцу file_id в представлениях каталога sys.master_files или sys.database_files.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере возвращаются имена файлов для `file_ID 1` и `file_ID` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```sql  
SELECT FILE_NAME(1) AS 'File Name 1', FILE_NAME(2) AS 'File Name 2';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
File Name 1           File Name 2  
----------------      ------------------------  
AdventureWorks2012_Data   AdventureWorks2012_Log  

(1 row(s) affected)
``` 
  
## <a name="see-also"></a>См. также:  
 [FILE_IDEX (Transact-SQL)](../../t-sql/functions/file-idex-transact-sql.md)   
 [Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
