---
title: Workflow - Tools - LocalMachineInfo Editor
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

Start &gt; Programs &gt; Symantec &gt; Workflow Designer &gt; Tools &gt; Local Machine Info Editor

> The Local Machine Info Editor lets you configure settings regarding publishing, data persistence, notifications, and other features. The settings in the Local Machine Info Editor apply only to the local computer.
> 
> 
> Chapter 35 - pg604

Symantec Glossary

> **Local Machine Info Editor**
> 
> 
> A client tool for Workflow Solution that is used primarily to configure servers accessible from the local computer. Also configures a few other settings including logging settings.
> 
> 
> [https://www.symantec.com/security_response/glossary/define.jsp?letter=l&word=local-machine-info-editor](https://www.symantec.com/security_response/glossary/define.jsp?letter=l&amp;word=local-machine-info-editor)  
> 	[https://us.norton.com/online-threats/glossary/l/local-machine-info-editor.html](https://us.norton.com/online-threats/glossary/l/local-machine-info-editor.html)

### File Location

    "[Install Drive]:\Program Files\Symantec\Workflow\Tools\LogicBase.LocalMachineInfo.Editor.exe"

###  
  
### Info
  
![Local Machine Info](images\LocalMachineInfo.png)

### Sections
  
Servers

| Servers | local |
| --- | --- |
| Default Server | (local) |

Highlight an item in the Servers list and click Edit.
  
![Local Machine Info - Server](images\LocalMachineInfo-Server.png)

Workflow Server

| Workflow Server Configuration | Workflow Server Setup |
| --- | --- |
| Default Workflow Persistence | Type: SQL; Connection String: Data Source=##;Initial Catalog=ProcessManager;Integrated Security=True;Pooling=True;Connect Timeout=30 |
| Application Properties Refresh Interval | 00:01:00 |

In the "Workflow Server" section if you click the ellipse (...) against "Workflow Server Setup" you will be taken to the

- [Server Extensions Configurator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=bec1d012-42aa-49f6-8355-01109d8d1d2f&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

Data Storage

| Object Storage Default Exchange Name | local.orm |
| --- | --- |

Local Machine

| Do Not Process Timeout And Escalations |  |
| --- | --- |
| Use Windows Integrated Authentication | True |
| Integrated Authentication URL | /ProcessManager/WindowsAuthentication.aspx |

Beta Functionality

| Enable Beta Features |  |
| --- | --- |
| Beta Key | (null) |

Contact Support to get a beta key (GUID), this allowed testing an original REST Generator that has now been redesigned and released as core component of the Product.

Remote Connections

| Ignore Certificate Warnings | True |
| --- | --- |

### Help
  
About the Local Machine Info Editor

- [https://support.symantec.com/en_US/article.HOWTO62219.html](https://support.symantec.com/en_US/article.HOWTO62219.html)

### Errors
  
Workflow Timeouts and Escalations are not Running

- [https://support.symantec.com/en_US/article.GUIDES10321.html](https://support.symantec.com/en_US/article.GUIDES10321.html)
