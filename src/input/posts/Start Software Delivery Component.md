---
title: Start Software Delivery Component
tags:
    - Workflow
    - Component
author: AlexHedley
# description: 
# articleId: 
published: 2017-10-06
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/start-software-delivery-component?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

### Component definition
  
The 'Start Software Delivery Component' creates a Software Delivery Process.
  
**Class:** ServiceDesk.SoftwareRequest.Core.Components.StartSoftwareDeliveryComponent  
**Library:** ServiceDesk.SoftwareRequest.Core.dll  
**Publisher:** Symantec Corporation
  
### Component icon
  
![cubes](images\cubes.png)
  
### Definition of component input/output value or values
  
CONFIGURATION
  
Connection

| Input value name | Input value data type | Example format |
| --- | --- | --- |
| Security Token |  |  |
| Timeout | Integer | 10000 |
| Url |  | [ProfileProperties].service_desk_settings_software_delivery_url/softwaredeliveryservice.asmx |

Profile Properties
  
- https://&lt;WORKFLOWSERVER&gt;/servicedesk.softwarerequest.delivery

Input

| Input value name | Input value data type | Example format |
| --- | --- | --- |
| Software Request | SoftwareRequest |  |

Output

| Input value name | Input value data type | Example format |
| --- | --- | --- |
| Process ID Result |  | SoftwareDeliveryProcessId |
| Result |  | StartSoftwareDeliveryResult |
| Return Process ID | Boolean | False |

###  
  
### Connection information
  
N/A
  
### Component settings
  
Usual Enabled etc

## Use case
  
Use this to create a Software Delivery Process based on a SoftwareRequested item from the RequestedSoftware data type.

### **Related**
  
[ServiceDesk - Software Request Process](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=253f9b2f-045e-4e05-acb9-fcc37005f674&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments) - DLLs

- [https://www.symantec.com/connect/articles/servicedesk-software-request-process-dlls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f4cef159-76c3-4b5b-9287-94aee6bec214&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
