---
title: Workflow - Plugins - Protirus - Zip
tags:
    - Workflow
    - Plugin
author: AlexHedley
# description: 
# articleId: 
published: 2017-12-06
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-plugins-protirus-zip?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

## Zip
  
The 'Zip' Plugin has been produced to match similar functionality as the Altiris Log Viewer which also has a Zip function.
  
The 'Protirus.Workflow.Plugins.xml' has a *&lt;files&gt;* section that can be configured to display which Log files will show by default. These can then be chosen and added to the package that is zipped.

### Plugin Icon
  
![Zip](images\Zip.png)

### Author
  
![Protirus_0](images\Protirus_0.png) [Protirus](https://www.protirus.com) ([Alex Hedley](https://www.symantec.com/connect/user/alexhedley))

### Perform Action
  
Open a Form that allows for Folder/File selection and then a Zip action to bundle the files to given directory.
  
![Workflow Plugins Zip](images\Workflow-Plugins-Zip.png)
  
Update the file with the ones you wish to show.

    <files>
        <filesDef>
          <name>processmanager.log</name>
          <show>true</show>
        </filesDef>
      ...
    </files>

### Alternative
  
Manually find the files and compress yourself.

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
