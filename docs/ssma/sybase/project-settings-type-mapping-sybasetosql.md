---
title: Параметры (сопоставление типов) проекта (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2698fb3a-f9e6-4e04-94e0-dad289d7ed0a
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 411cb12d17399e43ebdc454f5f55a5c5595972a2
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="project-settings-type-mapping-sybasetosql"></a>Параметры (сопоставление типов) проекта (SybaseToSQL)
На странице сопоставление типов **параметры проекта** диалоговое окно содержит настройки, установленные как SSMA преобразует типы данных Sybase адаптивной Server Enterprise (ASE) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типов данных.  
  
Сопоставление типов можно найти в **параметры проекта** и **параметры проекта по умолчанию** диалоговым окнам.  
  
-   Чтобы указать параметры сопоставления типов для всех будущих проектов SSMA на **средства** последовательно выберите пункты **параметры проекта по умолчанию**, выберите тип проекта миграции, для которого требуются параметры для просмотра и изменения из **миграции целевой версии** раскрывающийся список и выберите **сопоставление типов** в нижней части левой панели.  
  
-   Для задания параметров для текущего проекта на **средства** выберите пункт **параметры проекта**, а затем выберите **сопоставление типов** в нижней части левой панели.  
  
## <a name="options"></a>Параметры  
**Исходный тип**  
Сопоставленный тип данных ASE.  
  
**Тип целевого объекта**  
Целевой объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] тип данных для указанного типа данных ASE.  
  
См. в таблице в следующем разделе для SSMA по умолчанию для сопоставления типа Sybase.  
  
**Добавить**  
Щелкните, чтобы добавить в список сопоставления типа данных.  
  
**Правка**  
Щелкните для изменения выбранного типа данных в списке сопоставления.  
  
**Удалить**  
Щелкните, чтобы удалить сопоставление типов данных, выбранного из списка сопоставления.  
  
**По умолчанию**  
Щелкните, чтобы сбросить список сопоставления типа по умолчанию SSMA.  
  
## <a name="default-type-mapping"></a>Сопоставление типов по умолчанию  
Следующая таблица содержит сопоставление типов по умолчанию ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типов данных.  
  
|Тип данных ASE|Тип данных SQL Server|  
|-----------------|------------------------|  
|**bigint**|**bigint**|  
|**binary**|**binary**|  
|**двоичные [\*... 8000]**|**двоичные [\*]**|  
|**двоичные [8001..\*]**|**varbinary(max)**|  
|**бит**|**бит**|  
|**char**|**char**|  
|**char varying**|**varchar**|  
|**переменной типа char [\*... 8000]**|**varchar[\*]**|  
|**переменной типа char [8001..\*]**|**varchar(max)**|  
|**char [\*... 8000]**|**char[\*]**|  
|**char[8001..\*;]**|**varchar(max)**|  
|**character**|**char**|  
|**Изменение символа**|**varchar**|  
|**символ varying [\*... 8000]**|**varchar[\*]**|  
|**символ varying [8001..\*]**|**varchar(max)**|  
|**символ [\*... 8000]**|**char[\*]**|  
|**character[8001..\*]**|**varchar(max)**|  
|**date**|**date**|  
|**datetime**|**datetime2[3]**|  
|**dec**|**decimal**|  
|**dec[\*..\*]**|**decimal[\*]**|  
|**dec[\*..\*][\*..\*]**|**decimal[\*][\*]**|  
|**decimal**|**decimal**|  
|**decimal[\*..\*]**|**decimal[\*]**|  
|**decimal[\*..\*][\*..\*]**|**decimal[\*][\*]**|  
|**число двойной точности**|**float[53]**|  
|**float**|**float[53]**|  
|**число с плавающей запятой [\*... 15]**|**float[24]**|  
|**число с плавающей запятой [16..\*]**|**float[53]**|  
|**image**|**image**|  
|**int**|**int**|  
|**integer**|**int**|  
|**longsysname**|**nvarchar[255]**|  
|**money**|**money**|  
|**Национальный char**|**nchar**|  
|**Национальный char [\*... 4000]**|**nchar[\*]**|  
|**Национальный char переменной**|**nvarchar**|  
|**Национальный char переменной [\*... 4000]**|**nvarchar [\*]**|  
|**Национальный char переменной [4001..\*]**|**nvarchar(max)**|  
|**Национальный char [4001..\*]**|**nvarchar(max)**|  
|**символов национального алфавита**|**nchar**|  
|**национальных символов [\*... 4000]**|**nchar[\*]**|  
|**национальных символов [4001..\*]**|**nvarchar(max)**|  
|**изменение символов национального алфавита**|**nvarchar**|  
|**изменение символов национального алфавита [\*... 4000]**|**nvarchar [\*]**|  
|**изменение символов национального алфавита [4001..\*]**|**nvarchar(max)**|  
|**Национальный varchar**|**nvarchar**|  
|**Национальный varchar [\*... 4000]**|**nvarchar [\*]**|  
|**Национальный varchar [4001..\*]**|**nvarchar(max)**|  
|**nchar**|**nchar**|  
|**nchar переменной**|**nvarchar**|  
|**nchar varying [\*... 4000]**|**nvarchar [\*]**|  
|**nchar varying [4001..\*]**|**nvarchar(max)**|  
|**nchar [\*... 4000]**|**nchar[\*]**|  
|**nchar[4001..\*]**|**nvarchar(max)**|  
|**numeric**|**numeric**|  
|**numeric[\*..\*]**|**numeric[\*]**|  
|**numeric[\*..\*][\*..\*]**|**numeric[\*][\*]**|  
|**nvarchar**|**nvarchar**|  
|**nvarchar [\*... 4000]**|**nvarchar [\*]**|  
|**nvarchar[4001..\*]**|**nvarchar(max)**|  
|**real**|**float[24]**|  
|**smalldatetime**|**smalldatetime**|  
|**smallint**|**smallint**|  
|**smallmoney**|**smallmoney**|  
|**sysname**|**nvarchar[128]**|  
|**sysname[\*..\*]**|**nvarchar[255]**|  
|**text**|**text**|  
|**time**|**time[3]**|  
|**timestamp**|**rowversion**|  
|**tinyint**|**tinyint**|  
|**unichar**|**nchar**|  
|**unichar переменной**|**nvarchar**|  
|**различные unichar [\*... 4000]**|**nvarchar [\*]**|  
|**unichar переменной [4001..\*]**|**nvarchar(max)**|  
|**unichar [\*... 4000]**|**nchar[\*]**|  
|**unichar[4001..\*]**|**nvarchar(max)**|  
|**unitext**|**nvarchar(max)**|  
|**univarchar**|**nvarchar**|  
|**univarchar[\*..4000]**|**nvarchar [\*]**|  
|**univarchar[4001..\*]**|**nvarchar(max)**|  
|**без знака bigint**|**numeric[20][0]**|  
|**Целочисленное число без знака**|**bigint**|  
|**smallint без знака**|**int**|  
|**тип tinyint и без знака**|**tinyint**|  
|**varbinary**|**varbinary**|  
|**varbinary [\*... 8000]**|**varbinary [\*]**|  
|**varbinary [8001..\*]**|**varbinary(max)**|  
|**varchar**|**varchar**|  
|**varchar [\*... 8000]**|**varchar[\*]**|  
|**varchar[8001..\*]**|**varchar(max)**|  
  
