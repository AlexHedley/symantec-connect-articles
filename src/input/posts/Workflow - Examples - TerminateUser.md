---
title: Workflow - Examples - TerminateUser
# tags:
#     - 
author: AlexHedley
# description: 
articleId: 3812011
published: 2019-02-14
---

## Terminate User
  
![Workflow](images\Workflow.png) [Workflow - Examples](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=443c6adf-6a56-4c7f-b727-0ddeb8f9e0d9&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
Description:

> This process starts with a request form that the requester fills in to request an employee's termination. The process then moves forward to get manager's approval. After the manager's approval, the process informs IT, HR, Facilities and Security  to complete the termination process.The manager can deny the request in which case the denial is sent to the requester with the reason of denial.

Author Mail:

> support@symantec.com

Process Prefix: "ITSR-"
  
Documentation

| **Employee Termination Process**  <br>				  <br>				**Introduction**  <br>				  <br>				This document provides an overview of the Employee termination workflow project. Using a workflow to manage the process provides reliability in the authorization, processing, and communication between different departments within your organization.  <br>				  <br>				The roles that are significant to this process are outlined in the process business model and include the following:<br>
			<ul>				<li>Requester&nbsp;</li>				<li>Human Resources&nbsp;</li>				<li>Information Technology&nbsp;</li>				<li>Payroll&nbsp;</li>				<li>Security&nbsp;</li>				<li>Facilities<br>					&nbsp;</li>			</ul>
			<br>This image represents a high-level overview of the process and can also found under the process Business Model when the project is open in Workflow Designer:<br>
			<br>**Prerequisites**<br>
			<br>Before making this workflow project live, understand and configure the following:<br>
			<br>1. From the Properties tab in the project in the Workflow Designer, set the following details:  <br>				   a. Global Email Information  <br>				      i. SMTP Server – The server name or IP address of the outbound mail server  <br>				      ii. EMail From Address – Email address that all system generated emails should be sent from  <br>				   b. Administrative Contact  <br>				      i. Administrator Contact Name – The person or group who should be made aware of any process issues  <br>				      ii. Administrator Contact Info – The preferred method by which the administrator be contacted (used for instructing the user how to contact the system administrator in the event of a process error)  <br>				   c. Task Email Addresses – These are the email addresses to which new hire tasks will be sent when appropriate  <br>				      i. HR Email – Review requests and background findings  <br>				      ii. IT Email – Set up new network accounts and workstations  <br>				      iii. Facilities Email – Grant security access to company properties  <br>				      iv. Security Email – Complete badging and security paperwork  <br>				      v. Payroll Email – Setup employees in the company payroll system  <br>				      vi. HR Manager – Handles escalated HR tasks when necessary  <br>				  <br>				**Process Structure**  <br>				  <br>				Reviewing the process in Workflow Designer you will find that it is composed of several models within the project tree.  These roughly correspond to the various tasks that are required during the termination process.  Each step is customizable to meet the needs of a particular company. |
| --- |

![Workflow Project](images\WorkflowProject.png) Symantec.Workflow.TerminateUser.package
  
First we shall look at the Business Model.
  
![Employee](images\TerminateUser_TerminateEmployee.model_.png)

**Models**
  
Primary
  
![Primary](images\TerminateUser_Primary.model_.png)
  
Linked Models to others.

Facilities Termination Process
  
![Facilities Termination Process](images\TerminateUser_FacilitiesTerminationProcess.model_.png)
  
**Dialog Workflow(s)**
  
- Facilities Action Required For Employee Termination Process

HR Termination Process
  
![HR Termination Process](images\TerminateUser_HRTerminationProcess.model_.png)
  
**Dialog Workflow(s)**

- HR Approval Required
- HR Action Required For Employee Termination Process

IT Termination Process
  
![IT Termination Process](images\TerminateUser_ITTerminationProcess.model_.png)
  
**Dialog Workflow(s)**

- IT Action Required For Employee Termination Process
    - We can use an escalation model here if Risk is not handled in time.

Payroll Termination Process
  
![Payroll Termination Process](images\TerminateUser_PayrollTerminationProcess.model_.png)
  
**Dialog Workflow(s)**

- Payroll Dept. Action Required For Employee Termination Process

Security Termination Process
  
![Security Termination Process](images\TerminateUser_SecurityTerminationProcess.model_.png)
  
**Dialog Workflow(s)**

- Security Dept. Action Required For Employee Termination Process

Terminate User Request
  
![Terminate User Request](images\TerminateUser_TerminateUserRequest.model_.png)
  
**Dialog Workflow(s)**

- Employee Termination Request

Timeout Handling
  
![Timeout Handling](images\TerminateUser_TimeoutHandling.model_.png)
  
**Dialog Workflow(s)**

- Handle Timeouts

**Properties**

| Name | Category | Value |
| --- | --- | --- |
| HREmail | Task Emails | HR@demo.local |
| ITEmail | Task Emails | IT@demo.local |
| FacilitiesEmail | Task Emails | Facilities@demo.local |
| SecurityEmail | Task Emails | Security@demo.local |
| EmailFromAddress | Global Email Settings | no-reply@demo.local |
| SMTPServer | Global Email Settings | localhost |
| PayrollEmail | Task Emails | Payroll@demo.local |
| AdministratorContactName | Administrator | John Doe |
| AdministratorContactInfo | Administrator | Admin@demo.local |
| HRManager | Task Emails | HRManager@demo.local |

**Global Data**
  
N/A

Documented on Connect by:
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)​
