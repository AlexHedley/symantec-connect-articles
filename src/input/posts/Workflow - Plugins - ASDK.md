---
title: Workflow - Plugins - ASDK
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-11-28
---

## ASDK

| You may wish to backup this file before making any changes. |
| --- |

![Int](images\Int.png) Symantec.Components.Generated7.Altiris.ASDK
  
[Install Drive]:\Program Files\Symantec\Workflow\WorkflowProjects\Symantec.Components.Generated7.Altiris.ASDK

Double click on the Integration Component and click "Adjust Definitions"
  
![ASDK 1](images\ASDK_1.png)
  
### 1. SMP server
  
Choose your SMP server, this will be a list from the ![Workflow](images\Workflow.png) Workflow Explorer | Credentials | Symantec Management Platform
  
![ASDK 2](images\ASDK_2.png)
  
### 2. Components
  
This will run through all the Web Services.
  
- /altiris/asdk.ns/ItemManagementService.asmx
- /altiris/asdk.ns/CollectionManagementService.asmx
- /altiris/asdk.ns/ReportManagementService.asmx
- /altiris/asdk.ns/SecurityManagementService.asmx
- /altiris/asdk.ns/ResourceManagementService.asmx
- /altiris/asdk.ns/ScopingManagementService.asmx
- /altiris/asdk.ns/HierarchyManagementService.asmx
- /altiris/asdkasset/AssetManagementLibService.asmx
- /altiris/asdk.helpdesk/ContactManagementService.asmx
- /altiris/asdk.swd/softwaremanagementbasicservice.asmx
- /altiris/asdk.deploymentsolution/dstaskmanagementservice.asmx
- /altiris/asdk.ns.softwaredelivery/swdsolnadvertisementmanagementservice.asmx
- /altiris/asdk.ns.softwaredelivery/swdsolnpackagemanagementservice.asmx
- /altiris/asdk.ns.softwaredelivery/swdsolnprogrammanagementservice.asmx
- /altiris/asdk.smf/inventoryrulemanagementservice.asmx
- /altiris/asdk.smf/softwarecommandlinemanagementservice.asmx
- /altiris/asdk.smf/softwarecomponentmanagementservice.asmx
- /altiris/asdk.smf/softwarepackagemanagementservice.asmx
- /altiris/asdk.smf/softwareproductmanagementservice.asmx
- /altiris/asdk.swm/softwaredeliverypolicymanagementservice.asmx
- /altiris/asdk.swm/softwareportalmanagementservice.asmx
- /altiris/asdk.swm/softwaretasksmanagementservice.asmx

![ASDK 3](images\ASDK_3.png)
  
You can then tick any extra components you require in your Workflows.
  
![ASDK 4](images\ASDK_4.png)
  
Back to the Main Menu, click on "Compile and Close".
  
Add any Icons to the newly created components.
  
![ASDK 5](images\ASDK_5.png)

### Web Services
  
The list of WS that are used in the Generator are defined in the following file.

| This is just for reference, don't amend this file. |
| --- |

[Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins
  
![XML](images\XML.png) Symantec.Generators7.ASDK.xml

Associated Plugin.
  
![SLL](images\dll.png) Symantec.Generators7.ASDK.dll

Example content

    <configuration>
      <sources>
        <sourcedef>    <url>/altiris/asdk.ns/ItemManagementService.asmx</url>    <category>Altiris 7.Web Services.Item</category>
        </sourcedef>
        ...
      </sources>
      <components>
        <componentDef>
          <name>PushAltirisAgentToComputers</name>
        </componentDef>
        ...
      </components>
    </configuration>
