---
title: ServiceDesk - API - Incident
tags:
    - ServiceDesk
    - API
author: AlexHedley
# description: 
# articleId: 
published: 2018-10-01
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-api-incident?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

<?# Markdown ?>
<?!^ "./../includes/posts/servicedesk-api.md" /?>
<?#/ Markdown ?>

| ServiceDesk Version: | 8.5 |
| --- | --- |

> ### Incident
> 
> Allows the creation, modification and resolution of Incidents in ServiceDesk. The Incident Management module must be installed in ServiceDesk in order to use this service.
> 
> |  | API | Description |
> | --- | --- | --- |
> | POST | api/incident | Creates a new incident in ServiceDesk using the information provided |
> | PUT | api/incident/{incidentSessionId} | Can be used to modify certain fields on an existing incident, including title, description, impact/urgency and classification information. The state of the incident workflow will not be affected |
> | PATCH | api/incident/{incidentSessionId} | Resolves an existing incident that is in the work/resolve state using the closeCode and resolution values provided as part of the inbound Incident object. These two fields are required. All others are ignored. |
> | GET | api/incident/{incidentSessionId} | Returns the incident identified by the session id, regardless of the incident's state. |

---
  
## POST

> Creates a new incident in ServiceDesk using the information provided

    POST api/incident

## Request Information
  
### URI Parameters
  
*None*
  
### Body Parameters

    Incident

| Name | Description | Type | Additional information |
| --- | --- | --- | --- |
| SessionId | This is the unique identifier for an incident and can be used to query the API for updates on an existing incident. | globally unique identifier | None. |
| ProcessId | A more user-friendly identifier, like a "ticket number" for the incident. | string | None. |
| IncidentName | The title or name given to the incident when it is created | string | None. |
| IncidentDescription | Details of the incident submitted at the time of creation | string | None. |
| IncidentType | Incidents can be categorized into broad types such as "Break/Fix" or "How To". Acceptable incident types are configured within the ServiceDesk instance (in the ServiceDeskSettings application profile). | string | None. |
| AffectedUserEmail | The primary email address of the known ServiceDesk user who is affected by this incident. Incidents, according to ITIL, always affect a specific user. An "issue" affecting more than one user is called a Problem. So AffectedUserEmail is required. | string | None. |
| Classification | The classification is a hierarchical value where each node is separated by '.'. Like IncidentType, acceptable classification values are configured in the ServiceDesk instance, in this case, under Admin &gt; Data &gt; Hierarchy Data Service. The classification zeroes in on an area of expertise or responsibility within an IT organization. An example is "Hardware.Desktop.Disk". | string | None. |
| Impact | One of the components that is used (according to ITIL) to determine priority. The impact of an incident is breadth of the incident's effects across an organization. This can be asserted by the user submitting the incident but it is often modified by the technician who works it. | string | None. |
| Urgency | One of the components that is used to determine priority. The urgency of an incident describes to what degree the affected user's work is impeded. This can be asserted by the submitting user but it is often modified by the technician who works it. Acceptable values are set within the ServiceDesk instance. | string | None. |
| Priority | An incident's priority can be set directly, but most often it is derived from the combination of impact and urgency. Incident priority values are defined in the ServiceDeskSettings application profile in the ServiceDesk instance (along with Impact and Urgency values). The matrix that determines priority as a function of impact and urgency can be edited under the Incident Management process automation dashboard. Acceptable values are set within the ServiceDesk instance. | string | None. |
| AffectedLocationId | An incident can optionally be linked to a Location within the CMDB. | globally unique identifier | None. |
| AffectedDepartmentId | An incident can optionally be linked to a Department within the CMDB | globally unique identifier | None. |
| Status | This value is read-only. This is the current status of the incident workflow. | string | None. |
| Resolution | Must be provided when resolving an incident. This is free-text that should describe how/why the incident was resolved. According to ITIL "resolution" means that the affected user's ability to perform his or her work is restored. | string | None. |
| CloseCode | Must be provided when resolving an incident. This a quick indicator of how/why an incident was closed. Acceptable values are defined within the ServiceDesk instance. | string | None. |

### Request Formats

    application/json, text/json

    {
      "sessionId": "6b8f3da6-ed34-4e73-87b2-d31ff2c65e8d",
      "processId": "sample string 2",
      "incidentName": "sample string 3",
      "incidentDescription": "sample string 4",
      "incidentType": "sample string 5",
      "affectedUserEmail": "sample string 6",
      "classification": "sample string 7",
      "impact": "sample string 8",
      "urgency": "sample string 9",
      "priority": "sample string 10",
      "affectedLocationId": "1419220b-67cd-4a75-a3a3-54c6e1e90f3f",
      "affectedDepartmentId": "3e7e3c20-a18c-4b10-ab57-00f6b28ad300",
      "status": "sample string 13",
      "resolution": "sample string 14",
      "closeCode": "sample string 15"
    }

### Response Formats

---
  
## PUT

> Can be used to modify certain fields on an existing incident, including title, description, impact/urgency and classification information. The state of the incident workflow will not be affected

    PUT api/incident/{incidentSessionId}

## Request Information
  
### URI Parameters

| Name | Description | Type | Additional information |
| --- | --- | --- | --- |
| incidentSessionId |  | globally unique identifier | Required |

### Body Parameters
  
*As above*
  
### Request Formats
  
*As above*
  
### Response Formats

---
  
## PATCH

> Resolves an existing incident that is in the work/resolve state using the closeCode and resolution values provided as part of the inbound Incident object. These two fields are required. All others are ignored.

    PATCH api/incident/{incidentSessionId}

## Request Information
  
### URI Parameters

| Name | Description | Type | Additional information |
| --- | --- | --- | --- |
| incidentSessionId |  | globally unique identifier | Required |

### Body Parameters

| Name | Description | Type | Additional information |
| --- | --- | --- | --- |
| Resolution | Must be provided when resolving an incident. This is free-text that should describe how/why the incident was resolved. According to ITIL "resolution" means that the affected user's ability to perform his or her work is restored. | string | None. |
| CloseCode | Must be provided when resolving an incident. This a quick indicator of how/why an incident was closed. Acceptable values are defined within the ServiceDesk instance. | string | None. |

### Request Formats

    application/json, text/json

    {
      "resolution": "sample string 14",
      "closeCode": "sample string 15"
    }

### Response Formats

---
  
### GET

> Returns the incident identified by the session id, regardless of the incident's state.

    GET api/incident/{incidentSessionId}

## Request Information
  
### URI Parameters

| Name | Description | Type | Additional information |
| --- | --- | --- | --- |
| incidentSessionId |  | globally unique identifier | Required |

### Body Parameters
  
*None.*
  
### Response Formats

    Incident

---

[![Protirus](images\Protirus.png)](https://www.protirus.com/)
