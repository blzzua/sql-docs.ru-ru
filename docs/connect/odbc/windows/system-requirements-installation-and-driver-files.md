---
title: "Требования к системе для установки и файлы драйвера | Документы Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8e23264905c2a8b706b32a906d7dbf2dc3dd165b
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2018
---
# <a name="system-requirements-installation-and-driver-files"></a>Системные требования, установка и файлы драйвера
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] поддерживает подключения к SQL Server 2014, SQL Server 2012 R2, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro_md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]и [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)].  
  
ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows можно установить на компьютере, где также имеется одна или несколько версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client.  
  
ODBC Driver 13 и 13.1 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], дополнение к вышесказанному поддерживает SQL Server 2016. 

17 драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] выше из них поддерживает, а также 2017 г. SQL Server.
  
Имя драйвера, указываемое в строке подключения — `ODBC Driver 11 for SQL Server` или `ODBC Driver 13 for SQL Server` (для 13 и 13.1) или `ODBC Driver 17 for SQL Server`.
  
## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

Можно запускать приложения с помощью драйвера в следующих операционных системах Windows:  

-   Windows Server 2008 R2 
-   Windows Server 2012
-   Windows Server 2012 R2    
-   Windows Vista SP2 *(только для ODBC Driver 11)*  
-   Windows 7  
-   Windows 8
-   Windows 8.1
-   Windows 10
  
## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Установка Microsoft ODBC Driver for SQL Server

Драйвера при запуске `msodbcsql.msi` по одной из следующих ссылок:

- [Скачать Microsoft ODBC Driver 17 для SQL Server в Windows](https://www.microsoft.com/download/details.aspx?id=56567)
- [Скачать Microsoft ODBC Driver 13.1 for SQL Server в Windows](https://www.microsoft.com/download/details.aspx?id=53339)
- [Скачать Microsoft ODBC Driver 13 for SQL Server в Windows](https://www.microsoft.com/download/details.aspx?id=50420)
- [Загрузите драйвер Microsoft ODBC 11 для SQL Server в Windows](https://www.microsoft.com/download/details.aspx?id=36434). 

Это может быть установленных side-by-side с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client.  

При вызове `msodbcsql.msi`, клиентские компоненты устанавливаются по умолчанию. Клиентские компоненты — это файлы, поддерживающие работу приложения, разработанного с помощью драйвера. Чтобы установить компоненты пакета SDK, укажите `ADDLOCAL=ALL` в командной строке. Например:  
  
```  
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  
  
 Укажите `IACCEPTMSODBCSQLLICENSETERMS=YES` принять условия лицензии конечного пользователя, при использовании `/passive`, `/qn`, `/qb`, или `/qr` для установки. Этот параметр указывается только прописными буквами. Например:  
  
```  
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  
  
 Для выполнения автоматического удаления  
  
```  
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  
  
Если приложение использует драйвер, приложение должно быть указано, что он зависит от драйвера, с помощью параметра установки `APPGUID`. Это позволяет установщику драйвера о зависимых приложениях перед удалением. Чтобы задать зависимость от драйвера, задайте `APPGUID` параметр командной строки, код продукта при автоматической установке драйвера. (Код продукта необходимо создать при использовании установщика (Майкрософт) для формирования пакета установки приложения.) Например:  
  
```  
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Программы командной строки: sqlcmd.exe и bcp.exe

`bcp.exe` И `sqlcmd.exe` средств для использования с драйвер можно загрузить по адресу [Microsoft Command Line Utilities 11 для SQL Server](http://www.microsoft.com/download/details.aspx?id=36433), [Microsoft 13 служебные программы командной строки для SQL Server](https://www.microsoft.com/download/details.aspx?id=52680), или [Microsoft Command Line Utilities 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53591). Драйвер является необходимым условием для установки `sqlcmd.exe` и `bcp.exe`.
  
`bcp.exe` и `sqlcmd.exe` устанавливаются в `110\Tools` вложенной `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` для версии 11, и `130\Tools` 13 и 13.1.

Приложение, использующее функции BCP необходимо указать драйвер из той же версии, которая поставляется с файлом заголовка и библиотекой, использованными при компиляции приложения.  

Например, при компиляции приложения ODBC с `msodbcsql11.lib` и `msodbcsql.h`, используйте «ДРАЙВЕР = {ODBC Driver 11 для SQL Server}» в строке подключения.

## <a name="components-of-the-microsoft-odbc-driver-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Компоненты Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows 
 Драйвер ODBC для Windows состоит из следующих компонентов:
 
|Компонент|Описание|  
|---------------|-----------------|  
|msodbcsql17.dll или <br> msodbcsql13.dll или <br> msodbcsql11.dll|Файл библиотеки динамической компоновки (DLL), содержащий все функциональные возможности драйвера. Этот файл устанавливается в папку % SYSTEMROOT%\System32.|  
|msodbcdiag17.dll или <br> msodbcdiag13.dll или <br> msodbcdiag11.dll|Файл библиотеки динамической компоновки (DLL), содержащий интерфейс драйвера диагностики (трассировки). Этот файл устанавливается в папку % SYSTEMROOT%\System32.|
|msodbcsqlr17.rll или <br> msodbcsqlr13.rll или <br> msodbcsqlr11.rll|Сопутствующий файл ресурса для библиотеки драйвера. Этот файл устанавливается в папку % SYSTEMROOT%\System32\1033.| 
|s13ch_msodbcsql.chm или <br> s11ch_msodbcsql.chm |Файл справки мастера источников данных, описывающий, как создать источник данных для драйвера. Этот файл устанавливается в %SYSTEMROOT%\System32\1033 <br /> <br /> **Примечание:** нет файла chm для 17 драйвера ODBC. |  
|msodbcsql.h|Файл заголовка, содержащий все новые определения, необходимые для его использования.<br /><br /> **Примечание**  . Нельзя сослаться на msodbcsql.h и odbcss.h в одной программе.<br /><br /> msodbcsql.h 17 драйвера ODBC или 13 устанавливается в %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK. <br /> msodbcsql.h для ODBC Driver 11 устанавливается в %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.| 
|msodbcsql17.lib или <br> msodbcsql13.lib или <br> msodbcsql11.lib|Файл библиотеки, необходимый для вызова **bcp** служебных функций, которые входят в состав драйвера.<br /><br /> **Примечание:** при ссылке этот файл библиотеки в программе, убедитесь, что это в вашем системном пути, а также в системном пути, которые используют приложения.<br /><br /> msodbcsql17.lib или msodbcsql13.lib устанавливается в %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK.<br /> msodbcsql11.lib устанавливается в папку %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.|

  
## <a name="see-also"></a>См. также  
 [Драйвер Microsoft ODBC для SQL Server в Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
