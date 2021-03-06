---
title: "Транзакции | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-transactions
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: daa787c57cb8ba5b91f4bae3cff687bc50800338
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="transactions"></a>Transactions
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента реализует поддержку локальных транзакций. Потребитель может использовать распределенные или координируемые транзакции с помощью координатора распределенных транзакций (Майкрософт) (MS DTC). Для потребителей, которым требуется управление транзакциями, охватывающее несколько сеансов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента может соединять транзакции, инициированные и обслуживаемые координатором MS DTC.  
  
 По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента использует режим автоматического сохранения транзакций, где каждое отдельное действие в сеансе потребителя составляет полную транзакцию для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Локальный режим автоматической фиксации поставщика OLE DB для собственного клиента, и транзакции с автоматической фиксацией никогда не принадлежат более чем одного сеанса.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **ITransactionLocal** интерфейс, что позволяет потребителю использовать явно и неявно запускаемые транзакции в одном соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента не поддерживает вложенные локальные транзакции.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Поддержка локальных транзакций](../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)  
  
-   [Поддержка распределенных транзакций](../../relational-databases/native-client-ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Уровни изоляции &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
