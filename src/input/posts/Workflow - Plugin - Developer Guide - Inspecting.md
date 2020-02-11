---
title: Workflow - Plugin - Developer Guide - Inspecting
tags:
    - Workflow
    - Plugin
    - Developer Guide
author: AlexHedley
# description: 
# articleId: 
published: 2017-05-19
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-plugin-developer-guide-2?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I'm going to explain how to inspect other Plugins to learn how to implement items that aren't in the Developer Guide PDF.
  
Table of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=016f70af-1c51-438b-bbae-f98e86164f26&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=84ee5f15-df6c-44c7-8acd-e2764f0c4717&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Plugin](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=8aeca32a-9a00-4d91-b618-f6af07957e71&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2e508788-3a83-4a91-8e5b-18b28ca1cc02&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Advanced Plugin](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=5076bfd9-0b26-408c-b957-3bb5fb0b59c2&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=6d54d145-537c-40e6-86ca-b5dec2b1e972&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [WindowsForm](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80b95a29-8a1a-44ce-a616-87cf8e001dbd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

There are a number of decompilers available

- ![JustDecompile](images\JustDecompile.png) [JustDecompile](http://www.telerik.com/products/decompiler.aspx) from [Telerik](http://www.telerik.com/)
- ![dotPeek (S)](images\dotPeekS.png) [dotPeek](https://www.jetbrains.com/decompiler/) from ![JetBrains (S)](images\JetBrainsS.png) [JetBrains](https://www.jetbrains.com/)
- [ILSpy](http://ilspy.net/)

We need some Plugins to look at, grab them from the folder you deploy yours too.

> [Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins

There are a number to choose from, firstly we will look at [Create GUID](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0cb4ba5b-6f4b-4fe8-bc05-a16971bd1f5d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments).

    LogicBase.Plugins.CreateGUID.dll

Open

- *GUIDPlugIn.cs*

The main difference here is in the *PerformAction* method.

    public void PerformAction(AbstractOrchestrationProject project)
    {
        GUIDForm gUIDForm = new GUIDForm();
        if (gUIDForm.ShowDialog() == DialogResult.OK)
        {
            string guid = gUIDForm.Guid;
            ActionType selectedAction = gUIDForm.SelectedAction;
            if (selectedAction == ActionType.CreateAsDataComponent)
            {
                IComponentModel primaryComponentModel = project.GetPrimaryComponentModel();
                InsertDataComponent insertDataComponent = new InsertDataComponent();
                insertDataComponent.set_DataType(typeof(string));
                insertDataComponent.set_IsArray(false);
                insertDataComponent.set_Value(guid);
                insertDataComponent.Location = new PointF(20f, 20f);
                primaryComponentModel.AddComponent(insertDataComponent);
                return;
            }
            if (selectedAction == ActionType.CopyToClipboard)
            {
                Clipboard.SetDataObject(guid, true);
            }
        }
    }

In Workflow Manager click on the Menu - Plugins | Create GUID
  
![Workflow - Menu - Plugins - Create GUID](images\Workflow-Menu-Plugins-CreateGUID.png)
  
This opens a Form and depending on the chosen action it does either of two things.

| BUG: This states "current model" but actually puts it into the ![Model 1](images\Model1.png) Primary model. |
| --- |

If we look at the code it's asking for the Primary.

    IComponentModel primaryComponentModel = project.GetPrimaryComponentModel();

Or saving to the Clipboard

    Clipboard.SetDataObject(guid, true);

If you want to work with Components you will need to add a ref.

    using LogicBase.Components.Default.Process;

Find the component you want to work with and set the desired properties.

Custom Form
  
You can create a WinForms Form and design it how you would any C# project.
  
As you can see from the above code just create an instance and use how you would normally, nothing specific to WF.

---
  
You can try creating a Project from the DLL (using ![JustDecompile](images\JustDecompile.png) JustDecompile) but I've had issues getting this to work.
  
![JustDecompile-Project-RightClick](images\JustDecompile-Project-RightClick.png)
  
(load failed)

> E:\WF\LogicBase.Plugins.CreateGUID\LogicBase.Plugins.CreateGUID.csproj : error  : The project file could not be loaded. Data at the root level is invalid. Line 1, position 1.  E:\WF\LogicBase.Plugins.CreateGUID\LogicBase.Plugins.CreateGUID.csproj

If you look at the .csproj in notepad there is an object ref error.
  
If you copy another blank projects .csproj, rename it to this Project name you can play about with some files to make it work, add Existing Items and pull in the files that were created.
  
---

![Protirus](images\Protirus.png)
