---
title: Workflow - Plugins - Reset Cache
tags:
    - Workflow
    - Plugin
author: AlexHedley
# description: 
# articleId: 
published: 2017-05-23
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-plugins-reset-cache?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

## Reset Cache
  
The Reset Cache plugin ...
  
### Component icon
  
N/A
  
### Author
  
LogicBase / ![Symantec](images\Symantec.png) Symantec

### Perform Action
  
There is no indication that the action has been performed visually in Workflow Manager.
  
###  
  
### Alternative
  
N/A

### Location

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins\

### DLL
  
- LogicBase.Plugins.ResetCache.dll

### Code

    NotificationBus.GetInstance(Constants.CACHE_BUS_NAME).Notify(Constants.CACHE_RESET_MESSAGE_NAME);

Inputs

    //LogicBase.Core.Utilities - Constants
    Constants.CACHE_BUS_NAME = "DesignerCache";
    Constants.CACHE_RESET_MESSAGE_NAME = "ResetCache";

NotificationBus

    //LogicBase.Framework - NotificationBus

### Documentation
  
[Display any related Documentation]

- Title URL
    - Chapter/Page #

### Support
  
[Display any related Support Documents]

- Title
    - URL
