---
title: ServiceDesk - API
tags:
    - ServiceDesk
    - API
author: AlexHedley
# description: 
# articleId: 
published: 2018-10-01
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-api?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

<?# Markdown ?>
<?!^ "./../includes/posts/servicedesk-api.md" /?>
<?#/ Markdown ?>

| ServiceDesk Version: | 8.5 |
| --- | --- |

With ServiceDesk 8.5 a new REST API has been added.

> This API allows specific operations against the core ticket types within ServiceDesk. It can also be extended to support additional custom operations using a plugin pattern that lets you register your own controller libraries. This is useful if you have extended the definitions of the core ticket types to include additional properties, etc.

> The purpose of this API is to allow for closed-loop remediation scenarios involving other applications. Some application may, for example, detect events and raise alerts within your organization's data centers which require attention from an operations team which is using ServiceDesk. By leveraging this API, such applications can raise incidents and change requests in ServiceDesk and, in the case of incidents, automatically resolve them as well.

View the Details

    http://localhost/ServiceDeskApi/

See the Help

    http://localhost/ServiceDeskApi/Help

There are a few methods for

- Incident
- Change

You will need to Authorize for these to work but first check the [Configuring](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=becb0e82-72b6-40da-ad93-e5f3aad8afcd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) page to get setup.
  
---
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
