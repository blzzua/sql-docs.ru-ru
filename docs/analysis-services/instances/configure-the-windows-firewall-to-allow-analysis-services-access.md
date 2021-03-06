---
title: "Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports [Analysis Services]
- Windows Firewall [Analysis Services]
- firewall systems [Analysis Services]
ms.assetid: 7673acc5-75f0-4703-9ce2-87425ea39d49
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: 0cb0930e6fd3faf0b44c5b8ac46359ec959b85c9
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="configure-the-windows-firewall-to-allow-analysis-services-access"></a>Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Важный первый шаг предоставления доступа к [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] по сети состоит в определении того, требуется ли разблокировать порты брандмауэра. Для большинства установок необходимо создать по крайней мере одно правило брандмауэра для входящих подключений, которое разрешает подключаться к службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Требования к конфигурации брандмауэра зависят от того, как был установлен компонент служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   При установке экземпляра по умолчанию или создании отказоустойчивого кластера служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] откройте TCP-порт 2383.  
  
-   При установке именованного экземпляра откройте TCP-порт 2382. Именованные экземпляры используют динамическое назначение портов. В качестве службы обнаружения для служб Analysis Services служба обозревателя SQL Server прослушивает TCP-порт 2382 и перенаправляет запрос на подключение к порту, используемому в настоящее время службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   При установке служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint для поддержки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 откройте TCP-порт 2382. В [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] находится за пределами SharePoint. Входящие запросы к именованному экземпляру[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]исходят от веб-приложений SharePoint по сетевому подключению, поэтому для них требуется открытый порт. Как и в случае с другими именованными экземплярами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , создайте правило для входящих подключений для службы обозревателя SQL Server на TCP-порт 2382, чтобы разрешить доступ к [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].  
  
