---
title: ServiceDesk - Extensions
tags:
    - ServiceDesk
author: AlexHedley
# description: 
# articleId: 
published: 2018-11-09
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-extensions?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

## ServiceDesk
  
### Extensions

With SD 8.5
  
From the release notes

| Pre-built automation libraries for Incident, Problem, and Change modules. |
| --- |
| Incident, Problem, and Change Data Types are now refactored to include pre-built automation libraries. |

To extend a current process in IM / CM etc the following Article has been written.

How to add custom data to existing processes like Incident Management, Change Management etc
  
- https://www.symantec.com/connect/articles/how-add-custom-data-existing-processes-incident-management-change-management-etc

But the part to join your new custom data to the original ticket hasn't been documented.

Since you have extended your class to "RelationalMappingProcessData" there will be a

- WorkflowTrackingId

This is where you take the SessionID from your Incident/Change and map to the new Data Type.

You could create a Workflow that passes in the SessionId as an input.
  
This calls

- Get Incident Ticket By SessionId
    - Class: Symantec.ServiceDesk.Im.Core.Components.GetIncidentTicketBySessionId
    - Library: Symantec.ServiceDesk.Im.Core.dll

The maps using

- Single Value Mapping
    - Class: LogicBase.Components.Default.Mapping.SingleValueMappingComponent
    - Library: LogicBase.Components.Default.dll
- https://www.symantec.com/connect/articles/single-value-mapping

Map from your "SessionId" to "WorkflowTrackingId"
  
![ServiceDeskExtendedMapping](images\ServiceDeskExtendedMapping.png)
  
This will make the join between your two tables and be the association needed.

[![Protirus](images\Protirus.png)](https://www.protirus.com/)
