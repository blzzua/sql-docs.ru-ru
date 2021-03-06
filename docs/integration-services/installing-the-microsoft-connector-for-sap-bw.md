---
title: "Установка соединителя Microsoft Connector для SAP BW | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1d2716714e810143e17d3435c61de394e82b9bc
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="installing-the-microsoft-connector-for-sap-bw"></a>Установка Microsoft Connector для SAP BW
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector для SAP BW для SQL Server 2016 входит в пакет дополнительных компонентов SQL Server 2016. Чтобы установить Connector для SAP BW и сопутствующую документацию, скачайте и запустите установщик [с веб-страницы пакета дополнительных компонентов SQL Server 2016](http://go.microsoft.com/fwlink/?LinkId=746297).  
  
> [!IMPORTANT]  
>  Для работы с документацией по Microsoft Connector для SAP BW вы должны иметь представление о среде SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
> [!IMPORTANT]  
>  Для извлечения данных из SAP Netweaver BW требуется дополнительная лицензия SAP. Обратитесь к SAP, чтобы уточнить требования.  
  
## <a name="required-sap-files"></a>Необходимые файлы SAP  
 Чтобы использовать [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector для SAP BW, не нужно устанавливать клиентское ПО SAP (пользовательский графический интерфейс SAP) на локальном компьютере.  
  
 Однако необходимо скопировать файл соединителя SAP .NET (librfc32.dll) во вложенную папку в системном каталоге Windows. (Обычно это каталог **C:\Windows\system32**.)  
  
## <a name="considerations-for-64-bit-computers"></a>Замечания для 64-разрядных компьютеров  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector для SAP BW полностью поддерживает 64-разрядную версию [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. На 64-разрядном компьютере [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector для SAP BW имеет следующие дополнительные требования:  
  
-   Для запуска пакетов в 64-разрядном режиме в любой 64-разрядной ОС Windows скопируйте 64-разрядную версию файла графического пользовательского интерфейса SAP librfc32.dll в папку **system32** в каталоге Windows. (Обычно это каталог **C:\Windows\system32**.)  
  
-   Для запуска пакетов в 32-разрядном режиме в любой 64-разрядной ОС Windows скопируйте файл графического пользовательского интерфейса SAP librfc32.dll в папку **SysWow64** в каталоге Windows. (Обычно это каталог **C:\Windows\SysWow64**.)  
  
  
