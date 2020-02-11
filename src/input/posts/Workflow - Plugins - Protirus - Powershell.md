---
title: Workflow - Plugins - Protirus - Powershell
tags:
    - Workflow
    - Plugin
author: AlexHedley
# description: 
# articleId: 
published: 2017-12-06
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-plugins-protirus-pow?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

## Powershell
  
The 'Powershell' plugin opens a file picker, filters on Powershell file extensions (**.ps1*, **.psm1*, **.psd1*) and then runs the chosen file with custom param ($project) that can be used in your Powershell script.

### Plugin Icon
  
![Powershell 32](images\Powershell_32.png)

### Author
  
![Protirus 0.](images\Protirus_0.png) [Protirus](https://www.protirus.com) ([Alex Hedley](https://www.symantec.com/connect/user/alexhedley))

### Perform Action
  
Choose a Powershell file to run, you can chose whether to hide the powershell dialog.
  
This runs with a param of the Project Directory "-project"
  
So you can add the following to your powershell scripts to access this path.

    param([String]$project="")
    ...
    write-output $project

![Workflow Plugins Powershell](images\Workflow-Plugins-Powershell.png)
  
### ![Workflow Plugins Powershell OpenFile](images\Workflow-Plugins-Powershell-OpenFile.png)

### Alternative
  
Start | All Programs | Accessories | Windows PowerShell

    %SystemRoot%\system32\WindowsPowerShell\v1.0\powershell.exe

### Location

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins\

### DLL
  
- Protirus.Workflow.Plugins.dll

### Code

    powershell.exe -file "FILENAME"

Or

    powershell.exe -file "" -project ""

Or

    powershell.exe -windowstyle Hidden -file "" -project ""

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
