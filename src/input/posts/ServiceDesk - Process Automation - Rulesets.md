---
title: ServiceDesk - Process Automation - Rulesets
tags:
    - ServiceDesk
    - Process Automation
    - Rulesets
author: AlexHedley
# description: 
# articleId: 
published: 2018-05-03
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-process-automation-2?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

Table Of Contents
  
<?# Markdown ?>
<?!^ "./../includes/posts/servicedesk-process-automation.md" /?>
<?#/ Markdown ?>

Admin | Process Automation | [Choose Service] | Service Dashboard
  
![Admin_ProcessAutomation](images\Admin_ProcessAutomation.png)
  
Manage Rulesets
  
![Admin_ProcessAutomation_IM_ManageRulesets](images\Admin_ProcessAutomation_IM_ManageRulesets.png)
  
Actions | Add Rule
  
![Admin_ProcessAutomation_IM_ManageRulesets_Actions](images\Admin_ProcessAutomation_IM_ManageRulesets_Actions.png)
  
**Condition Groups :**  
How groups are evaluated:  o All groups must be met to satisfy o Any group satisfies
  
"Add Group"
  
![Admin_ProcessAutomation_IM_ManageRulesets_AddRule_Group](images\Admin_ProcessAutomation_IM_ManageRulesets_AddRule_Group.png)
  
**Actions:**   
Disposition (on successful actions): o Continue o Stop
  
"Add Action"
  
![Admin_ProcessAutomation_IM_ManageRulesets_AddRule_Action](images\Admin_ProcessAutomation_IM_ManageRulesets_AddRule_Action.png)
   
x Run next rule if any condition evaluation generates an error   
x Run next rule if any action execution generates an error

There are a number of Actions you can take, one example is "Route Incident".
  
This can to be either a "Specific Service Queue" or using a "Routing Table"
  
![](images\article-3733021-files_Admin_ProcessAutomation_IM_ManageRulesets_AddRule_Action_RouteIncident.png)
  
![](images\article-3733021-files_Admin_ProcessAutomation_IM_ManageRulesets_AddRule_Action_RouteIncident_Table.png)

---
  
Each of the Services have their own Ruleses and you can create your own with Custom Rulsets.
  
Each Service is further detailed on their own pages, this will list the Rulesets available to add Rules too.

- [**INCIDENT-MGMT**](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=5af06f41-56eb-47b1-85e7-26b5d69735e4&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [**CHANGE-MGMT**](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9a32b831-e328-40ce-b7fd-fdf0a905da66&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [**PROBLEM-MANAGEMENT**](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=5bb0d000-b426-43ab-87f3-cb683dffce07&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [**SD-SR-DELIVERY**](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3eb14f31-2111-4487-97e4-b65b4a451051&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
- [**SD-SR-APPROVAL**](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0fec5372-69cf-4e83-9906-21c605f4b325&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

If you want to learn more about the new Software Request Process Workflow check out my other Articles

- [ServiceDesk - Software Request Process](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=253f9b2f-045e-4e05-acb9-fcc37005f674&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [ServiceDesk - Software Request Process - Config](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e3acdfdc-8b09-4ca7-afb5-821c9cce9301&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

### Videos
  
[Jason Short](https://www.symantec.com/connect/user/jason-short) created a series of videos on ServiceDesk Configuration if you'd like to learn more.
  
ServiceDesk Configuration: Rulesets Overview  
[https://www.symantec.com/connect/videos/servicedesk-configuration-rulesets-overview](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0f092e8e-700b-410a-bb51-29ece6d88354&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

> This video will provide a good overview of rulesets in ServiceDesk. The video covers the basic components of a rule, as well as, how to configure rules to work together as part of more complex logic.

If you prefer a written Article to a video see the transcription below:

> There are 2 Ruleset Types.
> 
> - Process Events
>     - OnIncidentReceived
> - Data Events
>     - Comment added to ticket
> 
> Each Ruleset has 4 major components.
> 
> - Trigger
>     - Process/Data Events that cause a rule to be ran
> - Evaluation
>     - A rule does an Evaluation of specific data on that ticket
> - Action
>     - It occurs if that Evaluation is met
>         - Sending an email, setting a value on a ticket
> - Continuation Logic
>     - Whether or not to rule the next rule
> 
> Click on **Admin** | **Process Automation**
> 
> Expand **Incident Management** and click on **Service Dashboard**.
> 
> There will be a list of Rulesets, which tell you what Type they are.
> 
> **Process Events** happen at a fixed point in time, OnIncidentReceived or OnTicketAssigned.
> 
> Expand one of these and click on the ![](images\clip_image004.png) Lightning bolt then ![](images\clip_image006.png) **Add Rule**.
> 
> Add Group -&gt; Add Condition -&gt; “Any“ -&gt; +.
> 
> Add Action -&gt; choose Action -&gt; +.
> 
> There are some options in **Advanced** to continue certain rules.
> 
> Then you can **Save**.
> 
> Each rule overwrites data from the previous. Run the general rules first then the more specific so you can use the arrows to move it up the list.

ServiceDesk Customization: Send Incident to Workflow Ruleset Action  
[https://www.symantec.com/connect/videos/servicedesk-customization-send-incident-workflow-ruleset-action](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a968dcd0-80ba-43de-9f57-a2efbfba38b9&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
Extra WF Projects have been created to help with Rulesets
  
ServiceDesk 7.5 Rulesets & E-mail template Import/Export project  
[https://www.symantec.com/connect/videos/servicedesk-75-rulesets-e-mail-template-importexport-project](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d81c13cb-de06-4e21-a6cc-65787564d655&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
  
[![Protirus](images\Protirus.png)](https://protirus.com/)
