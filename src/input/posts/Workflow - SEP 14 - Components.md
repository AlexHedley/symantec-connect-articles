---
title: Workflow - SEP 14 - Components
tags:
    - Workflow
    - SEP
    - Component
author: AlexHedley
# description: 
# articleId: 
published: 2018-03-29
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-sep-14-components?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

With the ![Workflow](images\Workflow.png) WF 8.1 RU5 release a new set of ![SEP Task Tray](images\SEPTaskTray.png) SEP 14 Components were added to the Solution.
  
If you create a new Project and add the Integration Library "Symantec.Components.SEP14.dll"

    [Install Drive]:\Program Files\Symantec\Workflow\Shared\components\Symantec.Components.SEP14.dll

This will then allow you to use the Components within your Process.
  
4 new Properties will be added to your Project

<caption>Project Properties</caption>

| Name | Value |
| --- | --- |
| SEPUsername | *sepuser* |
| SEPPassword | ************* |
| Domain | *default* |
| SEPURL | *https://sepmServer:8446/sepm/api/v1/* |

Update these to values that will work in your environment.

These will show in your Component list under
  
Symantec | SEP14
  
![SEP 14 Components](images\SEP14Components.png)

There are then a number of sub groups containing Components.
  
Admin
  
- Get Admin Accounts List
- Get Admin Details
- Get Admin Details

Clients

- Get Computer List Component
- Move Computer Component

Commands

- Get Command Status Details
- Run Command Base Line
- Run Command Quarantine
- Run Command Update Content

Domain

- Get Domain By Id Component
- Get Domains Component
- Update Domain Component

Group

- Get Group Computers Component
- Get Groups List Component

### SEP API Documentation
  
Symantec Endpoint Protection Manager 14.x REST API Reference  
[https://support.symantec.com/en_US/article.DOC9447.html](https://support.symantec.com/en_US/article.DOC9447.html)
  
Symantec Endpoint Protection Manager API reference  
[https://support.symantec.com/en_US/article.HOWTO127961.html](https://support.symantec.com/en_US/article.HOWTO127961.html)
  
Endpoint Protection 14 REST API and PowerShell  
[https://support.symantec.com/en_US/article.HOWTO125873.html](https://support.symantec.com/en_US/article.HOWTO125873.html)
  
There is an online version of the API Docs
  
[https://apidocs.symantec.com/home/saep](https://apidocs.symantec.com/home/saep)

### Documentation
  
Configuring SEP 14 components from Workflow Solution
  
DOC10748 [https://support.symantec.com/en_US/article.DOC10748.html](https://support.symantec.com/en_US/article.DOC10748.html)
  
Symantec IT Management Suite 8.1 RU5 powered by Altiris technology Release Notes
  
[http://www.symantec.com/docs/DOC10712](http://www.symantec.com/docs/DOC10712)
  
**Feature**
  
Workflow support for Symantec Endpoint Protection 14
  
**Description**
  
From this release onwards, Workflow provides limited support for Symantec Endpoint Protection 14 components.
  
For more information refer to the following article: DOC10748
