---
title: ServiceDesk - Process Automation - SLA Milestones
tags:
    - ServiceDesk
    - Process Automation
    - SLA Milestones
author: AlexHedley
# description: 
# articleId: 
published: 2018-05-03
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-process-automation?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

Table Of Contents
  
<?# Markdown ?>
<?!^ "./../includes/posts/servicedesk-process-automation.md" /?>
<?#/ Markdown ?>

Admin | Process Automation | [Choose Service] | Service Dashboard
  
Manage SLA Milestones
  
![Admin_ProcessAutomation_IM_ManageSLAMilestones](images\Admin_ProcessAutomation_IM_ManageSLAMilestones.png)
  
Examples

| Name | Service ID |
| --- | --- |
| Resolution | INCIDENT-MGMT |
| Initial Response | INCIDENT-MGMT |

You can edit these
  
![Admin_ProcessAutomation_IM_ManageSLAMilestones_Edit](images\Admin_ProcessAutomation_IM_ManageSLAMilestones_Edit.png)

These are then used in the [SLA Levels](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4b11433a-3c97-4f48-83bd-a67cf42a8b71&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments). Each one has a Milestone value.

### Videos
  
ServiceDesk Configuration: SLA Framework Overview  
[https://www.symantec.com/connect/videos/servicedesk-configuration-sla-framework-overview](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=aa240cc3-3892-4490-b027-a91bd906786b&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

> This video provides an overview and demonstration of using the SLA framework in ServiceDesk 7.5.  The video will cover creating business hours, creating SLAs, applying SLAs based on rulesets, and taking action when an SLA is missed.

If you prefer a written Article to a video see the transcription below:

> There are 3 Principle Components
> 
> - Set Business Hours Configuration
> - Create SLAs
> - Rulesets for SLA
> 
> 
> 
> We need to set the Business Hours in ![](images\clip_image001.png) Process Manager.
> 
> 
> Go to **Admin** | **Data** | **Business Hours**
> 
> 
> There will be a **Business Hours Configuration** grouping with a **Default Business Hours** item. If you click on ![](images\clip_image001.png) then ![](images\clip_image003.png) **Edit** you can then set the Begin and End times as well as which days are the weekend.
> 
> 
> To add more click +
> 
> 
> 
> | Name: | Extended Hours |
> | --- | --- |
> | Begin Business Hours | 7:00 AM |
> | End Business Hours | 7:00 PM |
> | Holidays |  |
> | Date: | Description: |
> | Weekends | |  | Monday |  | Friday |<br>| --- | --- | --- | --- |<br>|  | Tuesday |  | Saturday |<br>|  | Wednesday | **X** | Sunday |<br>|  | Thursday |  |  | |
> 
> 
> 
> 
> 
> 
> 
> | Name: | 24x7 |
> | --- | --- |
> | Begin Business Hours | 12:00 AM |
> | End Business Hours | 11:59 PM |
> | Holidays |  |
> | Date: | Description: |
> | Weekends | |  | Monday |  | Friday |<br>| --- | --- | --- | --- |<br>|  | Tuesday |  | Saturday |<br>|  | Wednesday |  | Sunday |<br>|  | Thursday |  |  | |
> 
> 
> 
> 
> 
> 
> Now we can create some SLAs which we can assign these Hours too.
> 
> 
> Click on **Admin** | **Process Automation**  
> 	Expand **Incident Management** and click on **Service Dashboard**.
> 
> 
> There are a few options on the left hand side for SLAs.
> 
> - Manage SLA Levels
> - Manage SLA Escalations
> - Manage SLA Milestones
> 
> 
> 
> There are 2 Milestones
> 
> - Resolution
> - Initial Response
> 
> 
> 
> SLA Levels
> 
> 
> Click on Manage SLA Levels on the left hand side.
> 
> 
> We want to create a new one so click on **Add SLA Level**.
> 
> 
> Set some values.
> 
> 
> 
> | Service ID: | INCIDENT-MGMT |
> | --- | --- |
> | Level: | VIP |
> | Description: | This is for VIPs |
> | Milestone: | Initial Response |
> | Escalation: | Late |
> | Late Date: | Days: 0 Minutes: 30 |
> | Use Business Hours | **X** |
> | Business Hours: | Extended Hours |
> 
> 
> 
> Once you press **Save** this will show in the original list.
> 
> 
> Now we can use this in a Ruleset so click on **Manage Rulesets** on the left hand side.
> 
> 
> Expand OnIncidentReceived.
> 
> 
> Click on the ![](images\clip_image001.png)Lightning bolt then ![](images\clip_image002.png)**Add Rule**.
> 
> 
> Now we can add a **Group** and **Condition**.
> 
> 
> 
> | Affected User | Is VIP |
> | --- | --- |
> 
> 
> 
> Next is our **Action**.
> 
> 
> 
> | Set SLA | For Configuration Level | Initial Response - Late (VIP) |
> | --- | --- | --- |
> 
> 
> 
> Parameters
> 
> 
> 
> | Replace Existing SLAs: | X |
> | --- | --- |
> | User Date: | UseProcessStartDate |
> 
> 
> 
> We will now see the Rule in the list.

[![Protirus.png](images\Protirus.png)](https://protirus.com/)
