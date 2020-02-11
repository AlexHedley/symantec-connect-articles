---
title: Workflow - ProcessManager - WebPart - Developer Guide - Inspecting
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
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-processmanager-webpart?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I'm going to explain how to inspect other WebParts within Process Manager to see how they are implemented.
  
It's a great way to find how things are done and use them in your own WebParts.
  
Articles
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=aa0478d7-5f5a-4be4-8369-4c74f963deeb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=36a9f5ee-ab0b-42e7-a75e-590ba4f256ec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a3b54e8a-7492-4397-8512-8828defe25a7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74973282-5d27-4b12-a0d3-9ad29d38a2ce&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c1b3103c-afad-45f8-9f17-244fff752121&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other WebParts (this)
- [Controls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c20f9b40-20f8-4693-937a-7ca431c4d7ce&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) a WebPart
- WF/PM [Connection String](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=849d26ef-084e-426b-a064-fbb86730e6b8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Connecting to [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=77434eb5-7ee1-4bb4-bef1-ef566cce61fb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to retrieve data

- - -
  
There are a number of decompilers available, two of which I use are

- ![dotPeek (S)](images\dotPeekS.png) [dotPeek](https://www.jetbrains.com/decompiler/) from ![JetBrains (S)](images\JetBrainsS.png) [JetBrains](https://www.jetbrains.com/)
- ![JustDecompile.png](images\article-3686471-files_JustDecompile.png) [JustDecompile](http://www.telerik.com/products/decompiler.aspx) from [Telerik](http://www.telerik.com/)
- An SMP staff member told me about [ILSpy](http://ilspy.net/), I've not tried it yet but useful to add to the list.

We first need to locate some WebParts that come with Process Manager, navigate to the following folder.

    [Install Drive]:\Program Files\Symantec\Workflow\ProcessManager\bin

Take a copy of the following DLLs and add them to your Dev environment.

- LogicBase.Ensemble.Webparts.Default.dll
- Symantec.ServiceDesk.WebParts.dll

- LogicBase.Ensemble.dll
    - LogicBase.Ensemble.Reports.WebParts
        - ProcessInfo
        - etc

Open them in your decompiler of choice.
  
Navigate to "LogicBase.Ensemble.Webparts.Default" -&gt; 'HtmlEditorPart' and investigate the different methods.

- - -
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
