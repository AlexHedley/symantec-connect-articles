---
title: Using the REST Generator in Workflow 7.6
tags:
    - Workflow
    - REST
    - 7.6
    - Mobility Suite
author: AlexHedley
# description: 
# articleId: 
published: 2015-03-06
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/using-the-rest-generator-in-workflo?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I will explain how to use the REST Generator within [Workflow](http://www.symantec.com/connect/workflow-servicedesk) 7.6.
  
Follow up articles[​](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
- [Workflow - REST Generator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0c51c681-c801-4bcb-a02d-2c9c33c76f78&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Response Content) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70c640bd-f482-4db4-b56b-3770a85df85d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (PATHs) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c884d3-48d6-4f07-abfa-b6826cf35ae8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - Read Write JSON](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d8050704-5515-4e3c-8f82-0bc67a8260dc&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - REST - Response Header](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=92aa8f35-4dda-4afd-8639-1452c5e7e666&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

I'm going to be using the RESTful APIs available in to us from [http://swapi.co/](http://swapi.co/). The Star Wars API.
  
A little background:
  
REST or Representational State Transfer is an architecture style or design pattern used as a set of guidelines for creating web services which allow anything connected to a network (web servers, private intranets, smartphones, fitness bands, banking systems, traffic cameras, televisions etc.) to communicate with one another via a shared common communications protocol known as Hypertext Transfer Protocol (HTTP). The same HTTP verbs (GET, POST, PUT, DELETE etc.) used by web browsers to retrieve and display web pages, audio/video files, images etc. from remote servers and post data back to them when performing actions like filling out and submitting forms are used by all of the aforementioned devices/services to communicate with one another.
  
Link: [http://en.wikipedia.org/wiki/Representational\_state\_transfer](http://en.wikipedia.org/wiki/Representational_state_transfer)
  
To Test an APIs you could use a Chrome Plugin called ![PostmanLogo.png](images\article-3359911-files_PostmanLogo.png)Postman [[http://www.getpostman.com/](http://www.getpostman.com/)]
  
Or on a Mac there is an App you can get called Cocoa Rest Client [[http://mmattozzi.github.io/cocoa-rest-client/](http://mmattozzi.github.io/cocoa-rest-client/)]
  
Most APIs will require a Key to use them, but don't share it, luckily the Star Wars API doesn't need one.
  
Now go to your Workflow Server.
  
Open ![Workflow.png](images\article-3359911-files_Workflow.png) **Workflow Manager**.
  
**File** | **New Project** and create a new ![Forms (Web).png](images\Forms%2520%2528Web%2529.png) **Forms (Web)** Project.
  
Give this a name (*POC\_JSON\_WEB*).
  
We will be using this later to display our results.

Now back in the main Workflow Manager window click on
  
**File** | **New Project** and create a new ![Int.png](images\article-3359911-files_Int.png) **Integration** Project.
  
Give this a name (*POC\_JSON\_SW\_INT*).
  
![New Project - Integration_0.png](images\article-3359911-files_New+Project+-+Integration_0.png)
  
Scroll down to **Enterprise Resources** and choose ‘REST Generator’ and give it a name: "StarWars"
  
![Create Generator.png](images\article-3359911-files_Create+Generator.png)
  
Put in your

- Base URL: [http://swapi.co/api/](http://swapi.co/api/)
- Namespace: StarWars

then click Next.
  
![1. REST Service URL (Star Wars).png](images\1.%2520REST%2520Service%2520URL%2520%2528Star%2520Wars%2529.png)
  
Click Add.
  
Give it a name: "Planets"
  
You can change the Method to any of the following:

- GET
- PUT
- POST
- DELETE

![2. Components (1) (Star Wars).png](images\2.%2520Components%2520%25281%2529%2520%2528Star%2520Wars%2529.png)
  
Click on the ellipse (…) below ‘Response Content’.
  
Choose "JSON"
  
Then in Create choose "Create From Request"
  
![2. Components (3).png](images\2.%2520Components%2520%25283%2529.png)
  
Click Next
  
![Create From Request.png](images\article-3359911-files_Create+From+Request.png)
  
The response is then shown, click Next.
  
![Create From Request - JSON.png](images\article-3359911-files_Create+From+Request+-+JSON.png)
  
You will then see the Data Type that has been created, you edit this if necessary. Click Finish.
  
![Create From Request - DataType.png](images\article-3359911-files_Create+From+Request+-+DataType.png)
  
You will see the chosen Data Type, click OK.
  
![2. Components (4).png](images\2.%2520Components%2520%25284%2529.png)
  
Now you can click Finish and save your new Integration Project.
  
![2. Components (7).png](images\2.%2520Components%2520%25287%2529.png)
  
You can see what was generated for you.
  
![Generators Management.png](images\article-3359911-files_Generators+Management.png)

Back to your Web Forms Project.
  
Add the Library to this.
  
You can now call the INT and display the results in a Web Form.
  
![POC_JSON_WEB (2).png](images\POC_JSON_WEB%2520%25282%2529.png)
  
And your Web Page
  
![POC_JSON_WEB (3).png](images\POC_JSON_WEB%2520%25283%2529.png)
  
And there you have a way of retrieving data from an API and displaying it in a Web Form.
  
Follow up articles

- [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

[![Protirus.png](images\article-3359911-files_Protirus.png)](http://protirus.com/)
