---
title: Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite
# tags:
#     - 
author: AlexHedley
# description: 
published: 2015-05-06
---

In this Article I'm going to show you how to use HEADERS in the REST Component.
  
This builds upon a past [article](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) but shows using Parameters in Headers.
  
- [Workflow - REST Generator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0c51c681-c801-4bcb-a02d-2c9c33c76f78&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Response Content) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70c640bd-f482-4db4-b56b-3770a85df85d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (PATHs) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c884d3-48d6-4f07-abfa-b6826cf35ae8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - Read Write JSON](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d8050704-5515-4e3c-8f82-0bc67a8260dc&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - REST - Response Header](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=92aa8f35-4dda-4afd-8639-1452c5e7e666&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

I noted before that

| **Warning!**Passing the API key as a query parameter is not recommended and is deprecated.<br>
			<br>Support for passing the key via URL parameters will be removed in the near future. |
| --- |

So to rectify this we can pass it in the Header.
  
When you're creating the REST Generator there is a "**Headers...**" button, click this.
  
Now add the requried values.

| Content-Type | application/json |
| --- | --- |
| X-Nukona-API-Key-v1 | [lockapikey] |

Here [lockapikey] is a parameter denoted by the square brackets [ ].
  
If you have multiple methods make sure to name this apikey differently each time or you will get an error.
  
This will then be available within the Workflow.
  
![Request Headers.png](images\article-3412071-files_Request+Headers.png)
  
Once completed you can then set the Properties on your variable.
  
![Component Properties.png](images\article-3412071-files_Component+Properties.png)
  
Now in your Workflow you can set the API Key dynamically.
  
I like to use Profile Properties within Process Manager, so there is one place to maintain/administer it.
  
![REST Generator General.png](images\article-3412071-files_REST+Generator+General.png)
  
There is also a StatusCode you can get returned from the REST Generator, give this a name, but to use it you will need to declare it before.
  
![REST Generator HTTP.png](images\article-3412071-files_REST+Generator+HTTP.png)
  
Use an Add Data Element![Data_Add.png](images\article-3412071-files_Data_Add.png) and give it the same name.
  
![Add Data Element Configuration.png](images\article-3412071-files_Add+Data+Element+Configuration.png)
  
You can then use this Status Code for logging etc

Previous Articles

- [Using the REST Generator in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

[![Protirus.png](images\article-3412071-files_Protirus.png)](http://protirus.com/)
