---
title: ServiceDesk - Process Automation - Email Templates
tags:
    - ServiceDesk
    - Process Automation
author: AlexHedley
# description: 
# articleId: 
published: 2018-05-03
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-process-automation-1?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

Table Of Contents
  
- [Rulesets](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=38d43279-4c4d-41ba-a244-3d84b5d17f65&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Email Templates](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63623bbd-e8f1-4a12-8c2e-269238849335&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SLA Levels](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4b11433a-3c97-4f48-83bd-a67cf42a8b71&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SLA Escalations](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9593bfc5-f0ef-46ad-ba20-a877883d1949&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SLA Milestones](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3d6b7698-88d4-4c35-af34-04b6c13251e1&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Data Mapping](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e0436f19-3519-4dea-9ca9-3dc4c73e7003&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

Admin | Process Automation | [Choose Service] | Service Dashboard
  
Manage Email Templates
  
![Admin_ProcessAutomation_IM_ManageEmailTemplates](images\Admin_ProcessAutomation_IM_ManageEmailTemplates.png)
  
There will be a list of available Templates

| Name | Event Type | Description |
| --- | --- | --- |
| My Cool Template | None | Sent to everyone |

Click on "Add Email Template" at the bottom of the page to create a new one.
  
Or the "Action" button against each item then "Edit Email Template"
  
![Admin_ProcessAutomation_IM_ManageEmailTemplates_Actions](images\Admin_ProcessAutomation_IM_ManageEmailTemplates_Actions.png)
  
![Admin_ProcessAutomation_IM_ManageEmailTemplates_EditEmailTemplate](images\Admin_ProcessAutomation_IM_ManageEmailTemplates_EditEmailTemplate.png)

We now have a number of options to complete.
  
**Template Type** (Determines which Ruleset can use the Template)

- Process Event
- Data Event

There are a number properties you configure

| Name |  |
| --- | --- |
| Description |  |
| From |  |
| Subject |  |
| Body |  |

There is a list of "Available Fields" which can be added to various parts of the Email Template.
  
**Add To**

- From
- Subject
- Body

This is in the format of

    ${FIELDNAME}

So the Field name - example:

    ${AffectedDepartment}

This allows for values from the Incident to be added to the template dynamically based on the content there.
  
---
  
### Videos
  
ServiceDesk Configuration: Manage Email Templates in ServiceDesk  
[https://www.symantec.com/connect/videos/servicedesk-configuration-manage-email-templates-servicedesk](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=832251bc-f042-43ce-9135-3d0d72c1c13e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

> This video walks though managing email templates in ServiceDesk, as well as, creating rules to automatically send those templates based on process or data events.

If you prefer a written Article to a video see the transcription below:

> We can create Email Templates for both Process and Data events. We can then set up Rules Sets to send those emails based on events within the ticket life cycle.
> 
> Click on **Admin** | **Process Automation**
> 
> Expand **Incident Management** and click on **Service Dashboard**.
> 
> There is then a Menu Item for **Manage Email Templates** on the left hand side.
> 
> There are none by Default so click on **Add Email Template**.
> 
> You then need to pick a Template Type: ¤ Process Event or ¤ Data Event.
> 
> Process is generic and will allow any process to send it but Data is specific so the chosen Event is only allowed to send this.
> 
> As an Example choose Process Event, give it a *Name*, a *Description* then a *Subject*.
> 
> You can add Fields to the Email but you have to choose it in the Add To: section before selecting the Field. $(FieldName).
> 
> If we were to do a Data Event using “SLAMissed”
> 
> We can use these Templates in Rules so click on **Manage Rulesets** on the left hand side.
> 
> Expand OnIncidentReceived and click ![](images\clip_image001.png) ![](images\clip_image003.png) **Add Rule**.
> 
> Add Group " Add Condition -&gt; “Any” -&gt; +.
> 
> Add Action -&gt; “Send Email” -&gt; “To Affected User”
> 
> Parameters Template -&gt; “CreateIncidentConfirmation” (created above) -&gt; +.
> 
> Save
> 
> Expand SLAMissed and ![](images\clip_image001.png)  ![](images\clip_image003.png) **Add Rule**.
> 
> Add Group -&gt; Add Condition -&gt; “Any” -&gt; +.
> 
> Add Action -&gt; “Send Email” -&gt; “To All Assignees”
> 
> Parameters Template -&gt; “MissedSLA” -&gt; +.
> 
> Save

[![Protirus](images\Protirus.png)](https://protirus.com/)
