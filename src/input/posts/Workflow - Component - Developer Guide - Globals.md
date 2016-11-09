---
title: Workflow - Component - Developer Guide - Globals
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-11-09
---

In this Article I'm going to explain how to create a Global variable and add it to the Project when a Component is added into Workflow.
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=17aa2b9a-9092-40d0-afab-a6d8316de97d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70a9fde5-0d87-4b9d-a3be-0907567ffc00&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Help File](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80437c69-ccc3-47e6-a850-9cf3f301b340&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Logging](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63b72a9a-53b8-4d4b-bce3-5f0732b134d5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Inputs
    - [Checkbox](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74c56ef7-1119-40fe-9d5f-3c7a1d808d4c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [Dropdown / Combo](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=267159ac-b8e7-45b4-abe4-f85d78e30783&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2c3b3a6f-01d7-4157-a143-ba30c9edc930&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other Components
- [Creating Globals](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=cf54de06-be56-46ff-b937-148efa57eaec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Creating Project Properties](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4cfc07c5-404e-49b3-81b6-520d4ea43d5c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f3cf0097-06e7-42f3-a747-d0dff319c1e5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with a Web Service](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=26368883-708b-4432-999b-7064f2f25794&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

- - -
  
Set up a component how you would usually. The difference here is you can set information at a Project level.
  
I've implemented this in a component to get and set a Workflow Connection String.
  
You may have seen this when you add the [Create SMP Credentials](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9a4ab06f-59da-40a6-ab93-bd231db61036&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments), this is what I used as a basis

    Symantec.Components.Platform.dll
    namespace Symantec.Workflow.Components.Platform
    public class InitializeWorkflowSettings

![WorkflowGlobalData](images\WorkflowGlobalData.png)
  
So we need a reference to the Project.

    AbstractOrchestrationProject project = CurrentProjectHolder.GetInstance().Project;

When you add the Component to the Project you can set a Default value.
  
Give the data a name - here I've called mine "ConnectionString".

    public WorkflowSQLConnectionString()
    {
        if (!DesignMode.IsInDesignMode)
            return;
        AbstractOrchestrationProject project = CurrentProjectHolder.GetInstance().Project;
        if (project == null || project.GlobalData == null)
            return;
        if (project.GlobalData.Data["ConnectionString"] == null)
        {
            project.GlobalData.Data.Add(new DataDefinition("ConnectionString", typeof(string)));
            //project.GlobalData.Data["ConnectionString"].DefaultValue = (object)"Data Source=SERVER;Initial Catalog=ProcessManager;Integrated Security=True;Pooling=True;Connect Timeout=30";
            project.GlobalData.Data["ConnectionString"].DefaultValue = @"";
        }
    }

Finally in your Run method you can set this value.

    public override void Run(IData data)
    {
        ...
        data["[Global].ConnectionString"] = connectionString;
        ...
    }

This means you can now use the Global variable throughout your Workflow.
  
Usually I use a Profile Property (Application Property) in Process Manager instead of Globals/Project Properties as then you can update the values if you move the Projects between Servers/Environments but this way means it looks locally on the box and no need to update it anywhere else.
  
![Protirus](images\Protirus.png)
