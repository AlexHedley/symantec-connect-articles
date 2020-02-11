---
title: Workflow - Plugins - Protirus - Workflow Explorer
tags:
    - Workflow
    - Plugin
author: AlexHedley
# description: 
# articleId: 
published: 2017-12-06
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-plugins-protirus-wor?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

## Workflow Explorer (Running As)
  
The 'Workflow Explorer (Running As)' checks if Workflow Explorer is running and who has it open (the owner).
  
This is handy because it can only be open on one machine but gives no indiciation if it doesn't open, you can then contact the user to close it.

### Plugin Icon
  
![Workflow.png](images\Workflow.png)

### Author
  
![Protirus_0](images\Protirus_0.png) [Protirus](https://www.protirus.com) ([Alex Hedley](https://www.symantec.com/connect/user/alexhedley))

### Perform Action
  
Domain\Username or ![Workflow Plugins Protirus WorkflowExplorer NoOwner](images\Workflow-Plugins-Protirus-WorkflowExplorer-NoOwner.png)

### Alternative
  
Ctrl + Shift + Esc to open Windows Task Manager.
  
Click the "Processes" tab.
  
Tick ☑ "Show processes from all users"
  
Search for the Workflow Explorer (Symantec.Explorer.exe) and check the Process Owner.

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
