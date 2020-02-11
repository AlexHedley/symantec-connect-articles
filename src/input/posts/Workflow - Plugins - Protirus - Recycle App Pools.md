---
title: Workflow - Plugins - Protirus - Recycle App Pools
tags:
    - Workflow
    - Plugin
author: AlexHedley
# description: 
# articleId: 
published: 2017-12-06
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-plugins-protirus-rec?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

## Recycle App Pools
  
The 'Recycle App Pools' plugin allow you to Recycle a chosen App Pool via a Form.

### Plugin Icon
  
![Application Pool](images\ApplicationPool.png)
  
### Author
  
![Protirus 0](images\Protirus_0.png) [Protirus](https://www.protirus.com) ([Alex Hedley](https://www.symantec.com/connect/user/alexhedley))

### Perform Action
  
A Form is displayed with a list of App Pools, clicking on an App Pool will display the Applications within it.
  
You can Recycle a chose App Pool and check on it's current Status.
  
You can also open IIS.
  
![Workflow - Plugins - RecycleAppPools](images\Workflow-Plugins-RecycleAppPools.png)
  
###  
  
### Alternative
  
Open IIS Manager (Start | Administrative Tools | Internet Information Services (IIS) Manager)

    %windir%\system32\inetsrv\InetMgr.exe

### Location

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins\

### DLL
  
- Protirus.Workflow.Plugins.dll

### Code
  
N/A

### Customise
  
Can be hidden with a config change in the 'Protirus.Workflow.Plugins.xml' file.

### Documentation
  
[Display any related Documentation]

- Title URL
    - Chapter/Page #

### Support
  
[Display any related Support Documents]

- Title
    - URL
