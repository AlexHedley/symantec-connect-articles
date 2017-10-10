---
title: ServiceDesk - Software Request Process - WFs
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-10-10
---

In this series of Articles I'm going to explain how the new **Software Request Process** works in [ServiceDesk](https://www.symantec.com/products/service-desk) 8.1

This Article explains the different WFs that have been created and are published ready to use when you install SD.

Table Of Contents
  
- [Index](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=253f9b2f-045e-4e05-acb9-fcc37005f674&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Overview](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a5fdba6d-707b-44be-a051-b08e5a5cfe19&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Config](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e3acdfdc-8b09-4ca7-afb5-821c9cce9301&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SMP](https://www.symantec.com/connect/articles/servicedesk-software-request-process-smp)
- [Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=24530d5f-01a3-464d-846b-01482ee0c85e&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Hidden Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f39346c9-799f-4d1b-ba9b-7f0910cd9c74&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=28879800-dd5e-436b-8f8b-9bc7301fbb1e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [WFs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=736fee28-7f45-497e-b208-b3de50cde839&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [DLLs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f4cef159-76c3-4b5b-9287-94aee6bec214&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

You can find these projects in the base install of SD 8.1.

    [Install Drive]:\Program Files\Symantec\Workflow\WorkflowProjects\

- ![Workflow](images\Workflow.png) ServiceDesk.SoftwareRequest.Approval.package
- ![Workflow](images\Workflow.png) ServiceDesk.SoftwareRequest.Delivery.package

Each has it's own Process

- ServiceDesk.SoftwareRequest.Approval
- ServiceDesk.SoftwareRequest.Delivery

ServiceIds

- SD-SR-APPROVAL
- SD-SR-DELIVERY

Libraries ([DLLs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f4cef159-76c3-4b5b-9287-94aee6bec214&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments))

- ![DLLs](images\DLLs.png) ServiceDesk.SoftwareRequest.Automation.dll
- ![DLLs](images\DLLs.png) ServiceDesk.SoftwareRequest.Core.dll

The [Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=24530d5f-01a3-464d-846b-01482ee0c85e&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments) Article explains what SQL is used, these Components are taken from the following Projects:
  
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

I'll add more indepth explainations of the two WFs soon.

[![Protirus.png](images\Protirus.png)](https://protirus.com/)
