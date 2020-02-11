---
title: SMP - Reports - Assets Status
tags:
    - SMP
author: AlexHedley
# description: 
articleId: 3814461
published: 2019-01-14
# symantecUrl:
broadcomUrl: https://community.broadcom.com/groups/viewdocument/smp-reports-assets-status-1?CommunityKey=d89b2b1b-1b1c-40c7-88de-8a8a52ebf2a5&tab=librarydocuments
---

## ![SMP](images\smp.png) SMP
  
## Reports
  
### Asset's Status
  
Settings |  Notification Server | Resource and Data Class Settings | Resource Associations | ![Resource Association](images\ResourceAssociation.png) Asset’s Status

| ​GUID | 3028166f-c0d6-41d8-9cb7-f64852e0fd01 |
| --- | --- |

Details

| Parent | Asset |
| --- | --- |
| ​Child | ​​Fixed Asset Status Resource Type |

Settings |  Notification Server | Resource and Data Class Settings |  Resource Types | Asset Types | Generic Asset Types | ![Resource](images\Resource.png) Asset
  
Settings |  Notification Server | Resource and Data Class Settings |  Resource Types | Other Resources | ![Resource](images\icn16asset_gen.gif) Fixed Asset Status Resource Type

> If an Asset hasn't had a Status set it won't show as Active, so you need to check for this.

Get the Statuses of each Computer

    SELECT  
    vComputer.Name AS [ComputerName],  
    vRM_Fixed_Asset_Status_Resource_Type_Item.Name AS [Status] 
    FROM ResourceAssociation  
     INNER JOIN vComputer ON ResourceAssociation.ParentResourceGuid = vComputer.Guid  
     INNER JOIN vRM_Fixed_Asset_Status_Resource_Type_Item  
     ON ResourceAssociation.ChildResourceGuid = vRM_Fixed_Asset_Status_Resource_Type_Item.Guid 
    WHERE 
     (ResourceAssociation.ResourceAssociationTypeGuid = '3028166f-c0d6-41d8-9cb7-f64852e0fd01')

Another

     SELECT 
    RM_ResourceComputer.Guid AS ComputerGuid,  
    RM_ResourceComputer.Name AS ComputerName,  
    vUser.Guid AS UserGuid,  
    vUser.Name AS [User], 
    vRM_Fixed_Asset_Status_Resource_Type_Item.Guid AS [StatusGuid], 
    vRM_Fixed_Asset_Status_Resource_Type_Item.Name AS [Status] 
    FROM 
    RM_ResourceComputer  
    INNER JOIN ResourceAssociation ON RM_ResourceComputer.Guid = ResourceAssociation.ParentResourceGuid  
    INNER JOIN vUser ON ResourceAssociation.ChildResourceGuid = vUser.Guid  
    INNER JOIN ResourceAssociation AS ResourceAssociation_1 ON RM_ResourceComputer.Guid = ResourceAssociation_1.ParentResourceGuid  
    INNER JOIN vRM_Fixed_Asset_Status_Resource_Type_Item ON ResourceAssociation_1.ChildResourceGuid = vRM_Fixed_Asset_Status_Resource_Type_Item.Guid 
    WHERE 
    (ResourceAssociation.ResourceAssociationTypeGuid = 'ed35a8d1-bf60-4771-9dde-092c146c485a')  
    AND  
    (ResourceAssociation_1.ResourceAssociationTypeGuid = '3028166f-c0d6-41d8-9cb7-f64852e0fd01') 
    AND 
    ( 
     ( (@ComputerName IS NOT NULL) AND (RM_ResourceComputer.Name = @ComputerName) ) 
         OR 
         ( (@User IS NOT NULL) AND (vUser.Name = @User) ) 
        )

If you're interested in what Tables are used to maintain this check the following Article
  
Workflow - SMP - ASDK - Asset Ownership  
[https://www.symantec.com/connect/articles/workflow-smp-asdk-asset-ownership](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=7e9fe111-ca99-4880-adee-6532190f0eea&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
