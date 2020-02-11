---
title: ServiceDesk - WebPart - Assignments and Audit Info
tags:
    - ServiceDesk
    - WebPart
author: AlexHedley
# description: 
# articleId: 
published: 2017-06-05
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-webpart-assignments?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

| Version | SD 7.6 |
| --- | --- |

This download (Protirus.ServiceDesk.WebParts.dll) is a couple of custom Web Parts to show 'ServiceDesk Assignments' and the 'Auditing Incident Owner and Service Queue Changes'.
  
![WebParts - SD Assignments and Queue Info (1)](images\WebParts-SAssignmentsandQueueInfo1.png)
  
If you haven't see the following Article/Video I would advise doing so first.
  
**ServiceDesk 7.5 Track Assignments via Process Type Actions**  
[https://www-secure.symantec.com/connect/articles/servicedesk-75-track-assignments-process-type-actions](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=b4d5684c-792b-4428-9988-3a8dcb568102&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
  
**Send Incident to Workflow - Auditing Incident Owner and Service Queue Changes**  
[https://www-secure.symantec.com/connect/videos/send-incident-workflow-auditing-incident-owner-and-service-queue-changes](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=68be6670-379e-4fcb-bb87-e78145c07e1e&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
  
The idea is to save having to add Process Type Actions and an extra page to open and view, you can have all the information at your disposal on the Process View Page.
  
The Track Assignments you can use with only adding the below Stored Procedure to your DB but for the Auditing you will need to follow the video to add in the necessary tables via the Web App project.

As you can see in the Track Assignments article there is text file "track_all_assignments.txt" which we need to convert to a Stored Procedure, just add in the SessionID parameter and save as "sp_SD_TrackAssignments" (see attached) **[sp\_SD\_TrackAssignments]**.
  
Next we want a couple of SPs for the Audit info:
  
**[sp\_SD\_AuditProcessInfo]**

    SELECT [audit_process_info_id],[incident_session_id],[assigned_to_queue_name],[assigned_on_date],CASE 	WHEN [assigned_away_date] = '1753-01-01 00:00:00.000'		THEN			NULL		ELSE			[assigned_away_date]END 	AS [assigned_away_date],CASE 	WHEN [assigned_away_date] = '1753-01-01 00:00:00.000'		THEN			NULL 		ELSE			DATEDIFF(mi, [assigned_on_date], [assigned_away_date]) END 	AS [time_in_queue],[current_assignment]
    FROM [audit_process_info]
    WHERE [incident_session_id] = @sessionid
    ORDER BY[assigned_on_date] DESC

**[sp\_SD\_OwnerAuditInfo]**

    SELECT [owner_audit_info_id],[is_current_owner],[owner_email],[ownership_taken_on],CASE 	WHEN [ownership_relinquished] = '1753-01-01 00:00:00.000'		THEN			NULL		ELSE			[ownership_relinquished]END 	AS [ownership_relinquished],CASE 	WHEN [ownership_relinquished] = '1753-01-01 00:00:00.000'		THEN			NULL 		ELSE			DATEDIFF(mi, [ownership_taken_on], [ownership_relinquished]) END 	AS [ownership_time],[incident_session_id]
    FROM [owner_audit_info]
    WHERE[incident_session_id] = @sessionid
    ORDER BY[ownership_taken_on] DESC

Just update the first line to match the name of your Process Manager Instance and rename from ".txt" to ".sql" and run in your SSMS.

    USE [ProcessManager]

Now we need to upload the WebPart
  
Login to Process Manager
  
Admin -&gt; Portal -&gt; Plugin Upload
  
Choose **WebPart** from the "Plugin Type" and browse for the dll then click Upload.
  
This can take some time.
  
It will be saved to "[workflow dir]:\\ProcessManager\bin"
  
You may need an IIS Reset or WF Services restart.
  
Go to Admin -&gt; Portal -&gt; Web Parts Catalog
  
Click on the ![document_add](images\document_add.png) button and then give it a new Category name and search for each and add individually
  
- SDIncidentServiceQueueHistory
- SDTrackAssignmentsWebPart

Now these are available to add to the Process View Page.
  
Go to the Page in Admin -&gt; Portal -&gt; Manage Pages
  
Find your page and "Go To Page"
  
Site Actions | ModifyPage
  
Site Actions | Edit Page
  
Site Actions | Add Web Part
  
Now add the new web parts from the new Category you created and give them titles.

Here are a couple of examples depending on the state of the ticket:
  
![WebParts - SD Assignments and Queue Info](images\WebParts-SDAssignmentsandQueueInfo.png)

Old Links
  
**How to add a custom web part to a ServiceDesk/Workflow page in ServiceDesk/ Workflow 7.1 SP2 ?**
  
[https://support.symantec.com/en_US/article.TECH192190.html](https://support.symantec.com/en_US/article.TECH192190.html)
  
**Custom Data Types, Incident Forms, and the Process View Page – Putting them All Together**
  
[https://www-secure.symantec.com/connect/articles/custom-data-types-incident-forms-and-process-view-page-putting-them-all-together](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=886d8038-ffc4-4f70-88ec-f37cbe4a075e&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
