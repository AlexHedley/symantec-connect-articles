---
title: Workflow - Component - Developer Guide - Deploy
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-11-09
---

In this Article I'm going to explain how to deploy the component to a workflow server.
  
Table of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=17aa2b9a-9092-40d0-afab-a6d8316de97d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70a9fde5-0d87-4b9d-a3be-0907567ffc00&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Help File](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80437c69-ccc3-47e6-a850-9cf3f301b340&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Logging](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63b72a9a-53b8-4d4b-bce3-5f0732b134d5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Inputs
    - [Checkbox](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74c56ef7-1119-40fe-9d5f-3c7a1d808d4c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [Dropdown / Combo](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=267159ac-b8e7-45b4-abe4-f85d78e30783&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2c3b3a6f-01d7-4157-a143-ba30c9edc930&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other Components
- [Creating Globals](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=cf54de06-be56-46ff-b937-148efa57eaec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Creating Project Properties](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4cfc07c5-404e-49b3-81b6-520d4ea43d5c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f3cf0097-06e7-42f3-a747-d0dff319c1e5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with a Web Service](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=26368883-708b-4432-999b-7064f2f25794&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

In the [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) I suggested adding a Post Build event of

    xcopy "$(ProjectDir)$(OutDir)$(TargetName)$(TargetExt)" "\\WORKFLOWSERVER\e$\Program Files\Symantec\Workflow\Shared\customlib\" /Y

Replace WORKFLOWSERVER with the name of the ![Workflow](images\Workflow.png)WF Server and e$ to your install drive.
  
Another option, which would be better is to copy the file to another folder on the server then run the following script to copy it to **customlib**.
  
If you've ever packaged up a project and ticked include custom libs there is a install.bat that is created along with the project.
  
Just update the 'LBPath' to the correct drive.

    @echo off
    if !%1 == ! goto SetDefaultLBPath
    set LBPath=%~1
    goto CheckLBPath
    :SetDefaultLBPath
    set LBPath=E:\Program Files\Symantec\Workflow
    :CheckLBPath
    if not exist "%LBPath%" (
    echo The directory "%LBPath%" does not exist!
    echo Please provide the directory where LogicBase is installed as parameter 1.
    echo Put in quotes if it is a long path.
    PAUSE
    goto :eof
    )
    if not exist "%LBPath%\Designer\bin\LBUtil.exe" (
    echo The LogicBase Command Line Utility does not exist by path '%LBPath%\Designer\bin\LBUtil.exe'!
    echo Please provide the directory where LogicBase is installed correctly as parameter 1.
    echo Put in quotes if it is a long path.
    PAUSE
    goto :eof
    )
    @echo Moving files into platform...
    "%LBPath%\Designer\bin\LBUtil.exe" -InstallCustomLibs -warn
    PAUSE

Add it to the same folder as your dll and run.
  
![InstallLibsbat output](images\InstallLibsbatoutput.png)
  
Output

    Moving files into platform...
    LogicBase Studio Command Line Utility v Version 7.6.3 build number 4383
    
    Executing general actions.
    Installing libraries...
    Installing library Protirus.Components.Concat.dll
    1 libraries installed.
    Done.
    Press any key to continue . . .

Now the DLL should be in the CustomLib folder as the updated version.
  
Create a new Project, add the DLL as a Library and add the Component to your flow.
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
