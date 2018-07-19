---
title: Основные сведения о политиках безопасности | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- code access security [Reporting Services], security policies
- Execution permission set
- custom assemblies [Reporting Services], security
- permission sets [Reporting Services]
- expressions [Reporting Services], security
- evidence [Reporting Services]
- FullTrust permission set
- security policies [Reporting Services]
- named permission sets [Reporting Services]
ms.assetid: a9bf043a-139a-4929-9a58-244815323df0
caps.latest.revision: 31
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: de381c37c5ee461c3e7a813c524e317b3d93e348
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37188081"
---
# <a name="understanding-security-policies"></a>Основные сведения о политиках безопасности
  Любой код, выполняемый сервером отчетов, должен быть частью конкретной политики управления доступом для кода. Такие политики безопасности состоят из групп кода, которые сопоставляют свидетельство с множеством именованных наборов разрешений. Группы кода часто бывают связаны с именованным набором разрешений, который задает допустимые разрешения для кода в этой группе. Во время выполнения используется удостоверение, предоставленное доверенным узлом или загрузчиком, для определения того, к какой группе принадлежит код и какие разрешения с учетом этого должны быть предоставлены коду. Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] придерживаются этой архитектуры политики безопасности, определенной средой CLR платформы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. В следующих разделах приведено описание различных типов кода в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и связанных с ними правил политики.  
  
## <a name="report-server-assemblies"></a>Сборки сервера отчетов  
 Сборки сервера отчетов представляют собой сборки, которые содержат код, являющийся частью продукта служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] написаны с помощью сборок управляемого кода; все эти сборки имеют строгие имена (подписанные цифровой подписью). Группы кода для этих сборок определены с использованием условия **StrongNameMembershipCondition**, которое предоставляет свидетельство на основе информации открытого ключа для строгого имени сборки. Группе кода предоставляется набор разрешений **FullTrust**.  
  
## <a name="report-server-extensions-rendering-data-delivery-and-security"></a>Модули сервера отчетов (модули подготовки к просмотру, обработки данных, доставки и безопасности)  
 Модули сервера отчетов представляют собой пользовательские модули обработки данных, доставки, подготовки к просмотру и безопасности, создаваемые для расширения функциональных возможностей служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Необходимо предоставить разрешения **FullTrust** этим модулям или коду сборки в файлах конфигурации политики, связанных с компонентом служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], для которого создается модуль. Модули, поставляемые в составе служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], подписываются открытым ключом сервера отчетов и получают набор разрешений **FullTrust**.  
  
> [!IMPORTANT]  
>  Необходимо внести изменения в файлы конфигурации политики служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], чтобы обеспечить предоставление разрешений **FullTrust** для любых сторонних модулей. Если для пользовательских модулей не добавлена группа кода с разрешениями **FullTrust**, то эти модули не могут использоваться сервером отчетов.  
  
 Дополнительные сведения о файлах конфигурации политик в [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] см. в разделе [Использование файлов политики безопасности служб Reporting Services](using-reporting-services-security-policy-files.md).  
  
## <a name="expressions-used-in-reports"></a>Выражения, используемые в отчетах  
 Выражения отчетов представляют собой встроенные выражения кода или определяемые пользователем методы, содержащиеся в элементе **Code** файла языка определения отчетов. В файлах политики уже настроена конфигурация одной группы кода, которая предоставляет этим выражениям набор разрешений **Execution** по умолчанию. Эта группа кода выглядит примерно так:  
  
