---
title: SMP - Reports - Asset User Owners
# tags:
#     - 
author: AlexHedley
# description: 
articleId: 3814441
published: 2019-01-14
---

## ![SMP](images\smp.png) SMP
  
## Reports
  
### Asset User Owners
  
Settings | Notification Server | Resource and Data Class Settings | Resource Associations | CMDB Assocation Types | ![Resource Association](images\ResourceAssociation.png) Asset User Owners

| ​GUID | ed35a8d1-bf60-4771-9dde-092c146c485a |
| --- | --- |

Details

| ​From Type | Asset |
| --- | --- |
| ​To Type | ​User |

Settings |  Notification Server | Resource and Data Class Settings |  Resource Types | Asset Types | Generic Asset Types | ![Resource](images\Resource.png) Asset
  
Settings | Notification Server | Resource and Data Class Settings | Resource Types | Organizational Types | ![user](images\User.png) User

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

    DECLARE @UserGuid AS UniqueIdentifier = NULL
    
    SELECT 
        a.[Guid] AS [AssetGuid]
        ,a.[Name] AS [AssetName]
        --,rt.[Name] AS [AssetType]
        ,u.[Guid] AS [UserGuid]
        ,u.Email AS [UserEmail]
    FROM vRM_Asset_Item a
    INNER JOIN ResourceAssociation ra 
        ON a.Guid = ra.ParentResourceGuid AND ra.ResourceAssociationTypeGuid = 'ed35a8d1-bf60-4771-9dde-092c146c485a'
    INNER JOIN vUser u
        ON ra.ChildResourceGuid = u.Guid
    --INNER JOIN ResourceType rt
    --    ON rt.Guid = a.ResourceTypeGuid
    WHERE 
    (
        (@UserGuid IS NULL) 
        OR (@UserGuid IS NOT NULL AND u.Guid = @UserGuid)
    )
