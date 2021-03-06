---
title: "Запись объекта (ADO) | Документы Microsoft"
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
apitype: COM
f1_keywords:
- Record
helpviewer_keywords:
- Record object [ADO]
ms.assetid: db83ed2c-a8e3-460c-8682-64667e4d5d01
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aa00ab893549eee36bc1d1b0e858c7bc326fb83b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="record-object-ado"></a>Объект записи (ADO)
Представляет строку из [записей](../../../ado/reference/ado-api/recordset-object-ado.md) или поставщик данных или объект, возвращенный поставщиком частично структурированными данными, таких как файл или каталог.  
  
## <a name="remarks"></a>Remarks  
 Объект **запись** представляет одну строку данных и имеет некоторые общие сходства с одной строки **записей**. В зависимости от возможностей вашего поставщика **запись** объектов могут быть возвращены непосредственно от поставщика, а не одной строки **записей**, — например, когда SQL-запрос, который выбирает только одну строку выполнена. Или **запись** объекта можно получить непосредственно из **записей** объекта. Или **записи** могут быть возвращены непосредственно от поставщика в частично структурированные данные, такие как Microsoft Exchange поставщика OLE DB.  
  
 Можно просмотреть поля, связанные с **запись** объекта посредством [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции на **записи** объекта. ADO позволяет столбцов, возвращающих табличные значения объекта и включая **записей**, **SafeArray**и скалярных значений в **поля** коллекцию **записи** объекты.  
  
 Если **запись** представляет строку в **записей**, можно вернуться к, исходное **записей** с [источника](../../../ado/reference/ado-api/source-property-ado-record.md) свойство.  
  
 **Запись** объект также используется поставщиками частично структурированных данных таких как [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md), для моделирования древовидной структурой пространства имен. Каждый узел в дереве является **записи** объект со связанными столбцами. Столбцы могут представлять атрибуты этого узла и другие важные сведения. **Записи** объект может представлять листовым узлом и неконечного узла в древовидной структуре. Неконечные узлы могут иметь других узлов, как их содержимое, но конечные узлы не имеют такого содержимого. Листовые узлы обычно содержат двоичные потоки данных и неконечных узлов может иметь двоичный поток по умолчанию, связанные с ними. Свойства **записи** объекта определить тип узла.  
  
 **Записи** объекта также представляет альтернативный способ для навигации по иерархически организованных данных. Объект **запись** объект может быть создан для представления корень конкретного вложенного дерева в больших древовидная структура и новый **записи** объектов может быть открыт для представления дочерних узлов.  
  
 Ресурс (например, файл или каталог) можно однозначно идентифицировать абсолютный URL-адрес. A [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объект неявно создается и присвоено **запись** объекта при **записи** открывается с помощью абсолютный URL-адрес. Объект **подключения** объекта может быть явно задано значение **запись** объекта через [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойство. К файлам и каталогам, к которым можно обращаться с помощью **подключения** определить объект *контекста* в котором **записи** наблюдается операций.  
  
 Методы данных изменения и навигации на **запись** объект также принимает относительный URL-адрес, который находит ресурсу с помощью абсолютный URL-адрес или **подключения** контекста объекта в качестве отправной точки.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Объект **подключения** объект связан с каждым **записи** объекта. Таким образом **запись** операций объекта может быть включено в транзакцию путем вызова **подключения** объекта методы транзакции.  
  
 **Записи** объект не поддерживает события ADO и поэтому он не будет отвечать на уведомления.  
  
 В случае методов и свойств **записи** объекта, можно сделать следующее:  
  
-   Задание или возврат связанного **подключения** объекта с [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойство.  
  
-   Указать разрешения на доступ с [режим](../../../ado/reference/ado-api/mode-property-ado.md) свойство.  
  
-   Возвращает URL-адрес каталога, если таковое имеется, которое содержит ресурсом, представленным **запись** с [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md) свойство.  
  
-   Указывать абсолютный URL-адрес, относительный URL-адрес или **записей** откуда **запись** производные с [источника](../../../ado/reference/ado-api/source-property-ado-record.md) свойство.  
  
-   Указывает текущее состояние **запись** с [состояние](../../../ado/reference/ado-api/state-property-ado.md) свойство.  
  
-   Укажите тип **запись** — *простой*, *коллекции*, или *структурированный документ* — с [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)свойство.  
  
-   Остановить выполнение асинхронной операции с [отменить](../../../ado/reference/ado-api/cancel-method-ado.md) метод.  
  
-   Отмените регистрацию **запись** из источника данных с [закрыть](../../../ado/reference/ado-api/close-method-ado.md) метод.  
  
-   Скопируйте файл или каталог, представленный **запись** в другое место с [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) метод.  
  
-   Удаление файла или каталога и его подкаталогов, представленного **запись** с [макрокоманду УдалитьЗапись](../../../ado/reference/ado-api/deleterecord-method-ado.md) метод.  
  
-   Откройте **записей** , содержащий строки, которые представляют сущности, представленной файлы и подкаталоги **запись** с [GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md) метод.  
  
-   Move (переименовать) файл или каталог и подкаталоги, представленного **запись** в другое место с [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) метод.  
  
-   Связать **запись** существующими данными источника или создать новый файл или каталог с [откройте](../../../ado/reference/ado-api/open-method-ado-record.md) метод.  
  
 **Записи** объекта безопасные для использования.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Record](../../../ado/reference/ado-api/record-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Коллекция свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Записи и потоки](../../../ado/guide/data/records-and-streams.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
