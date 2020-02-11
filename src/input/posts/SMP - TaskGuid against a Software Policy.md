---
title: SMP - TaskGuid against a Software Policy
tags:
    - SMP
author: AlexHedley
# description: 
# articleId: 
published: 2017-04-19
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/smp-taskguid-against-a-software-p?CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&tab=librarydocuments
---

Whilst working with Software Delivery in the SMP I needed some information that was only available in the XML of the Policy itself.
  
There are Web Services to retrieve the Policy as XML and save it to file but this is a lot of overhead.

| http://localhost/Altiris/ASDK.SWM/SoftwareDeliveryPolicyManagementService.asmx |
| --- |

Get Delivery Items Component  
Class: Altiris7.WebServices.SoftwareDeliveryPolicyManagement.GetDeliveryItemsComponent  
Library: Symantec.Components.Generated7.Altiris.ASDK.dll
  
PolicyGuid
  
Get Delivery Item Setting Component  
Class: Altiris7.WebServices.SoftwareDeliveryPolicyManagement.GetDeliveryItemSettingComponent  
Library: Symantec.Components.Generated7.Altiris.ASDK.dll
  
PolicyGuid  
[DeliveryItems\_SoftwareResource[first].Guid]  
settingName = Package

Instead we can grab it in SQL, create a new Stored Procedure.

    spPRT_PolicySoftwareTaskGuid

Get the TaskGuid against a Software Policy ('TaskDeliveryItem')
  
TaskDeliveryItem SoftwareComponent TaskGuid.sql
  
![SQL 1](images\SQL_1.png)​
  
XML

    <item>
      ..
      <deliveryItems>
        <SoftwareDeliveryItem guid="GUID">
          ..
          <SoftwareComponent itemGuid="GUID" include="True" useOverrides="False">
          ..
        </SoftwareDeliveryItem>
        ..
      </deliveryItems>
      ..
    </item>

Or a piece of Software 'SoftwareDeliveryItem'
  
![](images\article-3674561-files_SQL_2.png)​
  
XML

    <item>
      ..
      <deliveryItems>
        <TaskDeliveryItem guid="GUID">
          ..
          <SoftwareComponent itemGuid="GUID" include="True" useOverrides="False">
          ..
        </TaskDeliveryItem>
        ..
      </deliveryItems>
      ..
    </item>

​
  
If you want more information about the *value* method and parsing XML in SQL check out the MS Article:
  
**value() Method (xml Data Type)**
  
[https://docs.microsoft.com/en-us/sql/t-sql/xml/value-method-xml-data-type](https://docs.microsoft.com/en-us/sql/t-sql/xml/value-method-xml-data-type)
  
(https://msdn.microsoft.com/en-us/library/ms178030.aspx)

[![Protirus](images\Protirus.png)](https://www.protirus.com/)​
