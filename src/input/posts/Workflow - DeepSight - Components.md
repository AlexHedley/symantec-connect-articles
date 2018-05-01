---
title: Workflow - DeepSight - Components
# tags:
#     - 
author: AlexHedley
# description: 
articleId: 3768101
published: 2018-05-01
---

## DeepSight™ Intelligence
  
[https://www.symantec.com/services/cyber-security-services/deepsight-intelligence](https://www.symantec.com/services/cyber-security-services/deepsight-intelligence)

> DeepSight™ Intelligence  
> 	Extend your teams with actionable cyber threat intelligence. Make sharper decisions to defend against emerging global threats.

### Components
  
Add them to your Project

    [Install Drive]:\Program Files\Symantec\Workflow\Shared\components\Symantec.Components.DeepSight.dll

![DeepSight_Components](images\DeepSight_Components.png)
  
Symantec  
  DeepSight  
    Database
  
- Save Attack Correlation Feed Item
- Save Common Feed Item
- Save Exposure Feed Item
- Save Intelligence Ip Feed Full Verbosity Item
- Save Intelligence Ip Feed Low Verbosity Item
- Save Malcode Feed Item
- Save Security Risk Feed Item
- Save Vulnerability Feed Item

Symantec  
  DeepSight

- Common Feed Item Converter
- Get Attack Correlation Feed Items
- Get Common Feed Items
- Get Exposure Feed Items
- Get Intelligence Ip Feed Full Verbosity Items
- Get Intelligence Ip Feed Low Verbosity Item
- Get Malcode Feed Item
- Get Security Risk Feed Item
- Get Vulnerability Feed Item

Properties
  
![Workflow_DeepSight_Properties](images\Workflow_DeepSight_Properties.png)

| Name | Value |
| --- | --- |
| DeepSightUsername |  |
| DeepSightPassword |  |
| DeepSightURL | https://datafeeds.symantec.com/feeds/datafeed.asmx |

### Data Feeds

    https://datafeeds.symantec.com/feeds/datafeed.asmx

- GetClientMenu
- GetCustomerDataFeedList
- GetFeedFile
- GetFeedFileList
- GetSequenceNoByFeedVersion

    https://datafeeds.symantec.com/feeds/datafeed.asmx?wsdl

### Intelligence

    http://deepsightinfo.symantec.com/DeepSight/Intelligence.asmx

- GetIpList
