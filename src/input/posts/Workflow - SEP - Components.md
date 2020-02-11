---
title: Workflow - SEP - Components
tags:
    - Workflow
    - SEP
    - Component
author: AlexHedley
# description: 
articleId: 3769501
published: 2018-05-09
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-sep-components?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

![QuarantineMachine](images\QuarantineMachine.png)
  
If you create a new Project and add the Integration Library "Symantec.Components.SEP.dll"

    [Install Drive]:\Program Files\Symantec\Workflow\Shared\components\Symantec.Components.SEP.dll

This will then allow you to use the Components within your Process.
  
### Properties
  
3 new Properties will be added to your Project when you drag on a component.
  
Project Properties

| Name | Value |
| --- | --- |
| SEPUsername | *sepuser* |
| SEPPassword | *\*\*\*\*\*\*\*\*\*\*\** |
| SEPURL | https://sepserver:8443/spc-webservice |

Update these to values that will work in your environment.

### Components
  
![Workflow_SEP_Components_1](images\Workflow_SEP_Components_1.png)
  
![Workflow_SEP_Components_2](images\Workflow_SEP_Components_2.png)
  
Symantec  
  SEP
  
Admin
  
- Create Domain Admin Account
- Create Limited Admin Account
- Create System Admin Account
- Delete Admin Account
- Get Admin Account List
- Get Database Info
- Get Server Properties

Clients

- Add Computer Account
- Clear Client List
- Get All Group GUIDs
- Get Client Group Settings
- Get Client Group Structure
- Get Client List
- Get Client List Page
- Get Clients In Group Brief
- Move Client

Commands

- Clear Command Detail List
- Get Command Detail Page
- Get Command Status Detail
- Get Command Status Summary
- Get Command Status Summary End Time
- Run Client Command Enable AP
- Run Client Command Reboot
- Run Client Command Scan
- Run Client Command Update Content
- Run Client Command Update Content And Scan
- Run Group Command Enable AP
- Run Group Command Reboot
- Run Group Command Scan
- Run Group Command Update Content
- Run Group Command Update Content And Scan
- Run Client Command Disable NTP
- Run Client Command Enable NTP
- Run Group Command Disable NTP
- Run Group Command Enable NTP

Policies

- Assign Policy To Group
- Get App Policy List
- Get Av Policy List
- Get Ce Policy List
- Get Custom Ips Policy List
- Get Fw Policy List
- Get Hi Policy List
- Get Ids Policy List
- Get Lu Content Policy List
- Get Lu Policy Settings List
- Withdraw Policy From Group

---
  
### Updated Versions
  
With the release of  ![Workflow](images\Workflow.png) WF 8.1 RU5 a selection of ![SEP Task Tray](images\SEPTaskTray.png) SEP 14 APIs were updated into a Components Library

- [Workflow - SEP 14 - Components](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=27d3a6a2-c04b-4cc4-81b6-58f991cc21f3&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
