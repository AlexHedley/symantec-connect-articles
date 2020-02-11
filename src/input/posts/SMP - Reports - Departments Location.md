---
title: SMP - Reports - Departments Location
tags:
    - SMP
author: AlexHedley
# description: 
articleId: 3814481
published: 2019-01-14
# symantecUrl:
broadcomUrl: https://community.broadcom.com/groups/viewdocument/smp-reports-departments-locatio?CommunityKey=d89b2b1b-1b1c-40c7-88de-8a8a52ebf2a5&tab=librarydocuments
---

## ![SMP](images\smp.png) SMP
  
## Reports
  
### Department's Location
  
Settings | Notification Server | Resource and Data Class Settings | Resource Associations | CMDB Assocation Types | ![Resource Association](images\ResourceAssociation.png) Department's Location

| ​GUID | ​9e4ced04-c03f-473c-b0c3-1c1d1b8df49b |
| --- | --- |

Details

| ​From Type | Department |
| --- | --- |
| ​To Type | ​Location |

Settings | Notification Server | Resource and Data Class Settings | Resource Types | Organizational Types | ![Department](images\Department.png) Department
  
Settings | Notification Server | Resource and Data Class Settings | Resource Types | Organizational Types | ![Location](images\location16.png) Location

If you go to a Department in
  
Home | Service and Asset Management | ![icnCustomView](images\icnCustomView.gif)Manage Configuration Items
  
![icnCustomView](images\icnCustomView.gif)CI Management | Organisational Types | ![Department](images\department16.png) Department
  
Scroll down to near the bottom there is a section for
  
**Department's Location**
  
This allows you to edit which Location a Department is in.

If you then need this information in a Report you can use the following SQL.

    DECLARE @LocationName AS nvarchar(255) = NULL
    DECLARE @DepartmentNameTerm AS nvarchar(255) = NULL
    
    SELECT
      d.[Guid] AS [DepartmentGuid],
      d.[Name] AS [DepartmentName],
      l.[Guid] AS [LocationGuid],
      l.[Name] AS [LocationName]
    FROM
      vRM_Department_Item d
      LEFT OUTER JOIN vRM_Location_Item l
      INNER JOIN ResourceAssociation AS ra1 ON l.Guid = ra1.ChildResourceGuid 
        ON ra1.ParentResourceGuid = d.Guid 
        AND ra1.ResourceAssociationTypeGuid = '9e4ced04-c03f-473c-b0c3-1c1d1b8df49b'
    WHERE
    (
    ((@LocationName IS NULL and (l.Name LIKE '%' or l.Name IS NULL)) OR (@LocationName IS NOT NULL AND l.Name = @LocationName))
    AND
    ((@DepartmentNameTerm IS NULL and (d.Name LIKE '%' or d.Name IS NULL)) OR (@DepartmentNameTerm IS NOT NULL AND d.Name LIKE '%' + @DepartmentNameTerm + '%'))
