---
title: "Команда (ADO - синтаксис WFC) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Command collection [ADO], ADO/WFC syntax
ms.assetid: 39d0aa06-03ac-4c9a-8400-83947756ef99
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 310b7c246fc5d7006cc2e358340d0aa062dc3ab3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="command-ado---wfc-syntax"></a>Команда (ADO - WFC синтаксис)
## <a name="package-commswfcdata"></a>пакет com.ms.wfc.data  
  
### <a name="constructor"></a>Конструктор  
  
```  
public Command()  
public Command(String commandtext)  
```  
  
### <a name="methods"></a>Методы  
  
```  
public void cancel()  
public com.ms.wfc.data.Parameter createParameter(String  
    Name, int Type, int Direction, int Size, Object Value)  
public Recordset execute()  
public Recordset execute(Object[] parameters)  
public Recordset execute(Object[] parameters, int options)  
public int executeUpdate(Object[] parameters)  
public int executeUpdate(Object[] parameters, int options)  
public int executeUpdate()  
```  
  
 **ExecuteUpdate** специальных вариантов метод, который вызывает базовый ADO **выполнение** метод определенных параметров. **ExecuteUpdate** метод не поддерживает возврат **записей** объекта, поэтому **выполнение** метода *параметры* параметр изменить с помощью **AdoEnums.ExecuteOptions.NORECORDS**. После **выполнение** метод завершения его обновленной *RecordsAffected* параметра передается обратно **executeUpdate** метод, который затем возвращается в виде **int**.  
  
### <a name="properties"></a>Свойства  
  
```  
public com.ms.wfc.data.Connection getActiveConnection()  
public void setActiveConnection(com.ms.wfc.data.Connection con)  
public void setActiveConnection(String conString)  
public String getCommandText()  
public void setCommandText(String command)  
public int getCommandTimeout()  
public void setCommandTimeout(int timeout)  
public int getCommandType()  
public void setCommandType(int type)  
public String getName()  
public void setName(String name)  
public boolean getPrepared()  
public void setPrepared(boolean prepared)  
public int getState()  
public com.ms.wfc.data.Parameter getParameter(int n)  
public com.ms.wfc.data.Parameter getParameter(String n)  
public com.ms.wfc.data.Parameters getParameters()  
public AdoProperties getProperties()  
```  
  
## <a name="see-also"></a>См. также  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
