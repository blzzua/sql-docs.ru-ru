---
title: "Класс SQLServerStatement | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5ef6ef57bda9fe69685c042b564306655c67f516
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverstatement-class"></a>Класс SQLServerStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет базовую реализацию функциональности инструкции JDBC.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Реализует:** [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerStatement  
```  
  
## <a name="remarks"></a>Замечания  
 Класс SQLServerStatement также предоставляет набор реализаций методов базового класса для подготовленных и вызываемых инструкций JDBC. Основной класс SQLServerStatement является выполнение инструкций SQL и дальнейшей передачей количества обновлений и результирующих наборов в приложение пользователя.  
  
 Этот класс поддерживает развертывание в класс SQLServerStatement, интерфейс ISQLServerStatement и интерфейсе java.sql.Statement. Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
