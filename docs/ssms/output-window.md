---
title: "Окно вывода SSMS | Microsoft Docs"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Output Window [SQL Server Management Studio]
- Activity Monitor [SQL Server Management Studio]
- Object Explorer [SQL Server Management Studio]
ms.assetid: a2ce1a07-b4e2-471c-87d2-b8de5e6c6864
caps.latest.revision: 1
author: shueybubbles
ms.author: davidshi
manager: kenvh
ms.translationtype: HT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 69d3f6ecaaf9299a8816ac56d5587051548ac1df
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="output-window-in-sql-server-management-studio"></a>Окно вывода в SQL Server Management Studio
Окно вывода можно открыть из меню "Вид" или с помощью сочетания клавиш CTRL+ALT+O. Существует несколько каналов выходных данных.

В следующей таблице представлен обзор типов сообщений, связанных с каждым каналом выходных данных.

|Channel|Description|
|-----------|---------------|  
|**Телеметрия**|Телеметрия — это поток [анонимных данных об использовании функций](sql-server-management-studio-ssms.md), собираемых корпорацией Майкрософт. Вы можете использовать эти события для сохранения собственных данных об использовании SSMS. Они помогают определить, какие узлы обозревателя объектов были развернуты и какие команды запускались в сеансе SSMS, пока было открыто окно вывода.|
|**Обозреватель объектов**|В этом канале выводится текст и затраченное время запросов SQL, необходимых для разворачивания узлов в обозревателе объектов. Каждый запрос записывает в журнал события начала и окончания запроса. У каждого события есть метка времени и универсальное имя ресурса, связанное с запрашиваемой сущностью. [Универсальное имя ресурса (URN)](https://technet.microsoft.com/library/microsoft.sqlserver.management.smo.urn(v=sql.90).aspx) ссылается на управляющий объект SQL Server и включает иерархию типа XPath. Например, URN для таблицы с именем "Table1" в базе данных "Db" на сервере "MyServer" будет иметь вид "Server[@Name='MyServer']/Database[@Name='Db']/Table[/@Name='Table1']". При разворачивании одного узла в обозревателе объектов возможно выполнение множества таких запросов с разными параметрами. Событие окончания запроса будет содержать затраченное время и текст TSQL. Эти данные могут быть полезны для анализа производительности сервера в тех случаях, когда какой-то узел в обозревателе объектов разворачивается слишком медленно. **Примечание**. Такие подробные сведения о запросах предоставляются не для всех узлов в обозревателе объектов.|
|**Монитор активности**|Этот канал запускается при [открытии Монитора активности](https://docs.microsoft.com/en-us/sql/relational-databases/performance-monitor/activity-monitor) для сервера. Этот поток содержит события, включающие часть текста запроса и временную отметку для каждого запроса, сообщения об ошибках и уведомления о приостановке монитора из-за проблем с подключением. Если монитор активности не отвечает или не обновляется, проверьте этот выходной канал для получения дополнительных сведений.|





