---
title: Workflow - SMP - ASDK - Asset Ownership
tags:
    - Workflow
    - SMP
    - ASDK
author: AlexHedley
# description: 
# articleId: 
published: 2015-10-09
# symantecUrl:
broadcomUrl: https://community.broadcom.com/groups/viewdocument/workflow-smp-asdk-asset-owner?CommunityKey=f076336e-1f97-4c5f-b14c-73b1bcb3af7c&tab=librarydocuments
---

In this Article I'm going to explain how Asset Ownership is controlled in the ![smp](images\smp.png) SMP and how to maintain it using ![Workflow](images\Workflow.png) Workflow and the ASDK.

Let's look at it in the SMP first.
  
Home | Service and Asset Management | Manage Configuration Items
  
Let's find a ![Computer](images\Computer.png) Computer
  
![Folder (-)](images\Folder-.png) CI Management | ![Folder](images\Folder.png) Computers and Peripherals | ![Computer](images\Computer.png) Computer
  
Search for one and Right-Click | ![Edit ()](images\Edit.png) Edit
  
Scroll down to **Asset Owners** and "Click to select..." or click the ![Edit](images\Edit.png)Edit button
  
![Edit - Computer - Asset Owners](images\_Edit-Computer-AssetOwners.png)
  
This can either be a User or a Department.
  
Search for the User, select and click OK.
  
This is configured using a Resource Association.
  
There are two, one for User and one for Department.
  
![Reports Folder](images\ReportsFolder.png) Settings | ![Folder](images\Folder.png) Notification Server | ![Folder](images\Folder.png) Resource and Data Class Settings | ![Folder](images\Folder.png) Resource Associations | ![Folder](images\Folder.png) CMDB Association Types | ![Resource Association](images\ResourceAssociation.png) Asset User Owner

| ​GUID | 'ed35a8d1-bf60-4771-9dde-092c146c485a' |
| --- | --- |

![Reports Folder](images\ReportsFolder.png) Settings | ![Folder](images\Folder.png) Notification Server | ![Folder](images\Folder.png) Resource and Data Class Settings | ![Folder](images\Folder.png) Resource Associations | ![Folder](images\Folder.png) CMDB Association Types | ![Resource Association](images\ResourceAssociation.png)  Asset Department Owner

| ​GUID | '1466e770-4413-4517-a89d-6599b8a7f144' |
| --- | --- |

You can see who is associated to what with the following SQL:

    SELECT * 
    FROM ResourceAssociation ra
    WHERE ra.ResourceAssociationTypeGuid = 'ed35a8d1-bf60-4771-9dde-092c146c485a'

So we need to create an Association, let's look to the SDK.
  
There's a "Create Resource Association​" we can use.
  
- http://localhost/altiris/asdk.ns/ResourceManagementService.asmx?op=CreateResourceAssociation

Inputs:

- resourceAssociationTypeGuid
- parentResourceGuid (*Asset*)
- childResourceGuid (*User*)

Create a ![Int](images\Int.png) Web Service Generator ([Video](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=7d413f83-dd96-4e73-9f5e-b4e0d7c21bab&amp;CommunityKey=492058b4-42be-43e7-991d-986f1ea9ba7f&amp;tab=librarydocuments))
  
We can now call this in our ![Workflow](images\Workflow.png) WF.
  
Try this then check the SQL and the RA Table should reflect this but if you then check in the ![smp](images\smp.png) SMP the **Asset Owners** section won't, what's going on?
  
(Other Associations work just fine)
  
Let's do some investigation, I like to use both a SQL Profiler and the Altiris Profiler.
  
We have a call to 'spResourceAssociationsInsert', this makes sense.

    EXECUTE spResourceAssociationsInsert 
       @ResourceAssociationTypeGuid=N'ed35a8d1-bf60-4771-9dde-092c146c485a', 
      @ParentResourceGuid=N'e4fc9fc1-a75a-4532-8a82-159d2477d0fa', 
      @ChildResourceGuid=N'f90f37c8-4562-48be-b8f3-3b0b4123086b', 
      @HistoryEnabled=1

But there is also another call to insert values into another Table (Inv\_Ownership\_Details).

    INSERT INTO 
      dbo.[Inv_Ownership_Details] ([_ResourceGuid], [Owner], [Ownership Percentage]) 
    VALUES 
      ('e4fc9fc1-a75a-4532-8a82-159d2477d0fa', 'f90f37c8-4562-48be-b8f3-3b0b4123086b', 100)