```  
<CodeGroup  
   class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="Execution"  
   Name="Report_Expressions_Default_Permissions"  
   Description="This code group grants default permissions for code in report expressions and Code element. ">  
    <IMembershipCondition  
       class="StrongNameMembershipCondition"  
       version="1"  
       PublicKeyBlob="002400..."  
    />  
</CodeGroup>  
```  
  
 Разрешение **Execution** позволяет выполнять код, но не использовать защищенные ресурсы. Все выражения, находящиеся в отчете, компилируются в сборку (называемую сборкой «хранилища выражений»), которая хранится в составе откомпилированного отчета. После вызова отчета на выполнение сервер отчетов загружает хранилище сборки выражений и преобразует вызовы, обращенные к этой сборке, в выполняемые выражения. Сборки хранилища выражений подписываются конкретным ключом, с помощью которого определяется группа кода для всех хранилищ выражений.  
  
 Выражения отчета ссылаются на коллекции объектной модели отчета (поля, параметры и т. д.) и выполняют такие простые задачи, как арифметические и строковые операции. Для кода, в котором осуществляются эти простые операции, требуется только разрешение **Execution**. По умолчанию определяемым пользователем методам в элементе **Code** и во всех пользовательских сборках предоставлено разрешение **Execution** в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Таким образом, применительно к большинству выражений текущая конфигурация не требует внесения изменений в какие-либо файлы политики безопасности. Чтобы предоставить дополнительные разрешения сборкам хранилищ выражений, администратор должен изменить файлы конфигурации политики сервера отчетов и конструктора отчетов, а также сменить группу кода выражений отчета. Такая настройка является глобальной, поэтому изменение заданных по умолчанию разрешений для хранилищ выражений затрагивает все отчеты. По этой причине, настоятельно рекомендуется помещать весь код, для которого требуется дополнительное обеспечение безопасности, в пользовательскую сборку. Только этой сборке будут предоставлены необходимые разрешения.  
  
> [!IMPORTANT]  
>  Код, предназначенный для использования в отчетах, в котором вызываются внешние сборки или защищенные ресурсы, должен быть включен в пользовательскую сборку. Это позволяет получить больший контроль над разрешениями, запрашиваемыми и подтверждаемыми в коде. Не следует выполнять вызовы защищенных методов в элементе **Code**. Для этого необходимо предоставить разрешения **FullTrust** хранилищу выражений отчета и обеспечить полный доступ к среде CLR для всего пользовательского кода.  
  
> [!CAUTION]  
>  Не предоставляйте разрешения **FullTrust** группе кода для хранилища выражений отчета. Сделав это, вы разрешите выполнять защищенные системные вызовы во всех выражениях отчета.  
  
## <a name="custom-assemblies-referenced-in-reports"></a>Пользовательские сборки, ссылаемые в отчетах  
 В некоторых выражениях отчета могут вызываться сборки кода сторонних разработчиков, известные также как пользовательские сборки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Сервер отчетов предполагает, что для этих сборок в файлах конфигурации политики имеется, по крайней мере, разрешение **Execution**. По умолчанию файлы политики, входящие в поставку служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], предоставляют разрешение **Execution** всем сборкам, начиная с зоны "Мой компьютер". Пользовательским сборкам по мере необходимости можно предоставлять дополнительные разрешения.  
  
 В некоторых случаях возникает необходимость выполнить операцию, для которой требуется конкретное разрешение кода в выражении отчета. Как правило, это означает, что в выражении отчета должен быть выполнен вызов защищенного метода библиотеки CLR (наподобие того, который получает доступ к файлам или системному реестру). В документации [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] приведено описание разрешений кода, необходимых для выполнения такого безопасного вызова; чтобы в вызывающем коде можно было выполнить подобный вызов, необходимо предоставить эти конкретные, безопасные разрешения. Если вызов выполняется из выражения отчета или элемента **Code**, то хранилищу сборки выражений нужно предоставить соответствующие разрешения. Но сразу после предоставления этих разрешений хранилищу выражений весь код, выполняемый в любом выражении любого отчета, получает такие же конкретные разрешения. Намного безопаснее осуществлять вызов из пользовательской сборки и предоставлять конкретные разрешения этой пользовательской сборке.  
  
## <a name="see-also"></a>См. также  
 [Управление доступом для кода в службах Reporting Services](code-access-security-in-reporting-services.md)   
 [Разработка безопасных приложений (службы Reporting Services)](secure-development-reporting-services.md)  
  
  