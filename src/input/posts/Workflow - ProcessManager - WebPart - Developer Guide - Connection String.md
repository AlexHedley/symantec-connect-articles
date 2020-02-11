---
title: Workflow - ProcessManager - WebPart - Developer Guide - Connection String
tags:
    - Workflow
    - Process Manager
    - WebPart
    - Developer Guide
author: AlexHedley
# description: 
# articleId: 
published: 2017-07-11
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-processmanager-webpart-8?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article we will see how to get the WF/PM Connection String to use within the WebPart.
  
Articles
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=aa0478d7-5f5a-4be4-8369-4c74f963deeb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=36a9f5ee-ab0b-42e7-a75e-590ba4f256ec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a3b54e8a-7492-4397-8512-8828defe25a7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74973282-5d27-4b12-a0d3-9ad29d38a2ce&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c1b3103c-afad-45f8-9f17-244fff752121&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other WebParts
- [Controls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c20f9b40-20f8-4693-937a-7ca431c4d7ce&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) a WebPart
- WF/PM [Connection String](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=849d26ef-084e-426b-a064-fbb86730e6b8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- Connecting to [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=77434eb5-7ee1-4bb4-bef1-ef566cce61fb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to retrieve data

- - -
  
Currently the previous Articles have shown static data either hardcoded into the WebPart, Input by the User when the configured or information available from the current Session of the PM instance.
  
To make it more useful we would need to be able to talk to the Process Manager database to retrieve data to display.
  
Where is this? Open the ![Workflow](images\Workflow.png) Workflow Explorer exe.
  
SymQ Configuration
  
SymQ_Local_Defaults
  
Scroll down to 'local.orm'
  
Edit to see the 'Sql Connection String'

    Data Source=SERVER;Initial Catalog=ProcessManager;Integrated Security=True;Pooling=True;Connect Timeout=30​

There is also the 'local.workflowsqlexchange-'.
  
Replace with your Server name and Database Instance.
  
We could hardcode this in the code for the WebPart but this wouldn't be very useful as if it ever changed you'd have to update the rebuild/redeploy the DLL.
  
Another option would be to create another web.config just for our WebPart and reference that.
  
We could also decrypt the Process Manager web.config as shown in a custom Script component added to a sample Workflow Project.

- [ServiceDesk 7.5 Track Assignments via Process Type Actions](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=b4d5684c-792b-4428-9988-3a8dcb568102&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)

We need a way to get this in code, thankfully "[bcason](https://www.symantec.com/connect/user/bcason)" has already shown us how.

> Workflow/ServiceDesk - How To Extract the (local.orm) Sql Connection String  
> 	Code (Script) Component Sql Connection String Extractor  
> 	[https://www.symantec.com/connect/blogs/workflowservicedesk-how-extract-localorm-sql-connection-string](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=28b50423-aa5a-4d68-8521-adbb306ee7ee&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)

Amend this to use as a class in our Project.
  
This is the reason for adding '*Symantec.SymQ.dll*' in a previous Article.
  
We can then call this method wherever we need a Connection String. This is shown in the [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=77434eb5-7ee1-4bb4-bef1-ef566cce61fb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) Article.
  
- - -
  
Related

| Coming Soon.... |
| --- |

local.orm SQL Connection String - Component

- Workflow Component Article
    - [https://www.symantec.com/connect/articles/localorm-sql-connection-string](https://www.symantec.com/connect/articles/localorm-sql-connection-string)
- Download
    - [https://www.symantec.com/connect/downloads/workflow-localorm-sql-connection-string-component](https://www.symantec.com/connect/downloads/workflow-localorm-sql-connection-string-component)

- - -
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
