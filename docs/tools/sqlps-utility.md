---
title: "Программа sqlps | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sqlps
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
caps.latest.revision: "22"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bd4e67397b52b3e7248ce061312517841eef38e5
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="sqlps-utility"></a>программа sqlps
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]**Sqlps** служебная программа запускает сеанс Windows PowerShell с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] командлеты и поставщика PowerShell загружена и зарегистрирована. Можно вводить команды или скрипты PowerShell, в которых используются компоненты [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell для работы с экземплярами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и их объектами.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]Используйте **sqlps** модуль PowerShell вместо него. Дополнительные сведения о модуле **sqlps** см. в разделе [Import the SQLPS Module](../relational-databases/scripting/import-the-sqlps-module.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlps   
[ [ [ -NoLogo ][ -NoExit ][ -NoProfile ]  
    [ -OutPutFormat { Text | XML } ] [ -InPutFormat { Text | XML } ]  
  ]  
  [ -Command { -  
             | script_block [ -args argument_array ]  
             | string [ command_parameters ]  
             }  
  ]  
]  
[ -? | -Help ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **-NoLogo**  
 Указывает, что служебная программа **sqlps** не должна отображать баннер со сведениями об авторских правах при запуске.  
  
 **-NoExit**  
 Указывает, что служебная программа **sqlps** должна продолжать выполняться после выполнения команд запуска.  
  
 **-NoProfile**  
 Указывает служебной программе **sqlps** не загружать профиль пользователя. В профилях пользователей записываются часто используемые псевдонимы, функции и переменные для использования в различных сеансах PowerShell.  
  
 **-OutPutFormat** { **Text** | **XML** }  
 Указывает, что выходные данные служебной программы **sqlps** будут отформатированы в виде текстовых строк (**Text**) либо представлены в сериализованном формате CLIXML (**XML**).  
  
 **-InPutFormat** { **Text** | **XML** }  
 Указывает, что входные данные служебной программы **sqlps** отформатированы в виде текстовых строк (**Text**) либо представлены в сериализованном формате CLIXML (**XML**).  
  
 **-Command**  
 Указывает команду для выполнения служебной программой **sqlps** . Служебная программа **sqlps** выполняет команду, а затем завершает работу, если только не указан параметр **-NoExit** . После параметра **-Command**не следует указывать какие-либо иные параметры, так как они будут интерпретироваться как параметры команды.  
  
 **-**  
 **-Command** — указывает, что служебная программа **sqlps** считывает входные данные с помощью стандартного ввода.  
  
 *блок_скрипта* [**- args *** массив_аргументов* ]  
 Указывает блок команд PowerShell для выполнения, который должен быть заключен в фигурные скобки: {}. Параметр*блок_скрипта* можно указывать только в случае вызова служебной программы **sqlps** из **PowerShell** или другого сеанса служебной программы **sqlps** . Параметр *массив_аргументов* представляет собой массив переменных PowerShell, содержащий аргументы для команд PowerShell из параметра *блок_скрипта*.  
  
 *string* [ *параметры_команды* ]  
 Указывает строку, содержащую команды PowerShell для запуска. Используйте формат **«& {***команда***}»**. Кавычки определяют строку, а оператор вызова (&) предписывает служебной программе **sqlps** выполнить команду.  
  
 [ **-?** | **-Help** ]  
 Показывает синтаксис параметров служебной программы **sqlps** .  
  
## <a name="remarks"></a>Remarks  
 Программа **sqlps** запускает среду PowerShell (PowerShell.exe) и загружает модуль [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell. Модуль, также именуемый **sqlps**, загружает и регистрирует следующие оснастки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell:  
  
-   Microsoft.SqlServer.Management.PSProvider.dll  
  
     Реализует поставщик [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell и связанные с ним командлеты, такие как **Encode-SqlName** и **Decode-SqlName**.  
  
-   Microsoft.SqlServer.Management.PSSnapin.dll  
  
     Реализует командлеты **Invoke-Sqlcmd** и **Invoke-PolicyEvaluation** .  
  
 С помощью служебной программы **sqlps** можно делать следующее.  
  
-   Вводить команды PowerShell в интерактивном режиме.  
  
-   Запускать файлы скриптов PowerShell.  
  
-   Запускать командлеты служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Использовать пути поставщика служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для передвижения по иерархии объектов среды служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 По умолчанию служебная программа **sqlps** запускается с политикой выполнения сценариев со значением **Ограничено**. Это предотвращает запуск любых скриптов PowerShell. Командлет **Set-ExecutionPolicy** обеспечивает возможность запуска как подписанных, так и любых других скриптов. Запускать следует только скрипты из надежных источников, а также рекомендуется защитить все входные и выходные файлы соответствующими разрешениями NTFS. Дополнительные сведения о включении скриптов PowerShell см. в разделе [Запуск скриптов Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=103166).  
  
 Версия программы **sqlps** в [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] и [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] была реализована как мини-оболочка Windows PowerShell 1.0. Мини-оболочки имеют определенные ограничения, такие как запрет на загрузку пользователями других оснасток, помимо загруженных мини-оболочкой. Эти ограничения не относятся к [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] и более поздним версиям программы, где изменилось использование модуля **sqlps** .  
  
## <a name="examples"></a>Примеры  
 **А. Запуск программы sqlps в по умолчанию интерактивном режиме без баннер авторских прав**  
  
```  
sqlps -NoLogo  
```  
  
 **Б. Запуск скрипта SQL Server PowerShell из командной строки**  
  
```  
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
 **В. Запуск скрипта SQL Server PowerShell из командной строки с продолжением выполнения после завершения скрипта**  
  
```  
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a>См. также  
 [Включение или отключение сетевого протокола сервера](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)  
  
  
