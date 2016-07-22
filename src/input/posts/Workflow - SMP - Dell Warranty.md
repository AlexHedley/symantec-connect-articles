---
title: Workflow - SMP - Dell Warranty
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-07-22
---

In this Article I'm going to explain how to use the new DELL API to get Warranty information and add it to your Assets in the SMP.
  
![Dell (S)](images\DellS.png)
  
First you will need to sign up to get access to the DELL API
  
[http://en.community.dell.com/dell-groups/supportapisgroup/](http://en.community.dell.com/dell-groups/supportapisgroup/)
  
There’s a powerpoint in the '[get started](http://en.community.dell.com/dell-groups/supportapisgroup/m/mediagallery/20428185/download.aspx)' section with an excel sheet embedded, that you will need to fill out to request API access.
  
Complete that, send it off then wait to hear back with your API Key.
  
Once you have that check out the DELL API page:
  
- [https://developer.dell.com/api](https://developer.dell.com/api)

Now for the config.
  
Create a new ![Data Classes](images\DataClasses.png) Data Class in the ![smp](images\smp.png) SMP to store the information retrieved from the API.
  
![Reports Folder](images\ReportsFolder) Settings | ![Folder](images\Folder.png) Notification Server | ![Folder](images\Folder.png) Resource and Data Class Settings | ![Folder](images\Folder.png) Data Classes | ![Folder](images\Folder.png) _Protirus |
  
![Data Classes](images\DataClasses.png) Simple Warranty

| Simple Warranty | String | Text to describe how this detail was achieved. e.g. Dell Warranty Import Workflow |
| --- | --- | --- |
| Warranty Until | Date |  |
| LastCheckedDate | Date |  |

Then you need to link it to a Computer/Asset Resource via settings.
  
![Reports Folder](images\ReportsFolder.png) Settings | ![Folder](images\Folder.png) Notification Server | ![Folder](images\Folder.png) Resource and Data Class Settings | ![Folder](images\Folder.png) Resource Types | ![Folder](images\Folder.png) Asset Types | ![Folder](images\Folder.png) Generic Asset Types
  
![Resource](images\Resource.png) Asset
  
Scroll down to Data Classes, click "Add data classes" and search for the new one.
  
![Asset Resource](images\AssetResource.png)
  
You might only want to store this information on a particular type of Resource so this can be modified, if necessary.

![Workflow](images\Workflow.png) Workflow
  
You'll need 7.6+ as we are going to be using the REST Generator.

> See my other [Articles](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) for more information.

The great thing about the REST Generator is it will create the DataTypes we need for the Warranty info, we only need a couple of fields but they are all there for future requirements.
  
We are going to be using the **AssetEntitlementData** in combination with **ServiceLevelDescription**.
  
There are some requirements when using the API including how often you can query the dataset and how many machines you can ask for.

> 5.3 API Access Criteria
> 
> 
> 5.3.1 Scheduled or Automated Retrieval of Warranty Information
> 
> 
> To avoid undue load on the Warranty Status API server, the following algorithm should be followed for scheduling or automating warranty retrievals:
> 
> - Query warranty API once for all new devices.
> - Query warranty API every 60-days for devices that have warranties expiring outside 1 year window.
> - Query warranty API every 30-days for devices that have warranties expiring inside a +/- 1 year window.
> - Query API every 15-days for warranties expiring between 45 to 90 days.
> - Query API weekly for warranties expiring between 30 to 45 days.
> - Query API daily for warranties expiring between -10 to 30 days.
> - Query API every 30 days for warranties expiring between -10 to -60 days.
> - Do not query for warranties for devices that have warranty expired more than 60 days.
> - Code Mapper Service need to be looked up only for new countries.
> 
> 
> 
> Dell\_Warranty\_Status\_Api\_Certification\_Guide\_v1-1.doc

You are also required to perform some tests and supply a list of results to confirm you have understood how to use the API and that you are using it correctly. We created a Web Forms Project to test and provide this data.

The first step when creating the main WFs is to get a list of Assets with their ServiceTags.
  
You could build a View for this, amend to suit your needs,

    SELECT DISTINCT a.Guid AS AssetGuid,a.NAME AS AssetName,rt.Guid AS ResourceTypeGuid,rt.NAME AS ResourceTypeName,COALESCE(hwcs.[Identifying Number], whc.[Serial Number]) AS [Identifying Number],sw.[Warranty Until],DATEDIFF(DAY, GETDATE(), sw.[Warranty Until]) AS NumOfDays,sw.LastCheckedDate,DATEDIFF(DAY, GETDATE(), sw.LastCheckedDate) AS LastCheckedDiff--,m.Manufacturer--,hwld.[Description]
    FROM vRM_Asset_Item AS aINNER JOIN ResourceType AS rt ON rt.Guid = a.ResourceTypeGuid--INNER JOIN Inv_Manufacturer m ON m._ResourceGuid = a.GuidLEFT OUTER JOIN Inv_HW_Computer_System AS hwcs ON hwcs._ResourceGuid = a.GuidLEFT OUTER JOIN Inv_HW_Chassis AS whc ON whc._ResourceGuid = a.GuidLEFT OUTER JOIN Inv_Simple_Warranty AS sw ON sw._ResourceGuid = a.GuidLEFT OUTER JOIN Inv_HW_Logical_Device AS hwld ON hwld._ResourceGuid = a.Guid
    WHERE--m.Manufacturer LIKE '%Dell%' ORhwld.[Description] LIKE '%Dell%'

Now that we have a list we want to filter it on the requirements above. We can use a **[Configurable Collection Filter](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=6193480f-7974-4a5b-a56d-75113ecff3df&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)** for this.
  
Next group them by sets of 50 and join the serial numbers together with **[Build Text From Elements](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c53e85f2-cc4c-4c26-915f-17a5256640a1&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)**.
  
Call the API and use the dataset returned.
  
We can now map the data to the SMP Resource and save.
  
![HWAM_DELLWARRANTY_UPDATER](images\HWAM_DELLWARRANTY_UPDATER.png)
  
This we created using a ![Monitoring](images\Monitoring.png) Monitoring Project so we could set it on a schedule and leave it to run in a given interval.

If you'd like a copy of this do get in touch [info@protirus.com](mailto:info@protirus.com?subject=Workflow%20-%20SMP%20-%20Dell%20Warranty&amp;body=Workflow%20-%20SMP%20-%20Dell%20Warranty)

- ![Web Form](images\WebForm.png) DELL\_API\_TestCertification\_Form
- ![Int](images\Int.png) DELL\_INT
- ![Monitoring](images\Monitoring.png) HWAM\_DELLWARRANTY\_UPDATER

---
  
Previous Downloads
  
[http://www.symantec.com/connect/downloads/dell-product-information-smp](https://community.broadcom.com/groups/viewdocument?DocumentKey=13045b3a-be58-41c4-b38e-8b4b06b7394c&amp;CommunityKey=36a652c6-c7e1-4701-af0f-b978f701f102&amp;tab=librarydocuments)
  
The captcha on the website can cause issues.
  
---
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
