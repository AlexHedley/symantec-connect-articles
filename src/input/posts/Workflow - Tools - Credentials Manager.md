---
title: Workflow - Tools - Credentials Manager
# tags:
#     - 
author: AlexHedley
# description: 
published: 2018-01-23
---

Table Of Contents
  
- [Application Editor](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=19195da8-6f79-40a5-b020-7932e20a53f4&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [BusinessTimeSpan Editor](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f72f9c48-ffc1-4b0d-9339-b9cae6cf2966&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Composer Theme Editor](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=824347c4-f538-4404-9f2f-59ca0658673a&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Credentials Manager](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63e53603-2ac2-46b8-9c06-8129bc483418&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [License Status Manager](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4ac6f1c4-6896-489d-801c-f4fef130a9be&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [LocalMachineInfo Editor](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4807af83-e87d-4449-9493-f96c546f5561&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Log Viewer](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2941c9ac-9aa9-44e6-a8b3-fe2d0ba95f29&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Messaging Console](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f41a78e3-cdf4-4c4c-93e2-331d3b44dfab&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Schedule Editor](https://www.symantec.com/connect/articles/workflow-tools-schedule-editor)
- [Screen Capture Util](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0d264462-736b-466e-bfa2-4c868cbf75a3&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Server Extensions Configurator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=bec1d012-42aa-49f6-8355-01109d8d1d2f&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Task Tray Tool](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=b84a792f-da66-4bc1-8c31-371f86bf37f6&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [ToolPreferences Editor](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=613c69e7-9838-4204-a0ee-bff67cf25033&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow Explorer](https://www.symantec.com/connect/articles/workflow-tools-workflow-explorer)

Start &gt; Programs &gt; Symantec &gt; Workflow Designer &gt; Tools &gt; Credentials Manager

> Credentials Manager lets you add, edit, or remove credentials for the Symantec Management Platform and solutions. Credentials Manager handles all of the credentials that you need to create and publish workflow processes. Every Workflow Designer or Workflow Server computer that needs to connect to the Symantec Management Platform computer must have credentials.
> 
> 
> Credentials Manager is part of Workflow Explorer, so you can also use it to work with SymQ and logging. You can also work with SymQ and logging from the main Workflow Explorer tool.
> 
> 
> Chapter 33 - User Guide

Symantec Glossary

> **Credentials Manager**  
> 	A secure store for the credentials that are used by Notification Server and installed solutions.
> 
> 
> https://www.symantec.com/security_response/glossary/define.jsp?letter=c&word=credential-manager

###  
  
### File Location

    "[Install Drive]:\Program Files\Symantec\Workflow\Tools\Symantec.Explorer.exe" -page CredentialManager" 

###  
  
### Info
  
You can create the following Credentials

- Active Directory
- Deployment Server
- Symantec Management Platform

These are saved as XML files in the following location.

    C:\ProgramData\Symantec\Workflow\

- Connections_ActiveDirectoryConnectionProfile.xml
- Connections_DeploymentServerConnectionProfile.xml
- Connections_NotificationServerConnectionProfile.xml
- *ProcessManager_ActiveDirectoryConnectionProfile.xml*

If the Credentials Manager has been tested and shows as successful but you are still getting errors in your workflow it might be worth nuking these Files, which will delete the stored creds and re-creating them. This can solve a number of issues.

### Screenshots
  
Active Directory
  
Click on the "Active Directory" tab.
  
![SWE_CredentialsManager_ActiveDirectory](images\SWE_CredentialsManager_ActiveDirectory.png)
  
Click on Add New and fill in the values.
  
![SWE_CredentialsManager_ActiveDirectory_AddNew](images\SWE_CredentialsManager_ActiveDirectory_AddNew.png)
  
You can highlight a Profile and click "Test"
  
![SWE_CredentialsManager_ActiveDirectory_Test_Succeed](images\SWE_CredentialsManager_ActiveDirectory_Test_Succeed.png)
  
Deployment Server
  
Click on the "Deployment Server" tab.
  
![SWE_CredentialsManager_DeploymentServer](images\SWE_CredentialsManager_DeploymentServer.png)

![SWE_CredentialsManager_DeploymentServer_NewProfile](images\SWE_CredentialsManager_DeploymentServer_NewProfile.png)
  
Symantec Management Platform
  
Click on the "Symantec Management Platform" tab.
  
![SWE_CredentialsManager_SMP](images\SWE_CredentialsManager_SMP.png)
  
Click on "Add" and fill in the required details.
  
![SWE_CredentialsManager_SMP_AddNew](images\SWE_CredentialsManager_SMP_AddNew.png)
  
You can also "Test" this to make sure it's valid.
  
![SWE_CredentialsManager_SMP_Test_Succeed](images\SWE_CredentialsManager_SMP_Test_Succeed.png)

### Help
  
About Credentials Manager  
[https://support.symantec.com/en_US/article.HOWTO62287.html](https://support.symantec.com/en_US/article.HOWTO62287.html)
  
Adding credentials in Credentials Manager  
[https://support.symantec.com/en_US/article.HOWTO62288.html](https://support.symantec.com/en_US/article.HOWTO62288.html)

### Errors
  
Credentials Manager crashes with error Symantec.Explorer.exe has stopped working  
[https://support.symantec.com/en_US/article.TECH180691.html](https://support.symantec.com/en_US/article.TECH180691.html)
