---
title: SMP - Reports - Assets Location
tags:
    - SMP
author: AlexHedley
# description: 
articleId: 3814471
published: 2019-01-14
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/smp-reports-assets-location?CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&tab=librarydocuments
---

## ![SMP](images\smp.png) SMP
  
## Reports
  
### Asset's Location
  
Settings |  Notification Server | Resource and Data Class Settings | Resource Associations | CMDB Assocation Types | ![Resource Association](images\ResourceAssociation.png) Asset’s Location

| ​GUID | 05de450f-39ea-4aae-8c5f-77817889c27c |
| --- | --- |

Details

| From Type | Asset |
| --- | --- |
| ​To Type | Location |

Settings |  Notification Server | Resource and Data Class Settings |  Resource Types | Asset Types | Generic Asset Types | ![Resource](images\Resource.png) Asset
  
Settings |  Notification Server | Resource and Data Class Settings |  Resource Types | Organisational Types | ![Location](images\location16.png) Location

    DECLARE @AssetGuid AS UniqueIdentifier = NULL --'00000000-0000-0000-0000-000000000000' 
    DECLARE @LocationGuid AS UniqueIdentifier = NULL --'00000000-0000-0000-0000-000000000000' 
    
    SELECT  
      ri.[Guid] AS [AssetGuid]  
      ,ri.[Name] AS [AssetName]
      --,rt.[Guid] AS [AssetTypeGuid]
      --,rt.[Name] AS [AssetType]
      ,l.[Guid] AS [LocationGuid]
      ,l.[Name] AS [LocationName] 
    FROM  
      vRM_Asset_Item ri  
      INNER JOIN ResourceAssociation ra 
        ON ri.Guid = ra.ParentResourceGuid
        AND (ra.ResourceAssociationTypeGuid = '05de450f-39ea-4aae-8c5f-77817889c27c') --Location  
      INNER JOIN vRM_Location_Item l 
        ON ra.ChildResourceGuid = l.Guid 
      --INNER JOIN ResourceType rt
      --  ON rt.Guid = ri.ResourceTypeGuid
    WHERE
    (
      (@AssetGuid IS NOT NULL AND ri.Guid = @AssetGuid)
      OR
      (@LocationGuid IS NOT NULL AND l.Guid = @LocationGuid)
    )

### Location Hierarchy
  
If you have a Hierarchy of Locations it's handy to add this in your Reports.
  
Just add the **Path** field.

    SELECT Guid, Path
    FROM dbo.fnAssetHierarchyTreeExcludeChildren('834BC951-D70F-48F4-9E8E-D7E32C68788D', NULL, 0x0, 0x0, 1)
    AS h

Example

| UK\England\Newcastle |
| --- |

query to build location hierarchy  
[https://www.symantec.com/connect/forums/query-build-location-hierarchy](https://community.broadcom.com/groups/viewthread?MessageKey=08e7d06d-37d0-46c4-a878-1d9e318ce109&amp;CommunityKey=2eae875e-f73e-4358-8452-7bb8f7f27f59&amp;tab=digestviewer#bm08e7d06d-37d0-46c4-a878-1d9e318ce109)

### Locations By Parent At Location
  
You may just wish to find the parent of a Location.
  
Settings |  Notification Server | Resource and Data Class Settings | Resource Associations | CMDB Assocation Types | ![Resource Association](images\ResourceAssociation.png) Location Hierarchy

| ​GUID | dc4689d9-1d2d-47cc-bf65-fd9437d08ed5 |
| --- | --- |

Details

| From Type | Location |
| --- | --- |
| ​To Type | Location |

Settings |  Notification Server | Resource and Data Class Settings |  Resource Types | Organisational Types | ![Location](images\location16.png) Location
  
Settings |  Notification Server | Resource and Data Class Settings |  Resource Types | Organisational Types | ![Location](images\location16.png) Location

    DECLARE @ParentLocationGuid AS UniqueIdentifier = NULL
    
    SELECT 
        li.[Guid]
        ,li.[Name]
        ,l.[Guid] AS ParentLocationGuid
        ,l.[Name] AS ParentLocationName
    FROM
        vRM_Location_Item li
    INNER JOIN ResourceAssociation ra
        ON li.[Guid] = ra.ParentResourceGuid AND ra.ResourceAssociationTypeGuid = 'dc4689d9-1d2d-47cc-bf65-fd9437d08ed5'
    INNER JOIN vRM_Location_Item l
        ON ra.ChildResourceGuid = l.[Guid]
    WHERE
        l.[Guid] = @ParentLocationGuid