Now we could just create a SQL Generator but I don't like to use these for any ALTER commands.
  
There must be a better way.
  
Let's have another look at those Web Services:
  
**Save Data Class** from **Resource Model**looks like it should work

- http://localhost/altiris/nswebservice/resourcemodel.asmx?op=SaveDataClass

Add that to our previous ![Int](images\Int.png) Integration component and try it out in ![Workflow](images\Workflow.png) WF.
  
This just doesn't work, there is no way to pass in any dynamic data so this can't be a viable solution.
  
[Toomas](https://www-secure.symantec.com/connect/user/toomas) was a great help and got us some sample code from the Asset Team.

    using System;
    using Client.ProxyClass;
    
    namespace client
    {class Program{	static readonly Guid OwnershipDetailsDataclassGuid = new Guid("0cd0318b-ad51-4d38-8ea3-2612d12189de");	private const string UserId = "put here user name";	private const string Password = "put here user password";
    	static void Main(string[] args)	{
    		var comp = new Guid("927a7afe-ab4d-40d1-b11f-72111e6d540d"); //<-set up computer guid		var user = new Guid("e0b8a57b-9b2b-4f07-8b9e-d66a3d65d678"); //<-set up user guid
    		var field0 = new DataClassFieldData { FieldName = "Owner", Value = user };		var field1 = new DataClassFieldData { FieldName = "Ownership Percentage", Value = 100.0 };		var row = new DataClassRowData { DataElements = new[] { field0, field1 } };		var dcd = new DataClassData		{			DataClassGUID = OwnershipDetailsDataclassGuid,			DataRows = new[] { row }		};
    		var client = new ResourceModelService {Credentials = new System.Net.NetworkCredential(UserId, Password)};		client.SaveDataClass(comp, new[] { dcd });	}}
    }

We tested this and got the **Inv\_Ownership\_Details** Table updating but how do we translate this into ![Workflow](images\Workflow.png) WF?
  
Maybe the ![Code (Script) Component](images\CodeScriptComponent.png) Script Generator? Or why don't we build a Component?
  
Where do we start?

- Symantec™ Workflow 7.5 Component Developer Guide
    - [https://support.symantec.com/en\_US/article.DOC5940.html](https://support.symantec.com/en_US/article.DOC5940.html)
- Symantec™ Workflow 7.6 Component Developer Guide
    - [https://support.symantec.com/en\_US/article.DOC8166.html](https://support.symantec.com/en_US/article.DOC8166.html)

That's a lengthy process in itself so that can be discussed in a future Article.
  
[Chris](http://www.symantec.com/connect/user/christophermcewen), a fellow Protirus C# Dev, got to work and created a Component we could use.

- ![dll](images\dll.png) Protirus.AssetOwner.Service.dll

If you'd like a copy of this do get in touch [info@protirus.com](mailto:info@Protirus.com?subject=Protirus.AssetOwner.Service.dll&amp;body=Workflow%20Asset%20Owner%20Component)
  
One last thing we need to do in our Workflow is to check if there is already an Owner Association before creating one, we can use the **Break Association** Web Service from **Resource Model**.

- http://localhost/altiris/nswebservice/resourcemodel.asmx?op=BreakAssociation

Now with a combination of the Break Association, Create Association and our new dll any Asset Ownership changes will now be reflected in the SMP.
  
* * *
 
<u>Useful Documents</u>
  
"&lt;Install Drive&gt;:\Program Files\Altiris\Altiris ASDK\Help\ASDK7.6.chm"
  
* * *
 
<u>Web Services</u>

- **Resource Model**
    - http://localhost/altiris/nswebservice/resourcemodel.asmx
        - Break Association
            - http://localhost/altiris/nswebservice/resourcemodel.asmx?op=BreakAssociation
        - Remove Data Class From Resource
            - http://localhost/altiris/nswebservice/resourcemodel.asmx?op=RemoveDataClassFromResource
        - Save Data Class
            - http://localhost/altiris/nswebservice/resourcemodel.asmx?op=SaveDataClass

- **Resource Management Service**
    - http://localhost/altiris/asdk.ns/ResourceManagementService.asmx​
        - Create Resource Association​
            - http://localhost/altiris/asdk.ns/ResourceManagementService.asmx?op=CreateResourceAssociation

* * *

<u>Symantec Case Info</u>

| Case Number | 08713954 | ETrack | ET3830607 |
| --- | --- | --- | --- |

* * *

[![Protirus.png](images\Protirus.png)](http://www.protirus.com/)
