---
title: Элемент Database описания рабочей нагрузки (DTA) | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 02bf075186f8bc9c8efc6fb05b9288f636494a7c
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="database-element-for-workload-dta"></a>Элемент Database описания рабочей нагрузки (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Указывает базу данных, в которой находится таблица трассировки рабочей нагрузки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необходимо наличие одного такого элемента, если не задан никакой другой тип рабочей нагрузки. Для родительского элемента **Workload**необходимо задать дочерний элемент **EventString**, **File** или **Database** , однако одновременно может использоваться только один из них. Например, если рабочая нагрузка определена посредством элемента **Database** , в том же входном XML-файле нельзя указывать рабочую нагрузку также с помощью элемента **File** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Workload &#40; DTA &#41;](../../tools/dta/workload-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания базы данных &#40; DTA &#41;](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [Элемент schema описания базы данных &#40; DTA &#41;](../../tools/dta/schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 Этот элемент с именем **DatabaseDetailsTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Не путайте этот элемент **Database** с элементом, корневым родительским элементом которого является **Configuration** . (См. раздел [Элемент Database описания конфигурации (DTA)](../../tools/dta/database-element-for-configuration-dta.md).)  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента **Database** см. в примере кода в разделе [Элемент Workload (DTA)](../../tools/dta/workload-element-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
