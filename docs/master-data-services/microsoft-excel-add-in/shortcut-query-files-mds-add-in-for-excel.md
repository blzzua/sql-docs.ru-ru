---
title: "Файлы ярлыков запросов (надстройка MDS для Excel) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: microsoft-excel-add-in
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ba0219a-6c40-41fa-aff9-8c8f41ef3220
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 17c5f85a973477cd7bd89c459dc78cc069b149d1
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="shortcut-query-files-mds-add-in-for-excel"></a>Файлы ярлыков запросов (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]файл ярлыка запроса позволяет быстро устанавливать соединение и загружать часто используемые данные. Они могут также использоваться в том случае, если необходим обмен данными MDS с другими пользователями. Вместо сохранения и отправки листа по электронной почте можно сохранить файл ярлыка запроса и отправить его. Это гарантирует, что и вы, и ваш адресат будете получать из репозитория MDS самые актуальные данные.  
  
 Файлы ярлыков запросов — это XML-файлы, которые содержат следующие данные.  
  
-   Соединение с репозиторием MDS.  
  
-   Модель, версия и сущность.  
  
-   Все фильтры, применявшиеся при создании ярлыка.  
  
-   Порядок столбцов слева направо, заданный при создании ярлыка.  
  
 Эти файлы можно сохранить в списке и выбрать при открытии надстройки. Их также можно экспортировать на компьютер или в общую папку или отправить другому пользователю.  
  
 Открывать файлы ярлыка запроса можно двумя способами: их можно импортировать либо дважды щелкнуть, чтобы автоматически открыть в приложении QueryOpener.  
  
## <a name="queryopener-application"></a>Приложение QueryOpener  
 Все пользователи, установившие [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] , имеют установленное приложение QueryOpener. Оно служит для открытия файлов ярлыков запросов в [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]. Если дважды щелкнуть файл ярлыка запроса, то это приложение автоматически открывает его в надстройке.  
  
 При открытии файла ярлыка запроса в приложении вам будет предложено сделать соединение «безопасным», а это означает, что вы доверяете содержимому из этого источника. (Для этого выберите параметр **Always allow connection to this address** (Всегда разрешать подключение по этому адресу) в окне запроса.) Каждый раз, когда соединение помечается как безопасное, оно добавляется в список. Если нужно очистить этот список, откройте диалоговое окно **Настройки** и в разделе **Серверы, добавленные в список безопасных** нажмите кнопку **Очистить все**.  
  
 Папка по умолчанию для приложения — *диск*:\Program Files\Microsoft SQL Server\130\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Сохранение содержимого активного листа в виде файла ярлыка запроса.|[Сохранение файла ярлыка запроса (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Отправка файла ярлыка запроса, который представляет содержимое активного листа.|[Отправка файла ярлыка запроса по электронной почте (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Соединения (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
-   [Надстройка Master Data Services для Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Безопасность (службы Master Data Services)](../../master-data-services/security-master-data-services.md)  
  
  
