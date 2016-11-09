---
title: Workflow - Component - Developer Guide - Logging
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-11-09
---

In this Article I'm going to explain how to Log information in your component.
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=17aa2b9a-9092-40d0-afab-a6d8316de97d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70a9fde5-0d87-4b9d-a3be-0907567ffc00&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Help File](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80437c69-ccc3-47e6-a850-9cf3f301b340&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Logging](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63b72a9a-53b8-4d4b-bce3-5f0732b134d5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- Inputs
    - [Checkbox](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74c56ef7-1119-40fe-9d5f-3c7a1d808d4c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [Dropdown / Combo](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=267159ac-b8e7-45b4-abe4-f85d78e30783&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2c3b3a6f-01d7-4157-a143-ba30c9edc930&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other Components
- [Creating Globals](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=cf54de06-be56-46ff-b937-148efa57eaec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Creating Project Properties](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4cfc07c5-404e-49b3-81b6-520d4ea43d5c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f3cf0097-06e7-42f3-a747-d0dff319c1e5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with a Web Service](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=26368883-708b-4432-999b-7064f2f25794&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

There are times when you wish to log information to the Workflow Logs, for the Project the component is in.

    [Install Drive]:\Program Files\Workflow\Logs\*.log

There are a number of log levels you can choose from.
  
Take the [Create Log Entry](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=48e3fe7e-27f5-400e-b541-0eb66b8272d8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) as an example of which.

- Info
- Error
- Debug
- Fatal
- Warn

We have a number of logging methods since we inherit from "AbstractSinglePathProcessComponent" =&gt; "AbstractSinglePathComponent" =&gt; "AbstractOrchestrationComponent"

    namespace LogicBase.Core
    {
        public abstract class AbstractOrchestrationComponent : IStorable, IOrchestrationComponent, IValidWithNofication, IValid
        {
            ...
            protected void LogDebug(IData data, string Debug);
            protected void LogError(IData data, Exception ex);
            protected void LogError(IData data, string message);
            protected void LogError(IData data, Exception ex, string message);
            protected void LogFatal(IData data, string message);
            protected void LogFatal(IData data, string message, Exception ex);
            protected void LogInfo(IData data, string Info);
            protected void LogWarn(IData data, string message);
            ...
        }
    }

If we start typing Log into VS we will get autocompletion for the following methods.
  
![WorkflowLogLevels](images\WorkflowLogLevels.png)
  
We could either call

    base.LogError(data, "No rows found.");

Or base. isn't necessary.

    LogError(data, "No rows found.");

Another thing I tend to do is add a [Checkbox](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74c56ef7-1119-40fe-9d5f-3c7a1d808d4c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to the component and use that as a way to decide whether to log the information information. You could pass in a Debug flag.
  
Another option it to always log to Info then turn on the logging level in Workflow Explorer.
  
![Protirus.png](images\Protirus.png)
