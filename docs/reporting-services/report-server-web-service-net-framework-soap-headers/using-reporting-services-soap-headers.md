---
title: "Использование заголовков SOAP служб Reporting Services | Документы Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: report-server-web-service-net-framework-soap-headers
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
caps.latest.revision: "39"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cce2217f03e945bc9b3c8eb3667792b7d1d078e3
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="using-reporting-services-soap-headers"></a>Использование заголовков SOAP служб Reporting Services
  Связь с методом веб-службы по протоколу SOAP имеет стандартный формат. Данные, закодированные в XML-документе, являются частью этого формата. XML-документ состоит из корневого элемента **Envelope**, который в свою очередь состоит из обязательного элемента **Body** и дополнительного элемента **Header**. Элемент **Body** содержит данные, соответствующие сообщению. Необязательный элемент **Header** может содержать дополнительную информацию, не связанную напрямую с конкретным сообщением. Каждый дочерний элемент **Header** называется заголовком SOAP.  
  
 Несмотря на то что заголовки SOAP могут содержать данные, связанные с сообщением, они в основном содержат информацию, обрабатываемую инфраструктурой веб-сервера.  
  
 Веб-службы сервера отчетов определяют несколько классов для использования в заголовке SOAP: <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader> и <xref:ReportExecution2005.ExecutionHeader>.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Методы пакетной обработки](../../reporting-services/report-server-web-service-net-framework-soap-headers/batching-methods.md)|Описывает, как объединять в пакет несколько операций в одну транзакцию с помощью класса <xref:ReportService2005.BatchHeader>.|  
|[Определение состояния выполнения](../../reporting-services/report-server-web-service-net-framework-soap-headers/identifying-execution-state.md)|Описывает, как управлять состоянием сеанса в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с помощью **SessionHeader**.|  
|[Определение пространства имен элементов для метода GetProperties](../../reporting-services/report-server-web-service-net-framework-soap-headers/setting-the-item-namespace-for-the-getproperties-method.md)|Описывает, как получить свойства, основанные либо на пути, либо на идентификаторе элемента, используя метод <xref:ReportService2010.ReportingService2010.GetProperties%2A> и заголовок SOAP <xref:ReportService2010.ItemNamespaceHeader>.|  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Технический справочник (службы SSRS)](../../reporting-services/technical-reference-ssrs.md)  
  
  
