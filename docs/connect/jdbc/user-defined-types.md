---
title: "Определяемые пользователем типы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ccd5c353efd622fa406bfeb5c5b9c44c9546364b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="user-defined-types"></a>Определяемые пользователем типы
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Определяемые пользователем типы (UDT) впервые появились в [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] позволяет разработчику возможность расширить серверную систему скалярных типов путем хранения объектов среды CLR в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. Определяемые пользователем типы могут содержать несколько элементов и поведение может, в отличие от традиционных псевдонимов типов данных, которые состоят из одного [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] системный тип данных. Ранее размер определяемых пользователем типов был ограничен 8 килобайтами. В [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)], была добавлена поддержка определяемых пользователем типов данных, размер которых превышает 64 килобайта. Начиная с версии 3.0 драйвер JDBC также поддерживает определяемые пользователем типы с размером более 64 килобайт при указании формата UserDefined.  
  
 Поведение определяемых пользователем типов с размером, не превышающим 8000 байт, не изменилось, но теперь поддерживаются более крупные, определяемые пользователем типы, для которых сообщается размер unlimited.  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
