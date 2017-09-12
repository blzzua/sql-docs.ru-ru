---
title: "DBCC PROCCACHE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC PROCCACHE
- DBCC_PROCCACHE_TSQL
- PROCCACHE_TSQL
- PROCCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- procedure cache [SQL Server]
- displaying procedure cache information
- DBCC PROCCACHE statement
ms.assetid: 7a4f9f8a-13ff-4bf2-ba29-c17012a23659
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 97e617e7867c90bf1e66c5e64e37b9039087d463
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-proccache-transact-sql"></a>DBCC PROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Отображает сведения о кэше процедур в табличном формате.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC PROCCACHE [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
 на  
 Позволяет указывать параметры.  
  
 NO_INFOMSGS  
 Подавляет все информационные сообщения с уровнями серьезности от 0 до 10.  
  
## <a name="remarks"></a>Замечания  
Кэш процедур используется для кэширования скомпилированных и исполняемых планов для ускорения выполнения пакетов. Элементы кэша процедур находятся на уровне пакета. Кэш процедур включает следующие записи:
-   Скомпилированные планы  
-   Планы выполнения  
-   Дерево алгебризатора  
-   Расширенные процедуры  
  
## <a name="result-sets"></a>Результирующие наборы  
В следующей таблице описаны столбцы в результирующем наборе.
  
|Имя столбца|Description|  
|-----------------|-----------------|  
|**Процедура получения NUM**|Общее количество страниц, используемое всеми записями кэша процедур.|  
|**NUM proc получения используется**|Общее число страниц, занятых всеми используемыми в данный момент записями.|  
|**NUM proc получения active**|Только для обратной совместимости. Общее число страниц, занятых всеми используемыми в данный момент записями.|  
|**размер кэша proc**|Общее число элементов в кэше процедур.|  
|**использовать кэш процесса**|Общее число элементов, используемых в настоящий момент.|  
|**Сброс кэша процедур active**|Только для обратной совместимости. Общее число элементов, используемых в настоящий момент.|  
  
## <a name="permissions"></a>Permissions  
Необходимо быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** .
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
