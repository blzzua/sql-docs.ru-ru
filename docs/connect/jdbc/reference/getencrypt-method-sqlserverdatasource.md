---
title: "Метод getEncrypt (SQLServerDataSource) | Документы Microsoft"
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
apiname: getEncrypt Method (SQLServerDataSource)
apilocation: getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cb76a00e1fdf8b2999675bc1949e8cc06ff25d9b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getencrypt-method-sqlserverdatasource"></a>Метод getEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает **логическое** значение, указывающее, включено ли свойство encrypt.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если шифрование включено. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойству encrypt присвоено **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] гарантирует, что [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] использует шифрование SSL для всех данных, передаваемых между клиентом и сервером, если сервер имеет установленный сертификат.  
  
 Если свойство шифрования не задано или равно **false**, драйвер не будет применять [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] поддержку SSL-шифрования. Если [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] экземпляр не настроен на принудительное шифрование протокола SSL, то соединение устанавливается без применения шифрования. Если [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] экземпляре настроено принудительное SSL-шифрования, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет автоматически включить SSL-шифрование при запуске на правильно настроенной виртуальной машины Java (JVM), иначе соединение будет разорвано и в работе драйвера будет вызвана Произошла ошибка. Если свойство шифрования не задано, [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md) метод возвращает значение по умолчанию **false**.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
