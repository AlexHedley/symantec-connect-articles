---
title: ServiceDesk - API - Authorization
tags:
    - ServiceDesk
    - API
author: AlexHedley
# description: 
# articleId: 
published: 2018-10-01
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-api-authorization?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

<?# Markdown ?>
<?!^ "./../includes/posts/servicedesk-api.md" /?>
<?#/ Markdown ?>

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
