---
title: Начало работы с SSMA для Sybase консоли (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Launching SSMA Console
- Sybase Console,Output Conventions
- Sybase Console,Procedure for Using Console
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d63e1c4e3ecf3cd5f2537ec54db24be59a4d8ad5
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="getting-started-with-the-ssma-for-sybase-console-sybasetosql"></a>Начало работы с SSMA для Sybase консоли (SybaseToSQL)
В этом разделе описывается процедура запуска и начало работы с SSMA для Sybase консольного приложения. Здесь также приводятся соглашения используются в типичного окна вывода консоли SSMA.  
  
## <a name="launching-the-ssma-console"></a>Запуск консоли SSMA  
Чтобы запустить консольное приложение SSMA используйте следующие действия:  
  
1.  Перейдите на начальном экране и выберите пункт Все программы.  
  
2.  Нажмите кнопку **SQL Server Migration Assistant для Sybase командной строки** ярлык.  
  
    Отображает меню использования консоли SSMA и `(/? Help)`, чтобы помочь вам приступить к работе с консольного приложения.  
  
## <a name="using-the-ssma-console"></a>С помощью консоли SSMA  
После консоль успешно запускается в среде Windows, для работы с ней можно использовать следующие шаги:  
  
1.  Настройка консоли SSMA через файлы скриптов. Дополнительные сведения об этом разделе см. в разделе [Создание файлов скриптов &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
2.  [Создание файлов значение переменной &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [Создание файлов подключения сервера &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [Выполнение консоли SSMA &#40;SybaseToSQL&#41; ](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) зависимости от требований проекта. 
  
Дополнительные функции:  
  
1.  [Укажите пароль](http://msdn.microsoft.com/en-us/9b6a70f9-6840-4140-a059-bb7bd7ccc67c) и экспорта и импорта его на другие компьютеры окна.  
  
2.  [Составление отчетов](http://msdn.microsoft.com/en-us/19278f6a-6d58-4867-9d71-c6228040466e) для просмотра xml подробный вывод отчетов для оценки и преобразования и перемещение данных. Также можно создавать подробные отчеты для команд обновить и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
После выполнения команды сценария SSMA и параметры, консольная программа отображает результаты и сообщения (сведения, ошибка, т. д.) для пользователя на консоли или при необходимости перенаправляет выходные данные в XML-файл. Каждый тип сообщения в выводе обозначается уникальным цветом. Например текстовое сообщение в белый цвет обозначает команд файла скрипта; в зеленый цвет представляет запрос для ввода данных пользователем и т. д.  
  
![SSMAConsoleOutput_Sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "SSMAConsoleOutput_Sybase")  
  
Интерпретация цветовой выходные данные в консоли отображается в следующей таблице:  
  
|Color|Описание|  
|---------|---------------|  
|Красный|Неустранимая ошибка во время выполнения|  
|Серый|Метка даты и времени, сообщение для пользователя|  
|White|Файл команд, тип сообщения|  
|Желтый|Предупреждение|  
|Зеленый|Запрос для ввода данных пользователем|  
|Голубой|Начала, окончания и результат операции|  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
