---
title: Workflow - Plugins - Resource
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-11-28
---

## Resource

Re-run this when you create new ![](images\Resource.png) Resources and ![Data Classes](images\DataClasses.png) Data Classes in the ![SMP](images\smp.png) SMP.
  
This will make them available as DataTypes in your Workflows.

| You may wish to backup this file before making any changes. |
| --- |

![Int](images\Int.png) Symantec.Components.Generated7.Altiris.Resource
  
[Install Drive]:\Program Files\Symantec\Workflow\WorkflowProjects\Symantec.Components.Generated7.Altiris.Resource

Double click on the Integration Component and click "Adjust Definitions"
  
![Resource 1](images\Resource_1.png)

### 1. SMP server
  
Choose your SMP server, this will be a list from the ![Workflow](images\Workflow.png) Workflow Explorer | Credentials | Symantec Management Platform
  
![Resource 2](images\Resource_2.png)
  
### 2. Components
  
This will loop through all the Resources in your SMP, including custom ones.
  
![Resource 3](images\Resource_3.png)
  
There is then a list of Components you could generate.
  
I usually don't create components and use the generate Create/Update Resouce and map them in.
  
![Resource 4](images\Resource_4.png)
  
Back to the Main Menu, click on "Compile and Close".
  
If you do tick any you can use the Help Editor to add Icons.

[Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins
  
![DLL](images\dll.png) Symantec.Generators7.ASDK.ResourceService.dll
