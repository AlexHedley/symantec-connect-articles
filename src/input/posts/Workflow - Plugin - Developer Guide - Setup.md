---
title: Workflow - Plugin - Developer Guide - Setup
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-05-18
---

In this Article I'm going to explain how setup your environment for creating a Plugin.
  
Table of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=016f70af-1c51-438b-bbae-f98e86164f26&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=84ee5f15-df6c-44c7-8acd-e2764f0c4717&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Simple Plugin](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=8aeca32a-9a00-4d91-b618-f6af07957e71&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2e508788-3a83-4a91-8e5b-18b28ca1cc02&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Advanced Plugin](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=5076bfd9-0b26-408c-b957-3bb5fb0b59c2&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=6d54d145-537c-40e6-86ca-b5dec2b1e972&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [WindowsForm](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80b95a29-8a1a-44ce-a616-87cf8e001dbd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

You will need [Visual Studio](https://www.visualstudio.com/), download a version if you haven't already.
  
A ![Workflow](images\Workflow.png) Workflow Server to get the necessary DLLs.
  
Go to this server.
  
Go to your Workflow install location
  
The document states

> C:\Program Files\Altiris\Workflow Designer\Designer\Plugins

But you may have changed this on install, example:

> [Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins

Search for

> LogicBase.ToolShared.dll

> E:\Program Files\Symantec\Workflow\Shared\logicbaselib

Make a copy of this DLL and add it to your Dev environment.

We also need to get the necessary DLLs from the GAC (Global Assembly Cache)

    C:\Windows\Microsoft.NET\assembly\GAC_MSIL\

This may not show a list of DLLs as the viewer is configured using a RegKey.
  
\*Warning modifying the Registry can be dangerous, make sure you know what you're doing before you edit these. Take a copy first as a backup.

1. Launch RegEdit.
2. Navigate to **HKLM\Software\Microsoft\Fusion**
3. Add a **DWORD** called **DisableCacheViewer** and set the value to **1**.

Now search for 2 Libraries:

- LogicBase.Core.dll
- LogicBase.Framework.dll
- LogicBase.Components.Default.dll (You may also need Components if you're working with those)

Copy these to your Dev environment too.

Now we have the libs, we can create the VS project.
  
Start by creating a new ![Project - Class Library](images\Project-ClassLibrary.png) Class Library.

> Protirus.Workflow.Plugins

In the Project Folder add a new ![Folder](images\Folder.png) Folder called 'External Dependencies' (In Explorer)
  
Add the Symantec libs

- LogicBase.ToolShared.dll
- LogicBase.Core.dll
- LogicBase.Framework.dll

| NOTE: Make sure these are the correct versions from the correct WF box i.e. 7.5 / 7.6 / 8.0 / 8.1. |
| --- |

Now in the VS Project
  
Right Click -&gt; Add -&gt; New Solution Folder
  
Add Existing Item -&gt; Browse to the DLL and add

![References](images\References.png) References -&gt; Right Click -&gt; Add Reference
  
Expand Browse then right click Browse button
  
Go to this Folder and add the DLL.

Update the ![Properties](images\Properties.png) Properties, double click to open the window.
  
Click on Assembly Information,
  
Add the Description and Company info.

Check the Target Framework for .NET in Properties.

> .NET Framework 4.5.1

Now back to the .cs file that was created (![cs](images\cs.png) Class1.cs).
  
Rename this to the name of your Plugin

> ![cs](images\cs.png) ProtirusPlugin.cs

Add the *using* for the new namespaces

    using LogicBase.Components.Default.Process;
    using LogicBase.Core;
    using LogicBase.Framework;
    using LogicBase.Tool.Plugin;

We also need to add a couple of .NET References

    System.Drawing
    System.Windows.Forms;

Then add them to your code

    using System.Drawing;
    using System.Windows.Forms;

Now we are ready to code the Plugin.
  
We will need to implement one of the Interfaces from the ToolShared lib.
  
**IPlugin**

    public class ProtirusPlugin : IPlugin

And implement the required methods.

    public string Name { get; private set; }
    public string ToolTip { get; private set; }
    public string MenuLocation { get; private set; }
    public Shortcut MenuShortcut { get; private set; }
    public bool SeparatorAfter { get; private set; }
    public void PerformAction()
    {
        throw new NotImplementedException();
    }

**IProjectPlugin**

    public class ProtirusPlugin : IProjectPlugin

And implement the required methods.

    public void PerformAction(AbstractOrchestrationProject project)
    {
        //messageBox.Show("project action on project " + project.MainFile.FullName);
        throw new NotImplementedException();
    }

Finally
  
**IPluginUI**

    public class Protirus : IPluginUI

And implement the required methods.

    public int GetMenuPosition(string[] names)
    {
        throw new NotImplementedException();
    }
    
    public int GetToolBarPosition(string[] names)
    {
        throw new NotImplementedException();
    }
    
    public Image Image { get; private set; }
    public bool ShowInMenu { get; private set; }
    public bool ShowInToolBar { get; private set; }

Or all three

    public class Protirus : IProjectPlugin, IPluginUI //IPlugin,
    {
        ...
    }

Now we have all the necessary method stubs but nothing actually happens, onto the next Article [Simple Component](https://www.symantec.com/connect/articles/workflow-plugin-developer-guide-simple-component) to create a working item.
  
- - -
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
