---
title: "Программирование объектов безопасности AMO | Документы Microsoft"
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
- programming [AMO]
- Analysis Management Objects, security
- AMO, security
ms.assetid: 5d963721-6e6e-46eb-bc9b-18724dd0b751
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ee56a1d89bdf9d5712dcdb70043be95b9195d0ba
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="programming-amo-security-objects"></a>Программирование объектов безопасности AMO
  В службах [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]для программирования объектов безопасности или выполнения программ, в которых используются объекты безопасности AMO, необходимо быть членом группы администраторов сервера или администраторов базы данных. Администратор сервера или администратор базы данных — это уровни доступа, обеспечиваемые службами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 В службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] пользователь получает доступ к объекту через сочетание ролей и разрешений, назначенных этому объекту. Дополнительные сведения см. в разделе [классы безопасности AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-security-classes.md).  
  
## <a name="role-and-permission-objects"></a>Объекты ролей и разрешений  
 Роли сервера содержат в коллекции одну и только одну роль, роль администратора. Новые роли в коллекцию ролей сервера добавлять нельзя. Членство в роли администратора дает полный доступ ко всем объектам на сервере.  
  
 Объекты <xref:Microsoft.AnalysisServices.Role> создаются на уровне базы данных. Обслуживание ролей сводится к добавлению или удалению членов роли, а также ролей в объекте <xref:Microsoft.AnalysisServices.Database>. Если с ролью связан хотя бы один объект <xref:Microsoft.AnalysisServices.Permission>, то удалить ее невозможно. Чтобы удалить роль, необходимо произвести поиск во всех объектах <xref:Microsoft.AnalysisServices.Permission>, находящихся в объектах <xref:Microsoft.AnalysisServices.Database>, и удалить объект <xref:Microsoft.AnalysisServices.Role> из разрешений. Только после этого объект <xref:Microsoft.AnalysisServices.Role> можно будет удалить из объекта <xref:Microsoft.AnalysisServices.Database>.  
  
 Разрешения указывают, какие действия разрешены над объектом, для которого эти разрешения установлены. Разрешения могут быть предоставлены для следующих объектов: <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.MiningStructure>, и <xref:Microsoft.AnalysisServices.MiningModel>. Обслуживание разрешений сводится к предоставлению и отмене прав доступа при помощи соответствующего свойства доступа. У каждого разрешения на доступ есть свойство, которому может быть установлен требуемый уровень доступа. Доступ может быть определен для следующих операций: Process, ReadDefinition, Read, Write и Administer. Доступ Administer задается только для объекта <xref:Microsoft.AnalysisServices.Database>. Уровень безопасности администратора базы данных достигается только при предоставлении роли разрешения на администрирование базы данных.  
  
 В следующем образце создаются четыре роли: администраторы баз данных, обработчики, писатели и читатели.  
  
 Администраторы баз данных могут администрировать указанные базы данных.  
  
 Обработчики могут обрабатывать все объекты в базе данных и проверять результаты. Для проверки результатов указанному кубу необходимо явно предоставить право доступа на чтение объекта базы данных, поскольку разрешения на чтение не распространяется на дочерние объекты.  
  
 Писатели могут выполнять чтение и запись в указанный куб, а их доступ к ячейкам ограничен ячейками «США» в измерении клиентов.  
  
 Читатели могут выполнять чтение в указанном кубе, а их доступ к ячейкам ограничен ячейками «США» в измерении клиентов.  
  
```  
static public void CreateRolesAndPermissions(Database db, Cube cube)  
{  
    Role role;  
    DatabasePermission dbperm;  
    CubePermission cubeperm;  
  
    #region Create the Database Administrators role  
  
    // Create the Database Administrators role.  
    role = db.Roles.Add("Database Administrators");  
    role.Members.Add(new RoleMember("")); // e.g. domain\user  
    role.Update();  
  
    // Assign administrative permissions to this role.  
    // Members of this role can perform any operation within the database.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Administer = true;  
    dbperm.Update();  
  
    #endregion  
  
    #region Create the Processors role  
  
    // Create the Processors role.  
    role = db.Roles.Add("Processors");  
    role.Members.Add(new RoleMember("")); // e.g. myDomain\johndoe  
    role.Update();  
  
    // Assign Read and Process permissions to this role.  
    // Members of this role can process objects in the database and query them to verify results.  
    // Process permission applies to all contained objects, i.e. all dimensions and cubes.  
    // Read permission does not apply to contained objects, so we must assign the permission explicitly on the cubes.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Process = true;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    cubeperm.Update();  
  
    #endregion  
  
    #region Create the Writers role  
  
    // Create the Writers role.  
    role = db.Roles.Add("Writers");  
    role.Members.Add(new RoleMember("")); // e.g. redmond\johndoe  
    role.Update();  
  
    // Assign Read and Write permissions to this role.  
    // Members of this role can discover, query and writeback to the Adventure Works cube.  
    // However cell access and writeback is restricted to the United States (in the Customer dimension).  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    cubeperm.Write = WriteAccess.Allowed;  
    cubeperm.CellPermissions.Add(new CellPermission(CellPermissionAccess.Read, "[Customer].[Country-Region].CurrentMember is [Customer].[Country-Region].[Country-Region].&[United States]"));  
    cubeperm.CellPermissions.Add(new CellPermission(CellPermissionAccess.ReadWrite, "[Customer].[Country-Region].CurrentMember is [Customer].[Country-Region].[Country-Region].&[United States]"));  
    cubeperm.Update();  
  
    #endregion  
  
    #region Create the Readers role  
  
    // Create the Readers role.  
    role = db.Roles.Add("Readers");  
    role.Members.Add(new RoleMember("")); // e.g. redmond\johndoe  
    role.Update();  
  
    // Assign Read permissions to this role.  
    // Members of this role can discover and query the Adventure Works cube.  
    // However the Customer dimension is restricted to the United States.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    Dimension dim = db.Dimensions.GetByName("Customer");  
    DimensionAttribute attr = dim.Attributes.GetByName("Country-Region");  
    CubeDimensionPermission cubedimperm = cubeperm.DimensionPermissions.Add(dim.ID);  
    cubedimperm.Read = ReadAccess.Allowed;  
    AttributePermission attrperm = cubedimperm.AttributePermissions.Add(attr.ID);  
    attrperm.AllowedSet = "{[Customer].[Country-Region].[Country-Region].&[United States]}";  
    cubeperm.Update();  
  
    #endregion  
}  
```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices>   
 [Знакомство с классами объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Программирование объектов безопасности AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-security-objects.md)   
 [Разрешения и права доступа &#40; Analysis Services — многомерные данные &#41;](http://msdn.microsoft.com/library/59fa3573-f985-46cb-8042-7da71bd59a7b)   
 [Логическая архитектура &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Объекты базы данных &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
