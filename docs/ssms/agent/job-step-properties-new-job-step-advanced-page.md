---
title: Свойства шага задания — создание шага задания (страница "Дополнительно") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ag.job.stepadvanced.f1
ms.assetid: bdecfd4f-bcd8-4ba2-8ada-fbb636314f40
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d5be411757ec857af16582fd561c968d67af1bb6
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="job-step-properties---new-job-step-advanced-page"></a>Свойства шага задания — создание шага задания (страница "Дополнительно")
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Используйте эту страницу для просмотра и изменения свойств шага задания агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="options"></a>Параметры  
**Действие при успехе**  
Устанавливается действие, выполняемое агентом сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] при успешном завершении шага задания.  
  
**Повторные попытки**  
Устанавливается количество повторных попыток агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] выполнить неудачно завершившийся шаг задания.  
  
**Интервал повтора (в минутах)**  
Устанавливается интервал времени ожидания агентом сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] между последовательными повторными попытками.  
  
**Действие при ошибке**  
Устанавливается действие, выполняемое агентом сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] при неудачном завершении шага задания.  
  
## <a name="options-for-transact-sql-job-steps"></a>Параметры для шагов задания языка Transact-SQL  
**Выходной файл**  
Устанавливается файл, используемый для вывода из шага задания. Этот параметр доступен только членам предопределенной роли сервера **sysadmin** .  
  
**...**  
Перейдите к файлу, используемому для вывода из шага задания.  
  
**Вид**  
В сервере [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)]эта кнопка отключена, и просмотр выходных файлов невозможен. Вместо этого для просмотра выходных файлов шага задания используйте приложение «Блокнот».  
  
**Дописать выходные данные в существующий файл**  
Выходные данные добавляются к существующему содержимому таблицы. В противном случае содержимое файла переписывается каждый раз при выполнении шага задания.  
  
**Сохранять данные журнала в таблице**  
Записывает выходные данные шага задания в таблицу **sysjobstepslogs** базы данных **msdb** .  
  
**Вид**  
После того как шаг задания выполнится хотя бы раз, нажмите кнопку **Просмотр** для просмотра его выходных данных в таблице.  
  
**Дописать выходные данные в существующую запись в таблице**  
Выходные данные добавляются к существующему содержимому таблицы. В противном случае содержимое таблицы переписывается каждый раз при выполнении шага задания.  
  
**Включить в журнал выходные данные шага**  
Выберите этот параметр для включения вывода из шага задания в журнал заданий.  
  
**Выполнять от имени**  
Если пользователь является членом предопределенной роли сервера **sysadmin** , он может выбрать другое имя входа SQL для выполнения этого шага задания.  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a>Параметры для шагов задания операционной системы (CmdExec)  
**Выходной файл**  
Устанавливается файл, используемый для вывода из шага задания.  
  
**...**  
Перейдите к файлу, используемому для вывода из шага задания.  
  
**Вид**  
В сервере [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)]эта кнопка отключена, и просмотр выходных файлов невозможен. Вместо этого для просмотра выходных файлов шага задания используйте приложение «Блокнот».  
  
**Дописать выходные данные в существующий файл**  
При каждом выполнении шага задания его вывод добавляется к имеющемуся содержимому файла.  
  
**Сохранять данные журнала в таблице**  
Записывает выходные данные шага задания в таблицу **sysjobstepslogs** базы данных **msdb** .  
  
**Вид**  
После того как шаг задания выполнится хотя бы раз, нажмите кнопку **Просмотр** для просмотра его выходных данных в таблице.  
  
**Дописать выходные данные в существующую запись в таблице**  
Выходные данные добавляются к существующему содержимому таблицы. В противном случае содержимое таблицы переписывается каждый раз при выполнении шага задания.  
  
**Включить в журнал выходные данные шага**  
Выберите этот параметр для включения вывода из шага задания в журнал заданий.  
  
## <a name="options-for-powershell-job-steps"></a>Параметры для шагов задания языка PowerShell  
**Выходной файл**  
Устанавливается файл, используемый для вывода из шага задания.  
  
**...**  
Перейдите к файлу, используемому для вывода из шага задания.  
  
**Вид**  
В сервере [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)]эта кнопка отключена, и просмотр выходных файлов невозможен. Вместо этого для просмотра выходных файлов шага задания используйте приложение «Блокнот».  
  
**Дописать выходные данные в существующий файл**  
При каждом выполнении шага задания его вывод добавляется к имеющемуся содержимому файла.  
  
**Сохранять данные журнала в таблице**  
Записывает выходные данные шага задания в таблицу **sysjobstepslogs** базы данных **msdb** .  
  
**Вид**  
После того как шаг задания выполнится хотя бы раз, нажмите кнопку **Просмотр** для просмотра его выходных данных в таблице.  
  
**Дописать выходные данные в существующую запись в таблице**  
Выходные данные добавляются к существующему содержимому таблицы. В противном случае содержимое таблицы переписывается каждый раз при выполнении шага задания.  
  
**Включить в журнал выходные данные шага**  
Выберите этот параметр для включения вывода из шага задания в журнал заданий.  
  
## <a name="options-for-replication-queue-reader-job-steps"></a>Параметры шагов заданий для агента чтения очереди репликации  
**Server**  
Устанавливает сервер, чтобы выполнить шаг задания для считывания очереди репликации.  
  
**База данных**  
Устанавливает базу данных, чтобы выполнить шаг задания для считывания очереди репликации.  
  
## <a name="options-for-sql-server-analysis-services-job-steps"></a>Параметры для шагов задания служб SQL Server Analysis Services  
**Выходной файл**  
Устанавливается файл, используемый для вывода из шага задания. Этот параметр доступен только членам предопределенной роли сервера **sysadmin** .  
  
**...**  
Перейдите к файлу, используемому для вывода из шага задания.  
  
**Вид**  
В сервере [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)]эта кнопка отключена, и просмотр выходных файлов невозможен. Вместо этого для просмотра выходных файлов шага задания используйте приложение «Блокнот».  
  
**Дописать выходные данные в существующий файл**  
Выходные данные добавляются к существующему содержимому таблицы. В противном случае содержимое файла переписывается каждый раз при выполнении шага задания.  
  
**Сохранять данные журнала в таблице**  
Записывает выходные данные шага задания в таблицу **sysjobstepslogs** базы данных **msdb** .  
  
**Вид**  
После того как шаг задания выполнится хотя бы раз, нажмите кнопку **Просмотр** для просмотра его выходных данных в таблице.  
  
**Дописать выходные данные в существующую запись в таблице**  
Выходные данные добавляются к существующему содержимому таблицы. В противном случае содержимое таблицы переписывается каждый раз при выполнении шага задания.  
  
**Включить в журнал выходные данные шага**  
Выберите этот параметр для включения вывода из шага задания в журнал заданий.  
  
## <a name="see-also"></a>См. также:  
[Управление шагами задания](../../ssms/agent/manage-job-steps.md)  
  
