---
title: Workflow - Plugins - Protirus - Restart IIS
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-12-06
---

## Restart IIS
  
The 'Restart IIS' plugin will restart IIS on the Workflow box using the currently logged in user..

### Plugin Icon
  
![WebServer](images\WebServer.png)
  
### Author
  
![Protirus 0](images\Protirus_0.png) [Protirus](https://www.protirus.com) ([Alex Hedley](https://www.symantec.com/connect/user/alexhedley))

### Perform Action
  
IIS will be restarted using the currently logged in user.
  
###  
  
### Alternative
  
Open IIS Manager (Start | Administrative Tools | Internet Information Services (IIS) Manager)

    %windir%\system32\inetsrv\InetMgr.exe

    iisreset

    Process.Start("net", "stop w3svc"); //net stop IISADMIN
    Process.Start("net", "start w3svc"); //net start IISADMIN

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
