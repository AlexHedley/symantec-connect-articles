---
title: Workflow - Plugins - Create GUID
tags:
    - Workflow
    - Plugin
author: AlexHedley
# description: 
# articleId: 
published: 2017-05-24
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-plugins-create-guid?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

## Create GUID
  
The 'Create GUID' Plugin allows you to generate a random GUID, which can then either be copied to the clipboard or added to the  Primary Model of the current Workflow Project.
  
### Component icon
  
N/A
  
### Author
  
LogicBase / ![Symantec](images\Symantec.png) Symantec

### Perform Action
  
Plugins | Create GUID
  
![Workflow - Menu - Plugins - Create GUID](images\Workflow-Menu-Plugins-CreateGUID.png)

| BUG: This states "current model" but actually puts it into the ![Model 1](images\Model1.png) Primary model. |
| --- |

### Alternative
  
N/A

### Location

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins\

### DLL
  
- LogicBase.Plugins.CreateGUID.dll

### Code
  
Generate a GUID

    return Guid.NewGuid().ToString();

Copy to Clipboard

    Clipboard.SetDataObject(guid, true);

Create Component with the Guid pre-populated.

- [Add New Data Element](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a1fe7799-786f-402d-af88-d1560d2834d8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

There is more information in the following Article

- [Workflow - Plugin - Developer Guide - Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=6d54d145-537c-40e6-86ca-b5dec2b1e972&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

### Documentation
  
[Display any related Documentation]

- Title URL
    - Chapter/Page #

### Support
  
[Display any related Support Documents]

- Title
    - URL
