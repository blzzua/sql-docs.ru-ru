---
title: "Уровень изоляции транзакций курсора | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 88831b0ef8d0ecf1ecb5a0a8fee3d2918af2c2c8
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="cursor-transaction-isolation-level"></a>Уровень изоляции транзакций курсора
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Режим полной блокировки курсоров основывается на взаимодействии между атрибутами параллелизма и уровнем изоляции транзакций, установленным клиентом. Клиенты ODBC устанавливают транзакции уровень изоляции с использованием [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) атрибутов SQL_ATTR_TXN_ISOLATION или SQL_COPT_SS_TXN_ISOLATION. Режим блокировки специфической среды курсора определяется комбинацией режимов блокировки параллелизма и параметров уровня изоляции транзакции.  
  
 Поддерживаются следующие уровни изоляции транзакций курсора [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента:  
  
-   Зафиксированная операция чтения (SQL_TXN_READ_COMMITTED)  
  
-   Незафиксированная операция чтения (SQL_TXN_READ_COMMITTED)  
  
-   Операция чтения с возможностью повторения (SQL_TXN_REPEATABLE_READ)  
  
-   Сериализуемый (SQL_TXN_SERIALIZABLE)  
  
-   Моментальный снимок (SQL_TXN_SS_SNAPSHOT)  
  
 Обратите внимание, что ODBC API определяет дополнительные уровни изоляции транзакций, но они не поддерживаются в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента.  
  
## <a name="see-also"></a>См. также  
 [Свойства курсора](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
