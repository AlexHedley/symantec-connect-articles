---
title: Workflow - CCS - Components
tags:
    - Workflow
    - CCS
    - Component
author: AlexHedley
# description: 
articleId: 3767741
published: 2018-04-27
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-ccs-components?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

### Symantec Control Compliance Suite
  
[https://www.symantec.com/products/control-compliance-suite](https://www.symantec.com/products/control-compliance-suite)

> Assess. Remediate. Comply.  
> 	Identify security gaps and pinpoint vulnerabilities to prioritize remediation and reduce risk and automate compliance assessments for over 100 regulations, mandates, and best practice frameworks including GDPR, HIPAA, NIST, PCI and SWIFT.

![CCS](images\CCS.png)

An example API URL

    https://{host}:{port}/CCS/Services/{Applications/Standards/SMJobService}/{securityType}

Add the CCS DLL to your Project

    Symantec.Components.CCS.dll

You can find this in the following folder:

    [Install Drive]:\Program Files\Symantec\Workflow\Shared\components\Symantec.Components.CCS.dll

There are a number of sections under Symantec | CCS folder:
  
- Asset
- Exception
- Job
- Policy
- Standards
- Tags

![Workflow_CCS_Components_1](images\Workflow_CCS_Components_1.png)

Symantec  
  CCS  
    Asset

- Create Asset Evaluation Job
- Create Asset Import Job
- Create Asset Update Job
- Get All Asset Type
- Get Asset Tags
- Get Assets
- Get Check Evaluation Results
- Remove Tag From Asset
- Run Asset Evaluation Job
- Run Asset Import Job
- Tag Asset

![Workflow_CCS_Components_2](images\Workflow_CCS_Components_2.png)
  
Symantec  
  CCS  
    Exception

- Create Exception

Job

- Execute Job
- Get Job Details
- Get Job Status
- Subscribe To Job

Policy

- End Policy Approval
- End Policy Review
- Get Policy Details
- Get Policy Info
- Publish Policy
- Request Policy Clarification
- Repsond To Policy
- Respond To Policy Clarification
- Set Policy To Draft
- Start Policy Approval
- Start Policy Review

Standards

- Get Standards

Tags

- Get Tags

Workflow Properties are added to the Project when you drag on a Component
  
![Workflow_CCS_Properties](images\Workflow_CCS_Properties.png)

| Name | Value |
| --- | --- |
| CCSApiHost |  |
| CCSApiUsername |  |
| CCSApiPassword |  |
| CCSApiPort |  |

### API
  
Symantec™ Control Compliance Suite 11.1 ISS API Reference Help  
https://support.symantec.com/en\_US/article.DOC6316.html
  
Control Compliance Suite (CCS) ISS API's by example.  
https://support.symantec.com/en\_US/article.TECH235638.html
