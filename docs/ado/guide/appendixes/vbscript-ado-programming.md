---
title: "Программирование ADO VBScript | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ADO, VBScript
- VBScript [ADO]
ms.assetid: 6aaaf6d0-1376-4473-bea6-b81f2645a9ac
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f725eec0027d1c06715b72785a1fe06a4fa4cedb
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="vbscript-ado-programming"></a>Программирование ADO VBScript
## <a name="creating-an-ado-project"></a>Создание проекта ADO  
 Microsoft Visual Basic, Scripting Edition не поддерживает библиотеки типов, поэтому вам не нужно ссылке ADO в проекте. Следовательно не связанные функции, такие как завершение командной строки поддерживаются. Кроме того по умолчанию ADO перечисляемые константы не определены в VBScript.  
  
 Тем не менее ADO предоставляет с двумя включить файлы, содержащие следующие определения для использования с VBScript.  
  
-   Для использования сценариев на стороне сервера Adovbs.inc, который устанавливается в папку c:\Program Files\Common Files\System\ado\ по умолчанию.  
  
-   Для использования сценариев на стороне клиента Adcvbs.inc, который устанавливается в папку c:\Program Files\Common Files\System\msdac\ по умолчанию.  
  
 Можно либо скопировать и вставить определения констант из этих файлов в ASP-страниц или, при выполнении скриптов на стороне сервера, скопируйте файл Adovbs.inc в папку на веб-сайте и ссылки на его со страницы ASP следующим образом:  
  
```  
<!--#include File="adovbs.inc"-->  
```  
  
## <a name="creating-ado-objects-in-vbscript"></a>Создание объектов ADO в VBScript  
 Нельзя использовать **Dim** инструкцию, чтобы назначить объекты определенного типа на языке VBScript. Кроме того, не поддерживает VBScript **New** синтаксисом, используемым с **Dim** инструкции на языке Visual Basic для приложений. Вместо этого необходимо использовать **CreateObject** вызов функции:  
  
```  
Dim Rs1  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
```  
  
## <a name="vbscript-examples"></a>Примеры VBScript  
 Ниже приведен общий пример программирования на стороне сервера VBScript в файле активные страницы сервера (ASP):  
  
```  
<%  @LANGUAGE="VBSCRIPT" %>  
<%  Option Explicit %>  
<!--#include File="adovbs.inc"-->  
<HTML>  
    <BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
  
    <!-- Your ASP Code goes here -->  
<%  
Dim Source  
Dim Connect  
Dim Rs1  
  
Source = "SELECT * FROM Authors"  
Connect = "Provider=sqloledb;Data Source=srv;" & _  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
Rs1.Open Source, Connect, adOpenForwardOnly  
Response.Write("Success!")  
%>  
    </BODY>  
</HTML>  
```  
  
 Подробные примеры VBScript входят в состав документации по ADO. Дополнительные сведения см. в разделе [примеры кода ADO в Visual Basic Scripting Edition](../../../ado/reference/ado-api/ado-code-examples-vbscript.md).  
  
## <a name="differences-between-vbscript-and-visual-basic"></a>Различия между VBScript и Visual Basic  
 Использование ADO с VBScript аналогична использованию ADO в Visual Basic различными способами, в том числе использование синтаксиса. Однако существуют значительные различия:  
  
-   VBScript поддерживает только вариант тип данных, который может содержать разные типы данных. Необходимых данных можно хранить в тип данных Variant, и данные будут работать неправильно из-за приведения, выполненных VBScript. Распознает необходимый ADO и соответствующим образом преобразует значение в тип Variant.  
  
-   Нельзя использовать **на ошибки goto \<label >** в VBScript.  
  
-   VBScript поддерживает некоторые встроенные функции Visual Basic, такие как **Msgbox**, **даты**, и **IsNumeric**. Тем не менее так как VBScript является подмножеством Visual Basic, поддерживаются не все встроенные функции. Например, VBScript не поддерживает **формат** функции и функций файлового ввода-вывода.
