---
title: SMP - ASDK - 8.5 RU2
# tags:
#     - 
author: AlexHedley
# description: 
articleId: 3838261
published: 2019-06-04
---

With the release of ITMS 8.5 RU2 there were some new Web Service methods added to the following:
  
### Collection Management Service
  
- GetExclusionGuids
- GetInclusionGuids
- IsExclusion / IsExclusionX
- IsInclusion / IsInclusionX

### Patch Management Service

- CreatePatchInstallationTask
- EditPatchInstallationTask
- SetGuidCollectionProperty
- SetPluginPolicyMicrosoftUpdateOptions

You may want to update the Zero Day Patch ![Workflow](images\Workflow_0.png) Workflow to leverage these new methods:
  
Workflow Template - Zero Day Patch  
https://www.symantec.com/connect/videos/workflow-template-zero-day-patch

### Resource Management Service

- SetAssetOwner / SetAssetOwnerX
- SetAssetState / SetAssetStateX

### Resource Model**(NSWebService)**

- GetDataClassRows / GetDataClassRows2
- SaveDataClassRows

---
  
To keep track of updates you can compare Web Service Methods using a tool I've written

- [https://protirus.github.io/SMPWebServiceDiff/](https://protirus.github.io/SMPWebServiceDiff/)

---
  
### Documentation
  
Symantec™ IT Management Suite 8.5 RU2 Release Notes  
[https://support.symantec.com/en\_US/article.DOC11423.html](https://support.symantec.com/en_US/article.DOC11423.html)  
DOC11423
