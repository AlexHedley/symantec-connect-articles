---
title: Workflow Profile Definition Error
tags:
    - Workflow
    - error
author: AlexHedley
# description: 
published: 2015-04-22
---

Have you ever tried to add a Profile and got an error:

"Value cannot be null. Parameter name: value"

![Add Profile Definition.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3401451-files_Add%20Profile%20Definition.png)

* * *

You can't have a <span style="font-family: &quot;Arial&quot;, sans-serif; font-size: 10pt">uniqueidentifier as a datatype for your Foreign Key or include this another in your Profile.</span>

* * *

You can't have your Foreign Key Field (usually SessionID) as the <u>first</u> Field in your Table/View.

* * *

<span style="font-family: &quot;Arial&quot;, sans-serif; font-size: 10pt">Check the data types on the fields you are selecting. If you see any "_nchar_" change them to _nvarchar_.  

This shouldn't be a problem with respect to the data, anything you can fit in an nchar will also fit in nvarchar of the same size.</span>

* * *

If you look in the Logs

  <INSTALL FOLDER>:\Program Files\Symantec\Workflow\Logs\**processmanager.log**

you should see a similar error:

<pre>Error,20 April 2015 08:11:43,[global] Application 'LogicBase.Ensemble' error [global] Client Host Information: [global] IP: ::1 [global] HostName: ::1 [global] -- error.ToString() -- [global] System.Web.HttpCompileException: e:\Program Files\Symantec\Workflow\ProcessManager\ProfileServices\**<PROFILE NAME>**Service.asmx(76): error CS1001: Identifier expected [global] at System.Web.Compilation.AssemblyBuilder.Compile() [global] at System.Web.Compilation.BuildProvidersCompiler.PerformBuild() [global] at System.Web.Compilation.BuildManager.CompileWebFile(VirtualPath virtualPath) [global] at System.Web.Compilation.BuildManager.GetVPathBuildResultInternal(VirtualPath virtualPath, Boolean noBuild, Boolean allowCrossApp, Boolean allowBuildInPrecompile) [global] at System.Web.Compilation.BuildManager.GetVPathBuildResultWithNoAssert(HttpContext context, VirtualPath virtualPath, Boolean noBuild, Boolean allowCrossApp, Boolean allowBuildInPrecompile) [global] at System.Web.UI.WebServiceParser.GetCompiledType(String inputFile, HttpContext context) [global] at System.Web.Services.Protocols.WebServiceHandlerFactory.GetHandler(HttpContext context, String verb, String url, String filePath) [global] at System.Web.Script.Services.ScriptHandlerFactory.GetHandler(HttpContext context, String requestType, String url, String pathTranslated) [global] at System.Web.HttpApplication.MapHttpHandler(HttpContext context, String requestType, VirtualPath path, String pathTranslated, Boolean useAppConfig) [global] at System.Web.HttpApplication.MapHandlerExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() [global] at System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously)</pre>

* * *

When a Profile is created an .asmx file is created in the following folder:

  <INSTALL DRIVE>:\Program Files\Symantec\Workflow\ProcessManager\ProfileServices\**<PROFILE NAME>**Service.asmx

There is also a record added to

  [ProcessManager].[dbo].[ProfileDefinition]

* * *

To add a new Profile

**Process Manager** | **Admin** | **Data** | **Lists and Profiles**

**Add Profile Definition (Existing Table)**

![Add Profile Definition (Existing Table).png](/connect/sites/default/files/users/user-2946791/Add%20Profile%20Definition%20%28Existing%20Table%29.png)

* * *

[![Protirus.png](https://higherlogicdownload.s3.amazonaws.com/BROADCOM/SymantecInlineImages/article-3401451-files_Protirus.png)](http://protirus.com/)
