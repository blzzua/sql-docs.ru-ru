---
title: "Расширение вывода ошибок с помощью компонента скрипта | Документы Майкрософт"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-data-flow-script-component-examples
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ff54224860771a8cbb4c21d6262558519dd771be
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="enhancing-an-error-output-with-the-script-component"></a>Расширение вывода ошибок с помощью компонента скрипта
  По умолчанию два дополнительных столбца в выводе ошибок служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ErrorCode и ErrorColumn, содержат только числовые коды, представляющие номер ошибки и идентификатор столбца, в котором произошла ошибка. Эти числовые значения могут быть малополезны без соответствующего описания ошибки и имени столбца.  
  
 В этом разделе описывается, как добавить имя столбца и описание ошибки к существующим выходным данным ошибок в потоке данных с помощью компонента скрипта. В следующем примере с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, доступ к которому можно получить через свойство <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> компонента скрипта, добавляется описание ошибки, соответствующее конкретному стандартному коду ошибки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Затем в примере с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData130.GetIdentificationStringByID%2A> того же интерфейса добавляется имя столбца, соответствующее зарегистрированному идентификатору журнала обращений и преобразований.  
  
> [!NOTE]  
>  Если нужно создать компонент, который будет полезен в нескольких задачах потока данных и нескольких пакетах, рекомендуется в качестве основы использовать этот образец компонента скрипта. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Пример  
 В приведенном примере компонент скрипта, настроенный в качестве преобразования, используется для добавления имени столбца и описания ошибки к существующим выходным данным ошибок в потоке данных.  
  
 Дополнительные сведения о том, как настроить компонент скрипта для использования в качестве преобразования в потоке данных см. в разделах [Создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) и [Создание асинхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Настройка этого примера компонента скрипта  
  
1.  Перед созданием нового компонента скрипта настройте вышестоящий компонент в потоке данных для перенаправления строк в его вывод ошибок при возникновении ошибки или усечения. В целях тестирования, возможно, следует настроить компонент таким образом, чтобы гарантировать возникновение ошибок, — например, настроив преобразование «Уточняющий запрос» между двумя таблицами, в котором уточняющий запрос непременно приведет к ошибке.  
  
2.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве преобразования.  
  
3.  Соедините вывод ошибок вышестоящего компонента с новым компонентом скрипта.  
  
4.  Откройте **Редактор преобразования "Скрипт"** и на странице **Скрипт** для свойства **ScriptLanguage** выберите язык скрипта.  
  
5.  Нажмите кнопку **Изменить скрипт**, чтобы открыть интегрированную среду разработки средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSTA), и добавьте приведенный ниже пример кода.  
  
6.  Закройте среду VSTA.  
  
7.  В редакторе преобразования "Скрипт" на странице **Входные столбцы** выберите столбцы ErrorCode и ErrorColumn.  
  
8.  На странице **Входы и выходы** добавьте два новых столбца.  
  
    -   Добавьте новый выходной столбец типа **String** с именем **ErrorDescription**. Увеличьте длину нового столбца по умолчанию до 255 для поддержки длинных сообщений.  
  
    -   Добавьте еще один новый выходной столбец типа **String** с именем **ColumnName**. Увеличьте длину нового столбца по умолчанию до 255 для поддержки длинных значений.  
  
9. Закройте **редактор преобразования "Скрипт"**.  
  
10. Соедините выход компонента скрипта с подходящим назначением. Назначение «Неструктурированный файл» проще всего при настройке в случае нерегламентированной отладки.  
  
11. Запустите пакет.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
      Row.ErrorDescription = _  
        Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
      Dim componentMetaData130 = TryCast(Me.ComponentMetaData, IDTSComponentMetaData130)  
      If componentMetaData130 IsNot Nothing Then  
        Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn)  
         End If  
  
    End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
{  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
      Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
      var componentMetaData130 = this.ComponentMetaData as IDTSComponentMetaData130;  
      if (componentMetaData130 != null)  
        {  
            Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn);  
        }  
  
    }  
}  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок в данных](../../integration-services/data-flow/error-handling-in-data.md)   
 [Использование выводов ошибок в компоненте потока данных](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
  
  
