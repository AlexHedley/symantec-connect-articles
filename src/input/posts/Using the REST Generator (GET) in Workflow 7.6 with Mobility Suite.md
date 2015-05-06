---
title: Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite
tags:
    - Workflow
    - Mobility Suite
    - REST
    - 7.6
author: AlexHedley
# description: 
published: 2015-05-06
---

In this Article I will explain how to use the REST Generator within [Workflow](http://www.symantec.com/connect/workflow-servicedesk).

This builds upon a past [article](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments) but shows using Parameters to make the component more flexible.

Follow up articles

*   [Workflow - REST Generator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0c51c681-c801-4bcb-a02d-2c9c33c76f78&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments)
*   [Using the REST Generator in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments)
*   [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments)
*   [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments)
*   [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments)
*   [Using the REST Generator (Response Content) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70c640bd-f482-4db4-b56b-3770a85df85d&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments)
*   [Using the REST Generator (PATHs) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c884d3-48d6-4f07-abfa-b6826cf35ae8&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments)
*   [Workflow - Read Write JSON](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d8050704-5515-4e3c-8f82-0bc67a8260dc&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments)
*   [Workflow - REST - Response Header](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=92aa8f35-4dda-4afd-8639-1452c5e7e666&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments)

I'm going to be using the RESTful APIs available in to us in the [Mobility Suite](http://www.symantec.com/mobility/).

To Test an APIs you could use a Chrome Plugin called ![PostmanLogo.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_PostmanLogo.png)Postman [[http://www.getpostman.com/](http://www.getpostman.com/)] or on a Mac there is an App you can get called Cocoa Rest Client [[http://mmattozzi.github.io/cocoa-rest-client/](http://mmattozzi.github.io/cocoa-rest-client/)]

Most APIs will require a Key to use them, make sure you have this to hand but don't share it.

We shall work with the Mobility API.

*   [v5.2](http://www.symantec.com/business/support/index?page=content&id=DOC8151)
*   [v5.1](http://www.symantec.com/business/support/index?page=content&id=DOC7685)
*   [v4.4](http://www.symantec.com/business/support/index?page=content&id=DOC7372)

Login to your Tennant [[#.appcenterhq.com/](#.appcenterhq.com/)] [[https://myappcenterh.appcenterhq.com/admin/landing](https://myappcenterh.appcenterhq.com/admin/landing)]

Go to Admin Console. If you are in the App Store click on the top right hand link [Admin Console].

v5.2 - **Settings** | <span>**Mobility Manager configuration** | **APIs**</span>

<span> (</span>v5.1 Admin | Settings | APIs)

Click on the "Create New Access Key"

**![Data API.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_Data API.png)**

Copy this Key as we will be using it soon.

Now go to your Workflow Server.

Open ![Workflow.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_Workflow.png) **Workflow Manager**.

**File** | **New Project** and create a new ![Forms (Web).png](/connect/sites/default/files/users/user-2946791/Forms%20%28Web%29.png) **Forms (Web)** Project.

Give this a name (_POC_AppCenter_WEB_).

![New Project - Forms (Web).png](/connect/sites/default/files/users/user-2946791/New%20Project%20-%20Forms%20%28Web%29.png)

In the Project Pane click on the top level Project ![Project.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_Project.png) POC_AppCenter_WEB

Go to the **Properties** tab and click **Add Property**, give it a 'name' of _API_KEY_ with the 'value' of the _key_ you copied before.

<table>

<tbody>

<tr>

<td>name</td>

<td>API_KEY</td>

</tr>

<tr>

<td>value</td>

<td><your api key></td>

</tr>

</tbody>

</table>

Encode this using either [http://meyerweb.com/eric/tools/dencoder/](http://meyerweb.com/eric/tools/dencoder/) or in Fiddler [[http://www.telerik.com/fiddler](http://www.telerik.com/fiddler)] Tools | Text Wizard... (Ctrl+E)

![Project - Properties - Add Property.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_Project%20-%20Properties%20-%20Add%20Property.png)

This will now be available to you in your Project.

(I like to make these as Profile Properties in Process Manager so they can be shared across Projects)

Choose an API you'd like to use. We shall get a list of Apps.

[https://<tenant>.appcenterhq.com/api1/apps](https://<tenant>.appcenterhq.com/api1/apps)

Now that the Project is set up we can create the Generator.

Back in the main Workflow Manager window click on

**File** | **New Project** and create a new ![Int.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_Int.png) **Integration** Project.

Give this a name (_POC_REST_INT_).

![New Project - Integration.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_New%20Project%20-%20Integration.png)

Scroll down to **Enterprise Resources** and choose the new **REST Generator**.

Give the Generator a name (_AppCenter_) and click OK.

![Create Generator_0.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_Create%20Generator_0.png)

Put in your variables:

<table>

<tbody>

<tr>

<td>Base URL:</td>

<td>https://**#**.appcenterhq.com/</td>

</tr>

<tr>

<td>Namespace:</td>

<td>AppCenter</td>

</tr>

</tbody>

</table>

* Replace **#** with your Tenant name

![1. REST Service URL_0.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_1.%20REST%20Service%20URL_0.png)

Click **Next**.

Now if we choose the API.

Add a NAME, choose your METHOD, and add the API.

<table>

<tbody>

<tr>

<td>Name</td>

<td>Apps</td>

</tr>

<tr>

<td>Method</td>

<td>GET</td>

</tr>

<tr>

<td>URL</td>

<td>api1/apps?[urlparams]</td>

</tr>

</tbody>

</table>

You need to Save or click Next then Back to make the Properties available.

Click on Properties (along the Top)

Your **urlparams** will show. give it a Type and be sure to uncheck the **URL Encode** option.

![2. Components.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_2.%20Components.png)

Now we want to configure the Response Content.

Click on the ellipse (...)

Choose JSON as the Format and click on 'Create' the 'Create From Request'

![2\. Components (1)_0.png](/connect/sites/default/files/users/user-2946791/2.%20Components%20%281%29_0.png)

Put in your params

<pre>start=0&limit=100&api_key=##</pre>

*paste in your encoded api_key (we will use the Property later in the WF)

<table>

<tbody>

<tr>

<td>

**Warning!** Passing the API key as a query parameter is not recommended and is deprecated.

Support for passing the key via URL parameters will be removed in the near future.

</td>

</tr>

</tbody>

</table>

Click Next.

![Request (1).png](/connect/sites/default/files/users/user-2946791/Request%20%281%29.png)

It will then show the return.

![Request (2).png](/connect/sites/default/files/users/user-2946791/Request%20%282%29.png)

It will then be selected as your Data Type.

![Response Content.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_Response%20Content.png)

Click on the 'Edit' to see the Data Types that have been created.

![Data Types.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_Data%20Types.png)

Finally click **Finish**.

OK the next screen then **Recompile and Close**.

(Add an Icon and any Description etc.)

![Help Editor.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_Help%20Editor.png)

Back to the sample Project.

Add this newly created Library.

![Project.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_Project.png) Project | Libraries | Add...

Select the dll, double click or click **Add** then click **OK**. (Untick Publish)

Find the Component and add it into your Workflow.

![Workflow (1).png](/connect/sites/default/files/users/user-2946791/Workflow%20%281%29.png)

Double Click and add in your Parameters.

<pre>start=0&limit=100&api_key=[[ProjectProperties].api_key]</pre>

Add a Web Form and display the data.

![Workflow (2).png](/connect/sites/default/files/users/user-2946791/Workflow%20%282%29.png)

Run the Form.

![Workflow (3).png](/connect/sites/default/files/users/user-2946791/Workflow%20%283%29.png)

Follow up articles

*   [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments)
*   [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments)

[![Protirus.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3366661-files_Protirus.png)](http://protirus.com/)
