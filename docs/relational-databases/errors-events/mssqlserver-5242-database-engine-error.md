---
title: "MSSQLSERVER_5242 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 5242 (Database Engine error)
ms.assetid: 712b1a10-2f87-41df-a111-1ed9f14102d4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 38444abe57894f79cac3eed5e7b67bb70ed947d8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver5242"></a>MSSQLSERVER_5242
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|5242|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|В ходе выполнения внутренней операции в базе данных «%.*ls» (идентификатор: %d) на странице %S_PGID была обнаружена несогласованность. Обратитесь в службу технической поддержки. Номер ссылки %ld.|  
  
## <a name="explanation"></a>Объяснение  
На странице базы данных возникла несогласованность, на которую указывает сообщение об ошибке.  
  
## <a name="see-also"></a>См. также:  
[DBCC CHECKDB (Transact-SQL)](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[Файлы и файловые группы базы данных](~/relational-databases/databases/database-files-and-filegroups.md)  
  
