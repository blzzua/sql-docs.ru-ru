---
title: "Установить максимальный размер файла для файла трассировки (приложение SQL Server Profiler) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum file size for traces
- size [SQL Server], trace files
ms.assetid: e86dc4ce-5aa3-4c0d-acb5-c9e8871ed963
caps.latest.revision: "24"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5f3825b505604bb3d80bc640983a00bf9c80ae87
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="set-a-maximum-file-size-for-a-trace-file-sql-server-profiler"></a>установить максимальный размер для файла трассировки (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Используйте следующую процедуру, чтобы задать максимальный размер файла для файла трассировки.  
  
### <a name="to-set-a-maximum-file-size-for-a-trace-file"></a>Указание максимального размера файла трассировки  
  
1.  В меню **Файл** выберите команду **Создать трассировку**и подключитесь к экземпляру Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Отображается диалоговое окно **Свойства трассировки**.  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки**не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис**выберите пункт **Параметры**и снимите флажок **Начать трассировку немедленно после установления соединения** .  
  
2.  В поле **Имя трассировки** введите имя трассировки.  
  
3.  В списке **Имя шаблона**выберите шаблон трассировки.  
  
4.  Выберите **Сохранить в файл**и укажите файл, в который будут сохранены данные о трассировке.  
  
5.  В поле **Установить максимальный размер файла** укажите максимальный размер файла трассировки. Когда файл достигает максимального размера, события трассировки перестают туда записываться. Если выбран параметр **Включить операцию переключения на файл продолжения** (выбран по умолчанию), то происходит следующее:  
  
     Если выбран параметр «операция переключения на файл продолжения», то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] закрывает текущий файл, как только он достигнет максимального размера, а затем создает новый файл. У каждого нового файла будет то же имя, что и у предыдущего, но к этому имени будет добавляться целое число, соответствующее порядковому номеру файла. Например, если первоначальный файл трассировки назывался filename_1.trc, то следующий будет filename_2.trc и т.д. Если новому файлу продолжения назначено имя, которое уже используется существующим файлом, то существующий файл будет перезаписан, при условии, что он не является доступным только для чтения. Параметр «операция переключения на файл продолжения» устанавливается автоматически при сохранении данных трассировки в файл.  
  
     Если параметр «операция переключения на файл продолжения» включен, то трассировка будет продолжаться до тех пор, пока не будет остановлена другими средствами. Чтобы трассировка останавливалась по достижении максимального размера файла, отключите параметр «операция переключения на файл продолжения».  
  
    > [!NOTE]  
    >  В файловой системе FAT32 максимально допустимый размер файла немногим меньше 4 гигабайт (ГБ). Если файл трассировки достигает такого размера, то трассировка завершается с ошибкой «Недостаточно места на диске». Чтобы можно было создавать файлы большего размера, используйте NTFS.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
