---
title: "sys.sp_flush_log (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- sp_flush_log_TSQL
- sys.sp_flush_log
- sys.sp_flush_log_TSQL
- sp_flush_log
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_flush_log
ms.assetid: 75cc9f52-3b1f-4754-b1e7-ce0dd3323bc9
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b4347cb94ab7e6e42418f7b0380250debbdcad03
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysspflushlog-transact-sql"></a>sys.sp_flush_log (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Выполняет фиксацию на диск журнала транзакций текущей базы данных, таким образом фиксируя все ранее выполненные отложенные долговечные транзакции.  
  
 Если для улучшения производительности используются отложенные долговечные транзакции, но также необходимо гарантированно ограничить объем данных, теряемый при сбое сервера или отработке отказа, то рекомендуется выполнять `sys.sp_flush_log` по регулярному расписанию. Например, если нужно обеспечить потерю не более х секунд данных, процедуру `sp_flush_log` следует выполнять каждые х секунд.  
  
 Выполнение хранимой процедуры `sys.sp_flush_log` гарантирует, что все ранее зафиксированные отложенные устойчивые транзакции будут сделаны долговечными. См. раздел общих понятий [управление устойчивостью транзакций](../../relational-databases/logs/control-transaction-durability.md) для получения дополнительной информации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
  
sys.sp_flush_log  
  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Код возврата 1 означает успешное завершение.  Все другие значения означают неуспешное завершение.  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="sample-code"></a>Образец кода  
  
```sql  
.  
EXECUTE sys.sp_flush_log  
  
```  
  
  
