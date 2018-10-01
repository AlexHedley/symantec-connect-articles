---
title: ServiceDesk - API - Extending
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

> ## Extending the API
> 
> 
> It is possible to extend the API by including a custom assembly containing additional controllers in the Extensions folder under the bin directory. Any controllers found here will be registered as endpoints. There are a few things to note regarding these extensions:
> 
> 
> Attribute-based routing does not work (so you cannot set the route using an attribute on the controller class). Instead the API requires that your controllers follow the routing template “api/{controller}/{id}” meaning that the controller class must be named [Type Name]Controller and the GET, PUT and PATCH methods must take a string or GUID called “id” as their first parameter. These are standard REST conventions anyway.
> 
> 
> If you want xmldoc comments attached to your controllers and types to appear in the Help page of the UI, you’ll need to manually place the genereated xml document for your project into the App\_Data folder of the API.
> 
> 
> Be sure to add this code at the top of your controller methods, unless you intend for your method to be accessible even if the API is disabled and/or intend to allow sessionless access:
> 
> 
> 
>     VerifyApiEnabled();
>     VerifySession();
> 
> 
> 
> The first line will cause a 403 to be returned when the ApiEnabled config setting is set to false or is missing. The second will cause a 403 to be returned unless the session is verified. If you want to allow sessionless access to a method, don't include this line AND add an AllowAnonymousAttribute to the controller method.

---
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
