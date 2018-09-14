---
title: ServiceDesk - Process Automation - Data Mapping
# tags:
#     - 
author: AlexHedley
# description: 
articleId: 3733071
published: 2018-05-03
---

Table Of Contents
  
- [Rulesets](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=38d43279-4c4d-41ba-a244-3d84b5d17f65&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Email Templates](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63623bbd-e8f1-4a12-8c2e-269238849335&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SLA Levels](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4b11433a-3c97-4f48-83bd-a67cf42a8b71&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SLA Escalations](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9593bfc5-f0ef-46ad-ba20-a877883d1949&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SLA Milestones](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3d6b7698-88d4-4c35-af34-04b6c13251e1&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Data Mapping](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e0436f19-3519-4dea-9ca9-3dc4c73e7003&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

Admin | Process Automation | [Choose Service] | Service Dashboard
  
Manage Data Mapping
  
![Admin_ProcessAutomation_IM_ManageDataMapping](images\Admin_ProcessAutomation_IM_ManageDataMapping.png)
  
Some Data Mapping is already configured in the base install, you can amend to your own requirements and add your own.

| Name |
| --- |
| Change Impact/Urgency Matrix |
| Incident Impact/Urgency Matrix |
| Problem Impact/Urgency Matrix |
| Routing Table: Classification |
| Routing Table: Location |

You can add/amend these via the Action
  
![Admin_ProcessAutomation_IM_ManageDataMapping_Actions](images\Admin_ProcessAutomation_IM_ManageDataMapping_Actions.png)
  
Then Edit/Remove and Add Mapping Values.
  
You can also update the Mapping Name.
  
![Admin_ProcessAutomation_IM_ManageDataMapping_IU](images\Admin_ProcessAutomation_IM_ManageDataMapping_IU.png)
  
This can be any two Keys and a Value.

| Key1 | Key2 | Value |
| --- | --- | --- |
| Single User | Non-Urgent Service | Low |
| Small Group or VIP | Non-Urgent Service | Low |
| ... |  |  |

### Videos
  
ServiceDesk Configuration: Data Mapping and Routing Rules  
[https://www.symantec.com/connect/videos/servicedesk-configuration-data-mapping-and-routing-rules](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=859d2fe0-3614-4ef9-9e55-7689d2171ac2&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

> This video will cover how to setup data mapping in ServiceDesk and utilize those mapping tables as part of Routing Rule sets.

If you prefer a written Article to a video see the transcription below:

> If we check "INCIDENT-MGMT"
> 
> 
> For the Data Mapping there will be 3 Tables.
> 
> - Impact/Urgency Matrix
> - Routing Table: Classification
> - Routing Table: Location
> 
> 
> 
> Start with the **Impact/Urgency Matrix** and click on the ![](images\clip_image001.png)Lightning bolt then ![](images\clip_image002.png) **Edit Data Mapping**.
> 
> 
> There are two Keys 1 is for Urgency and 2 is for Impact then a value. There are default ones set up from install.
> 
> 
> 
> | Key1 | Urgency |
> | --- | --- |
> | Key2 | Impact |
> 
> 
> 
> Example
> 
> 
> 
> | Key1 | Key2 | Value |
> | --- | --- | --- |
> | Non-Urgent Service | Single User | Low |
> | Support Service | Small Group or VIP | Normal |
> | Core Business Service | Department/LOB/Branch | Emergency |
> 
> 
> 
> You can amend these to how your Company works.
> 
> 
> This will then be available to you in the Incident
> 
> 
> The next one is **Classification** which is empty by default.
> 
> 
> **Key1** is the Category.
> 
> 
> Hardware.Mobile
> 
> 
> These are split by a “.”
> 
> 
> It covers all sublevels if you don’t specify one.
> 
> 
> So “Hardware.Mobile.iPhone” and “Hardware.Mobile.Andriod” would be covered by “Hardware.Mobile”.
> 
> 
> The **Value** is the name of the Queue, choose one then **Save** and **Close** this.
> 
> 
> 
> | Key1 | Hardware.Mobile |
> | --- | --- |
> | Value | Mobile Queue |
> 
> 
> 
> We can now use this in a [Ruleset](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=38d43279-4c4d-41ba-a244-3d84b5d17f65&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments).
> 
> 
> Back on the left hand side click **Manage Rulesets**.
> 
> 
> We want to expand the Ruleset: OnIncidentReceived
> 
> 
> Click on the ![](images\clip_image001.png) Lightning bolt and then ![](images\clip_image003.png) **Add Rule**.
> 
> 
> Now click **Add Group** -&gt; **Add Condition**, From the dropdown choose “Classification” and “Is Set” then click on +.
> 
> 
> Now in the **Actions** section we want to add an action of “Route Incoming Incident” -&gt; “Using Category Routing Table” -&gt; “Routing Table: Classification” +.
> 
> 
> Finally click **Save**.

[![Protirus.png](images\Protirus.png)](https://protirus.com/)