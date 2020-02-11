---
title: Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite
tags:
    - Workflow
    - REST
    - 7.6
    - Mobility Suite
author: AlexHedley
# description: 
# articleId: 
published: 2015-05-06
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/using-the-rest-generator-response?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I will explain how to use the REST Generator within [Workflow](http://www.symantec.com/connect/workflow-servicedesk).

This builds upon a past [article](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) but shows using Parameters to make the component more flexible.
  
Follow up articles
  
- [Workflow - REST Generator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0c51c681-c801-4bcb-a02d-2c9c33c76f78&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Response Content) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70c640bd-f482-4db4-b56b-3770a85df85d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (PATHs) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c884d3-48d6-4f07-abfa-b6826cf35ae8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - Read Write JSON](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d8050704-5515-4e3c-8f82-0bc67a8260dc&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - REST - Response Header](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=92aa8f35-4dda-4afd-8639-1452c5e7e666&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

I'm going to be using the RESTful APIs available in to us in the [Mobility Suite](http://www.symantec.com/mobility/).
  
To Test an APIs you could use a Chrome Plugin called ![PostmanLogo.png](images\article-3366661-files_PostmanLogo.png)Postman [[http://www.getpostman.com/](http://www.getpostman.com/)] or on a Mac there is an App you can get called Cocoa Rest Client [[http://mmattozzi.github.io/cocoa-rest-client/](http://mmattozzi.github.io/cocoa-rest-client/)]
  
Most APIs will require a Key to use them, make sure you have this to hand but don't share it.
  
We shall work with the Mobility API.

- [v5.2](http://www.symantec.com/business/support/index?page=content&amp;id=DOC8151)
- [v5.1](http://www.symantec.com/business/support/index?page=content&amp;id=DOC7685)
- [v4.4](http://www.symantec.com/business/support/index?page=content&amp;id=DOC7372)

Login to your Tennant [#.appcenterhq.com/] [[https://myappcenterh.appcenterhq.com/admin/landing](https://myappcenterh.appcenterhq.com/admin/landing)]
  
Go to Admin Console. If you are in the App Store click on the top right hand link [Admin Console].
  
v5.2 - **Settings** | **Mobility Manager configuration** | **APIs**
  
**** (v5.1 Admin | Settings | APIs)
  
Click on the "Create New Access Key"
  
**![Data API.png](images\article-3366661-files_Data+API.png)**
  
Copy this Key as we will be using it soon.
  
Now go to your Workflow Server.
  
Open ![Workflow.png](images\article-3366661-files_Workflow.png) **Workflow Manager**.
  
**File** | **New Project** and create a new ![Forms (Web).png](images\Forms%2520%2528Web%2529.png) **Forms (Web)** Project.
  
Give this a name (*POC\_AppCenter\_WEB*).
  
![New Project - Forms (Web).png](images\New%2520Project%2520-%2520Forms%2520%2528Web%2529.png)
  
In the Project Pane click on the top level Project ![Project.png](images\article-3366661-files_Project.png) POC\_AppCenter\_WEB
  
Go to the **Properties** tab and click **Add Property**, give it a 'name' of *API\_KEY* with the 'value' of the *key* you copied before.

| name | API\_KEY |
| --- | --- |
| value | &lt;your api key&gt; |

Encode this using either [http://meyerweb.com/eric/tools/dencoder/](http://meyerweb.com/eric/tools/dencoder/) or in Fiddler [[http://www.telerik.com/fiddler](http://www.telerik.com/fiddler)] Tools | Text Wizard... (Ctrl+E)
  
![Project - Properties - Add Property.png](images\article-3366661-files_Project+-+Properties+-+Add+Property.png)
  
This will now be available to you in your Project.
  
(I like to make these as Profile Properties in Process Manager so they can be shared across Projects)

Choose an API you'd like to use. We shall get a list of Apps.
  
[https://&lt;tenant&gt;.appcenterhq.com/api1/apps](https://&lt;tenant&gt;.appcenterhq.com/api1/apps)

Now that the Project is set up we can create the Generator.
  
Back in the main Workflow Manager window click on
  
**File** | **New Project** and create a new ![Int.png](images\article-3366661-files_Int.png) **Integration** Project.
  
Give this a name (*POC\_REST\_INT*).
  
![New Project - Integration.png](images\article-3366661-files_New+Project+-+Integration.png)
  
Scroll down to **Enterprise Resources** and choose the new **REST Generator**.
  
Give the Generator a name (*AppCenter*) and click OK.
  
![Create Generator_0.png](images\article-3366661-files_Create+Generator_0.png)
  
Put in your variables:

| Base URL: | https://**#**.appcenterhq.com/ |
| --- | --- |
| Namespace: | AppCenter |

\* Replace **#** with your Tenant name
  
![1. REST Service URL_0.png](images\article-3366661-files_1.+REST+Service+URL_0.png)
  
Click **Next**.
  
Now if we choose the API.
  
Add a NAME, choose your METHOD, and add the API.

| Name | Apps |
| --- | --- |
| Method | GET |
| URL | api1/apps?[urlparams] |

You need to Save or click Next then Back to make the Properties available.
  
Click on Properties (along the Top)
  
Your **urlparams** will show. give it a Type and be sure to uncheck the **URL Encode** option.
  
![2. Components.png](images\article-3366661-files_2.+Components.png)
  
Now we want to configure the Response Content.
  
Click on the ellipse (...)
  
Choose JSON as the Format and click on 'Create' the 'Create From Request'
  
![2. Components (1)_0.png](images\2.%2520Components%2520%25281%2529_0.png)
  
Put in your params

    start=0&limit=100&api_key=##

\*paste in your encoded api\_key (we will use the Property later in the WF)

| **Warning!**Passing the API key as a query parameter is not recommended and is deprecated.<br>
			<br>Support for passing the key via URL parameters will be removed in the near future. |
| --- |

Click Next.
  
![Request (1).png](images\Request%2520%25281%2529.png)
  
It will then show the return.
  
![Request (2).png](images\Request%2520%25282%2529.png)
  
It will then be selected as your Data Type.
  
![Response Content.png](images\article-3366661-files_Response+Content.png)
  
Click on the 'Edit' to see the Data Types that have been created.
  
![Data Types.png](images\article-3366661-files_Data+Types.png)
  
Finally click **Finish**.
  
OK the next screen then **Recompile and Close**.
  
(Add an Icon and any Description etc.)
  
![Help Editor.png](images\article-3366661-files_Help+Editor.png)
  
Back to the sample Project.
  
Add this newly created Library.
  
![Project.png](images\article-3366661-files_Project.png) Project | Libraries | Add...
  
Select the dll, double click or click **Add** then click **OK**. (Untick Publish)
  
Find the Component and add it into your Workflow.
  
![Workflow (1).png](images\Workflow%2520%25281%2529.png)
  
Double Click and add in your Parameters.

    start=0&limit=100&api_key=[[ProjectProperties].api_key]

Add a Web Form and display the data.
  
![Workflow (2).png](images\Workflow%2520%25282%2529.png)
  
Run the Form.
  
![Workflow (3).png](images\Workflow%2520%25283%2529.png)
  
Follow up articles

- [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

[![Protirus.png](images\article-3366661-files_Protirus.png)](http://protirus.com/)
