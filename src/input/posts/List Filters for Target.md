---
title: List Filters for Target
tags:
    - Workflow
    - Component
author: AlexHedley
# description: 
# articleId: 
published: 2017-10-06
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/list-filters-for-target?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

### Component definition
  
The 'List Filters for Target' returns a "Filters" array.
  
**Class:** ServiceDesk.SoftwareRequest.Core.Components.ListFiltersForTargetComponent  
**Library:** ServiceDesk.SoftwareRequest.Core.dll  
**Publisher:** Symantec Corporation
  
### Component icon
  
![cubes](images\cubes.png)
  
### Definition of component input/output value or values
  
Authentication

| Input value name | Input value data type | Example format |
| --- | --- | --- |
| Security Token |  | [Global].NSAuthenticationToken |

NSConfig

| Input value name | Input value data type | Example format |
| --- | --- | --- |
| Notification Server Address |  | [[Global].NotificationServer] |
| Use HTTPS | Boolean | [[Global].NSUsesHTTPS] |

Settings

| Input value name | Input value data type | Example format |
| --- | --- | --- |
| Is Enabled | Boolean | True |

Configuration

| Input value name | Input value data type | Example format |
| --- | --- | --- |
| Target Guid | Unique Identifier | 00000000-0000-0000-0000-000000000000 |
| Result Variable Name |  | Filters |
| Override Default Url | Boolean | False |
| Report Webservice Url | Text | http://&lt;SMPServer&gt;/altiris/asdk.ns/ReportManagementService.asmx |

Advanced

| Input value name | Input value data type | Example format |
| --- | --- | --- |
| Disable Web Proxy Detection | Boolean | True |
| Timeout | Number | 10000 |

General

| Input value name | Input value data type | Example format |
| --- | --- | --- |
| Throw Exception on Bad Values | Boolean | False |

###  
  
### Connection information
  
Needs an NS component for authentication.
  
- [Create SMP Credentials](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9a4ab06f-59da-40a6-ab93-bd231db61036&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

### Component settings
  
Usual Enabled etc

## Use case
  
Retrieve an array of Filters (ResourceTargetFilter) based on a Target Guid.

### Source
  
See [ServiceDesk - Software Request Process - Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=24530d5f-01a3-464d-846b-01482ee0c85e&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
  
![SMP](images\smp.png) SMP
  
Reports | Service and Asset Management | ServiceDesk | Filters for Target

| ReportId | 3B061581-A918-45D3-811D-152EFAAB0346 |
| --- | --- |
| Url | http://&lt;SMPSERVER&gt;/altiris/asdk.ns/ReportManagementService.asmx |
| Item Page | http://&lt;SMPSERVER&gt;/altiris/console/ItemPage.aspx?ItemGuid=3B061581-A918-45D3-811D-152EFAAB0346 |
| XML | http://&lt;SMPSERVER&gt;/Altiris/NS/ItemAsXml.aspx?ItemGuid=3B061581-A918-45D3-811D-152EFAAB0346 |

### **Related**
  
[ServiceDesk - Software Request Process](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=253f9b2f-045e-4e05-acb9-fcc37005f674&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments) - DLLs

- [https://www.symantec.com/connect/articles/servicedesk-software-request-process-dlls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f4cef159-76c3-4b5b-9287-94aee6bec214&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
