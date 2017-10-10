---
title: ServiceDesk - Software Request Process - Config
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-10-10
---

In this Article I'm going to explain how the new **Software Request Process** works in [ServiceDesk](https://www.symantec.com/products/service-desk) 8.1 can be configured in Process Manager.

Table Of Contents
  
- [Index](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=253f9b2f-045e-4e05-acb9-fcc37005f674&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Overview](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a5fdba6d-707b-44be-a051-b08e5a5cfe19&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Config](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e3acdfdc-8b09-4ca7-afb5-821c9cce9301&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [SMP](https://www.symantec.com/connect/articles/servicedesk-software-request-process-smp)
- [Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=24530d5f-01a3-464d-846b-01482ee0c85e&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Hidden Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f39346c9-799f-4d1b-ba9b-7f0910cd9c74&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=28879800-dd5e-436b-8f8b-9bc7301fbb1e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [WFs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=736fee28-7f45-497e-b208-b3de50cde839&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [DLLs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f4cef159-76c3-4b5b-9287-94aee6bec214&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

There are a numbe of options that can be configured for the Requests.
  
Rulesets can be ran at different points in the Request.
  
Different Teams can be added to the Tasks.
  
Emails can be sent to Managers / SAM / Requestors etc.

### Application Properties
  
Firstly we will take a look at the new Application Properties that can be configured in Process Manager.
  
Login to Process Manager (As an Admin)
  
Admin | Data | Application Properties
  
ServiceDeskSettings
  
There are two new sections/categories
  
Software Delivery

| Property | Value |
| --- | --- |
| SoftwareDeliveryUrl | https://&lt;SERVER&gt;/servicedesk.softwarerequest.delivery |
| SdAssetManagementTaskTimeoutInDays | 365 |
| SdSoftwareManagementTaskTimeoutInDays | 365 |
| SdHoldTaskTimeoutInDays | 365 |
| SdConfirmationTaskTimeoutInDays | 3 |
| SdRemediationTaskTimeoutInDays | 365 |
| SdAuthorizationTaskTimeoutInDays | 365 |
| SdSoftwareProductCmdbPath | altiris/console |

Software Request

| Property | Value |
| --- | --- |
| SoftwareRequestUrl | https://&lt;SERVER&gt;/ServiceDesk.SoftwareRequest.Approval |
| SrInitialApprovalTimeoutInDays | 365 |
| SrHoldTaskTimeoutInDays | 365 |
| SrPendingTaskTimeoutInDays | 365 |

### Groups
  
Next go to
  
Admin | Users | Accounts | List Groups

- Application Users
- Software Asset Managers
- Software Librarians

### Rulesets
  
Admin | Process Automation

- Software Delivery
    - 11 Rulesets
    - 0 Email Templates
- Software Request
    - 8 Rulesets
    - 0 Email Templates

**Software Delivery**
  
Service Dashboard : SD-SR-DELIVERY

- OnDeliveryAuthorizationDenied
- OnDeliveryAuthorizationGranted
- OnDeliveryAuthorizationPaused
- OnDeliveryAuthorizationResumed
- OnDeliveryCompleted
- OnDeliveryConfirmed
- OnDeliveryFailed
- OnManagedSoftwareDeliveryStarted
- OnRemediationNeeded
- OnSoftwareManagementTaskCompleted
- OnUnmanagedSoftwareDeliveryStarted

**Software Request**
  
Service Dashboard : SD-SR-APPROVAL

- OnApprovalTaskTimedOut
- OnPendingTaskTimedOut
- OnRequestApproved
- OnRequestDenied
- OnRequestFulfilled
- OnRequestPlacedOnHold
- OnRequestReceived
- OnRequestResumed

You can configure these to send emails etc if they are triggered.

[![Protirus](images\Protirus.png)](https://protirus.com/)
