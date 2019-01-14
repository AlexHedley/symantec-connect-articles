---
title: SMP - Reports - Asset Department Owners
# tags:
#     - 
author: AlexHedley
# description: 
articleId: 3814431
published: 2019-01-14
---

## ![SMP](images\smp.png) SMP
  
## Reports
  
### Asset Department Owners
  
Settings | Notification Server | Resource and Data Class Settings | Resource Associations | CMDB Assocation Types | ![Resource Association](images\ResourceAssociation.png) Asset Department Owner

| ​GUID | 1466e770-4413-4517-a89d-6599b8a7f144 |
| --- | --- |

Details

| ​From Type | Asset |
| --- | --- |
| ​To Type | ​Department |

Settings |  Notification Server | Resource and Data Class Settings |  Resource Types | Asset Types | Generic Asset Types | ![Resource](images\Resource.png) Asset
  
Settings | Notification Server | Resource and Data Class Settings | Resource Types | Organizational Types | ![Department](images\Department.png) Department

If you go to a Computer in
  
Home | Service and Asset Management | ![icnCustomView](images\icnCustomView.gif)Manage Configuration Items
  
![icnCustomView](images\icnCustomView.gif)CI Management | Computers and Peripherals | ![Computer](images\computer16.png)Computer
  
Scroll down to near the bottom there is a section for
  
**Asset Owners**
  
This allows you to edit which Owner you wish to have against the Asset.
  
This can either be
  
- User
- Department

If you then need this information in a Report you can use the following SQL.

    DECLARE @DepartmentGuid AS UniqueIdentifier = NULL
    
    SELECT 
        a.[Guid] AS [AssetGuid]
        ,a.[Name] AS [AssetName]
        --,rt.[Name] AS [AssetType]
        ,d.[_ResourceGuid] AS [DepartmentGuid]
        ,d.[Name] AS [DepartmentName]
    FROM vRM_Asset_Item a
    INNER JOIN ResourceAssociation ra 
        ON a.Guid = ra.ParentResourceGuid AND ra.ResourceAssociationTypeGuid = '1466e770-4413-4517-a89d-6599b8a7f144'
    INNER JOIN vDepartment d
        ON ra.ChildResourceGuid = d._ResourceGuid
    --INNER JOIN ResourceType rt
    --    ON rt.Guid = a.ResourceTypeGuid
    WHERE 
    (
        (@DepartmentGuid IS NULL) 
        OR (@DepartmentGuid IS NOT NULL AND d._ResourceGuid = @DepartmentGuid)
    )
