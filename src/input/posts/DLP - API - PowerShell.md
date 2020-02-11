---
title: DLP - API - PowerShell
tags:
    - DLP
    - API
    - PowerShell
author: AlexHedley
# description: 
# articleId: 
published: 2020-02-10
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/dlp-api-powershell?CommunityKey=65cf8c43-bb97-4e96-ae0b-0db8ba1b4d07&tab=librarydocuments
---

With the release of DLP 15.7 a new REST API has been added to Enforce.
  
- [DLP - API](https://www.symantec.com/connect/articles/dlp-api)
- [DLP - API - REST](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f6319a99-6c61-4d58-8554-f8cbdd380e4d&amp;CommunityKey=65cf8c43-bb97-4e96-ae0b-0db8ba1b4d07&amp;tab=librarydocuments)
    - [https://apidocs.symantec.com/home/DLP15.7](https://apidocs.symantec.com/home/DLP15.7)

From that I've started to write a new PowerShell Module to interact with this REST API.
  
You can find the code on GitHub:

- [PoShSymcDLP](https://github.com/Protirus/PoShSymcDLP)

Methods

- Query Incidents
- Update one more more incidents
- Get all possible values of prevent action statuses or protect action statuses
- Get all Incident Status values. These are custom defined statuses
- Editable Incident Attributes
- Get Incident History
- Static Incident Attributes
- Logoff

It's open to PRs and any help you can provide.
  
RoadMap

- Add Tests (Pester)
- Documentation (platyPS)
- Publish to the [PowerShellGallery](https://www.powershellgallery.com/)

---
  
What's New and What's Changed in Symantec Data Loss Prevention 15.x  
DOC10601  
https://support.symantec.com/us/en/article.doc10601.html

| Version | 15.7 |
| --- | --- |

Enforce Server and platform features  
Table 1-5 New and changed Enforce Server and platform features for Symantec Data Loss Prevention 15.7

| Feature | Short description |
| --- | --- |
| New incident reporting APIs based on REST | The new Incident Reporting REST API provides easier implementation and expanded functionality compared to the original Incident Reporting and Update API, which was based on SOAP.  <br>			See “New incident reporting APIs based on REST” on page 23. |

New incident reporting APIs based on REST  
Data Loss Prevention 15.7 makes available a set of public RESTful APIs for incident reporting.  
You can use the REST APIs to integrate incident data with other applications to provide dynamic reporting, create a custom incident remediation process, or support business processes that rely on DLP incidents.  
The new REST APIs replace the capabilities of the Incident Reporting and Update API, which was based on SOAP technology. REST APIs are generally better performing and easier to use that SOAP-based APIs. While the SOAP-based APIs for incident reporting are still supported, new integrations requiring custom incident reporting should leverage theREST-based APIs. The Incident Reporting and Update SOAP APIs are deprecated in Data Loss Prevention 15.7.  
For more information about the incident reporting REST APIs, refer to the DLP 15.7 REST API documentation.
  
Symantec™ Data Loss Prevention 15.7  
REST API Guide  
https://apidocs.symantec.com/home/DLP15.7
  
SOAP-based Incident Reporting and Update API, and Incident Data Views  
The SOAP-based version of the Incident Reporting and Update API and Incident Data Views are deprecated.
