---
title: Workflow - Tools - Log Viewer
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

Start &gt; Programs &gt; Symantec &gt; Workflow Designer &gt; Tools &gt; Log Viewer

> The Log Viewer is one of the modules of Workflow Explorer. You can view, sort, and save log messages in the Log Viewer.
> 
> 
> Chapter 36 - pg607

Symantec Glossary

> **Log Viewer**
> 
> 
> [No item found]
> 
> 
> https://www.symantec.com/security_response/glossary/define.jsp?letter=l&word=

### File Location

    "[Install Drive]:\Program Files\Symantec\Workflow\Tools\Symantec.Explorer.exe" -page LogViewer

###  
  
### Info
  
The Log Viewer is a tab in [Workflow Explorer](https://www.symantec.com/connect/articles/workflow-tools-workflow-explorer).
  
The Log Viewer can group the logs by column, just drag a column header into the top section.
  
You can have this auto refresh so new logs show up, you can clear or clear all.
  
There is a save option to backup the logs too.
  
They are available at

    [Install Drive]:\Program Files\Symantec\Workflow\Logs\

### Screenshots
  
![SWE LogViewer](images\SWE_LogViewer.png)

### Logging Level
  
There are different Logging Levels in Workflow, these can be set in the "[Create Log Entry](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=48e3fe7e-27f5-400e-b541-0eb66b8272d8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)" component.

- All
- Fatal
- Error
- Warn
- Info
- Debug

To change what is shown in the logs click on the "Current Running Processes" tab, right click on the Process you wish to modify.
  
![Logging Level](images\Workflow-LogViewer-LoggingLevel_1.png)
  
Or select the row in the table and click "Configure Logging".
  
![Logging Level](images\Workflow-LogViewer-LoggingLevel_2.png)
  
Then select the level and switch back to the "Log Viewer" tab.
  
<u>Forum</u>
  
How do I change the logging level of Workflow log viewer in version 7.1?  
https://www.symantec.com/connect/forums/how-do-i-change-logging-level-workflow-log-viewer-version-71

### Help
  
About the Log Viewer  
[https://support.symantec.com/en_US/article.HOWTO62221.html](http://​https://support.symantec.com/en_US/article.HOWTO62221.html)

### Alternatives
  
Workflow/ServiceDesk Log Analysis Tool  
[https://www.symantec.com/connect/articles/workflowservicedesk-log-analysis-tool](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4053458c-4949-4015-95fd-cdf8428267c6&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)

### Errors
