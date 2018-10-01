---
title: ServiceDesk - API - Authorization
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

> ### Authorization
> 
> Provides authentication method. The API simply passes through the authentication paradigm from ProcessManager. The API consumer is responsible for managing the provided token and handling authentication failures.
> 
> |  | API | Description |
> | --- | --- | --- |
> | POST | api/authorization/token | Attempts to authenticate using the credentials provided and returns a token if successful. The returned token must be provided as the Authentication header for all subsequent requests. If authentication fails a 403 response will be returned. |

## Request

    POST api/authorization/token

## Request Information
  
### URI Parameters
  
None
  
### Body Parameters

| Name | Description | Type | Additional information |
| --- | --- | --- | --- |
| Username |  | string | None. |
| Password |  | string | None. |

### Request Formats

    application/json, text/json

    {
      "username": "sample string 1",
      "password": "sample string 2"
    }

### Response Formats

    "00000000-0000-0000-0000-000000000000"

---
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
