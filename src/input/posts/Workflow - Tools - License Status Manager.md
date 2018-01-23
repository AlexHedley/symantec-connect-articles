---
title: Workflow - Tools - License Status Manager
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

Start &gt; Programs &gt; Symantec &gt; Workflow Designer &gt; Tools &gt; License Status Manager

> The License Status Manager lets you view licensing information about Workflow and Workflow-related applications (such as ServiceDesk). This tool also lets you run tests on your license to verify that it works properly. The tool does not create or manage licensing. The Symantec Management Platform manages all licensing. The tool communicates with the Symantec Management Platform to determine licensing information.
> 
> 
> Chapter 34 - User Guide

Symantec Glossary

> **License Status Manager**  
> 	[No Item Found]  
> 	Description
> 
> 
> https://www.symantec.com/security_response/glossary/define.jsp

###  
  
### File Location

    "[Install Drive]:\Program Files\Symantec\Workflow\Tools\Symantec.LicenseStatus.Editor.exe"

### Info
  
![Application Licenses](images\LicenseStatusManager_ApplicationLicenses.png)
  
You can Export the Machine Key but you need to add a Company before your click Export.
  
![Runtime Licenses](images\LicenseStatusManager_RuntimeLicensesLicenses.png)
  
This allows you to choose a location to Export too.
  
Default file "LicenseMachineKey"
  
![Export](images\LicenseStatusManager_RuntimeLicensesLicenses_Export.png)
  
This uses "Symantec.Workflow.Licensing.MachineData" and RSA.
  
You can see some information if you open this in Notepad.

**Add** requires a ".symwflic" file type.

### Help
  
About the License Status Manager  
[https://support.symantec.com/en_US/article.HOWTO62218.html](https://support.symantec.com/en_US/article.HOWTO62218.html)

### Errors
  
ServiceDesk 7.x Licensing Error Messages and Troubleshooting Ideas  
[https://support.symantec.com/en_US/article.HOWTO50304.html](https://support.symantec.com/en_US/article.HOWTO50304.html)
  
Check the following SMP Service

- http://[SMPServername]/Altiris/ServiceDesk/licensing.asmx

### Plugins
  
Workflow - Plugins - License Status  
[https://www.symantec.com/connect/articles/workflow-plugins-license-status](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=231dfb42-45bc-4b54-9a0e-25c6968220ad&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
