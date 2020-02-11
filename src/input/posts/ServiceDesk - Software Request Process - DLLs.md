---
title: ServiceDesk - Software Request Process - DLLs
tags:
    - ServiceDesk
    - Software Request Process
author: AlexHedley
# description: 
# articleId: 
published: 2017-10-10
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-software-request-proc-2?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this series of Articles I'm going to explain how the new **Software Request Process** works in [ServiceDesk](https://www.symantec.com/products/service-desk) 8.1.
  
This Article explains the new DLLs that shipped with the Process and has links to the component pages.

Table Of Contents
  
- [Index](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=253f9b2f-045e-4e05-acb9-fcc37005f674&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Overview](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a5fdba6d-707b-44be-a051-b08e5a5cfe19&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Config](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e3acdfdc-8b09-4ca7-afb5-821c9cce9301&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SMP](https://www.symantec.com/connect/articles/servicedesk-software-request-process-smp)
- [Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=24530d5f-01a3-464d-846b-01482ee0c85e&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Hidden Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f39346c9-799f-4d1b-ba9b-7f0910cd9c74&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=28879800-dd5e-436b-8f8b-9bc7301fbb1e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [WFs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=736fee28-7f45-497e-b208-b3de50cde839&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [DLLs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f4cef159-76c3-4b5b-9287-94aee6bec214&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)

For this Article I will list the new Components in the DLLs that have been added for the Process.
  
I'll be adding [Component Articles](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=85f6ec73-8a87-43b9-a87f-743497fa0fb0&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) as an when, check back for updated links.
  
If you check the usual *customlib* folder you will find the new DLLs.

    [Install Drive]:\Program Files\Symantec\Workflow\Shared\customlib\

**![DLL](images\dll.png) ServiceDesk.SoftwareRequest.Core.dll**

- ServiceDesk.SoftwareRequest.Core
    - RequestedSoftwareDataService
    - SoftwareRequestDataService
        - ListSoftwareInRequest

- ServiceDesk.SoftwareRequest.Core.Components
    - [GetRequestedSoftwareBySessionIdComponent](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9424808e-fdc2-4c41-aca4-c14aa838b954&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [GetSoftwareRequestBySessionIdComponent](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=facb821e-573e-45cc-832e-d881aea77e37&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [ListAvailableSoftwareComponent](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=79dcc4d5-42bb-4946-8484-b8912a7ea7c6&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [ListDeliveryPoliciesForManagedDeliveryPolicy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e1413deb-6b36-4008-b34d-19225f14b823&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [ListFiltersForTargetComponent](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=23fcefd1-e78c-452f-bd24-f6e12b1631dc&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [ListReleasesForSoftwareProductComponent](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f94e55e1-a628-4057-8223-6cf674215043&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [SaveRequestedSoftwareComponent](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a0ba3d1e-5e37-403b-a47f-4a3562c3a852&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [SaveSoftwareRequestComponent](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f2c0071f-a4f5-4ae8-b57e-c45ca770893e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - SoftwareRequestProcessComponent
    - [StartSoftwareDeliveryComponent](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=5fa352cb-728a-4e80-8e98-bb3f3afbe7fb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

- ServiceDesk.SoftwareRequest.Core.DataTypes
    - AvailableSoftware
    - ManagedDeliveryPolicy
    - RequestedSoftware
    - RequestedSoftwareStatus
    - RequestedSoftwareType
    - ResourceTargetFilter
    - SdAmTaskCompleteMessage
    - SdConfirmationTaskCompleteMessage
    - SdDaTaskCompleteMessage
    - SdDaTaskPauseMessage
    - SdHoldTaskResumeMessage
    - SdRemediationTaskCompleteMessage
    - SdSmTaskCompleteMessage
    - SoftwareDeliveryTaskAssignmentType
    - SoftwareDeliveryTaskType
    - SoftwareLicenseInfo
    - SoftwareLicenseType
    - SoftwareRelease
    - SoftwareRequest
    - SoftwareRequestTaskAssignmentType
    - SoftwareRequestTaskType
    - SrApprovalTaskCompleteMessage
    - SrApprovalTaskPauseMessage
    - SrDeliveryFlowCompleteMessage
    - SrHoldTaskResumeMessage
    - SrPendingTaskCloseMessage
    - UserDevice

- ServiceDesk.SoftwareRequest.Core.Properties
    - AssemblyDataHandlersAttribute
    - Settings
    - StringResources

- ServiceDesk.SoftwareRequest.Core.SoftwareDeliveryService
    - KeyValueDataType
    - SoftwareDeliveryService
    - StartSoftwareDeliveryCompletedEventArgs
    - StartSoftwareDeliveryReturn

**![DLL](images\dll.png) ServiceDesk.SoftwareRequest.Automation.dll**

- ServiceDesk.SoftwareRequest.Automation.Actions
- ServiceDesk.SoftwareRequest.Automation.Conditions
- ServiceDesk.SoftwareRequest.Automation.Properties
- ServiceDesk.SoftwareRequest.Automation.RulesetArguments
- ServiceDesk.SoftwareRequest.Automation.TemplateContexts

---
  
Documentation
  
Symantec ServiceDesk 8.1 Documentation
  
[https://www.symantec.com/connect/forums/symantec-servicedesk-81-documentation](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=cfc7ef69-2520-4a10-9344-7a5de64ee9f8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=digestviewer#bmcfc7ef69-2520-4a10-9344-7a5de64ee9f8)

- Release Notes - [http://www.symantec.com/docs/DOC9618](http://www.symantec.com/docs/DOC9618)

| Feature | Description |
| --- | --- |
| Added Software request process | From this release onwards, you can create Software delivery requests, manage these requests and deliver software to the client computers using computer filters. |

[![Protirus](images\Protirus.png)](https://protirus.com/)
