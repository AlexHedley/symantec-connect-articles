---
title: ServiceDesk - Software Request Process - Overview
tags:
    - ServiceDesk
    - Software Request Process
author: AlexHedley
# description: 
# articleId: 
published: 2017-10-10
# symantecUrl:
broadcomUrl: 
---

In this Article I'm going to explain how the new **Software Request Process** works in [ServiceDesk](https://www.symantec.com/products/service-desk) 8.1.

Table Of Contents
  
- [Index](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=253f9b2f-045e-4e05-acb9-fcc37005f674&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Overview](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a5fdba6d-707b-44be-a051-b08e5a5cfe19&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Config](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e3acdfdc-8b09-4ca7-afb5-821c9cce9301&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SMP](https://www.symantec.com/connect/articles/servicedesk-software-request-process-smp)
- [Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=24530d5f-01a3-464d-846b-01482ee0c85e&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Hidden Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f39346c9-799f-4d1b-ba9b-7f0910cd9c74&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=28879800-dd5e-436b-8f8b-9bc7301fbb1e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [WFs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=736fee28-7f45-497e-b208-b3de50cde839&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [DLLs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f4cef159-76c3-4b5b-9287-94aee6bec214&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

This comes in the base install of SD 8.1 and can be viewed by going to the the '**Submit Request**' page, under '**IT Services**' then '**Software Request**'.

You have to have AMS, CMS and Software Management Framework installed on the SMP. You have to define proper software products that are managed, deliverable and licensed

1. product has a software release component.
2. product has a software license associated. Delivery will be blocked by the workflow if a license is not available
3. the release component is installable via a file and has a managed delivery policy.
4. The policy is setup based on a target with a filter. delivery works by putting the device into the target's filter (inclusion list)

Firstly you need to configure a Managable and Deliverable piece of Software in your SMP.

| This will be an upcoming article [[SMP](https://www.symantec.com/connect/articles/servicedesk-software-request-process-smp)] from [@SamPace](https://www.symantec.com/connect/user/sam-pace) |
| --- |

Login.
  
Manage | Software
  
Deliverable Software - Software Releases
  
You need to set up a Managed Delivery Policy which has a Target and corresponding Filter so an Asset can be added and have the software pushed.
  
Make sure to set Ownership of an Asset to the User you wish to test with.

Login to your Process Manager
  
Submit Request
  
Click on 'IT Services'
  
Then 'Request Software'
  
![ProcessManager SubmitRequest ITServices](images\ProcessManager_SubmitRequest_ITServices.png)
  
The logged in User has to be known by both the SMP and PM with the same Email address.
  
This will show a list of Owned Assets, choose one from the dropdown (Target Devices)
  
Enter a phonenumber.
  
![SoftwareRequest Submission Step1](images\SoftwareRequest_Submission_Step1.png)
  
Choose a piece of Software
  
![SoftwareRequest Submission Step2](images\SoftwareRequest_Submission_Step2.png)
  
You can request a piece of Software that isn't in the Catalog, this will create a Task for SAM team to complete.
  
Next give a Justification
  
![SoftwareRequest Submission Step3](images\SoftwareRequest_Submission_Step3.png)

Review
  
![SoftwareRequest Submission Step4](images\SoftwareRequest_Submission_Step4.png)
  
Confirm
  
You will then get a Ticket Number (SR-#)
  
![SD-00001](images\SD-00001.png)

Approvals
  
The Request will go into a Queue to be actioned.
  
1st Tier Approver - "Software Asset Managers"
  
[IMAGE] - Request PVP

The default logic is to go to the Requestor's Manager, if there isn't one fallback to the SAM.
  
This can be configured in the Rule Engine to any Group or any User.

Now action the Ticket using the Process Actions.
  
Click Approve.
  
![Approve Deny](images\ApproveDeny.png)

This is pased to the Workflow Repsonse Queue to move to the next stage and create a Software Delivery Ticket (SDT)
  
Refresh the page after a few seconds.
  
Fulfilment phase

Expand Related Processes and open this new Ticket.
  
This is again assigned to the Software Asset Managers (SAM) Group.
  
Here you can Authorize Delivery using another Action as all the configuration has already been set up and has allowed the process to get to the Task: Delivery Authorization (80%).
  
Click on the Task
  
This shows the Licensing information and options to see it in the SMP via a link.
  
![Delivery Authorisation](images\DeliveryAuthorisation.png)

Here you can check and select the Release, Delivery Policy and Filter.

| Only support Filter based Targets. |
| --- |

Click Authorize.
  
Check the SMP Filter to confirm it has been added.
  
[IMAGE]
  
The Request then returns to the Requestor to confirm the Software has been delivered.
  
Custom Notifications at each step can be configured and sent to relevant parties.
  
The User has an option to confirm/deny delivery.
  
![Delivery Confirmation](images\DeliveryConfirmation.png)

A remediation task is created if the user states there has been a problem.
  
This task will loop back once an Analyst has checked, the user can then confirm again, this has a couple of days timeout.

---
  
Documentation
  
Symantec ServiceDesk 8.1 Documentation
  
[https://www.symantec.com/connect/forums/symantec-servicedesk-81-documentation](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=cfc7ef69-2520-4a10-9344-7a5de64ee9f8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=digestviewer#bmcfc7ef69-2520-4a10-9344-7a5de64ee9f8)

- Release Notes - [http://www.symantec.com/docs/DOC9618](http://www.symantec.com/docs/DOC9618)

| Feature | Description |
| --- | --- |
| Added Software request process | From this release onwards, you can create Software delivery requests, manage these requests and deliver software to the client computers using computer filters. |

[![Protirus](images\Protirus.png)](https://protirus.com/)
