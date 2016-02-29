---
title: ServiceDesk - Classification
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-02-29
---

In this Article I'm going to explain a way of getting the Classifications from the Process Manager db for use within your Workflows.

In an Incdient in ServiceDesk you can set classification.
  
These are created and administered at **Admin** | **Data** | **Hierarchy Data Service**
  
- http://localhost/ProcessManager/Hierarchy/HierarchyItemListing.aspx

When they are stored against the ticket they are saved as a "." separated string

- e.g. Hardware.Desktop

These are split and joined within the various Workflows.

I had the need in a WF to check if given string was an available Classification before setting it.
  
I can use the below CTE that takes in a @flag parameter of 'Hardware', being the Second Level item, below 'Incident Management' to check it exists and then show all it's siblings.

    DECLARE @ParentChildLocationRAT UNIQUEIDENTIFIER
    SET @ParentChildLocationRAT = '3B4F3C0E-31DF-4AB3-A05F-C6F0550A9305'; --'Incident Management' FROM [HierarchyCategory]
    DECLARE @flag nvarchar(255) = 'hardware'
    
    BEGIN
    WITH CTE_HierarchyAssociatedPairs
        AS (
            SELECT 
        hi.parentHierarchyItemid,
        name 'name',
        HierarchyItemid,
        0 as Depth,
        name as flag
            FROM [HierarchyItem] hi
            where HierarchyCategoryID = @ParentChildLocationRAT--'3B4F3C0E-31DF-4AB3-A05F-C6F0550A9305'
            
            UNION ALL
            
      SELECT 
       hi1.parentHierarchyItemid,
       hi1.name,
       hi1.HierarchyItemid,
                ha.Depth + 1 AS Depth,
                ha.flag
            FROM [HierarchyItem] hi1
            JOIN CTE_HierarchyAssociatedPairs ha ON hi1.parentHierarchyItemid = ha.HierarchyItemid
            )
        SELECT DISTINCT *
        FROM CTE_HierarchyAssociatedPairs
        WHERE flag = @flag
        ORDER BY Depth
    END

Result

| parentHierarchyItemid | name | HierarchyItemid | Depth | flag |
| --- | --- | --- | --- | --- |
| NULL | Hardware | {Guid} | 0 | Hardware |
| {Guid} | Desktop | {Guid} | 1 | Hardware |
| {Guid} | Drive | {Guid} | 1 | Hardware |
| {Guid} | CPU or Blade | {Guid} | 2 | Hardware |

One use for this is with the Email Monitor.
  
Say you put a Classification in the body of an email and wish to map it to a ticket you could split it, pass the first value to this SP, return the results then filter on the subsequent depth fields to get at least a parital match classification set. This could be if it was incorrect in the email or classifications had been removed from Process Manager.

| Subject | New Incident |
| --- | --- |
| Message | My computer has broken<br>
			<br>Please fix<br>
			<br>{Classification: Hardware.Desktop.Computer}  <br>				{Team: Support} |

So Hardware is found, then Desktop is found but Computer isn't so only the first two are mapped in.

* * *
 
In a previous version of ServiceDesk the Classification was split into separate Fields, this could made it easier for reporting and other requirements.
  
If you have migrated it and it is stored as a "." separated string in the new version and want it back into the separate Fields you could use the following.
  
This does assume there are only **10** levels.
  
(Create by our resident SQL Guru [Kev](https://www-secure.symantec.com/connect/user/kevin-huntley-protirus))
  
You could create a Stored Procedure that gets Incident Details with the Classification split

- sp\_IncidentWithSplitClassification

    WITH e1(n) 
    AS 
    (SELECT 1 UNION ALL SELECT 1 UNION ALLSELECT 1 UNION ALL SELECT 1 UNION ALL SELECT 1 UNION ALL SELECT 1 UNION ALL SELECT 1 UNION ALL SELECT 1 UNION ALL SELECT 1 UNION ALL SELECT 1
    )
    ,e2(n) 
    AS 
    (SELECT 0 UNION ALLSELECT ROW_NUMBER() OVER (ORDER BY (SELECT NULL)) FROM 		(SELECT 1 as 'n'			FROM 				e1 a,				e1 b, 				e1 c)  cj
    )
    ,IMwithSplit AS 
    (SELECT [ProcessId]	  ,[SessionId]	  ,[ReportProcessId]	  ,[CurrentTask]	  ,[IncidentName]	  ,[IncidentDescription]	  ,[IncidentType]	  ,[Classification]	  ,[SubmittedBy]	  ,[AffectedUser]	  ,[Owner]	  ,[TicketStatus]	  ,[CurrentlyAssignedQueueId]	  ,SUBSTRING(Classification,n+1,ISNULL(NULLIF(CHARINDEX('.',classification,N+1),0)-(N+1),8000)) 'csplit'	  ,ROW_NUMBER() OVER (PARTITION BY processid ORDER BY (e.n)) rnoFROM 	ImIncidentTicket itLEFT JOIN 	e2 e	ON e.n <= 1000WHERE 	SUBSTRING(Classification, n, 1) = '.' OR	n = 0
    )SELECT [ProcessId]
        ,[SessionId],ISNULL([1],'') AS  'Classification1',ISNULL([2],'') AS 'Classification2',ISNULL([3],'') AS 'Classification3',ISNULL([4],'') AS 'Classification4',ISNULL([5],'') AS 'Classification5',ISNULL([6],'') AS 'Classification6',ISNULL([7],'') AS 'Classification7',ISNULL([8],'') AS 'Classification8',ISNULL([9],'') AS 'Classification9',ISNULL([10],'') AS 'Classification10'
    FROM IMwithSplit
    PIVOT
    (max(csplit) for rno in ([1],[2],[3],[4],[5],[6],[7],[8],[9],[10])
    ) pvt

Classification = "Software.Altiris.CMDB"
  
Result

| ProcessId | SessionId | Classification1 | Classification2 | Classification3 | Classification4 | Classification5 | Classification6 | Classification7 | Classification8 | Classification9 | Classification10 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| IM-000002 | {Guid} | Software | Altiris | CMDB |  |  |  |  |  |  |  |

* * *
 
<u>Forum</u>
  
**Export the Hierarchy Classifications to a Spreadsheet**
  
[https://www-secure.symantec.com/connect/forums/export-hierarchy-classifications-spreadsheet](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=3f0dcc84-f934-4897-bb3d-e519556c76ad&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=digestviewer#bm3f0dcc84-f934-4897-bb3d-e519556c76ad)
  
Category, Parent, Item

    SELECT 
        p.Name AS Category, 
        i.Name AS Parent, 
        o.Name AS Item
    FROM 
        [HierarchyCategory] AS p 
        INNER JOIN [HierarchyItem] AS i ON p.HierarchyCategoryID = i.HierarchyCategoryID 
        LEFT OUTER JOIN [HierarchyItem] AS o ON i.HierarchyItemID = o.ParentHierarchyItemID
    ORDER BY 
        Category, Parent

* * *
 
Get a Simple List

    SELECT 
        i.name as Parent, 
        o.name as Item
    FROM 
        [HierarchyItem] o
        INNER JOIN [HierarchyItem] i ON i.HierarchyItemID = o.ParentHierarchyItemID

* * *
 
**Email Routing and Classification**
  
[https://www-secure.symantec.com/connect/forums/email-routing-and-classification](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=6b9410ea-ec8a-4ea4-8d97-c182de0ce82d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=digestviewer#bm6b9410ea-ec8a-4ea4-8d97-c182de0ce82d)

* * *

[![Protirus.png](images\Protirus.png)](https://www.protirus.com/)
