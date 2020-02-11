---
title: Get Requested Software By Session ID
tags:
    - Workflow
    - Component
author: AlexHedley
# description: 
# articleId: 
published: 2017-10-06
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/get-requested-software-by-session-i?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

### Component definition
  
The 'Get Requested Software By Session ID' takes a "SessionId" input and returns a "RequestedSoftwareObject" object.
  
**Class:** ServiceDesk.SoftwareRequest.Core.Components.GetRequestedSoftwareBySessionIdComponent  
**Library:** ServiceDesk.SoftwareRequest.Core.dll  
**Publisher:** Symantec Corporation
  
### Component icon
  
![cubes](images\cubes.png)
  
### Definition of component input value or values
  
Table: Input values

| Input value name | Input value data type | Example format |
| --- | --- | --- |
| Workflow Tracking Id (Session Id) | Unique Identifier | 00000000-0000-0000-0000-000000000000 |
| Exchange Name (Storage) | Text | local.orm |

###  
  
### Definition of component output value or values
  
Table: Output values

| Input value name | Input value data type | Example format |
| --- | --- | --- |
| Requested Software Variable | Text | RequestedSoftwareObject |

###  
  
### Connection information
  
Using the "local.orm" for Storage.

### Component settings
  
Usual Enabled etc

## Use case
  
Retrieve a Requested Software Item based on the SessionId of the Ticket.

### **Related**
  
[ServiceDesk - Software Request Process](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=253f9b2f-045e-4e05-acb9-fcc37005f674&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments) - DLLs
  
[https://www.symantec.com/connect/articles/servicedesk-software-request-process-dlls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f4cef159-76c3-4b5b-9287-94aee6bec214&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
