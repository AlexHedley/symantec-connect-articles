---
title: SMP - Resource Target - Operations
tags:
    - SMP
author: AlexHedley
# description: 
articleId: 3808001
published: 2018-11-29
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/smp-resource-target-operations?CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&tab=librarydocuments
---

## ![SMP](images\smp.png) SMP
  
### Resource Target
  
### Operation
  
What are the different Opertions?

| # | Operation |
| --- | --- |
| 0 | Union |
| 1 | Intersect |
| 2 | Except |

They are mentioned in the following Forum post:
  
Create Resource Target component  
[https://www.symantec.com/connect/forums/create-resource-target-component](https://community.broadcom.com/groups/viewthread?MessageKey=e2f88907-fcdc-42bf-9dd5-2996237bf4df&amp;CommunityKey=56cfcefc-8f2b-4200-b0e3-e33f564377e6&amp;tab=digestviewer#bme2f88907-fcdc-42bf-9dd5-2996237bf4df)

> The "operation" element in each Target Filter defines the logical operation that will be performed between the resources contained in the the filter and base organizational group (in the case of the first filter), or between the filter's resources and the resource set derived from the previous filter opertation (in the case of the second and subsequent filters). Only three values are allowed: "Intersect," "Union," and "Except."

If you want to see which Filters are in a Target you can use a Report added to SD in 8.1 or run the following SQL.
  
- ServiceDesk - Software Request Process - Reports
    - [https://www.symantec.com/connect/articles/servicedesk-software-request-process-reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=24530d5f-01a3-464d-846b-01482ee0c85e&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)

**Filters for Target**
  
![Filters for Target SQL](images\FiltersforTarget_SQL.png)
  
For Example:
  
**All Computers without Software Update Plug-in Installed Target**

- [http://localhost/Altiris/NS/ItemAsXml.aspx?ItemGuid=96F806F1-D46D-47AA-BB40-2E2E5EFBF4C3](http://localhost/Altiris/NS/ItemAsXml.aspx?ItemGuid=96F806F1-D46D-47AA-BB40-2E2E5EFBF4C3)

| TargetName | CollectionName | FilterType | Operation | CollectionGuid |
| --- | --- | --- | --- | --- |
| All Computers without Software Update Plug-in Installed Target | Windows Computers | 1 | 1 | E3A71B08-1612-44A6-9F71-7D359D5475B4 |
| All Computers without Software Update Plug-in Installed Target | Computers with Software Update Plug-in Installed | 1 | 2 | D3BA9CA7-5E71-4D76-B961-1BA0B436AACB |
| All Computers without Software Update Plug-in Installed Target | Windows Computers Requiring Symantec Management Agent Upgrade | 1 | 2 | 04B75635-A594-48B6-9A2F-B79A0D78F6B5 |
| All Computers without Software Update Plug-in Installed Target | UNIX/Linux/Mac Computers Requiring Symantec Management Agent Upgrade | 1 | 2 | EDC60302-F96A-4BBC-9B68-402EAEAD63D5 |
| All Computers without Software Update Plug-in Installed Target | All Computers | 1 | 1 | EB3A1A12-E1C7-4431-B060-F0333E4E488C |
| All Computers without Software Update Plug-in Installed Target | Linux Computers | 1 | 0 | 6D05AC39-2CBF-4DA0-BCA1-0E64CA22A59C |

As XML

    <targetFilters>
     <targetFilter guid="{657df9f3-f6a5-4d1f-afd4-27e845c96d24}" type="Altiris.NS.StandardItems.Targeting.ResourceCollectionTargetFilter" assembly="Altiris.NS.StandardItems" offset="0">
      <operation>Intersect</operation> 
      <resourceCollectionGuid>{e3a71b08-1612-44a6-9f71-7d359d5475b4}</resourceCollectionGuid> 
     </targetFilter>
     <targetFilter guid="{38f6c355-8cd9-4b04-8f72-7680f479b979}" type="Altiris.NS.StandardItems.Targeting.ResourceCollectionTargetFilter" assembly="Altiris.NS.StandardItems" offset="1">
      <operation>Union</operation> 
      <resourceCollectionGuid>{6d05ac39-2cbf-4da0-bca1-0e64ca22a59c}</resourceCollectionGuid> 
      </targetFilter>
     <targetFilter guid="{5b6b51f1-6a29-4a7a-bf4f-296fe9e1f33b}" type="Altiris.NS.StandardItems.Targeting.ResourceCollectionTargetFilter" assembly="Altiris.NS.StandardItems" offset="2">
      <operation>Except</operation> 
      <resourceCollectionGuid>{d3ba9ca7-5e71-4d76-b961-1ba0b436aacb}</resourceCollectionGuid> 
     </targetFilter>
     <targetFilter guid="{6322d66d-7b96-4594-b352-375c546780ec}" type="Altiris.NS.StandardItems.Targeting.ResourceCollectionTargetFilter" assembly="Altiris.NS.StandardItems" offset="3">
      <operation>Except</operation> 
      <resourceCollectionGuid>{04b75635-a594-48b6-9a2f-b79a0d78f6b5}</resourceCollectionGuid> 
     </targetFilter>
     <targetFilter guid="{947f3bc8-c74b-4ded-b041-444137a5875e}" type="Altiris.NS.StandardItems.Targeting.ResourceCollectionTargetFilter" assembly="Altiris.NS.StandardItems" offset="4">
      <operation>Except</operation> 
      <resourceCollectionGuid>{edc60302-f96a-4bbc-9b68-402eaead63d5}</resourceCollectionGuid> 
      </targetFilter>
     <targetFilter guid="{edb9c0cf-1ee9-4ba2-bc47-5bdf23ad5b05}" type="Altiris.NS.StandardItems.Targeting.ResourceCollectionTargetFilter" assembly="Altiris.NS.StandardItems" offset="5">
      <operation>Intersect</operation> 
      <resourceCollectionGuid>{eb3a1a12-e1c7-4431-b060-f0333e4e488c}</resourceCollectionGuid> 
     </targetFilter>
    </targetFilters>

The Operation Column is an Int (ENUM) in SQL so just shows the number, not the name.

[![Protirus.png](images\Protirus.png)](https://www.protirus.com/)
