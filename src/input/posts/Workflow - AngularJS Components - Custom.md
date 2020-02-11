---
title: Workflow - AngularJS Components - Custom
tags:
    - Workflow
    - AngularJS
author: AlexHedley
# description: 
# articleId: 
published: 2017-09-07
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-angularjs-components-c?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I will run through how to use some custom [AngularJS](https://angular.io/) javascript and css to add anything to a form.

Table Of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3baf8485-eabd-43ff-8cc0-767906273a44&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Grid](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a05d59e4-87ed-45b5-abd4-574974d05185&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Date Pickers](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a06bd03c-3430-482a-bdaf-0ff9aff23c8e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Charts](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=fac5c517-6ba6-4cbe-8aad-dd2b2beff237&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Custom](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=062791d7-60fd-4702-9ac5-1bcdf0f2dfc4&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) - Checkers (this)
- [Page Source](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3607359c-2ba3-4491-acfd-a29c88639fcd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- ...

Firstly we need some Angular code,

- [https://github.com/zackargyle/ngCheckers](https://github.com/zackargyle/ngCheckers)

![Text Rich Marked](images\text_rich_marked.png)
  
Merge Text - add the source

| LogicBase.Components.Default.Process.MergeTextComponent |
| --- |
| [https://www.symantec.com/connect/articles/merge-text](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=7f67ec31-0a2d-4799-b2e5-68fd59b5607d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) |

In the MergeText add the CSS and JS.
  
CSS

    <style type="text/css">
      ...
    </style>

JS

    <script type="text/javascript">
      ...
    </script>

Finally add the HTML

    <html ng-app='ngCheckers'>
      ...
    </html>

![window_edit](images\window_edit.png)
  
Include Html

| LogicBase.Components.FormBuilder.AdvancedComponents.Include.IncludeHtmlComponent |
| --- |
| [https://www.symantec.com/connect/articles/includehtml](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=59eb4f91-9e56-46c3-9c25-96ea90ec279c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) |

Use the Merge Text as the "Text To Include"
  
![Appearance](images\AngularJS-IncludeHtml-EditComponent-Appearance.png)

Set the Property in the "General" tab to "Use Angular JS".
  
![AngularJS](images\AngularJS-IncludeHtml-EditComponent-UseAngularJS.png)
  
Run it in the browser and enjoy your game of Checkers.
  
![Checkers](images\AngularJS-CustomComponent-Checkers.png)

[![Protirus.png](images\Protirus.png)](https://www.protirus.com)
