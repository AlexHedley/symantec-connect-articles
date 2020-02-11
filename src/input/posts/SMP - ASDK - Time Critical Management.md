---
title: SMP - ASDK - Time Critical Management
tags:
    - SMP
    - ASDK
author: AlexHedley
# description: 
# articleId: 
published: 2018-09-29
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/smp-asdk-time-critical-manageme-1?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

IT Management Suite (ITMS) 8.5 Documentation  
DOC11076  
[https://support.symantec.com/en_US/article.DOC11076.html](https://support.symantec.com/en_US/article.DOC11076.html)

| SMP Version: | 8.5 |
| --- | --- |

Workflow 8.5 Release Notes  
DOC11090  
[http://www.symantec.com/docs/DOC11090](http://www.symantec.com/docs/DOC11090)
  
pg 6 / 13
  
Time Critical Management
  
New Features

| Feature | Description |
| --- | --- |
| Time Critical Management portal | The **Time Critical Management** portal lets you gather inventory on endpoints in real time so that you can perform immediate hardware and software state analysis. You can also perform various actions on endpoints in real time. |

[https://help.symantec.com/cs/itms8.5/WORKSPACES/v128281304_v125848311/About-Time-Critical-Management?locale=EN_US](https://help.symantec.com/cs/itms8.5/WORKSPACES/v128281304_v125848311/About-Time-Critical-Management?locale=EN_US)

> The Time Critical Management workspace lets you gather inventory on endpoints in real time so that you can perform immediate hardware and software state analysis. You can also perform various actions on endpoints in real time.
> 
> To allow receiving the inventory data and running tasks on endpoints in real time, persistent connection is implemented and used for communication between Notification Server and endpoints. Persistent connection also allows real time communication with the endpoints that are outside of the internal corporate network and use Cloud-enabled Management (CEM) to communicate with Notification Server.
> 
> See About the Symantec Management Agent communication using persistent connection
> 
> Depending on the Time Critical Management task, you can perform it either in the Time Critical Management workspace or in the Symantec Management Console.
> Table: Time Critical Management tasks
> 
> | Task | Portal | Description |
> | --- | --- | --- |
> | Verify that the inventory data is up-to-date. | Time Critical Management | On the Time Critical Management page, you can search for data classes for which you want to verify that the data is up-to-date.<br>
> 				<br>If the data is older than you require, you can immediately update it.<br>
> 				<br>See [Verifying that the inventory data is up-to-date](https://help.symantec.com/cs/ITMS8.5/WORKSPACES/v128086707_v125848311/Verifying-that-the-inventory-data-is-up-to-date?locale=EN_US "Verifying that the inventory data is up-to-date") |
> | Run tasks in real time. | Time Critical Management | After you find the data classes that you require, you can then select endpoints on which you want to perform further actions. For example, you can run a specific task on selected systems.<br>
> 				<br>See [Running a task in real time](https://help.symantec.com/cs/ITMS8.5/WORKSPACES/v128086816_v125848311/Running-a-task-in-real-time?locale=EN_US "Running a task in real time")<br>
> 				<br>You can save selected endpoints as a target or a CSV file, or send the results in an email.<br>
> 				<br>See [Create Resource Target dialog box](https://help.symantec.com/cs/ITMS8.5/WORKSPACES/v128086813_v125848311/Create-Resource-Target-dialog-box?locale=EN_US "Create Resource Target dialog box")<br>
> 				<br>See [Specify Email Parameters dialog box](https://help.symantec.com/cs/ITMS8.5/WORKSPACES/v128086819_v125848311/Specify-Email-Parameters-dialog-box?locale=EN_US "Specify Email Parameters dialog box") |
> | Immediately push policies to the endpoints. | Symantec Management Console | You can select any policy and push it immediately to the required endpoints.<br>
> 				<br>Note that the policy is immediately delivered to the endpoints, but it runs according to the specified schedule.<br>
> 				<br>See [Pushing a policy in real time](https://help.symantec.com/cs/ITMS8.5/SMPLAT/v128281310_v125258922/Pushing-a-policy-in-real-time?locale=EN_US "Pushing a policy in real time") |
> 
> 
> 
> To open the Time Critical Management workspace, use the menu in the Symantec Management Console or enter the Symantec Endpoint Management Workspaces URL in the web browser.

This brings the associated ASDK methods:

| Feature | Description |
| --- | --- |
| New features of ASDK. | The following enhancements are introduced in ASDK:<br>
			<br>■ On a server side, ASDK is able to run tasks and policies over the WebSocket protocol. ASDK is extended with methods specific to Time Critical Management:<br>
			<ul>				<li>TaskManagement.ExecuteTCMTask</li>				<li>TaskManagement.GetTCMTaskStatus</li>				<li>TaskManagement.GetTCMTaskResults</li>				<li>TaskManagement.GetTCMTaskResult</li>				<li>ResourceManagementLib.PushPolicy</li>			</ul>
			<br>■ **CreateResourceTarget** method can now create a target in a custom folder if the **parentFolderGuid** element with custom folder's Guid is in target's source XML.<br>
			<br>If the **parentFolderGuid** element is not in source XML, the target is created in the root target folder. |

Lets look at these individually
  
**Task Management**
  
- http://localhost/Altiris/ASDK.Task/TaskManagementService.asmx

There are 4 new methods.
  
## Add Inputs

- ExecuteTCMTask
    - taskGuid
    - executionName
    - inputParameters

Returns

    <ExecuteTCMTaskResult>guid</ExecuteTCMTaskResult>

- GetTCMTaskStatus
    - taskId - Guid

    <GetTCMTaskStatusResult>
      <ID>guid</ID>
      <NotStarted>int</NotStarted>
      <InProgress>int</InProgress>
      <Completed>int</Completed>
      <Total>int</Total>
      <Failed>int</Failed>
      <Succeeded>int</Succeeded>
      <Progress>double</Progress>
    </GetTCMTaskStatusResult>

- GetTCMTaskResults
    - taskId - Guid

This returns an Array of

    <TCMTaskStatusResult>
      <Agent>guid</Agent>
      <Result>None or Started or Failed or Succeeded or Executed</Result>
    </TCMTaskStatusResult>

- GetTCMTaskResult
    - taskId - Guid
    - agent - Guid

This returns

    <GetTCMTaskResultResult>None or Started or Failed or Succeeded or Executed</GetTCMTaskResultResult>

As with most ASDK methods if there is an input of a Guid there is another version created which allows a string instead.

- GetTCMTaskResult2
    - taskId - string
    - agent - string

**Resource Management**

- http://localhost/altiris/askd.ns/ResourceManagementService.asmx

- PushPolicy
    - ploicy - Guid

This returns an Array

    <PushPolicyResult>
      <Agent>guid</Agent>
      <Status>Pushed or NotConnected or EmptyPolicy or ActionFailed</Status>
    </PushPolicyResult>

---
  
There is the associated Console element
  
Login to the SMP
  
Home | Time Critical Management

    http://localhost/altiris/workspaces/timecriticalmanagement

---
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
