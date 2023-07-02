---
title: ServiceDesk - API - Demo
tags:
    - ServiceDesk
    - API
author: AlexHedley
# description: 
# articleId: 
published: 2018-10-01
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-api-demo?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

<?# Markdown ?>
<?!^ "./../includes/posts/servicedesk-api.md" /?>
<?#/ Markdown ?>

| ServiceDesk Version: | 8.5 |
| --- | --- |

Download Postman or an API client of your choice
  
Start by creating a new Postman Collection

- ServiceDesk API

Create a new Environment

| server | localhost |
| --- | --- |
| api | ServiceDeskApi |
| IncidentSessionID | [*TestSessionId*] |

Create a new Request
  
**Token**
  
POST

    http://{server}/{api}/api/authorization/token

Add a **Header**

| Content-Type | application/json |
| --- | --- |

**Body**

    {"Username": "admin@symantec.com","Password": "###"}

Response

    "GUID"

Now the useful part, in **Tests** you can store data that is returned in the Response, in variables. Just use some JS to parse the body returned from the call and store it in a new variable called "token".

    var jsonData = JSON.parse(responseBody);
    postman.setGlobalVariable("token", jsonData);

---
  
**Incident**
  
GET

    http://{server}/{api}/api/incident/{IncidentSessionID}

Add a **Header**

| Content-Type | application/json |
| --- | --- |
| Authorization | token *{{token}}* |

Response (an Incident)

    {
        "sessionId": "GUID",
        "processId": "IM-000001",
        "incidentName": "Test",
        "incidentDescription": "Test",
        "incidentType": "How To",
        "affectedUserEmail": "alex.hedley@email.com",
        "classification": "How To",
        "impact": "Single User",
        "urgency": "Non-Urgent Service",
        "priority": "Low",
        "affectedLocationId": "00000000-0000-0000-0000-000000000000",
        "affectedDepartmentId": "00000000-0000-0000-0000-000000000000",
        "status": "Assigned",
        "resolution": null,
        "closeCode": null
    }

---

> Note anywhere using variable {variable} add an extra set of {} as these are stripped out on the page.

[![Protirus](images\Protirus.png)](https://www.protirus.com/)
