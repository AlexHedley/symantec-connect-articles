---
title: Workflow - Plugin - Developer Guide - Advanced Plugin
tags:
    - Workflow
    - Plugin
    - Developer Guide
author: AlexHedley
# description: 
# articleId: 
published: 2017-07-17
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-plugin-developer-guide-1?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I'm going to explain some more advanced features of Plugin creation.
  
Table of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=016f70af-1c51-438b-bbae-f98e86164f26&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=84ee5f15-df6c-44c7-8acd-e2764f0c4717&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Plugin](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=8aeca32a-9a00-4d91-b618-f6af07957e71&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2e508788-3a83-4a91-8e5b-18b28ca1cc02&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Advanced Plugin](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=5076bfd9-0b26-408c-b957-3bb5fb0b59c2&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=6d54d145-537c-40e6-86ca-b5dec2b1e972&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [WindowsForm](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80b95a29-8a1a-44ce-a616-87cf8e001dbd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

[​](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=016f70af-1c51-438b-bbae-f98e86164f26&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
There is another Interface you can use to conditionally show a Plugin.

    public class ProtirusPlugin : IConditionalPlugin

Implement the following method
  
ShowPlugin
  
*This is from the Developer Guide.*

    public bool ShowPlugin()
    {
        // To Update
        return (CurrentProjectHolder.GetInstance().Project.GetProjectType() == ProjectTypeEnum.maestro);
    }

> Gets a value indicating if the plugin should be displayed.

ProjectTypeEnum doesn't exist anymore but searching in the DLLs I found

    namespace LogicBase.Tool.Common
    public enum ProductType
    {
        Maestro,
        Harmony,
        Metronome,
        Divo,
        Composer,
        Universal
    }

Or

    LogicBase.Tool
    public static class ProjectType
    
    string[] strArrays = new string[] { 
      ".Workflow", ".Decision", ".Integration", ".WebForms", 
      ".WinForms", ".Harmony", ".Maestro", ".Virtuoso", 
      ".Metronome", ".Monitoring", ".Composer", ".WinComposer" 
    };

Pull in the following

    using LogicBase.Core.Utilities;

Looking into this I couldn't find the matching Projects so I'm going to check the ProjectType another way.

    ProjectTypeData ptd = CurrentProjectHolder.GetInstance().Project.ProjectSetupData.ProjectType;
    Guid projectTypeId = ptd.ProjectTypeId;
    string projectTypeName = ptd.ProjectTypeName;
    Debug.Print(string.Format(@"ProjectTypeId {0} | ProjectTypeName {1}", projectTypeId, projectTypeName));

- ![Decision Only](images\DecisionOnly.png) LogicBase.Core.Models.Decision.DescisionProject, LogicBase.Core
- ![Forms (Web)](images\FormsWeb.png) LogicBase.Core.Models.Dialog.FormDialogProject, LogicBase.Core
- ![Monitoring](images\Monitoring.png) LogicBase.Core.Models.Monitoring.MonitoringProject, LogicBase.Core
- ![App](images\App.png) LogicBase.Core.Models.Flexi.FlexiProject, LogicBase.Core
- ![WorkflowProject](images\WorkflowProject.png) LogicBase.Core.Models.Workflow.WorkflowProject, LogicBase.Core
- ![Int](images\Int.png) Integration

[![Protirus](images\Protirus.png)](https://www.protirus.com/)
