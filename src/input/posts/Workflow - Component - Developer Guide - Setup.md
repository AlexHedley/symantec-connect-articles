---
title: Workflow - Component - Developer Guide - Setup
tags:
    - Workflow
    - Component
    - Developer Guide
author: AlexHedley
# description: 
# articleId: 
published: 2016-11-09
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-component-developer-gu-8?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I'm going to explain how setup your environment for creating a Component.
  
Table of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=17aa2b9a-9092-40d0-afab-a6d8316de97d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70a9fde5-0d87-4b9d-a3be-0907567ffc00&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
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

You will need [Visual Studio](https://www.visualstudio.com/), download a version if you haven't already.
  
A ![Workflow](images\Workflow.png) Workflow Server to get the necessary DLLs.
  
Go to this server.
  
We need to get the necessary DLLs from the GAC (Global Assembly Cache)

    C:\Windows\Microsoft.NET\assembly\GAC_MSIL\

This may not show a list of DLLs as the viewer is configured using a RegKey.
  
\*Warning modifying the Registry can be dangerous, make sure you know what you're doing before you edit these. Take a copy first as a backup.

1. Launch RegEdit.
2. Navigate to **HKLM\Software\Microsoft\Fusion**
3. Add a **DWORD** called **DisableCacheViewer** and set the value to **1**.

Now search for 3 Libraries:

- LogicBase.Components.Default.dll
- LogicBase.Core.dll
- LogicBase.Framework.dll

Now we have the libs, we can create the VS project.
  
Start by creating a new ![Project - Class Library](images\Project-ClassLibrary.png) Class Library.
  
In the Project Folder add a new ![Folder](images\Folder.png) Folder 'External Dependencies' (In Explorer)
  
Add the 3 Symantec libs

- LogicBase.Components.Default.dll
- LogicBase.Core.dll
- LogicBase.Framework.dll

Make sure these are the correct versions from the correct WF box i.e. 7.5 / 7.6 / 8.0.
  
Now in the VS Project
  
Right Click -&gt; Add -&gt; New Solution Folder
  
Add Existing Item -&gt; Browse to the 3 DLLs and add them
  
![References](images\References.png) References -&gt; Right Click -&gt; Add Reference
  
Expand Browse then right click Browse button
  
Go to this Folder and add the 3 DLLs again.
  
Update the ![Properties](images\Properties.png) Properties, double click to open the window.
  
Click on Assembly Information,
  
Add the Description and Company info - this is used in the Component within Workflow.
  
![Assembly_Information](images\Assembly_Information.png)
  
Check the Target Framework for .NET in Properties.

Now back to the .cs file that was created.
  
Rename this to the name of your component - i.e. ![cs.png](images\cs.png) Concat.cs
  
Add the *using* for the new namespaces

    using LogicBase.Core;
    using LogicBase.Core.Data;
    using LogicBase.Core.Data.DataTypes;
    using LogicBase.Core.PropertySheets;
    using LogicBase.Framework;
    
    using LogicBase.Core.Data.TypeEditors;
    using System.ComponentModel;

We also need to add a couple of .NET References for

    System.Drawing

    System.Drawing.Design

Then add a using statement

    using System.Drawing.Design;

Next add an Image to the project (Protirus.Workflow.Protirus.png), this will be the Component image,
  
Change the Build Action to **Embedded Resource**
  
![Protirus.Workflow.Protirus](images\Protirus.Workflow.Protirus.png)
  
You could use images from WF:

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Images\

- general
- processmanager

Next we want to add some metadata to the project.
  
This can be done between the *namespace* and the *public class*

    /// <summary>
    ///     Custom component for joining two strings.
    /// </summary>
    /// 
    [Serializable,
    ComponentCategory("Protirus"),
    ComponentImage("Protirus.Workflow.Protirus.png"),
    ComponentName("Protirus Concat"),
    ComponentDescription("This component joins two Strings."),
    ComponentHelp("http://www.protirus.com/components/"),
    ComponentUsage("Requires two strings."),
    ComponentExample("String a = 'Hello' String b = 'World', this will return 'Hello World', if Add Space is True."),
    ComponentPublisher("Protirus", "www.protirus.com")]
    [PropertyPageOrder("General", "Configuration", "Settings")]

Not all properties are used in the component and will need to update in the corresponding *.libconfig* file.
  
These are located:

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Help\

I'll explain how to create/update these in a later tutorial.

- [Help File](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80437c69-ccc3-47e6-a850-9cf3f301b340&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

Now we need to conform to some protocols for the components to be useable in Workflow.
  
Extend the Class

    public class Concat : AbstractSinglePathProcessComponent, ISinglePathDataAdded

Now implement the required methods.
  
First "**AbstractSinglePathProcessComponent**"

    public override void Run(IData data)
    {
    }
    
    public override void ReadFromStream(ObjectReadStream info)
    {
    }
    
    public override void WriteToStream(ObjectWriteStream info)
    {
    }

And the "**ISinglePathDataAdded**"

    public DataDefinition[] GetAddedData()
    {
    }

Now we have all the necessary method stubs but nothing actually happens, onto the next Article [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to create a working item.

[![Protirus](images\Protirus.png)](https://www.protirus.com/)
