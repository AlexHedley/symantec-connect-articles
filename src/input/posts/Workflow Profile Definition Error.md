---
title: Workflow Profile Definition Error
tags:
    - Workflow
    - Error
author: AlexHedley
# description: 
# articleId: 
published: 2015-04-22
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-profile-definition-error?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

Have you ever tried to add a Profile and got an error:
  
"Value cannot be null. Parameter name: value"
  
![Add Profile Definition.png](images\article-3401451-files_Add+Profile+Definition.png)
  
* * *
 
You can't have a uniqueidentifier as a datatype for your Foreign Key or include this another in your Profile.

* * *
 
You can't have your Foreign Key Field (usually SessionID) as the <u>first</u> Field in your Table/View.

* * *
 
Check the data types on the fields you are selecting. If you see any "*nchar*" change them to *nvarchar*.  
  
This shouldn't be a problem with respect to the data, anything you can fit in an nchar will also fit in nvarchar of the same size.

* * *
 
If you look in the Logs
  
&lt;INSTALL FOLDER&gt;:\Program Files\Symantec\Workflow\Logs\**processmanager.log**
  
you should see a similar error:

    Error,20 April 2015 08:11:43,[global] Application 'LogicBase.Ensemble' error
    [global] Client Host Information:
    [global] IP: ::1
    [global] HostName: ::1
    [global] -- error.ToString() --
    [global] System.Web.HttpCompileException: e:\Program Files\Symantec\Workflow\ProcessManager\ProfileServices\<PROFILE NAME>Service.asmx(76): error CS1001: Identifier expected
    [global]    at System.Web.Compilation.AssemblyBuilder.Compile()
    [global]    at System.Web.Compilation.BuildProvidersCompiler.PerformBuild()
    [global]    at System.Web.Compilation.BuildManager.CompileWebFile(VirtualPath virtualPath)
    [global]    at System.Web.Compilation.BuildManager.GetVPathBuildResultInternal(VirtualPath virtualPath, Boolean noBuild, Boolean allowCrossApp, Boolean allowBuildInPrecompile)
    [global]    at System.Web.Compilation.BuildManager.GetVPathBuildResultWithNoAssert(HttpContext context, VirtualPath virtualPath, Boolean noBuild, Boolean allowCrossApp, Boolean allowBuildInPrecompile)
    [global]    at System.Web.UI.WebServiceParser.GetCompiledType(String inputFile, HttpContext context)
    [global]    at System.Web.Services.Protocols.WebServiceHandlerFactory.GetHandler(HttpContext context, String verb, String url, String filePath)
    [global]    at System.Web.Script.Services.ScriptHandlerFactory.GetHandler(HttpContext context, String requestType, String url, String pathTranslated)
    [global]    at System.Web.HttpApplication.MapHttpHandler(HttpContext context, String requestType, VirtualPath path, String pathTranslated, Boolean useAppConfig)
    [global]    at System.Web.HttpApplication.MapHandlerExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute()
    [global]    at System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously)

* * *
 
When a Profile is created an .asmx file is created in the following folder:
  
&lt;INSTALL DRIVE&gt;:\Program Files\Symantec\Workflow\ProcessManager\ProfileServices\**&lt;PROFILE NAME&gt;**Service.asmx
  
There is also a record added to
  
[ProcessManager].[dbo].[ProfileDefinition]
  
* * *

To add a new Profile
  
**Process Manager** | **Admin** | **Data** | **Lists and Profiles**
  
**Add Profile Definition (Existing Table)**
  
![Add Profile Definition (Existing Table).png](images\Add%2520Profile%2520Definition%2520%2528Existing%2520Table%2529.png)

* * *
 
[![Protirus.png](images\article-3401451-files_Protirus.png)](http://protirus.com/)
