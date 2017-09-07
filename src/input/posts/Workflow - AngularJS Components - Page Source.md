---
title: Workflow - AngularJS Components - Page Source
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-09-07
---

In this Article I will run through the differences in the Page Source when you add [AngularJS](https://angular.io/) to your Web Forms.

Table Of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3baf8485-eabd-43ff-8cc0-767906273a44&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Grid](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a05d59e4-87ed-45b5-abd4-574974d05185&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Date Pickers](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a06bd03c-3430-482a-bdaf-0ff9aff23c8e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Charts](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=fac5c517-6ba6-4cbe-8aad-dd2b2beff237&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Custom](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=062791d7-60fd-4702-9ac5-1bcdf0f2dfc4&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) - Checkers
- [Page Source](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3607359c-2ba3-4491-acfd-a29c88639fcd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- ...

There are changes to the JS / CSS files.
  
The Angular Directives are added to the page.

For more information go to the following site and run through some tutorials.
  
![Angular Logo](images\Angular.png) [https://angular.io/](https://angular.io/)

If we run both projects in Debug and View Source on the page you can then use something like [https://www.diffchecker.com/](https://www.diffchecker.com/) to compare.
  
Key - O (Original) | A (Angular)

O

    <link type='text/css' rel='stylesheet' href='/SymWebInclude/styles/kendo.fb.min.css'/>

A

    <link type='text/css' rel='stylesheet' href='/SymWebInclude/styles/kendo.bootstrap.min.css'/>

There are a number of ScriptResouce files generated

    <script src="/DemoOFAngularJSComponents0/ScriptResource.axd?d=... type="text/javascript"></script>

Then the main change is the content of the page.
  
O

    <div 
     id="l1b" 
     tabindex="2" 
     class="fb-grid" 
     name="l1b" 
     style="height:200px;width:400px;position:absolute;left:41px;top:30px;-moz-box-sizing:border-box;box-sizing:border-box;-moz-resize:none;resize:none;overflow:visible;">
     ...
     <!-- Loads of hidden elements, then the Table -->
     <div class="fb-col-box">
      <div>
       <table cellspacing="0" cellpadding="0" style="width:5400px">
        ...
       </table>
      </div>
     ...
    </div>

A

    <div 
     id="l1b" 
     tabindex="2" 
     ng-controller="l1b_Ctrl" 
     k-options="controlConfig" 
     kendo-grid="" 
     name="l1b" 
     style="height:200px;width:400px;position:absolute;left:41px;top:30px;-moz-box-sizing:border-box;box-sizing:border-box;-moz-resize:none;resize:none;overflow:visible;">
    </div>

As you can see we now have an *ng-controller* which if we look at the documentation

    ng-controller="l1b_Ctrl"

[https://docs.angularjs.org/api/ng/directive/ngController](https://docs.angularjs.org/api/ng/directive/ngController)

> The `ngController` directive attaches a controller class to the view. This is a key aspect of how angular supports the principles behind the Model-View-Controller design pattern.

Scrolling further down the Source we see that the script has most of the content now. Adding all the new Filtering options etc.
  
O

    <script type="text/javascript">
     ...
     <script>var lfb=lfbInit('l2b');</script>
     <script>
      WebForm_InitCallback();$(function(){
       ...
      }
     </script>
     ...
    </script>

A

    <script>var lfb=lfbInit('l2b');</script>
    <script>
     angular.controller('l1b_Ctrl',function ($scope) {
      $scope.controlConfig = {
     ...
     }
    </script>

This is all generated for you but you can hook into the controls with their ids if you were wanting to implement extra functionality.

[![Protirus](images\Protirus.png)](https://www.protirus.com)
