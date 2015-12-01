---
title: Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite
# tags:
#     - 
author: AlexHedley
# description: 
published: 2015-12-01
---

In this Article I will explain how to use POST requests in the REST Generator within [Workflow](http://www.symantec.com/connect/workflow-servicedesk) and [Mobility Suite](http://www.symantec.com/mobility/).

This will assume knowledge of Workflow and REST APIs and it would be helpful to read through the previous articles.
  
Previous Articles
  
- [Workflow - REST Generator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0c51c681-c801-4bcb-a02d-2c9c33c76f78&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Response Content) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70c640bd-f482-4db4-b56b-3770a85df85d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (PATHs) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c884d3-48d6-4f07-abfa-b6826cf35ae8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - Read Write JSON](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d8050704-5515-4e3c-8f82-0bc67a8260dc&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - REST - Response Header](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=92aa8f35-4dda-4afd-8639-1452c5e7e666&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

This is an example of a POST Request using the Login API of App Center

From the Documentation:

Symantec Mobility Manager 5.4 API Reference Guide

- [https://support.symantec.com/en\_US/article.DOC9124.html](https://support.symantec.com/en_US/article.DOC9124.html)

***User Authentication***  
	The API also supports converting username/password credentials into a limited-lifetime API key (token) via a login method.  
	NOTE: API keys created using the login method will not work with the on\_behalf\_of parameter.  
	**Login**  
	URL: **/api1/login**  
	Methods:  
	• GET  
	  o None  
	• POST  
	  o Description: Login to receive an API key for subsequent requests.  
	  o Encoding: application/x-www-form-urlencoded  
	  o POST parameters:  
	     username: The Mobility Suite username  
	     password: The user’s password

• Returns: On success:  
	  • status: the status “okay”  
	  • api-key: the temporary API Key (not URL encoded!)  
	  • expiry: The expiration time as a unit timestamp.

    HTTPResponse: 200
    {
      "status": "okay",
      "api-key": "<the api key>",
      "expiry": 1412046458
    }

• Return-type: application/json

• Errors

    HTTPResponse: 401
    {
      "status": "error",
      "message": "User name or password not valid",
      "code": 105
    }

    HTTPResponse: 403
    {
      "status": "error",
      "message": "User does not have permission",
      "code": 0
    }

Let's build the REST Generator first:

Add

Change the Method to "POST"

Add your further URL "api1/login"

Give it a name - "Login"

Set the 'Request Content' to "Text"

![REST Integration Library - 2 Components](images\RESTIntegrationLibrary-2Components.png)

Now for the Respone Content choose the Format (JSON)

![REST Integration Library - Response Content](images\RESTIntegrationLibrary-ResponseContent.png)

You may need to create the Response Content "Manually" instead of "Create From Request", it doesn't handle POSTs too well.

Documentation from the API provider comes in handy, just create a Data Type how you would with the INT components and DBDT or DTs.

Give it a name - LoginResponse

![REST Integration Library - 2 Components - Data Tyoes - Edit Type](images\RESTIntegrationLibrary-2Components-DataTyoes-EditType.png)

Then 3 Properties

- status
- api-key
- expiry

![REST Integration Library - 2 Components - Data Tyoes - Edit Property](images\RESTIntegrationLibrary-2Components-DataTyoes-EditProperty.png)

![REST Integration Library - 2 Components - Data Tyoes - Edit Property - JSON Options](images\RESTIntegrationLibrary-2Components-DataTyoes-EditProperty-JSONOptions.png)

Back in Workflow

Add a ![Code (Script) Component](images\CodeScriptComponent.png) Code (Script) Component

![Scripted Component Wizard - 1 Input Parameters](images\ScriptedComponentWizard-1InputParameters.png)

Map the values from your process

![Scripted Component Wizard - 1 Input Parameters (Edit Parameter Mappings)](images\ScriptedComponenWizard-1InputParametersEditParameterMappings.png)

Set the output to **Text** and give it an output of **RequestContent**

![Scripted Component Wizard - 2 Result variable](images\ScriptedComponentWizard-2Resultvariable.png)

Choose your Language, I've picked VB.NET this time but you could use C#.

![Scripted Component Wizard - 3 Source Code](images\ScriptedComponentWizard-3SourceCode.png)

    Dim escapedUsername As String
    Dim escapedPassword As String
    
    escapedUsername = Uri.EscapeDataString(username)
    escapedPassword = Uri.EscapeDataString(password)
    
    'return "username=" & username & "&password=" & password
    return "username=" & escapedUsername & "&password=" & escapedPassword

Run a test to see the output.

![Scripted Component Wizard - 4 Test Page](images\ScriptedComponentWizard-4TestPage.png)

Now add the Login component that you created from the REST Generator.

Pass in your RequestContent

![Login Editor.png](images\LoginEditor.png)

Set the StatusCode etc.

Now you can login and get an API key to work with throughout the rest of your Workflow.

Previous Articles

- [Using the REST Generator in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

[![Protirus.png](images\Protirus.png)](https://www.protirus.com/)
