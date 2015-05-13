---
title: String with name 'XXX' has already been added - Workflow Integration Library
tags:
    - Workflow
    - Integration Library
author: AlexHedley
# description: 
published: 2015-05-13
---

So you've created an ![Int.png](images/Int.png) Integration Component with SQL Generators etc included.

You add a new Generator to the list, get to the end and after you '**Recompile and close**' the following warning shows:

![Integration Library - Error (1).png](/connect/sites/default/files/users/user-2946791/Integration%20Library%20-%20Error%20%281%29.png)

Open up ![Workflow.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3417051-files_Workflow.png) **Symantec Workflow Explorer** and go to the **Log Viewer** tab.

(<Install Drive>:\Program Files\Altiris\Workflow\Logs\logicbase.tool.generator.exe.log)

<pre>Application Name : LogicBase.Tool.Generator.exe Process ID : _##_ Date :_DD_/_MM_/_YYYY_ _HH_:_NN_:_SS_ Log Level :Error Log Category :LogicBase.Tool.Repository.OperationManager Machine Name : _<SERVERNAME>_ Message : System.ArgumentException: String with name '**XXX**' has already been added Parameter name: name at Symantec.Workflow.HelpEditor.Internal.ResxFile.AddString(String name, String value) at Symantec.Workflow.HelpEditor.Internal.FileWriter.WriteToolboxCategories(String baseCategoryPath, IEnumerable`1 categories) at Symantec.Workflow.HelpEditor.Internal.FileWriter.WriteToolbox(XmlWriter xml) at Symantec.Workflow.HelpEditor.AssemblyWriteFile.ExecuteAsync() at Symantec.Workflow.Manager.Common.Operation.BeginExecution()</pre>

The Help Editor will still open but you won't have the folder containing the component, like it would usually, given the Component name.

The reason from the Logs show there is an issue with a name that is trying to be created in the Help Editor File.

The component still exists it just won't be in it's own folder.

You will need to manually create this.

Select **Components** from the **Type** section and it will show:

![Help Editor (1).png](/connect/sites/default/files/users/user-2946791/Help%20Editor%20%281%29.png)

Under Toolbox select the top level folder _right-click_ and **Add**:

![Help Editor (2).png](/connect/sites/default/files/users/user-2946791/Help%20Editor%20%282%29.png)

Give it a **Name**:

![Help Editor - Name.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3417051-files_Help%20Editor%20-%20Name.png)

Now drag the component from the Components section into this new folder:

![Help Editor (3).png](/connect/sites/default/files/users/user-2946791/Help%20Editor%20%283%29.png)

It may appear in the top level folder as well (Test_INT) so just move it from there into the sub-folder.

<table border="0" cellpadding="0" cellspacing="0" style="width: 500px">

<tbody>

<tr>

<td>The fix will be added to the next rollup release for Workflow **7.6**.</td>

</tr>

</tbody>

</table>

<div>

* * *

![Protirus](images/Protirus.png)