-   Для [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 открывать порты в брандмауэре Windows не требуется. В качестве надстройки к SharePoint служба использует порты, настроенные для SharePoint, и устанавливает только локальные соединения с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , который загружает модели данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и выполняет к ним запросы.  
  
-   Для экземпляров служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , выполняющихся на виртуальных машинах Windows Azure, используйте альтернативные инструкции по настройке доступа к серверу. См. раздел [SQL Server Business Intelligence на виртуальных машинах Windows Azure](http://msdn.microsoft.com/library/windowsazure/jj992719.aspx).  
  
 Несмотря на то что экземпляр по умолчанию [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] прослушивает TCP-порт 2383, можно настроить сервер на прослушивание другого фиксированного порта подключения к серверу в следующем формате: \<имя_сервера >:\<номер_порта >.  
  
 Экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может использовать только один TCP-порт. На компьютерах с несколькими сетевыми платами или несколькими IP-адресами службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] прослушивают один TCP-порт для всех IP-адресов, назначенных этому компьютеру или указанных ему с помощью псевдонима. Если имеются особые требования в отношении нескольких портов, попробуйте настроить службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для доступа по протоколу HTTP. Затем можно установить несколько конечных точек HTTP для любых портов в выбранном формате. См. раздел [Настройка HTTP-доступа к службам Analysis Services в службах Internet Information Services (IIS) 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md).  
  
 Этот раздел состоит из следующих подразделов.  
  
-   [Проверка параметров порта и брандмауэра для служб Analysis Services](#bkmk_checkport)  
  
-   [Настройка брандмауэра Windows для экземпляра по умолчанию служб Analysis Services](#bkmk_default)  
  
-   [Настройка доступа в брандмауэре Windows для именованного экземпляра служб Analysis Services](#bkmk_named)  
  
-   [Настройка порта для кластера служб Analysis Services](#bkmk_cluster)  
  
-   [Настройка порта PowerPivot для SharePoint](#bkmk_powerpivot)  
  
-   [Использовать фиксированный порт для именованного экземпляра или экземпляра по умолчанию служб Analysis Services](#bkmk_fixed)  
  
 Дополнительные сведения о настройках брандмауэра Windows по умолчанию и описание портов TCP, влияющих на компонент Database Engine, службы Analysis Services, службы Reporting Services и службы Integration Services, см. в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
##  <a name="bkmk_checkport"></a> Проверка параметров порта и брандмауэра для служб Analysis Services  
 В операционных системах Microsoft Windows, поддерживаемых [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], брандмауэр Windows включен по умолчанию и блокирует удаленные соединения. Чтобы разрешить входящие запросы к службам Analysis Services, необходимо вручную открыть порт в брандмауэре. Программа установки SQL Server не выполняет этот шаг автоматически.  
  
 Параметры порта указываются в файле msmdsrv.ini и на странице свойств «Общие» экземпляра служб Analysis Services в среде SQL Server Management Studio. Если в поле **Порт** установлено положительное целочисленное значение, служба прослушивает фиксированный порт. Если в поле **Порт** установлено значение 0, служба прослушивает порт 2383, если это экземпляр по умолчанию, или динамически назначенный порт, если это именованный экземпляр.  
  
 Динамические назначения портов используются только именованными экземплярами. При запуске службы **MSOLAP$InstanceName** определяется, какой порт следует использовать. Можно определить действительный номер порта, используемый именованным экземпляром, выполнив следующие действия.  
  
-   Запустите диспетчер задач и щелкните **Службы** , чтобы получить идентификатор процесса (PID) **MSOLAP$InstanceName**.  
  
-   Запустите **netstat –ao –p TCP** из командной строки, чтобы просмотреть сведения TCP-порта для этого идентификатора PID.  
  
-   Проверьте порт с помощью SQL Server Management Studio и подключитесь к серверу служб Analysis Services в следующем формате: \<IP-адрес >:\<номер_порта >.  
  
 Хотя приложение может прослушивать указанный порт, подключения будут неудачными, если брандмауэр блокирует доступ. Для подключений к экземпляру служб Analysis Services необходимо разблокировать доступ к файлу msmdsrv.exe или фиксированному порту в брандмауэре, по которому ведется прослушивание. Остальные подразделы в этом разделе содержат соответствующие инструкции.  
  
 Чтобы выяснить, были ли параметры брандмауэра для служб Analysis Services определены ранее, используйте брандмауэр Windows в режиме повышенной безопасности на панели управления. На странице «Брандмауэр» в папке «Мониторинг» показан полный список правил, определенный для локального сервера.  
  
 Обратите внимание, что для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]все правила брандмауэра необходимо задавать вручную. Хотя службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и обозреватель SQL Server резервируют порты 2382 и 2383, ни программа установки SQL Server, ни одно из средств настройки не определяет правила брандмауэра, которые разрешают доступ к портам или исполняемым файлам программы.  
  
##  <a name="bkmk_default"></a> Настройка брандмауэра Windows для экземпляра по умолчанию служб Analysis Services  
 Экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] по умолчанию прослушивает TCP-порт 2383. Если установлен экземпляр по умолчанию и требуется использовать этот порт, то необходимо лишь разблокировать входящий доступ к TCP-порту 2383 в брандмауэре Windows, чтобы разрешить удаленный доступ к экземпляру по умолчанию служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Если установлен экземпляр по умолчанию и необходимо настроить службу для прослушивания фиксированного порта, см. подраздел [Использовать фиксированный порт для именованного экземпляра или экземпляра по умолчанию служб Analysis Services](#bkmk_fixed) в данном разделе.  
  
 Чтобы определить, выполняется ли служба как экземпляр по умолчанию (MSSQLServerOLAPService), проверьте имя службы в диспетчере конфигурации SQL Server. Экземпляр служб Analysis Services по умолчанию всегда указывается как **Службы SQL Server Analysis Services (MSSQLSERVER)**.  
  
> [!NOTE]  
>  В различных операционных системах Windows имеются различные средства для настройки брандмауэра Windows. В большинстве из этих средств можно выбирать между открытием определенного порта или исполняемого файла программы. Если нет особой причины указать исполняемый файл программы, рекомендуется указать порт.  
  
 При указании правила входящего подключения следует применять соглашение об именах, с помощью которого можно будет без труда находить правила впоследствии (например, **службы SQL Server Analysis Services (TCP-in) 2383**).  
  
#### <a name="windows-firewall-with-advanced-security"></a>Брандмауэр Windows в режиме повышенной безопасности  
  
1.  В Windows 7 или в Windows Vista на панели управления выберите раздел **Система и безопасность**, затем **Брандмауэр Windows**и **Расширенные параметры**. В Windows Server 2008 и в Windows Server 2008 R2 откройте меню "Администрирование" и выберите пункт **Брандмауэр Windows в режиме повышенной безопасности**. В Windows Server 2012 откройте страницу "Приложения" и введите **Брандмауэр Windows**.  
  
2.  Щелкните правой кнопкой мыши **Правила для входящих подключений** и выберите **Создать правило**.  
  
3.  В поле "Тип правила" выберите значение **Порт** и нажмите кнопку **Далее**.  
  
4.  В диалоговом окне "Протокол и порты" выберите протокол **TCP** и введите номер порта **2383** в поле **Определенные локальные порты**.  
  
5.  В поле "Действие" выберите значение **Разрешить соединение** и нажмите кнопку **Далее**.  
  
6.  В поле "Профиль" уберите все сетевые расположения, не применимые к текущему развертыванию, и нажмите кнопку **Далее**.  
  
7.  В поле "Имя" введите описательное имя этого правила (например, службы **SQL Server Analysis Services (tcp-in) 2383**) и нажмите кнопку **Готово**.  
  
8.  Чтобы проверить, разрешены ли удаленные соединения, откройте среду SQL Server Management Studio или Excel на другом компьютере и подключитесь к службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , указав сетевое имя сервера в поле **Имя сервера**.  
  
    > [!NOTE]  
    >  Другие пользователи не будут иметь доступа к этому серверу, пока им не будут предоставлены разрешения. Дополнительные сведения см. в разделе [Предоставление доступа к объектам и операциям (Analysis Services)](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md).  
  
#### <a name="netsh-advfirewall-syntax"></a>Синтаксис Netsh AdvFirewall  
  
-   Следующая команда создает правило входящего подключения, которое разрешает входящие запросы для порта TCP 2383.  
  
    ```  
    netsh advfirewall firewall add rule name="SQL Server Analysis Services inbound on TCP 2383" dir=in action=allow protocol=TCP localport=2383 profile=domain  
    ```  
  
##  <a name="bkmk_named"></a> Настройка доступа в брандмауэре Windows для именованного экземпляра служб Analysis Services  
 Именованные экземпляры служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] могут прослушивать либо указанный фиксированный порт, либо динамически назначаемый порт, при этом служба обозревателя SQL Server предоставляет сведения о соединении, используемом службой на момент соединения.  
  
 Служба обозревателя SQL Server прослушивает TCP-порт 2382. Протокол UDP не используется. TCP — единственный протокол передачи, используемый службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Чтобы разрешить удаленный доступ к именованному экземпляру служб Analysis Services, выберите один из следующих методов:  
  
-   Используйте динамическое назначение порта и службу обозревателя SQL Server. Разблокируйте порт, используемый службой обозревателя SQL Server, в брандмауэре Windows. Подключиться к серверу в следующем формате: \<имя_сервера >\\< имя_экземпляра\>.  
  
-   Используйте совместно фиксированный порт и службу обозревателя SQL Server. Такой подход позволяет подключиться, используя следующий формат: \<имя_сервера >\\< имя_экземпляра\>идентичное к динамическим назначением порта, за исключением того, что в этом случае сервер прослушивает фиксированный порт. В этом варианте служба обозревателя SQL Server обеспечивает разрешение имен для экземпляра служб Analysis Services, прослушивающего фиксированный порт. Для использования этого метода настройте сервер на прослушивание фиксированного порта, разблокируйте доступ к этому порту и разблокируйте доступ к порту, используемому службой обозревателя SQL Server.  
  
 Служба обозревателя SQL Server используется только с именованными экземплярами, с экземпляром по умолчанию она не используется никогда. Эта служба автоматически устанавливается и включается при установке любого компонента SQL Server в качестве именованного экземпляра. Если выбран метод, для которого требуется служба обозревателя SQL Server, необходимо следить за тем, чтобы она оставалась включенной и запускалась на сервере.  
  
 Если использовать службу обозревателя SQL Server невозможно, необходимо назначить фиксированный порт в строке подключения, минуя разрешение имени домена. Если служба обозревателя SQL Server не используется, то в строке подключения всех клиентских соединений должен указываться номер порта (например, AW-SRV01:54321).  
  
 **Вариант 1: используйте динамическое назначение порта и разблокируйте доступ к службе браузера SQL Server.**  
  
 Динамическое назначение портов для именованных экземпляров служб Analysis Services выполняется с помощью **MSOLAP$InstanceName** при запуске службы. По умолчанию служба требует первый обнаруженный доступный номер порта, используя различные номера портов при каждом перезапуске службы.  
  
 Разрешение имени экземпляра обеспечивается службой обозревателя SQL Server. Разблокирование TCP-порта 2382 для службы обозревателя SQL Server всегда необходимо, если для именованного экземпляра используется динамическое назначение порта.  
  
> [!NOTE]  
>  Служба обозревателя SQL Server прослушивает как порт UDP 1434, так и порт TCP 2382 для компонента Database Engine и служб Analysis Services соответственно. Даже если порт UDP 1434 уже разблокирован для службы обозревателя SQL Server, необходимо разблокировать порт TCP 2382 для служб Analysis Services.  
  
#### <a name="windows-firewall-with-advanced-security"></a>Брандмауэр Windows в режиме повышенной безопасности  
  
1.  В Windows 7 или в Windows Vista на панели управления выберите раздел **Система и безопасность**, затем **Брандмауэр Windows**и **Расширенные параметры**. В Windows Server 2008 и в Windows Server 2008 R2 откройте меню "Администрирование" и выберите пункт **Брандмауэр Windows в режиме повышенной безопасности**. В Windows Server 2012 откройте страницу "Приложения" и введите **Брандмауэр Windows**.  
  
2.  Чтобы разблокировать доступ к службе обозревателя SQL Server, щелкните правой кнопкой мыши **Правила для входящих подключений** и выберите **Создать правило**.  
  
3.  В поле "Тип правила" выберите значение **Порт** и нажмите кнопку **Далее**.  
  
4.  В диалоговом окне "Протокол и порты" выберите протокол **TCP** и введите номер порта **2382** в поле **Определенные локальные порты**.  
  
5.  В поле "Действие" выберите значение **Разрешить соединение** и нажмите кнопку **Далее**.  
  
6.  В поле "Профиль" уберите все сетевые расположения, не применимые к текущему развертыванию, и нажмите кнопку **Далее**.  
  
7.  В поле "Имя" введите описательное имя этого правила (например, **обозреватель SQL Server (tcp-in) 2382**) и нажмите кнопку **Готово**.  
  
8.  Чтобы убедиться, что разрешены удаленные подключения, откройте среду SQL Server Management Studio или Excel на другом компьютере и подключитесь к службам Analysis Services, указав сетевое имя сервера и имя экземпляра в следующем формате: \<имя_сервера > \\< имя_экземпляра\>. Например, на сервере с именем **AW-SRV01** и именованным экземпляром **Finance**именем сервера будет **AW-SRV01\Finance**.  
  
 **Вариант 2: используйте фиксированный порт для именованного экземпляра.**  
  
 В качестве альтернативы можно назначить фиксированный порт, а затем разблокировать доступ к этому порту. Этот метод обеспечивает лучшие возможности аудита, чем те, которые доступны при разрешении доступа к исполняемому файлу программы. По этой причине использование фиксированного порта — рекомендуемый метод для доступа к любому экземпляру служб Analysis Services.  
  
 Чтобы назначить фиксированный порт, следуйте инструкциям в подразделе [Использовать фиксированный порт для именованного экземпляра или экземпляра по умолчанию служб Analysis Services](#bkmk_fixed) этого раздела, затем вернитесь к этому подразделу, чтобы разблокировать порт.  
  
#### <a name="windows-firewall-with-advanced-security"></a>Брандмауэр Windows в режиме повышенной безопасности  
  
1.  В Windows 7 или в Windows Vista на панели управления выберите раздел **Система и безопасность**, затем **Брандмауэр Windows**и **Расширенные параметры**. В Windows Server 2008 и в Windows Server 2008 R2 откройте меню "Администрирование" и выберите пункт **Брандмауэр Windows в режиме повышенной безопасности**. В Windows Server 2012 откройте страницу "Приложения" и введите **Брандмауэр Windows**.  
  
2.  Чтобы разблокировать доступ к службам Analysis Services, щелкните правой кнопкой мыши **Правила для входящих подключений** и выберите **Создать правило**.  
  
3.  В поле "Тип правила" выберите значение **Порт** и нажмите кнопку **Далее**.  
  
4.  В диалоговом окне "Протокол и порты" выберите протокол **TCP** и введите фиксированный порт в поле **Определенные локальные порты**.  
  
5.  В поле "Действие" выберите значение **Разрешить соединение** и нажмите кнопку **Далее**.  
  
6.  В поле "Профиль" уберите все сетевые расположения, не применимые к текущему развертыванию, и нажмите кнопку **Далее**.  
  
7.  В поле "Имя" введите описательное имя этого правила (например, **SQL Server Analysis Services через порт 54321**) и нажмите кнопку **Готово**.  
  
8.  Чтобы убедиться, что разрешены удаленные подключения, откройте среду SQL Server Management Studio или Excel на другом компьютере и подключитесь к Analysis Services, указав сетевое имя сервера и номер порта в следующем формате: \<имя_сервера >: \<номер_порта >.  
  
#### <a name="netsh-advfirewall-syntax"></a>Синтаксис Netsh AdvFirewall  
  
-   Следующие команды создают правила для входящих подключений, которые разблокируют TCP-порт 2382 для службы обозревателя SQL Server и фиксированный порт, указанный для экземпляра служб Analysis Services. Можно выполнить любую из этих команд, чтобы разрешить доступ к именованному экземпляру служб Analysis Services.  
  
     В этом образце команды порт 54321 фиксированный. Обязательно замените его на действительный порт, используемый в вашей системе.  
  
    ```  
    netsh advfirewall firewall add rule name="SQL Server Analysis Services (tcp-in) on 54321" dir=in action=allow protocol=TCP localport=54321 profile=domain  
    ```  
  
    ```  
    netsh advfirewall firewall add rule name="SQL Server Browser Services inbound on TCP 2382" dir=in action=allow protocol=TCP localport=2382 profile=domain  
    ```  
  
##  <a name="bkmk_fixed"></a> Использовать фиксированный порт для именованного экземпляра или экземпляра по умолчанию служб Analysis Services  
 В этом разделе объясняется, как настроить службы Analysis Services для прослушивания фиксированного порта. Фиксированный порт обычно используется, если службы Analysis Services установлены как именованный экземпляр, но к этому методу можно также прибегнуть, если требования бизнеса или безопасности указывают, что не следует использовать порты по умолчанию.  
  
 Обратите внимание, что при использовании фиксированного порта изменяется синтаксис соединения для экземпляра по умолчанию: необходимо добавить номер порта к имени сервера. Например, при подключении к локальному, используемому по умолчанию экземпляру служб Analysis Services, прослушивающему порт 54321 в среде SQL Server Management Studio, потребуется ввести «localhost:54321» в качестве имени сервера в диалоговом окне «Соединение с сервером» в среде Management Studio.  
  
 При использовании именованного экземпляра, можно назначить фиксированный порт, не изменяя способ указания имени сервера (в частности, можно использовать \<servername\instancename > для подключения к именованному экземпляру, на прослушивание фиксированного порта). Это применимо, только если служба обозревателя SQL Server работает, а порт, который она прослушивает, разблокирован. Служба обозревателя SQL Server будет обеспечивать перенаправление на фиксированный порт, на основе \<имя_сервера\имя_экземпляра >. Если открыты порты как для службы обозревателя SQL Server, так и для именованного экземпляра Analysis Services, прослушивающего фиксированный порт, служба обозревателя SQL Server разрешит соединение с именованным экземпляром.  
  
1.  Определите доступный порт TCP/IP, который можно использовать.  
  
     Список зарезервированных и зарегистрированных портов, которые не следует использовать, см. в разделе [Номера портов (IANA)](http://go.microsoft.com/fwlink/?LinkID=198469). Для просмотра списка TCP-портов, которые уже используются в системе, откройте окно командной строки и введите **netstat –a –p TCP** .  
  
2.  После выбора порта укажите его, изменив настройку конфигурации **Port** в файле msmdsrv.ini. Указать порт можно также на странице "Общие свойства" экземпляра служб Analysis Services в среде SQL Server Management Studio.  
  
3.  Перезапустите службу.  
  
4.  Настройте в брандмауэре Windows разблокировку выбранного порта TCP. Или, если для именованного экземпляра используется фиксированный порт, разблокируйте TCP-порт, указанный для этого экземпляра, и TCP-порт 2382 для службы обозревателя SQL Server.  
  
5.  Выполните проверку, подключившись локально (в среде Management Studio), а затем удаленно из клиентского приложения на другом компьютере. В среде Management Studio, подключитесь к экземпляру по умолчанию службы Analysis Services, указав имя сервера в следующем формате: \<имя_сервера >:\<номер_порта >. Для именованного экземпляра укажите имя сервера как \<имя_сервера >\\< имя_экземпляра\>.  
  
##  <a name="bkmk_cluster"></a> Настройка порта для кластера служб Analysis Services  
 Отказоустойчивый кластер служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] всегда прослушивает TCP-порт 2383 независимо от того, установлен ли он как экземпляр по умолчанию или именованный экземпляр. После установки в отказоустойчивый кластер Windows службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не используют динамическое назначение портов. Необходимо открыть TCP-порт 2383 на каждом узле кластера, на котором работают службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения о кластеризации служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]см. в разделе [Кластеризация служб SQL Server Analysis Services](http://go.microsoft.com/fwlink/p/?LinkId=396548).  
  
##  <a name="bkmk_powerpivot"></a> Настройка порта PowerPivot для SharePoint  
 Архитектура сервера для [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] существенно различается в зависимости от используемой версии SharePoint.  
  
 **SharePoint 2013**  
  
 В SharePoint 2013 службы Excel перенаправляют запросы к модели данных Power Pivot, которые будут загружены в экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] за пределами среды SharePoint. Соединения устанавливаются стандартным образом, когда клиентская библиотека служб Analysis Services на локальном компьютере отправляет запрос удаленному экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в той же сети.  
  
 Так как [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] всегда устанавливает службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] как именованный экземпляр, необходимо помнить о наличии службы обозревателя SQL Server и использовании динамического назначения портов. Как упоминалось ранее, служба обозревателя SQL Server прослушивает TCP-порт 2382 для определения запросов на подключение, отправляемых к именованным экземплярам служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , и перенаправляет их на текущий порт.  
  
 Обратите внимание, что службы Excel в SharePoint 2013 не поддерживают синтаксис соединения с фиксированным портом, поэтому удостоверьтесь в том, что служба обозревателя SQL Server доступна.  
  
 **SharePoint 2010**  
  
 При использовании SharePoint 2010 открывать порты в брандмауэре Windows не нужно. SharePoint открывает необходимые порты и такие надстройки, как [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, которые работают в пределах среды SharePoint. В установке [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint 2010 системная служба [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] имеет монопольное право на использование локального экземпляра служб SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]), установленного на том же компьютере. Используются локальные, но не сетевые подключения для доступа к локальному модулю служб Analysis Services, который загружает данные, выполняет запросы и обрабатывает данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на сервере SharePoint. Для получения данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] из клиентских приложений запросы направляются через порты, открытые программой установки SharePoint (в частности, определяются правила для входящих подключений при доступе к SharePoint — 80, центру администрирования SharePoint версии 4, веб-службам SharePoint и SPUserCodeV4). Веб-службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] выполняются в пределах фермы SharePoint, поэтому правил брандмауэра SharePoint достаточно для удаленного доступа к данным [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме SharePoint.  
  
## <a name="see-also"></a>См. также  
 [Служба обозревателя SQL Server (ядро СУБД и SSAS)](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md)   
 [Запуск, остановка, приостановка, возобновление и перезапуск ядра СУБД, агента SQL Server и обозревателя SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)   
 [Настройка брандмауэра Windows для доступа к компоненту Database Engine](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
  
