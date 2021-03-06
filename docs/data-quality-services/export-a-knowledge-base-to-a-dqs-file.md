---
title: Экспорт базы знаний в файл DQS | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: ''
ms.component: data-quality-services
ms.reviewer: ''
ms.suite: sql
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a324ead5-c8aa-4e26-abe3-ef415add00f8
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2e07762d37b8e18abd96a4976c636752588774f8
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="export-a-knowledge-base-to-a-dqs-file"></a>Экспорт базы знаний в файл .dqs
  В этом разделе описывается экспорт всей базы знаний в файл данных DQS в службах [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Экспортировать в файл данных можно домен или всю базу знаний. Сведения об экспорте домена см. в разделе [Экспорт домена в файл DQS](../data-quality-services/export-a-domain-to-a-dqs-file.md).  
  
 Экспорт базы знаний в файл DQS и последующий импорт в качестве другой базы знаний упрощает процесс создания знаний и экономит время. Благодаря этому можно использовать базу знаний и ее знания совместно с другими пользователями. Файл DQS будет содержать все сведения базы знаний, включая домены и политику сопоставления, кроме присоединенных ссылочных данных. После импорта файла DQS следует повторно добавить необходимые домены в соответствующие службы ссылочных данных. Экспортируются как опубликованные, так и неопубликованные данные базы знаний.  
  
 Файл данных DQS, созданный в процессе экспорта, зашифровывается, его просмотр становится невозможным.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Чтобы экспортировать базу знаний в файл данных DQS, необходимо создать и открыть базу знаний. Файл DQS не требуется, он будет создан в процессе экспорта.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для экспорта базы знаний в файл данных DQS необходимо быть членом роли dqs_kb_editor или dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="Export"></a> Export a knowledge base to a .dqs file  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Запуск клиентского приложения Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране клиента [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] откройте базу знаний в разделе управления доменами.  
  
3.  На странице «Управление доменами» (при любой выбранной вкладке) щелкните значок **Экспортировать данные базы знаний** над списком «Домен» и выберите **Экспортировать базу знаний**. Кроме того, вы можете щелкнуть правой кнопкой мыши список **Домен** , указать пункт **Экспорт**, а затем **Экспортировать базу знаний**.  
  
4.  В диалоговом окне **Экспорт в файл данных** перейдите в папку, где планируется сохранить файл, присвойте файлу имя или оставьте имя базы знаний, оставьте **Файлы данных DQS (\*.dqs)** в качестве **Типа файла** и нажмите кнопку **Сохранить**.  
  
5.  В диалоговом окне **Экспортировать базу знаний** убедитесь, что в строке состояния сообщается о завершении экспорта. Нажмите кнопку **ОК**.  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После экспорта домена в файл DQS  
 После экспорта базы знаний в файл DQS можно импортировать базу знаний на тот же сервер [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (с новым именем) или на другой сервер [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
  
