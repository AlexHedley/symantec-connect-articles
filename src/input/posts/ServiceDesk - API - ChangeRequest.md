---
title: ServiceDesk - API - ChangeRequest
tags:
    - ServiceDesk
    - API
author: AlexHedley
# description: 
# articleId: 
published: 2018-10-01
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-api-changerequest?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

- [Index](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d54b726c-cf91-42f3-a0fe-436a3d559c14&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Configuring](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=becb0e82-72b6-40da-ad93-e5f3aad8afcd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Extending](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=6d994fd8-1056-49a7-8228-488a03300d41&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Endpoints
    - [Authorization](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=30d60bd5-f273-41b4-a1ff-67a40becd4dd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [ChangeRequest](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9a8c56d0-0069-49df-8f18-a4228bddd4a8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [Incident](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=bf651a3b-b5a6-4054-b348-3aa2c4414826&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Demo](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=739bf091-178b-4fd7-b214-0b62f4db987c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

| ServiceDesk Version: | 8.5 |
| --- | --- |

> ### ChangeRequest
> 
> Submit change requests and fetch them back. The Change Management module must be installed in your ServiceDesk environment.
> 
> |  | API | Description |
> | --- | --- | --- |
> | POST | api/changerequest | Creates a new change request in ServiceDesk using the information provided |
> | GET | api/changerequest/{changeRequestSessionId} | Gets a ChangeRequest by its session id (also known as workflow tracking id). |

---
  
## POST

> Creates a new change request in ServiceDesk using the information provided

    POST api/changerequest

## Request Information
  
### URI Parameters
  
*None*
  
### Body Parameters

    ChangeRequest

| Name | Description | Type | Additional information |
| --- | --- | --- | --- |
| SessionId | This is the unique identifier for a change request and can be used to query the API for updates on an existing change ticket. | globally unique identifier | None. |
| ProcessId | A more user-friendly identifier, like a "ticket number" for the change request. | string | None. |
| RequestTitle | The title or given name to the change request when created | string | None. |
| RequestDescription | Details os the change request submitted at the time of creation | string | None. |
| RequiredCompletionDate | The date by which this change should be completed, for planning purposes | date | None. |
| BusinessJustification | A business justification for implementing the requested change | string | None. |
| Impact | This MUST be one of the configured values for Impact in the ServiceDesk settings in ProcessManager | string | None. |
| Urgency | This MUST be one of the configured values for Urgency in the ServiceDesk settings in ProcessManager | string | None. |
| Priority | This MUST be one of the configured values for Priority in the ServiceDesk settings in ProcessManager | string | None. |
| TimeZone | Use the standard strings for time zone: https://msdn.microsoft.com/en-us/library/ms912053(v=winembedded.10).aspx | string | None. |
| ChangeType | One of the core ITIL change types. Typically, Normal should be used. The use of Emergency or Standard will change the process that's followed. See ServiceDesk documentation for details. | SimpleChangeType | None. |
| TemplateName | The name of a template to use for this change ticket. If a template is provided here, the ticket will be setup with planning information AND some of the provided fields in this payload will be overwritten from the template, so use this carefully. Templates are configured in the ProcessManager portal. | string | None. |
| RiskScore | A string indicating a "score" for the risk level of this change. How this is calculated/used, if at all, is up to you | string | None. |
| RiskAssessment | An explanation of the risk score, if provided | string | None. |
| CostOfImplementing | A string indicating and/or explaining the cost of implementing this change | string | None. |
| CostOfNotImplementing | A string indicating and/or explaining the cost of NOT implementing this change | string | None. |

---

SimpleChangeType

| Name | Value | Description |
| --- | --- | --- |
| Normal | 0 |  |
| Standard | 1 |  |
| Emergency | 2 |  |

---

### Request Formats

    application/json, text/json

    {
      "sessionId": "8c21db93-649a-4455-a1b0-3595de5f797c",
      "processId": "sample string 2",
      "requestTitle": "sample string 3",
      "requestDescription": "sample string 4",
      "requiredCompletionDate": "2018-10-03T08:36:17.9348115+01:00",
      "businessJustification": "sample string 6",
      "impact": "sample string 7",
      "urgency": "sample string 8",
      "priority": "sample string 9",
      "timeZone": "sample string 10",
      "changeType": "Normal",
      "templateName": "sample string 11",
      "riskScore": "sample string 12",
      "riskAssessment": "sample string 13",
      "costOfImplementing": "sample string 14",
      "costOfNotImplementing": "sample string 15"
    }

### Response Formats

---
  
## GET

> Creates a new change request in ServiceDesk using the information provided

    GET api/changerequest/{changeRequestSessionId}

## Request Information
  
### URI Parameters

| Name | Description | Type | Additional information |
| --- | --- | --- | --- |
| changeRequestSessionId |  | globally unique identifier | Required |

### Body Parameters
  
*None*
  
### Request Formats
  
*None*
  
### Response Formats

    ChangeRequest

---
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
