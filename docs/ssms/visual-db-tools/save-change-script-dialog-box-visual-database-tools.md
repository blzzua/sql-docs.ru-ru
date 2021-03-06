---
title: "Диалоговое окно \"Сохранить скрипт изменений\" (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 33081b924b39c921304ed2de2648cea202d0c96a
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a>Диалоговое окно "Сохранить скрипт изменений" (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Это диалоговое окно показывает скрипт [!INCLUDE[tsql](../../includes/tsql_md.md)] изменений, сделанных со времени последнего сохранения таблицы. Оно также позволяет сохранить скрипт в текстовом файле в выбранном местоположении.  
  
Открыть это диалоговое окно также можно после совершения несохраненных изменений таблицы в конструкторе таблиц. В меню **Конструктор таблиц** выберите пункт **Создать скрипт изменения**.  
  
> [!NOTE]  
> Скрипты изменений, содержащиеся в визуальных инструментах для баз данных, не содержат средств обработки ошибок. Они предполагают, что объекты базы данных не изменились с момента открытия инструментального средства; поэтому возникновение проблем, связанных с изменением объектов, невозможно. Перед выполнением скрипта изменений следует включить соответствующие инструкции обработки ошибок.  
  
## <a name="options"></a>Параметры  
**Автоматически создавать скрипт изменений при каждом сохранении**  
Если флажок установлен, то диалоговое окно **Сохранить скрипт изменений** будет выводиться каждый раз при сохранении изменений таблицы.  
  
**Да**  
Разверните диалоговое окно **Сохранить** , где можно выбрать местоположение текстового файла.  
  
**Нет**  
Отменить создание скрипта изменения.  
  
