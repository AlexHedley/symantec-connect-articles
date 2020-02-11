---
title: Workflow - ProcessManager - WebPart - Developer Guide
tags:
    - Workflow
    - Process Manager
    - WebPart
    - Developer Guide
author: AlexHedley
# description: 
# articleId: 
published: 2017-07-11
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-processmanager-webpart-1?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this set of Articles I'm going to explain how to create a simple webpart for use within ![Workflow](images\Workflow.png) Workflow / ServiceDesk ProcessManager.
  
I will run through the different parts needed to create a usable webpart.
  
Each one will build upon what we have learnt in a previous article, so don't skip any :p
  
Articles
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=aa0478d7-5f5a-4be4-8369-4c74f963deeb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=36a9f5ee-ab0b-42e7-a75e-590ba4f256ec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a3b54e8a-7492-4397-8512-8828defe25a7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74973282-5d27-4b12-a0d3-9ad29d38a2ce&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c1b3103c-afad-45f8-9f17-244fff752121&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other WebParts
- [Controls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c20f9b40-20f8-4693-937a-7ca431c4d7ce&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) a WebPart
- WF/PM [Connection String](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=849d26ef-084e-426b-a064-fbb86730e6b8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Connecting to [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=77434eb5-7ee1-4bb4-bef1-ef566cce61fb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to retrieve data

- - -
  
Below is a list of documentation that would be useful to read.
  
**Documentation**
  
Symantec™ Workflow 8.1 Component Developer Guide  
[https://support.symantec.com/en\_US/article.DOC9626.html](https://support.symantec.com/en_US/article.DOC9626.html)

- Chapter 9
    - About writing webparts for Process Manager    198
    - Writing webparts for Process Manager             198

Symantec™ Workflow 8.0 Component Developer Guide  
[https://support.symantec.com/en\_US/article.DOC8700.html](https://support.symantec.com/en_US/article.DOC8700.html)
  
Symantec™ Workflow 7.6 Component Developer Guide  
[https://support.symantec.com/en\_US/article.DOC8166.html](https://support.symantec.com/en_US/article.DOC8166.html)
  
Symantec™ Workflow 7.5 SP1 Component Developer Guide  
[https://support.symantec.com/en\_US/article.DOC7226.html](https://support.symantec.com/en_US/article.DOC7226.html)  
  
Symantec™ Workflow 7.5 Component Developer Guide  
[https://support.symantec.com/en\_US/article.DOC5940.html](https://support.symantec.com/en_US/article.DOC5940.html)
  
Workflow Documentation  
[https://www.symantec.com/connect/articles/workflow-documentation](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=001862c9-ba6d-47ab-b44d-f052615e375b&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
- - -
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
