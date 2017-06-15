---
title: "Методы управления пространством имен сервера отчетов | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- reports [Reporting Services], managing
- management methods [Reporting Services]
- methods [Reporting Services], about methods
- methods [Reporting Services]
ms.assetid: 2aa43ce9-f51e-408a-8ce0-b40d3dd62561
caps.latest.revision: 37
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 1550f5e7c429df8fa6ee660fd00fa79047296e55
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="report-server-namespace-management-methods"></a>Методы управления пространством имен сервера отчетов
  Веб-служба управления сервером отчетов содержит методы, которые можно использовать для управления отчетами, папками и ресурсами в базе данных сервера отчетов.  
  
|Метод|Действие|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CancelJob%2A>|Отменяет выполнение задания.|  
|<xref:ReportService2010.ReportingService2010.CreateFolder%2A>|Добавляет папку в базу данных сервера отчетов или в библиотеку SharePoint.|  
|<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A>|Добавляет новый элемент в базу данных сервера отчетов или в библиотеку SharePoint Этот метод применим к **отчетов**, **модели**, **набора данных**, **компонент**, **ресурсов**, и **DataSource** типов элементов.|  
|M:ReportService2010.ReportingService2010.CreateReportEditSession(System.String,System.String,System.Byte[],ReportService2010.Warning[]@)|Создает новый сеанс изменения отчета.|  
|<xref:ReportService2010.ReportingService2010.DeleteItem%2A>|Удаляет элемент из базы данных сервера отчетов или из библиотеки SharePoint.|  
|<xref:ReportService2010.ReportingService2010.FindItems%2A>|Возвращает элементы базы данных сервера отчетов или библиотеки SharePoint, которые соответствуют указанным условиям поиска.|  
|<xref:ReportService2010.ReportingService2010.FireEvent%2A>|Инициирует событие, основанное на предоставленных параметрах.|  
|<xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>|Возвращает список параметров для данного расширения.|  
|<xref:ReportService2010.ReportingService2010.GetItemType%2A>|Получает тип элемента в базе данных сервера отчетов или в библиотеке SharePoint, если элемент существует.|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|Возвращает значения одного или нескольких свойств элемента в базе данных сервера отчетов или в библиотеке SharePoint.|  
|<xref:ReportService2010.ReportingService2010.GetItemDefinition%2A>|Получает определение или содержимое элемента. Этот метод применим к **отчетов**, **модели**, **набора данных**, **компонент**, **ресурсов**, и **DataSource** типов элементов.|  
|<xref:ReportService2010.ReportingService2010.GetItemReferences%2A>|Возвращает список ссылок элементов каталога, связанных с элементом.|  
|<xref:ReportService2010.ReportingService2010.GetReportServerConfigInfo%2A>|Возвращает сведения о подключенном экземпляре сервера отчетов или обо всех экземплярах сервера отчетов в масштабном развертывании.|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|Возвращает одно или несколько системных свойств.|  
|<xref:ReportService2010.ReportingService2010.ListChildren%2A>|Возвращает список дочерних элементов указанной папки.|  
|<xref:ReportService2010.ReportingService2010.ListDatabaseCredentialRetrievalOptions%2A>|Возвращает список поддерживаемых параметров получения учетных данных.|  
|<xref:ReportService2010.ReportingService2010.ListEvents%2A>|Возвращает список модулей обработки событий в том виде, как они представлены в файле конфигурации сервера отчетов.|  
|<xref:ReportService2010.ReportingService2010.ListJobs%2A>|Возвращает список заданий, выполняющихся на сервере отчетов.|  
|<xref:ReportService2010.ReportingService2010.ListExtensions%2A>|Возвращает список модулей, настроенных для данного типа модулей.|  
|<xref:ReportService2010.ReportingService2010.ListExtensionTypes%2A>|Возвращает список поддерживаемых типов расширений.|  
|<xref:ReportService2010.ReportingService2010.ListItemTypes%2A>|Возвращает список поддерживаемых типов элементов каталога.|  
|<xref:ReportService2010.ReportingService2010.ListJobActions%2A>|Возвращает список поддерживаемых действий заданий.|  
|<xref:ReportService2010.ReportingService2010.ListJobStates%2A>|Возвращает список поддерживаемых состояний заданий.|  
|<xref:ReportService2010.ReportingService2010.ListJobTypes%2A>|Возвращает список поддерживаемых типов заданий.|  
|<xref:ReportService2010.ReportingService2010.ListParents%2A>|Находит родительские элементы для данного элемента.|  
|<xref:ReportService2010.ReportingService2010.ListSecurityScopes%2A>|Возвращает список поддерживаемых областей безопасности.|  
|<xref:ReportService2010.ReportingService2010.Logoff%2A>|Выполняет выход из системы для текущего пользователя, выполняющего запросы к веб-службе. Этот метод применим только в собственном режиме.|  
|<xref:ReportService2010.ReportingService2010.LogonUser%2A>|Выполняет вход в систему пользователя и аутентифицирует запрос пользователя к веб-службе сервера отчетов. Этот метод применим только в собственном режиме.|  
|<xref:ReportService2010.ReportingService2010.SetItemReferences%2A>|Задает элементы каталога, связанные с элементом.|  
|<xref:ReportService2010.ReportingService2010.MoveItem%2A>|Перемещает или переименовывает элемент.|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|Задает одно или несколько свойств элемента.|  
|<xref:ReportService2010.ReportingService2010.SetItemDefinition%2A>|Задает определение или содержимое указанного элемента. Этот метод применим к **отчетов**, **модели**, **набора данных**, **компонент**, **ресурсов**, и **DataSource** типов элементов.|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|Задает одно или несколько системных свойств элемента в базе данных сервера отчетов или ферме SharePoint.|  
|<xref:ReportService2010.ReportingService2010.ValidateExtensionSettings%2A>|Проверяет параметры модулей служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Методы веб-службы для сервера отчетов](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Технический справочник (службы SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  