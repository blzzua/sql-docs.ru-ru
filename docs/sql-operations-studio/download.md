---
title: Загрузите и установите Microsoft SQL Studio операций (Предварительная версия) | Документы Microsoft
description: Загрузка и установка Microsoft SQL операций Studio (Предварительная версия) для Windows, macOS или Linux
ms.custom: tools|sos
ms.date: 03/28/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5bf4e79bc1f7092ebe95ff29079f3412306cf7b1
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2018
---
# <a name="download-and-install-sql-operations-studio-preview"></a>Загрузите и установите Studio операций SQL (Предварительная версия)

[!INCLUDE[name-sos](../includes/name-sos.md)] выполняется на Windows, macOS и Linux.

Загрузить и установить последний выпуск *общедоступной предварительной версии марта*:

|Платформа|Загрузить|Дата выпуска| Версия |
|:---|:---|:---|:---|
|Windows|[Установщик](https://go.microsoft.com/fwlink/?linkid=870837)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=870838)|28 марта 2018 |0.27.3|
|MacOS|[.zip](https://go.microsoft.com/fwlink/?linkid=870839)|28 марта 2018 |0.27.3|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=870842)<br>[.RPM](https://go.microsoft.com/fwlink/?linkid=870841)<br>[. tar.gz](https://go.microsoft.com/fwlink/?linkid=870840)|28 марта 2018 |0.27.3|

Дополнительные сведения о последнем выпуске см. в разделе [заметки о выпуске](release-notes.md).

## <a name="get-sql-operations-studio-preview-for-windows"></a>Получение операций SQL Studio (Предварительная версия) для Windows

Этот выпуск [!INCLUDE[name-sos](../includes/name-sos-short.md)] включает стандартные возможности установщика Windows и .zip: 

**Установщик**

1. Загрузите и запустите [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] установщик Windows](https://go.microsoft.com/fwlink/?linkid=870837).
1. Запуск [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] приложения.


**ZIP-файл**

1. Загрузить [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] .zip для Windows](https://go.microsoft.com/fwlink/?linkid=870838).
2. Найдите загруженный файл и извлеките его.
3. Выполнить `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>Получить для macOS Studio операций SQL (Предварительная версия)

1. Загрузить [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] для macOS](https://go.microsoft.com/fwlink/?linkid=870839).
2. Чтобы развернуть содержимое ZIP-файл, дважды щелкните его.
3. Чтобы сделать [!INCLUDE[name-sos](../includes/name-sos-short.md)] в *запуска*, перетащите *sqlops.app* для *приложений* папки.


## <a name="get-sql-operations-studio-preview-for-linux"></a>Получить Studio операций SQL (Предварительная версия) для Linux

1. Загрузите [! ВКЛЮЧИТЬ[имя sos](../includes/name-sos-short.md) для Linux с помощью одного из установщиков или tar.gz архива:
    - [.deb](https://go.microsoft.com/fwlink/?linkid=870842)
    - [.RPM](https://go.microsoft.com/fwlink/?linkid=870841)
    - [. tar.gz](https://go.microsoft.com/fwlink/?linkid=870840)
1. Чтобы извлечь файл и запустите [!INCLUDE[name-sos](../includes/name-sos-short.md)], откройте новое окно терминала и введите следующие команды:

   **Debian установки:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
   ```

   **RPM установки:**
   ```bash
   cd ~
   yum install ./Downloads/sqlops-linux-<version string>.rpm

   sqlops
   ```

   **tar.gz установки:**
   ```bash 
   cd ~ 
   cp ~/Downloads/sqlops-linux-<version string>.tar.gz ~ 
   tar -xvf ~/sqlops-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/sqlops-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   sqlops 
   ``` 

   > [!NOTE]
   > В Debian, Redhat и Ubuntu могут быть потеряны зависимости. Используйте следующие команды для установки этих зависимостей в зависимости от вашей версии Linux:
   

   **Debian:** 
   ```bash
   sudo apt-get install libuwind8
   ```

   **Redhat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-sql-operations-studio-preview"></a>Удаление операций SQL Studio (Предварительная версия)

Если вы установили [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] с помощью установщика Windows, удалите так же, как удалить любое другое приложение Windows.

Если вы установили [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] с расширением ZIP или других архива, просто удалите файлы.

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

[!INCLUDE[name-sos](../includes/name-sos-short.md)] выполняется на Windows, Linux и macOS и поддерживается на следующих платформах:

### <a name="windows"></a>Windows
- Windows 10 (64-разрядная)
- Windows 8.1 (64-разрядная)
- Windows 8 (64-разрядная)
- Требуется Windows 7 (SP1) (64-разрядная версия) - [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64-разрядная версия)
- Windows Server 2012 (64-разрядная версия)
- Windows Server 2008 R2 (64-разрядная версия)

### <a name="macos"></a>MacOS
- macOS 10.13 Сьерра высокого уровня
- macOS 10.12 Сьерра

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server версии 12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>Проверка обновлений
Чтобы проверить наличие последних обновлений, щелкните значок шестеренки в левом нижнем углу окна и нажмите кнопку **проверять наличие обновлений**

## <a name="next-steps"></a>Следующие шаги

См. один из следующих краткие руководства, чтобы приступить к работе:
- [Подключиться & запрос SQL Server](quickstart-sql-server.md)
- [Подключиться & запроса базы данных Azure SQL](quickstart-sql-database.md)
- [Подключиться & запроса хранилища данных Azure](quickstart-sql-dw.md)

Участие в [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Заявление о конфиденциальности Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) и [сбора данных об использовании](usage-data-collection.md).
