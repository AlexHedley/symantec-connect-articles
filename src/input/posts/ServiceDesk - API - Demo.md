---
title: ServiceDesk - API - Demo
# tags:
#     - 
author: AlexHedley
# description: 
published: 2018-10-01
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
