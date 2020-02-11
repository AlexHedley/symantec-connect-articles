---
title: Workflow - AngularJS Components - Grid
tags:
    - Workflow
    - AngularJS
author: AlexHedley
# description: 
# articleId: 
published: 2017-09-04
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-angularjs-components-g?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I will run through how to enable [AngularJS](https://angular.io/) when using a Grid Component.

Table Of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3baf8485-eabd-43ff-8cc0-767906273a44&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Grid](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a05d59e4-87ed-45b5-abd4-574974d05185&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Date Pickers](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a06bd03c-3430-482a-bdaf-0ff9aff23c8e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Charts](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=fac5c517-6ba6-4cbe-8aad-dd2b2beff237&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Custom](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=062791d7-60fd-4702-9ac5-1bcdf0f2dfc4&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) - Checkers
- [Page Source](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3607359c-2ba3-4491-acfd-a29c88639fcd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- ...

Firstly you will need to enable AngularJS in your Project.
  
Once you have created a new Project, go to the main ![Project](images\Project.png) Project and tick "Use AngularJs Capability".
  
![](images\article-3706911-files_AngularJS+-+Project+-+Use+AngularJS+Capability.png)
  
Add a Form Component onto your Project.

| LogicBase.Components.FormBuilder.FormBuilderComponent |
| --- |
| [https://www.symantec.com/connect/articles/form-builder](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=32c32964-6af1-4ef5-a7ce-d68e85a6ef95&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) |

Then drag a Grid Component onto your Form.

| Logicbase.Components.FormBuilder.InfragisticsComponents.WebGrid.GridComponent |
| --- |
| [https://www.symantec.com/connect/content-external/workflow-id\_Logicbase.Components.FormBuilder.InfragisticsComponents.WebGrid.GridComponent/workflow](https://www.symantec.com/connect/content-external/workflow-id_Logicbase.Components.FormBuilder.InfragisticsComponents.WebGrid.GridComponent/workflow) |

Right Click and "Edit Component".
  
Click on the "General" tab.
  
Tick "Use Angular JS".
  
![AngularJS - Component - Edit - Use AngularJS](images\AngularJS-Component-Edit-UseAngularJS.png)
  
Configure your component to get some Data then run the Project.

If you create a clone of the example, but turn off AngularJS and run both you will see the difference in the Grid.
  
![AngularJS - Grid Comparison](images\AngularJS-GridComparison.png)
  
You will see there are extra options against the Column Headings.
  
![AngularJS - Grid - Dropdown Options](images\AngularJS-Grid-DropdownOptions.png)
  
You can Filter any row
  
![AngularJS - Grid - Dropdown Options - Filter](images\AngularJS-Grid-DropdownOptions-Filter.png)

| Filter |
| --- |
| Is equal to |
| Is not equal to |
| Starts with |
| Contains |
| Does not contain |
| Ends with |

Not much work needed for a lot of extra functionality.

[![Protirus](images\Protirus.png)](https://www.protirus.com)
