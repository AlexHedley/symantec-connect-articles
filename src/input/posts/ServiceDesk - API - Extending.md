---
title: ServiceDesk - API - Extending
tags:
    - ServiceDesk
    - API
author: AlexHedley
# description: 
# articleId: 
published: 2018-10-01
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-api-extending?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

<?# Markdown ?>
<?!^ "./../includes/posts/servicedesk-api.md" /?>
<?#/ Markdown ?>

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
