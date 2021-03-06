---
title: "SET TEXTSIZE (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 04/12/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTSIZE_TSQL
- TEXTSIZE
- SET_TEXTSIZE_TSQL
- SET TEXTSIZE
dev_langs:
- TSQL
helpviewer_keywords:
- SET TEXTSIZE statement
- SELECT statement [SQL Server], text size returned
- size [SQL Server], text and image data
- TEXTSIZE option
- text size returned [SQL Server]
ms.assetid: 787154a6-39a6-4dd6-a6d0-67b4364f95d5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5ecffd26c600d3a224824aa9a64ce347cd2f9fbc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="set-textsize-transact-sql"></a>SET TEXTSIZE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Указывает размер данных типа **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **text**, **ntext** и **image**, возвращаемых инструкцией SELECT.  
  
> [!IMPORTANT]  
>  Типы данных **ntext**, **text** и **image** будут исключены в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Следует избегать использования этих типов данных при новой разработке и запланировать изменение приложений, использующих их в настоящий момент. Вместо них следует использовать типы данных **nvarchar(max)**, **varchar(max)**и **varbinary(max)** .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SET TEXTSIZE { number }   
```  
  
## <a name="arguments"></a>Аргументы  
 *number*  
 Размер данных типа **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **text**, **ntext** или **image** в байтах. *number* должно быть целым числом не более 2 147 483 647 (2 ГБ).  Значение –1 означает неограниченный размер. Значение 0 устанавливает размер в 4 КБ, принятый по умолчанию.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (10.0 и выше ) и драйвер ODBC для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически указывают `-1` (неограниченно) при подключении.  
  
 **Драйверы до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для Native Client и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для Native Client (версия 9) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически устанавливают для параметра TEXTSIZE значение 2147483647 при подключении.  
  
## <a name="remarks"></a>Remarks  
 Установка SET TEXTSIZE влияет на работу функции @@TEXTSIZE.  
  
 Значение TEXTSIZE устанавливается во время выполнения, а не во время синтаксического анализа.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public** .  
  
## <a name="see-also"></a>См. также:  
 [@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
