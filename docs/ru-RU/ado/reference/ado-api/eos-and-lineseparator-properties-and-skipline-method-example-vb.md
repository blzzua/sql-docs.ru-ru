---
title: Электрической ПЕРЕГРУЗКИ LineSeparator свойства и пример метода SkipLine (VB) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- LineSeparator property [ADO], Visual Basic example
- Skipline method [ADO], Visual Basic example
- EOS property [ADO], Visual Basic example
ms.assetid: 77ce3042-9ebc-44ba-a4ff-0f1b1fd4a9c4
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91216e314108febc7231c16235c02bb723b875b8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="eos-and-lineseparator-properties-and-skipline-method-example-vb"></a>Электрической ПЕРЕГРУЗКИ LineSeparator свойства и пример метода SkipLine (Visual Basic)
В этом примере показано, как управлять текстового потоки по одной строке за раз. Эффект от изменения разделителя строк из возврата и перевода каретки по умолчанию (**adCRLF**) для просто перевода строки (**adLF**) или символ возврата каретки (**adCR**) отображается.  
  
```  
'BeginSkipLineVB  
Private Sub cmdSkipLine_Click()  
    On Error GoTo ErrorHandler  
  
    'Declare variables  
    Dim i As Integer  
    Dim objStream As Stream  
    Dim strLine, strChar As String  
  
    'Instantiate and open stream  
    Set objStream = New Stream  
    objStream.Open  
  
    'Set line separator to line feed  
    objStream.LineSeparator = adLF  
  
    'Load text content of list box into stream  
    'One line at a time  
    For i = 0 To (List1.ListCount - 1)  
        objStream.WriteText List1.List(i), adWriteLine  
    Next  
  
    'Display the entire stream  
    Debug.Print "Whole Stream:"  
    objStream.Position = 0  
    Debug.Print objStream.ReadText  
  
    'Display the first line  
    Debug.Print "First Line:"  
    objStream.Position = 0  
    strLine = objStream.ReadText(adReadLine)  
    Debug.Print strLine  
    Debug.Print "Line length: " + Str(Len(strLine))  
  
    'Skip a line, then display another line  
    Debug.Print "Third Line:"  
    objStream.SkipLine  
    strLine = objStream.ReadText(adReadLine)  
    Debug.Print strLine  
    Debug.Print "Line length: " + Str(Len(strLine))  
  
    'Switch line separator to carriage return  
    'All items from list will be considered one line  
    'Assuming no CRs have been loaded into stream  
    Debug.Print "Whole Stream/First Line:"  
    objStream.Position = 0  
    objStream.LineSeparator = adCR  
    strLine = objStream.ReadText(adReadLine)  
    Debug.Print strLine  
    Debug.Print "Line length: " + Str(Len(strLine))  
    Debug.Print "Stream size: " + Str(objStream.Size)  
  
    'Use EOS to Determine End of Stream  
    Debug.Print "Character by character:"  
    objStream.Position = 0  
    Do Until objStream.EOS  
        strChar = objStream.ReadText(1)  
        Debug.Print strChar  
    Loop  
  
    ' clean up  
    objStream.Close  
    Set objStream = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not objStream Is Nothing Then  
        If objStream.State = adStateOpen Then objStream.Close  
    End If  
    Set objStream = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
  
Private Sub Form_Load()  
    List1.AddItem "This is the first line"  
    List1.AddItem "This is the second line"  
    List1.AddItem "This is the third line"  
End Sub  
'EndSkipLineVB  
```  
  
## <a name="see-also"></a>См. также  
 [Свойство электрической ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md)   
 [Свойство LineSeparator (ADO)](../../../ado/reference/ado-api/lineseparator-property-ado.md)   
 [Метод SkipLine](../../../ado/reference/ado-api/skipline-method.md)