---
title: Workflow - Sharepoint
tags:
    - Workflow
author: AlexHedley
# description: 
# articleId: 
published: 2016-07-08
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-sharepoint?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

Workflow offers a couple of options when working with Sharepoint.
  
There is the Integration Component for Sharepoint List manipulation or there is the library.
  
New ![Int](images\Int.png)

****

Integration Component  
Choose "Microsoft"  
SharePoint Lists Generator
  
![Create Generator - Sharepoint List Generator](images\CreateGenerator-SharepointListGenerator.png)
  
Next fill in your details

| Sharepoint site: |  |
| --- | --- |
|  | Use authentication |
| Username: |  |
| Password: |  |
| Domain: |  |

Choose which Lists you want to work with
  
![Sharepoint List](images\SharepointList.png)
  
Give it a Namespace and Component names
  
![Sharepoint List - Components](images\SharepointList-Components.png)
  
Add this Library to your Workflow and pull in the components you need.
  
You can use the Search Items where ID - IS NOT NULL if you want all items returned.
  
Precreated DLL
  
Another option is to use the DLL created by Symantec.  
Create a Web Forms project and add in:

    LogicBase.Components.SharePoint.dll

This will then prompt and tell you new Properties have been created.
  
When you drag on a component some Properties will be created for.
  
- SharepointUsername
- SharepointPassword
- SharepointDomain
- SharepointHost

![Sharepoint Property - Username](images\SharepointProperty-Username.png) ![Sharepoint Property - Password](images\SharepointProperty-Password.png)
  
![Sharepoint Property - Domain](images\SharepointProperty-Domain.png) ![Sharepoint Property - Host](images\SharepointProperty-Host.png)
  
Go to the ![Project](images\Project.png) Project Root then the **Properties** Tab.
  
![Project - Properties - Sharepoint](images\Project-Properties-Sharepoint.png)
  
There will then be a number of Components available to you:
  
![Components - Sharepoint](images\Components-Sharepoint.png)

- Add Document
- Add List Item
- Create Document Workspace
- Create Folder
- Delete Document Workspace
- Delete Folder
- Document List ([https://www.symantec.com/connect/articles/document-list](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=81354724-ec65-4cad-816f-f8d9fb2b550f&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments))
- Find Document Workspace Doc
- Get Document Workspace Data
- Rename Document Workspace

Forum
  
[https://www.symantec.com/connect/forums/workflow-reading-sharepoint-list](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=e85ebb47-071f-4137-8100-5d2f47e8b766&amp;CommunityKey=492058b4-42be-43e7-991d-986f1ea9ba7f&amp;tab=digestviewer#bme85ebb47-071f-4137-8100-5d2f47e8b766)
  
[https://www.symantec.com/connect/forums/workflow-and-sharepoint-lists](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=bef0f064-e339-4b2f-8708-977fbc6b3ff3&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=digestviewer#bmbef0f064-e339-4b2f-8708-977fbc6b3ff3)
  
[https://www.symantec.com/connect/forums/how-get-list-items-sharepoint-list-within-workflow](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=0721efbc-1bf1-443b-bdfb-edf8d2cd7d30&amp;CommunityKey=492058b4-42be-43e7-991d-986f1ea9ba7f&amp;tab=digestviewer#bm0721efbc-1bf1-443b-bdfb-edf8d2cd7d30)
  
Articles
  
[https://www.symantec.com/connect/articles/symantec-workflow-and-microsoft-sharepoint](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d36f9941-9c17-4130-b689-a647735ee194&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
