---
title: SMP - ASDK - 8.5 RU3
# tags:
#     - 
author: AlexHedley
# description: 
published: 2019-10-23
---

With the release of ITMS 8.5 RU3 there were some new Web Service methods added to the following:

| Feature | Description |
| --- | --- |
| Enhancements of the Symantec Administrator Software Development Kit (ASDK) application programming interface (API). | The Symantec ASDK provides APIs that you can use to automate and customize the Symantec Management Platform. You can call APIs through Web services, COM, and the Windows command line (CLI). In 8.5 RU3, the following new API methods for interfacing with Task Management are introduced:<br>
			<br>■ CreateClientJob  <br>				■ CreateServerJob  <br>				■ AddTaskFirstToJob  <br>				■ AddTaskLastToJob  <br>				■ CreateJobCondition  <br>				■ AddJobConditionRules  <br>				■ AddTaskToJobConditionThenGroup  <br>				■ AddTaskToJobConditionElseGroup  <br>				■ RemoveJobCondition  <br>				■ RemoveNodeFromJob  <br>				■ RemoveAllNodesFromJob  <br>				■ ConfirmJobChanges<br>
			<br>For more information, see the Symantec ASDK Help at<br>
			<br><br>    C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Symantec\ASDK |
| Enhancements of Patch Management Workflow Web Service application programming interface (API). | Patch Management Workflow Web Service is installed with Patch Management Solution. The service contains API that accesses the functionality of Notification Server (NS) and lets you perform various patch management actions.<br>
			<br>You can access the service at<br>
			<br><br>    http://localhost/Altiris/patchmanagementcore/patchworkflowsvc.asmx<br><br>
			<br>In 8.5 RU3, the following enhancements are introduced:<br>
			<br>■ HTML Help page The page includes list of available methods, detailed method descriptions, and usage examples for some methods. You can access the page at<br>
			<br><br>    http://localhost/Altiris/patchmanagementcore/patchworkflowsvc.html<br><br>
			<br>■ New API methods:<br>
			<br>- CreateWindowsUpdateAssessmentTask  <br>				- CreateWindowsUpdateInstallationTask  <br>				- EditWindowsUpdateAssessmentTask  <br>				- EditWindowsUpdateInstallationTask<br>
			<br>For more information, see the knowledge base article [DOC11543](https://support.symantec.com/us/en/article.doc11543.html). |

### Task Management Service
  
- CreateClientJob
- CreateServerJob
- AddTaskFirstToJob
- AddTaskLastToJob
- CreateJobCondition
- AddJobConditionRules
- AddTaskToJobConditionThenGroup
- AddTaskToJobConditionElseGroup
- RemoveJobCondition
- RemoveNodeFromJob
- RemoveAllNodesFromJob
- ConfirmJobChanges

### Patch Management Service

- CreateWindowsUpdateAssessmentTask
- CreateWindowsUpdateInstallationTask
- EditWindowsUpdateAssessmentTask
- EditWindowsUpdateInstallationTask

You may want to update the Zero Day Patch ![Workflow](images\Workflow_0.png) Workflow to leverage these new methods:

Workflow Template - Zero Day Patch  
https://www.symantec.com/connect/videos/workflow-template-zero-day-patch

---

To keep track of updates you can compare Web Service Methods using a tool I've written

- [https://protirus.github.io/SMPWebServiceDiff/](https://protirus.github.io/SMPWebServiceDiff/)

---

### Documentation

Symantec™ IT Management Suite 8.5 RU3 Release Notes  
[https://support.symantec.com/us/en/article.doc11603.html](https://support.symantec.com/us/en/article.doc11603.html)  
doc11603
