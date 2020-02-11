---
title: Workflow - AngularJS Components - Date Picker
tags:
    - Workflow
    - AngularJS
author: AlexHedley
# description: 
# articleId: 
published: 2017-09-07
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-angularjs-components-d?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I will run through how to enable [AngularJS](https://angular.io/) when using a DatePicker Component.

Table Of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3baf8485-eabd-43ff-8cc0-767906273a44&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Grid](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a05d59e4-87ed-45b5-abd4-574974d05185&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Date Pickers](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a06bd03c-3430-482a-bdaf-0ff9aff23c8e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Charts](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=fac5c517-6ba6-4cbe-8aad-dd2b2beff237&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Custom](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=062791d7-60fd-4702-9ac5-1bcdf0f2dfc4&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) - Checkers
- [Page Source](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3607359c-2ba3-4491-acfd-a29c88639fcd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- ...

On a Web Form add a Date Picker Component.
  
![Calendar Preferences](images\calendar_preferences.png)

| LogicBase.Components.FormBuilder.AdvancedComponents.DatePickerComponent |
| --- |
| [https://www.symantec.com/connect/articles/datepicker](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=7c24fa77-9624-4a45-8017-e831d0bcab27&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) |

![Date Time](images\date-time.png)

| LogicBase.Components.FormBuilder.AdvancedComponents.DateTimePickerComponent |
| --- |
| [https://www.symantec.com/connect/articles/datetimepicker](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=317551f4-9e6c-4db5-a792-1d72f16776e1&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) |

Edit the settings and go to the "Appearance" tab where you can check the "Use Angular JS" box.
  
![AngularJS - Date Picker - Edit Component - Use AngularJS](images\AngularJS-DatePicker-EditComponent-UseAngularJS.png)
  
Fill in the other properties where appropriate.

Then run your app in Debug to see the differences.
  
New
  
![AngularJS - DateTime - Date - New](images\AngularJS-DateTime-Date-New.png)

![AngularJS - DateTime - Time - New](images\AngularJS-DateTime-Time-New.png)

Original
  
​![AngularJS - DateTime - Date - Original](images\AngularJS-DateTime-Date-Original.png)
  
The time doesn't change much.

As you can see there is different styling, more rounded corners and some more information.

[![Protirus](images\Protirus.png)](https://www.protirus.com)