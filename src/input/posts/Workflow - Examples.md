---
title: Workflow - Examples
tags:
    - Workflow
    - Examples
author: AlexHedley
# description: 
articleId: 3811961
published: 2019-02-14
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-examples?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

![](images\Workflow.png) Workflow comes with a set of Examples to get to grips with how to work with the Designer and allow you to run those common scenarios in your company.
  
Go to the following folder on your WF box.

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Examples\

There are 6 ![WorkflowProject](images\WorkflowProject.png) Workflows and 2 ![Int](images\Int.png) Integration Projects.
  
- [New Hire](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f83b1618-369f-46c5-aed4-459335fab063&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - NewHireLib
- [Request Access To Network Share](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=10c3f25a-4786-43b0-92d8-d7342449ec17&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Request Cell Phone](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0690277d-d0b8-410c-a2b3-0589b79bc3a6&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - CellPhoneRequestUserCustomLib
- [Reset Password](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=31380f2a-2e42-4725-938e-0942188f0c08&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Terminate User](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=67b40128-8bf8-4cfd-8662-e26cb4e315fc&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Vacation Request](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=212baef3-189d-4030-8fdd-b2534c9b6a67&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

See the summaries below then click on the individual links for more info about the Projects.

- NewHireLib.package
- Symantec.Workflow.New Hire.package

> Use this form to process a new hire.

- Symantec.Workflow.RequestAccessToNetworkShare.package

> This process will enable the user to request access/permissions to a shared drive. The requester can request for himself/herself or someone else. By default, the request is initially sent to the Share Manager for approval. (However, the recipient's manager can receive an approval step first; this step is disabled out of the box.) On approval from the Share Manager, the recipient is granted access to the shared folder. The Share Manager can also add the user to a group that has permission on that folder. If this is decided, the group manager receives an approval task for the request. If a group does not have a manager, as set in AD, the Service Managers group receives the task and can either add the user to the group, select a different group, or asisgn a manager to the group. If a new manager is assigned, that manager receives the original task to approve the addition of the new user; all subsequent tasks for this group will be handled by the new manager.

- CellPhoneRequestUserCustomLib.package
- Symantec.Workflow.RequestCellPhone.package

> Use this process to request a new cell phone, or a replacement cell phone for one that was lost, broken, or stolen. The process begins with submission of the request, followed by manager approval (unless the requestor is the recipient's manager), and processing by Purchasing. If a phone is broken, an additional screen provides information on what to do with the broken phone. If a phone is lost or stolen, an additional screen captures information on the event and the process forwards that information automatically to Security. New employees receiving a phone must agree to a liability/terms of usage agreement.

- Symantec.Workflow.ResetPassword.package

> Allows you to reset a password automatically in Active Directory.   
> 	• Enables a manager to reset the Active Directory password for an employee. Also enables a user to request a password reset for another user, with manager approval required.   
> 	• Initiated by browsing to a Password Reset Request form

- Symantec.Workflow.TerminateUser.package

> This process starts with a request form that the requester fills in to request an employee's termination. The process then moves forward to get manager's approval. After the manager's approval, the process informs IT, HR, Facilities and Security  to complete the termination process.The manager can deny the request in which case the denial is sent to the requester with the reason of denial.

- Symantec.Workflow.VacationRequest.package

> This process enables a user to request time off. The process is intended to work in conjunction with a timeoff/HR-type system to determine whether an employee is eligible for time off, and to decrement that time. The time off request goes to a manager for processing, and upon approval or rejection, notification goes to the requester.

Documented on Connect by:
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)​
