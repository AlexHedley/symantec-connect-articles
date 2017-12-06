---
title: Workflow - Plugins - Protirus - Restart Workflow Services
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-12-06
---

## Restart Workflow Services
  
The 'Restart Workflow Services' plugin will restart the Workflow Service (*swfsvr*) as your user account.

### Plugin Icon
  
![Services](images\Services.png)

### Author
  
![Protirus 0](images\Protirus_0.png) [Protirus](https://www.protirus.com) ([Alex Hedley](https://www.symantec.com/connect/user/alexhedley))

### Perform Action
  
Workflow Service (*swfsvr*) will be restarted using the currently logged in user.
  
###  
  
### Alternative
  
Open 'Task Tray Tool' - Start | All Programs | Symantec | Workflow Designer | Tools  
("[Install Drive]:\Program Files\Symantec\Workflow\Tools\LogicBase.Local.TaskTray.exe")
  
Restart Server Extensions
  
![TaskTrayTool-RestartServerExtensions](images\TaskTrayTool-RestartServerExtensions.png)

### Location

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins\

### DLL
  
- Protirus.Workflow.Plugins.dll

### Code

    net stop swfsvr
    net start swfsvr

###  
  
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
