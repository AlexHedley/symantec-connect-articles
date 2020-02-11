---
title: Workflow - Plugin - Developer Guide - Deploy
tags:
    - Workflow
    - Plugin
    - Developer Guide
author: AlexHedley
# description: 
# articleId: 
published: 2017-07-11
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-plugin-developer-guide?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I'm going to explain how to deploy the Plugin to a ![Workflow](images\Workflow.png) Workflow server.
  
Table of Contents[​](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=016f70af-1c51-438b-bbae-f98e86164f26&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=016f70af-1c51-438b-bbae-f98e86164f26&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=84ee5f15-df6c-44c7-8acd-e2764f0c4717&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Plugin](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=8aeca32a-9a00-4d91-b618-f6af07957e71&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2e508788-3a83-4a91-8e5b-18b28ca1cc02&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Advanced Plugin](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=5076bfd9-0b26-408c-b957-3bb5fb0b59c2&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=6d54d145-537c-40e6-86ca-b5dec2b1e972&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [WindowsForm](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80b95a29-8a1a-44ce-a616-87cf8e001dbd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

From the Guide:

> **Publishing a plugin**  
> 	To publish a plugin  
> 	1 Publish your DLL plugin from Workflow Designer.  
> 	   See “Creating a plugin for Process Manager in Workflow Designer” on page 195.  
> 	2 Move the published DLL plugin into the DLL containing your plugin class in the C:\Program Files\Altiris\Workflow Designer\Designer\Plugins directory.  
> 	   If the plugin is in this folder, Symantec Workflow can retrieve it and load it on startup.

This path might be different so change to yours.

Build your component, in Visual Studio.

> Build | Build Solution (Ctrl+Shift+B)

Check the output path from the 'Output | Build' window.

    E:\WF\Protirus.Workflow.Plugins\Protirus.Workflow.Plugins\bin\Debug\Protirus.Workflow.Plugins.dll

Copy the *dll* and add it to a folder on your WF Server.
  
You could create a Build Event that copies the output to the WF Server.

> Properties | Buld Events | Post-build event command line:

![VS - Build Events.png](images\VS-BuildEvents.png)

    xcopy "$(ProjectDir)$(OutDir)$(TargetName)$(TargetExt)" "\\WORKFLOWSERVER\e$\Program Files\Symantec\Workflow\Designer\Plugins\" /Y

This can run into problems once the WF manager is running or a Project is open, as the DLL is in use so the /Y flag can't overwrite the file.
  
You will need to close the Project/Manager and copy again.
  
One option would be to have a holding folder somewhere on the server which you copy to.

[![Protirus](images\Protirus.png)](https://www.protirus.com/)
