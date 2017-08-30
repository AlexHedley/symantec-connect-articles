---
title: ServiceDesk - Software Request Process - Reports
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-08-30
---

With the new "Software Request Process" in [ServiceDesk](https://www.symantec.com/products/service-desk) 8.1 there have been some new Reports added to the SMP.

If you login to a new SMP 8.1.
  
Reports | Service and Asset Management | ServiceDesk
  
- Delivery Policies for Software Release
- Filters for Target
- Releases for Software Product

**Delivery Policies for Software Release**

    SELECT 
             itmr.ParentItemGuid as PolicyGuid, 
             itm.Name as PolicyName
    FROM 
             ItemReference itmr
             INNER JOIN Item as itm on itm.[Guid] = itmr.ParentItemGuid
    WHERE 
             itmr.Hint='manageddelivery uses software resource'
             and  itmr.ChildItemGuid = '%releaseGuid%'

**Filters for Target**

    select 
             itm1.Name as TargetName, 
             itm2.Name as CollectionName,
             tf.FilterType as FilterType, 
             tf.Operation as Operation, 
             tfc.CollectionGuid as CollectionGuid
    from 
             TargetFilter  tf
             inner join TargetFilterCollection tfc on tf.Guid = tfc.TargetFilterGuid
             inner join Item itm1 on itm1.Guid = tf.ResourceTargetGuid
             inner join Item itm2 on itm2.Guid = tfc.CollectionGuid
    where 
             tf.ResourceTargetGuid = '%targetGuid%'

**Releases for Software Product**

    DECLARE @raIdProductContainsComponent uniqueidentifier
    SET @raIdProductContainsComponent = '9d67b0c6-beff-4fcd-86c1-4a40028fe483'
    
    SELECT 
             rel.[Guid] as ReleaseGuid,
             rel.[Name] as ReleaseName
    FROM
             [RM_ResourceSoftware_Release] rel
             INNER JOIN [ResourceAssociation] as raProductContainsComponent
                     INNER JOIN [vRM_Software_Product_Item] as prd
                              on raProductContainsComponent.ResourceAssociationTypeGuid = @raIdProductContainsComponent
                              and prd.[Guid] = raProductContainsComponent.ParentResourceGuid
                     on       rel.[Guid] = raProductContainsComponent.ChildResourceGuid
    WHERE
             prd.[Guid] = '%productGuid%'

This is used in the following Workflow:
  
ServiceDesk.SoftwareRequest.Delivery
  
Model: Delivery Authorization  
Form: Delivery Authorization  
SelectedFilter - Items
  
List Targets for Policy (Altiris7.WebServices.Scoping.GetResourceTargetsComponent)  
- https://localhost/altiris/asdk.ns/ScopingManagementService.asmx?op=GetResourceTargets  
PolicyItemGuid: [SelectedPolicy.PolicyGuid]  
Result: TargetsForPolicy
  
List Filters for Target (ServiceDesk.SoftwareRequest.Core.Components.ListFiltersForTargetComponent)  
- Report in SMP  
Target Guid: [EachTargetGuid]  
ResultVariableName: FiltersForEachTarget
  
Mapping Component: Ticket Status: Authorized/Delivery  
SelectedFilter - CollectionGuid gets mapped to RequestedSoftware - DeliverdByTargetId
  
Model: Delivery Flow  
Embedded Rule Model: Deliver Software
  
Add target device to filter (Altiris7.WebServices.Collections.AddInclusionsComponent)  
- https://localhost/altiris/asdk.ns/CollectionManagementService.asmx?op=AddExclusions  
Collection Item Guid: [SoftwareTicket.DeliveredByTargetId]  
Item Guids: [SoftwareTicket.TargetDeviceId]

**Related Articles**
  
Useful SQL queries concerning Collections/Filters  
[https://www.symantec.com/connect/articles/useful-sql-queries-concerning-collectionsfilters](https://community.broadcom.com/groups/viewdocument?DocumentKey=f5b18caf-a738-45a1-99e9-688abf47b244&amp;CommunityKey=d5a4f95a-fa38-4bdd-82d5-2daec4b3ca5c&amp;tab=librarydocuments)
  
Locate a Target's guid so that you can then update its membership  
[https://www.symantec.com/connect/articles/locate-targets-guid-so-you-can-then-update-its-membership](https://community.broadcom.com/groups/viewdocument?DocumentKey=e5bf9822-323e-49bf-aa08-646aff939983&amp;CommunityKey=d5a4f95a-fa38-4bdd-82d5-2daec4b3ca5c&amp;tab=librarydocuments)
