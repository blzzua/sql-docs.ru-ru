---
title: "Метод setSendStringParametersAsUnicode (SQLServerDataSource) | Документы Microsoft"
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
apiname: SQLServerDataSource.setSendStringParametersAsUnicode
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 49198d63-76cb-4843-8d04-e49b1fbb6916
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3d987c3c3665fc20ce6439ae796e2d5d279622db
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="setsendstringparametersasunicode-method-sqlserverdatasource"></a>Метод setSendStringParametersAsUnicode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Наборы **логическое** значение, указывающее, включена ли отправка параметров на сервер в Юникоде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setSendStringParametersAsUnicode(boolean sendStringParametersAsUnicode)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sendStringParametersAsUnicode*  
  
 **значение true,** Если строковые параметры отправляются на сервер в Юникоде. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойство sendStringParametersAsUnicode имеет значение **true**, который является значением по умолчанию, строковые параметры отправляются на сервер в Юникоде. Если для свойства sendStringParametersAsUnicode задано значение **false** строковые параметры отправляются на сервер в формате ASCII/MBCS, а не в ЮНИКОДЕ. Если sendStringParametersAsUnicode не задано, [getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md) возвращает значение по умолчанию **true**.  
  
 Дополнительные сведения о свойстве соединения sendStringParametersAsUnicode см. в разделе [задание свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
