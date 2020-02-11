---
title: Workflow - Plugins - ASDKTask
tags:
    - Workflow
    - Plugin
author: AlexHedley
# description: 
# articleId: 
published: 2017-11-28
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-plugins-asdktask?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

## ASDKTask

| You may wish to backup this file before making any changes. |
| --- |

![Int](images\Int.png)![](images\wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw%3d%3d) Symantec.Components.Generated7.Altiris.ASDKTask
  
[Install Drive]:\Program Files\Symantec\Workflow\WorkflowProjects\Symantec.Components.Generated7.Altiris.ASDKTask

Double click on the Integration Component and click "Adjust Definitions"
  
![ASDKTask 1](images\ASDKTask_1.png)

### 1. SMP server
  
Choose your SMP server, this will be a list from the ![](images\Workflow.png) Workflow Explorer | Credentials | Symantec Management Platform
  
![ASDKTask 2](images\ASDKTask_2.png)
  
### 2. Tasks
  
All the tasks from the TaskManagementService will be generated for use within your Workflows.
  
- http://localhost/Altiris/ASDK.Task/TaskManagementService.asmx
- https://localhost/Altiris/ASDK.Task/TaskManagementService.asmx

![ASDKTask 3](images\ASDKTask_3_.png)

You can select whichever ones you wish to use, there is also a search option.
  
It used to be a good idea to copy/paste the whole term as each letter typed would filter slowly.
  
![ASDKTask 4](images\ASDKTask_4.png)
  
Back to the Main Menu, click on "Compile and Close".
  
You now have a new section under Symantec | SMP 7 | Tasks (with icons!)
  
![ASDKTask 5](images\ASDKTask_5.png)

[Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins
  
![DLL](images\dll.png) Symantec.Generators7.ASDK.TaskService.dll
