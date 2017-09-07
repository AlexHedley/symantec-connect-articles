---
title: Workflow - AngularJS Components - Charts
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-09-07
---

In this Article I will run through how to enable [AngularJS](https://angular.io/) when using Chart Components.

Table Of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3baf8485-eabd-43ff-8cc0-767906273a44&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Grid](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a05d59e4-87ed-45b5-abd4-574974d05185&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Date Pickers](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a06bd03c-3430-482a-bdaf-0ff9aff23c8e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Charts](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=fac5c517-6ba6-4cbe-8aad-dd2b2beff237&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Custom](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=062791d7-60fd-4702-9ac5-1bcdf0f2dfc4&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) - Checkers
- [Page Source](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3607359c-2ba3-4491-acfd-a29c88639fcd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- ...

Create a new Project and add a Web Form to your main Model.

Search for a Web Chart Component and add it to your page.

Setup the necessary properties to display some data.

**Web Chart**

| LogicBase.Components.FormBuilder.AdvancedComponents.WebChart.WebChartComponent |
| --- |
| [https://www.symantec.com/connect/articles/webchart](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a09a0b07-e705-41cb-a561-56c48e3bfd97&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) |
| https://www.symantec.com/connect/content-external/workflow-id_LogicBase.Components.FormBuilder.AdvancedComponents.WebChart.WebChartComponent/workflow |

As usual Edit the Component and in the "General" tab tick the "Use Angular JS" box.
  
![AngularJS - WebChart - Edit Component](images\AngularJS-WebChart-EditComponent.png)

Run the app in Debug and you will get some interactive Charts.
  
![AngularJS - Graphs](images\AngularJS-Graphs.png)
  
If you click on the Legend this will Show/Hide the data. Hover over the points and if the property has been set you can see the Data Labels. There is lots you can configure depending on how you wish to use the Chart.

There are other types of Charts you can use in Workflow:

**Dynamic Guage**

| LogicBase.Components.FormBuilder.Components.DynamicGuageComponent |
| --- |
| [https://www.symantec.com/connect/articles/dynamic-configurable-guage](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=523625db-3066-456a-8d23-cbdc473e3938&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) |
| https://www.symantec.com/connect/content-external/workflow-id\_LogicBase.Components.FormBuilder.Components.DynamicGuageComponent/workflow |

No option to use AngularJS, unless I've missed the setting.

[![Protirus](images\Protirus.png)](https://www.protirus.com)​
