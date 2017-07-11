---
title: Workflow - ProcessManager - WebPart - Developer Guide - Setup
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-07-11
---

In this Article I'm going to explain how to setup your environment for creating a WebPart.
  
Articles
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=aa0478d7-5f5a-4be4-8369-4c74f963deeb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=36a9f5ee-ab0b-42e7-a75e-590ba4f256ec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Simple](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a3b54e8a-7492-4397-8512-8828defe25a7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74973282-5d27-4b12-a0d3-9ad29d38a2ce&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c1b3103c-afad-45f8-9f17-244fff752121&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other WebParts
- [Controls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c20f9b40-20f8-4693-937a-7ca431c4d7ce&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) a WebPart
- WF/PM [Connection String](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=849d26ef-084e-426b-a064-fbb86730e6b8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Connecting to [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=77434eb5-7ee1-4bb4-bef1-ef566cce61fb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to retrieve data

---
  
You will need [Visual Studio](https://www.visualstudio.com/), download a version if you haven't already.
  
A ![Workflow](images\Workflow.png) Workflow Server to get the necessary DLLs.
  
Go to this server.
  
Go to your Workflow install location.

    [Install Drive]:\Program Files\Symantec\Workflow\

Search for

- LogicBase.Ensemble.dll
- LogicBase.Ensemble.Framework.dll

    [Install Drive]:\Program Files\Symantec\Workflow\ProcessManager\bin

Make a copy of these DLLs and add them to your Dev environment.
  
We also need to get the necessary DLLs from the GAC (Global Assembly Cache)

    C:\Windows\Microsoft.NET\assembly\GAC_MSIL\

This may not show a list of DLLs as the viewer is configured using a RegKey.

| \* Warning modifying the Registry can be dangerous, make sure you know what you're doing before you edit these. Take a copy first as a backup. |
| --- |

1. Launch RegEdit.
2. Navigate to **HKLM\Software\Microsoft\Fusion**
3. Add a **DWORD** called **DisableCacheViewer** and set the value to **1**.

Now search for 2 Libraries:

- LogicBase.Core.dll
- LogicBase.Framework.dll

In future Articles we will also be using

- Symantec.SymQ.dll

- - -
  
Now we have the libs, we can create the VS project.
  
Start by creating a new ![Project - Class Library](images\Project-ClassLibrary.png) Class Library.

> Protirus.ProcessManager.WebParts

In the Project Folder add a new ![Folder](images\Folder.png) Folder called 'External Dependencies' (In Explorer)
  
Add the Symantec libs

- LogicBase.Ensemble.dll
- LogicBase.Ensemble.Framework.dll
- LogicBase.Core.dll
- LogicBase.Framework.dll
- Symantec.SymQ.dll

| NOTE: Make sure these are the correct versions from the correct WF box i.e. 7.5 / 7.6 / 8.0 / 8.1. |
| --- |

Now in the VS Project
  
Right Click -&gt; Add -&gt; New Solution Folder ('External Dependencies')
  
Add Existing Item -&gt; Browse to the DLL(s) and add.

![References](images\References.png) References -&gt; Right Click -&gt; Add Reference
  
Expand Browse then right click Browse button.
  
Go to this Folder and add the DLL.

Update the ![Properties](images\Properties.png) Properties, double click to open the window.
  
Click on Assembly Information,
  
Add the Description and Company info.
  
It's also a good idea to update the version to match the WF version i.e. 7.6. You can then use minor versions to keep a record of your updates.

Check the Target Framework for .NET in Properties.

> .NET Framework 4.5.1

Now back to the .cs file that was created (![cs](images\cs.png) Class1.cs).
  
Rename this to the name of your WebPart

> ![cs](images\cs.png) ProtirusWebPart.cs

Add the *using* for the new namespaces

    using LogicBase.Core;
    using LogicBase.Framework;

Add the following References:

- System.Net.Http
- System.Web
- System.Web.Extensions

Finally we need to implement the following:

    ...
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    
    public class ProtirusWebPart : WebPart
    {
    }

You could create an ASP .NET Server Control project but depending on the VS version this Project may not be available.
  
We now have the barebone of a Project setup and ready to implment, next up the [Simple](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a3b54e8a-7492-4397-8512-8828defe25a7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) Article.
  
- - -
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
