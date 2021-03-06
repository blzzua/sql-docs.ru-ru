---
title: "Установка безопасных соединений в ADOMD.NET | Документы Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- connections [ADOMD.NET]
- security [ADOMD.NET]
ms.assetid: b084d447-1456-45a4-8e0e-746c07d7d6fd
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6916e57fc0135fc5688c6569eaeb8341caa23b82
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="connections-in-adomdnet---establishing-secure-connections"></a>Connections in ADOMD.NET - установка безопасных соединений
  При использовании соединения в ADOMD.NET метод безопасности, используемый для соединения зависит от значения **ProtectionLevel** свойстве строки соединения, используемый при вызове <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 **ProtectionLevel** свойство поддерживает четыре уровня безопасности: не прошедшие проверку подлинности, проверку подлинности, подписи и шифрования. Эти уровни безопасности описаны в приведенной далее таблице.  
  
> [!NOTE]  
>  Если принято решение использовать пул подключений к базе данных, возможность использовать базу данных для управления безопасностью отсутствует. Это происходит потому, что для объединения подключений в пул базе данных требуется, чтобы строки соединений были одинаковыми. Поэтому управлять безопасностью необходимо в другом месте.  
  
|Уровень безопасности|Значение ProtectionLevel|  
|--------------------|---------------------------|  
|*подключение без проверки подлинности*<br /> В соединении без проверки подлинности проверка подлинности не выполняется ни в какой форме. Соединение этого типа является наиболее широко поддерживаемым, но наименее безопасным.|**None**|  
|*подключение с проверкой подлинности*<br /> При соединении с проверкой подлинности выполняется проверка подлинности пользователя, устанавливающего соединение, однако дальнейший обмен данными не защищается. Этот вид соединения полезен тем, что можно установить личность пользователя или приложения, устанавливающего соединение с источником аналитических данных.|**Соединить**|  
|*подписанное соединение*<br /> В подписанном соединении выполняется проверка подлинности пользователя, запрашивающего соединение, а в дальнейшем обеспечивается неизменность передаваемых данных. Этот вид соединения полезен, когда необходимо проверять подлинность передаваемых данных. Однако подписанное соединение лишь предотвращает изменение содержимого пакета данных. При этом все еще остается возможность просматривать содержимое при передаче.<br /><br /><br /><br /> Обратите внимание, что подписанное соединение поддерживается только поставщиком XML для аналитики предоставляемые [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|**Целостность Pkt** или **PktIntegrity**|  
|*зашифрованное соединение*<br /> Зашифрованное соединение — тип соединения, используемого по умолчанию платформой ADOMD.NET. Соединение этого типа выполняет проверку подлинности пользователя, запрашивающего соединение, а в дальнейшем также шифрует передаваемые данные. Зашифрованное соединение — самый безопасный вариант соединения, которое может быть установлено платформой ADOMD.NET. Содержимое пакета данных не может быть просмотрено или изменено, что защищает данные во время передачи.<br /><br /><br /><br /> Зашифрованное соединение поддерживается только поставщиком XML для аналитики предоставляемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|**Pkt Privacy** или **PktPrivacy**|  
  
 Однако не все уровни безопасности доступны для всех видов соединений.  
  
-   Для соединения по протоколу TCP можно использовать только один из четырех уровней безопасности. В действительности соединение по протоколу TCP при использовании его в сочетании с встроенной безопасностью Windows обеспечивает самый безопасный метод подключения к источнику аналитических данных.  
  
-   HTTP-соединение может быть только соединением с проверкой подлинности. Таким образом **ProtectionLevel** свойству необходимо присвоить значение **Connect**.  
  
-   Соединение по протоколу HTTPS может быть только зашифрованным соединением. Таким образом **ProtectionLevel** свойству необходимо присвоить значение **Pkt Privacy** или **PktPrivacy**.  
  
## <a name="securing-tcp-connections"></a>Защита соединений по протоколу TCP  
 Для соединений TCP **ProtectionLevel** свойство поддерживает все четыре уровня безопасности, как показано в следующей таблице.  
  
|Значение ProtectionLevel|Используется с соединением по протоколу TCP|Результаты|  
|---------------------------|------------------------------|-------------|  
|**None**|Да|Задает соединение без проверки подлинности.<br /><br /> Поставщик запрашивает поток TCP, но при этом проверка подлинности пользователя, запрашивающего этот поток, не проводится ни в какой форме.|  
|**Соединить**|Да|Задает соединение с проверкой подлинности.<br /><br /> У поставщика запрашивается поток TCP, а затем контекст безопасности пользователя, запрашивающего поток проходит проверку подлинности на сервере: Если проверка подлинности успешно пройдена, никакие другие действия не выполняются. Если проверка подлинности дает отрицательный результат, то объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> отключается от многомерного источника данных и активизируется исключение.<br /><br /> После того как проверка подлинности завершилась успехом или ошибкой, контекст безопасности, используемый для проверки подлинности соединения, удаляется.|  
|**Целостность Pkt** или **PktIntegrity**|Да|Задает соединение с подписью.<br /><br /> У поставщика запрашивается TCP-поток, а затем контекст безопасности пользователя, запрашивающего поток, проходит проверку подлинности на сервере.<br /><br /> <br /><br /> Если проверка подлинности завершается успешно, объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> закрывает существующий поток TCP и открывает поток TCP с подписью для обработки всех запросов. Каждый запрос данных или метаданных проходит проверку подлинности с применением контекста безопасности, с которым открывалось соединение. Кроме того, каждый пакет получает цифровую подпись для гарантирования полезных данных пакета TCP от любых изменений.<br /><br /> <br /><br /> Если проверка подлинности дает отрицательный результат, то объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> отключается от многомерного источника данных и активизируется исключение.|  
|**Pkt Privacy** или **PktPrivacy**|Да|Задает зашифрованное соединение.<br /><br /> <br /><br /> Обратите внимание, что можно указать зашифрованное соединение, не задав **ProtectionLevel** свойства в строке подключения.<br /><br /> <br /><br /> У поставщика запрашивается поток TCP, после чего выполняется проверка подлинности контекста безопасности пользователя, запрашивающего поток, с помощью сервера.<br /><br /> <br /><br /> Если проверка подлинности завершается успешно, объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> закрывает существующий поток TCP и открывает зашифрованный поток TCP для обработки всех запросов. Каждый запрос данных или метаданных проходит проверку подлинности с применением контекста безопасности, с которым открывалось соединение. Кроме того, полезные данные каждого пакета TCP шифруются при помощи самого сложного метода шифрования из всех, которые поддерживаются как поставщиком, так и источником многомерных данных.<br /><br /> <br /><br /> Если проверка подлинности дает отрицательный результат, то объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> отключается от многомерного источника данных и активизируется исключение.|  
  
### <a name="using-windows-integrated-security-for-the-connection"></a>Использование встроенной безопасности Windows для соединения  
 Использование встроенной безопасности Windows является наиболее надежным способом установления и защиты соединения с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. В процессе проверки подлинности встроенная безопасность Windows не раскрывает учетные данные безопасности, например имя пользователя или пароль, вместо этого для установки личности используется идентификатор безопасности работающего в данный момент процесса. В большинстве клиентских приложений этот идентификатор безопасности представляет собой идентификатор текущего, вошедшего в систему пользователя.  
  
 Для использования встроенной безопасности Windows в строке соединения требуется указать следующие настройки.  
  
-   Для **встроенной безопасности** свойства, либо вы не задать это свойство или присвойте этому свойству значение **SSPI**.  
  
    > [!NOTE]  
    >  Встроенная безопасность Windows доступна только для подключений TCP так, как необходимо использовать подключения по протоколу HTTP **основные** для **встроенной безопасности** свойство.  
  
-   Для **ProtectionLevel** свойства, присвойте этому свойству значение **Connect**, **целостности Pkt**, или **Pkt Privacy**.  
  
## <a name="securing-http-connections"></a>Защита HTTP-соединений  
 Протоколы HTTPS и SSL можно использовать для внешней защиты связи с источником аналитических данных по протоколу HTTP.  
  
 Поскольку поставщик XMLA использует только безопасный протокол HTTP, HTTP-соединение в ADOMD.NET должно быть с подписью, как показано в следующей таблице.  
  
|Значение ProtectionLevel|Использование с протоколом HTTP или HTTPS|  
|---------------------------|----------------------------|  
|**None**|нет|  
|**Соединить**|HTTP|  
|**Целостность Pkt** или **PktIntegrity**|нет|  
|**Pkt Privacy** или **PktPrivacy**|HTTPS|  
  
### <a name="opening-a-secure-http-connection"></a>Открытие безопасного HTTP-соединения  
 Приведенный ниже показано, как использовать ADOMD.NET для открытия HTTP-соединение для **AdventureWorksAS** пример [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных:  
  
```vb  
Public Function GetAWEncryptedConnection( _  
    Optional ByVal serverName As String = "https:\\localhost\isapy\msmdpump.dll") _  
    As AdomdConnection  
  
    Dim strConnectionString As String = ""  
    Dim objConnection As New AdomdConnection  
  
    Try  
        ' To establish an encrypted connection, set the   
        ' ProtectionLevel setting to PktPrivacy.  
        strConnectionString = "DataSource=" & serverName & ";" & _  
            "Catalog=AdventureWorksAS;" & _  
            "ProtectionLevel=PktPrivacy;"  
  
        ' Note that username and password are not supplied here.  
        ' The current security context is used for authentication  
        ' purposes.  
  
        objConnection.ConnectionString = strConnectionString  
        objConnection.Open()  
    Catch ex As Exception  
        objConnection = Nothing  
        Throw ex  
    Finally  
        ' Return the encrypted connection.  
        GetAWEncryptedConnection = objConnection  
    End Try  
End Function  
  
```  
  
## <a name="see-also"></a>См. также  
 [Установление соединений в ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)  
  
  
