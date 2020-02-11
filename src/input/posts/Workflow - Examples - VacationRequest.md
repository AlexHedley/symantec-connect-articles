---
title: Workflow - Examples - VacationRequest
tags:
    - Workflow
    - Examples
author: AlexHedley
# description: 
articleId: 3812021
published: 2019-02-14
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-examples-vacationreque?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

## Vacation Request
  
![Workflow](images\Workflow.png) [Workflow - Examples](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=443c6adf-6a56-4c7f-b727-0ddeb8f9e0d9&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Examples\

Description:

> This process enables a user to request time off. The process is intended to work in conjunction with a timeoff/HR-type system to determine whether an employee is eligible for time off, and to decrement that time. The time off request goes to a manager for processing, and upon approval or rejection, notification goes to the requester.

Author mail:

> nancy\_mitchelmore@symantec.com

Process Prefix: "ITSR-"
  
Documentation

| N/A |
| --- |

Business Model
  
![Vacation Request](images\VacationRequest_VacationRequest.model_.png)
  
Primary
  
![Primary](images\VacationRequest_Primary.model_.png)
  
**Dialog Workflow(s)**
  
- Absence Request
- Manager Approval

| **Absence Request**<br>
			<br>This process enables a user to request time off. The process is intended to work in conjunction with a timeoff/HR-type system to determine whether an employee is eligible for time off, and to decrement that time. The time off request goes to a manager for processing, and upon approval or rejection, notification goes to the requester.<br>
			<br>---<br>
			<br>**Customization**<br><ul>				<li>Update the Absence Request Dialog Workflow [1.5] so that the employee's information (name, email, manager, available PTO and so forth) is pulled from an appropriate datasource.&nbsp;</li>				<li>Update Global Settings for the Business Time Span for Holidays and Weekends. &nbsp;The "Days Between" component in the Vacation Request Form uses the global settings (as opposed to the Project settings). &nbsp;Right click on the Task Tray Tool &gt; Shortcuts &gt; Busines Time Span Editor&nbsp;<ul>						<li>Default Values: &nbsp;Weekends = Saturday and Sunday / Holidays = Christmas and New Year's Day</li>					</ul>				</li>				<li>Require login credentials that is authenticated against an appropriate datasource</li>				<li>Configure "elevated approver" so that this information is dynamic instead of static<ul>						<li>Currently, this is a project property</li>					</ul>				</li>				<li>Update how timeouts and escalations are handled with Manager Approval [1.8]</li>				<li>Update the process so that the employee's leave balance is updated after the time has been taken [1.13]<br>					&nbsp;</li>			</ul>
			<br>---<br>
			<br>**Timed-Out Email:** The request was not processed in a timely manner and therefore canceled. The timeout date is either:<br><ul>				<li>The start date of the time-off request plus one day (for requests in the future),&nbsp;</li>				<li>Seven days after the requested end date (for requests in the past, when the end date is later than the date of submittal),&nbsp;</li>				<li>Seven days after the current date (for requests in the past, when the date of submittal is later than the end date of the request).</li>			</ul>
			<br>These values are configured in the Absence Request Dialog Workflow. |
| --- |

**Properties**

| Name | Value |
| --- | --- |
| MailFromAddress | no-reply@symantec.com |
| ElevatedApproverName | HR Approver |
| ElevatedApproverEmail | HRApprover@symantec.com |
| SMTPServer | localhost |
| CriticalErrorContactName | Process Admin |
| CriticalErrorContactInfo | processadmin@symantec.com |

**Global Data**

| Name | Value |
| --- | --- |
| DocumentCategoryID | 1 |

Documented on Connect by:
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)​
