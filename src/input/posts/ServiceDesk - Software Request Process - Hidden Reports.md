---
title: ServiceDesk - Software Request Process - Hidden Reports
tags:
    - ServiceDesk
    - Software Request Process
author: AlexHedley
# description: 
# articleId: 
published: 2017-09-07
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-software-request-proc?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

With the new "Software Request Process" in [ServiceDesk](https://www.symantec.com/products/service-desk) 8.1 there have been some new [Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=24530d5f-01a3-464d-846b-01482ee0c85e&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments) added to the SMP.

Table Of Contents
  
- [Index](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=253f9b2f-045e-4e05-acb9-fcc37005f674&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Overview](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a5fdba6d-707b-44be-a051-b08e5a5cfe19&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Config](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e3acdfdc-8b09-4ca7-afb5-821c9cce9301&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SMP](https://www.symantec.com/connect/articles/servicedesk-software-request-process-smp)
- [Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=24530d5f-01a3-464d-846b-01482ee0c85e&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Hidden Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f39346c9-799f-4d1b-ba9b-7f0910cd9c74&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=28879800-dd5e-436b-8f8b-9bc7301fbb1e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [WFs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=736fee28-7f45-497e-b208-b3de50cde839&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [DLLs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f4cef159-76c3-4b5b-9287-94aee6bec214&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

These can be found in the ![](images\article-3707841-files_smp.png) SMP.
  
Reports | Service and Asset Management | ServiceDesk

There are also a number of Hidden Reports.
  
---
  
**Available Software**
  
This shows what Software can be chosen for a Machine in the Request.
  
In the **Model: List Available Software** there is a new Component

| List Available Software |
| --- |
| ServiceDesk.SoftwareRequest.Core.Components.ListAvailableSoftwareComponent |
| ServiceDesk.SoftwareRequest.Core.dll |

This looks for a Repot with the following Guid: **7DF44266-9612-4B92-A52C-108161866642**
  
If you open any Report in a new Window you can see the URL used to view said Report.

| https://localhost/Altiris/console/?mainUrl=%2faltiris%2fconsole%2fItemPage.aspx%3fItemGuid%3d**[GUID]** |
| --- |

Run this through a [decoder](http://meyerweb.com/eric/tools/dencoder/) to make this more readable, and add the GUID on the end:

| https://localhost/altiris/console/ItemPage.aspx?ItemGuid=7DF44266-9612-4B92-A52C-108161866642 |
| --- |

Reports | Service and Asset Management | ServiceDesk | Available Software
  
This is a Hidden and uneditable Report, you could clone this to see, modify or just View as XML to see the SQL used.
  
SQL

    DECLARE @raIdProductContainsComponent uniqueidentifier
    DECLARE @raIdSoftwareProducttoCompany uniqueidentifier
    
    SET @raIdProductContainsComponent = '9d67b0c6-beff-4fcd-86c1-4a40028fe483'
    SET @raIdSoftwareProducttoCompany = 'd5c66d5a-7686-4ca2-b7c1-ac980576ce1d'
    
    SELECT DISTINCTdprd.[Guid] as ProductGuid, dprd.Name as ProductName,ver.[Version] as ProductVersion,company.[Name] as Manufacturer
    FROM [vAC_DeliverableSoftwareProducts] dprdINNER JOIN [ResourceAssociation] as raProductContainsComponent	INNER JOIN [RM_ResourceSoftware_Release] as rel 		on raProductContainsComponent.ResourceAssociationTypeGuid = @raIdProductContainsComponent		and raProductContainsComponent.ChildResourceGuid = rel.[Guid]	on dprd.[Guid] = raProductContainsComponent.ParentResourceGuidLEFT OUTER JOIN [ResourceAssociation] as raSoftwareProductToCompany	INNER JOIN [vRM_Company_Item] as company 		on raSoftwareProductToCompany.ResourceAssociationTypeGuid = @raIdSoftwareProducttoCompany		and raSoftwareProductToCompany.ChildResourceGuid = company.[Guid]	on dprd.[Guid] = raSoftwareProductToCompany.ParentResourceGuidLEFT OUTER JOIN [Inv_Software_Product_Version] as ver	on dprd.[Guid] = ver._ResourceGuid
    ORDER BY ProductName

[![Protirus](images\Protirus.png)](https://www.protirus.com)
