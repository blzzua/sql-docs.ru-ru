---
title: "catalog.create_environment (база данных SSISDB) | Документы Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 66367092-9f6e-40e6-90bd-81efb078ab70
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87099d08212705034db52a030e2cb1012b23c1a8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="catalogcreateenvironment-ssisdb-database"></a>catalog.create_environment (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Создает среду в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.create_environment [@folder_name =] folder_name  
     , [@environment_name =] environment_name  
  [  , [@environment_description =] environment_description ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [@folder_name =] *folder_name*  
 Имя папки, которая будет содержать среду. Параметр *folder_name* имеет тип **nvarchar(128)**.  
  
 [@environment_name =] *environment_name*  
 Имя среды. Параметр *environment_name* имеет тип **nvarchar(128)**.  
  
 [@environment_description=] *environment_description*  
 Необязательное описание среды. Параметр *environment_description* имеет тип **nvarchar(1024)**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на папку  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   роль базы данных;  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Имя папки не обнаружено  
  
-   Среда с таким именем уже существует в указанной папке  
  
## <a name="remarks"></a>Remarks  
 Имя среды должно быть уникальным в пределах папки.  
  
  
