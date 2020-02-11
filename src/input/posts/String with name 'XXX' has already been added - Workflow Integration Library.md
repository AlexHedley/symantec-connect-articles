---
title: String with name 'XXX' has already been added - Workflow Integration Library
tags:
    - Workflow
    - Error
author: AlexHedley
# description: 
# articleId: 
published: 2015-05-13
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/string-with-name-xxx-has-already?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

So you've created an ![Int.png](images\article-3417051-files_Int.png) Integration Component with SQL Generators etc included.
  
You add a new Generator to the list, get to the end and after you '**Recompile and close**' the following warning shows:
  
![Integration Library - Error (1).png](images\Integration%2520Library%2520-%2520Error%2520%25281%2529.png)
  
Open up ![Workflow.png](images\article-3417051-files_Workflow.png) **Symantec Workflow Explorer** and go to the **Log Viewer** tab.
  
(&lt;Install Drive&gt;:\Program Files\Altiris\Workflow\Logs\logicbase.tool.generator.exe.log)

    Application Name : LogicBase.Tool.Generator.exe
    Process ID : ##
    Date :DD/MM/YYYY HH:NN:SS
    Log Level :Error
    Log Category :LogicBase.Tool.Repository.OperationManager
    Machine Name : <SERVERNAME>
    Message : 
    System.ArgumentException: String with name 'XXX' has already been added
    Parameter name: name
       at Symantec.Workflow.HelpEditor.Internal.ResxFile.AddString(String name, String value)
       at Symantec.Workflow.HelpEditor.Internal.FileWriter.WriteToolboxCategories(String baseCategoryPath, IEnumerable`1 categories)
       at Symantec.Workflow.HelpEditor.Internal.FileWriter.WriteToolbox(XmlWriter xml)
       at Symantec.Workflow.HelpEditor.AssemblyWriteFile.ExecuteAsync()
       at Symantec.Workflow.Manager.Common.Operation.BeginExecution()

The Help Editor will still open but you won't have the folder containing the component, like it would usually, given the Component name.

The reason from the Logs show there is an issue with a name that is trying to be created in the Help Editor File.
  
The component still exists it just won't be in it's own folder.
  
You will need to manually create this.

Select **Components** from the **Type** section and it will show:
  
![Help Editor (1).png](images\Help%2520Editor%2520%25281%2529.png)
  
Under Toolbox select the top level folder *right-click* and **Add**:
  
![Help Editor (2).png](images\Help%2520Editor%2520%25282%2529.png)
  
Give it a **Name**:
  
![Help Editor - Name.png](images\article-3417051-files_Help+Editor+-+Name.png)
  
Now drag the component from the Components section into this new folder:
  
![Help Editor (3).png](images\Help%2520Editor%2520%25283%2529.png)
  
It may appear in the top level folder as well (Test\_INT) so just move it from there into the sub-folder.

| The fix will be added to the next rollup release for Workflow **7.6**. |
| --- |

* * *

![Protirus.png](images\article-3417051-files_Protirus.png)
