---
title: Workflow - Project Types - Integration - Author
tags:
    - Workflow
author: AlexHedley
# description: 
# articleId: 
published: 2018-03-16
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-project-types-integrat?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

Workflow Projects allow you to change meta data like the "Name", "Author mail" and "Description" within the Project editor.
  
The Integration Project does not.
  
As you can see from this example an "Application" and "Forms (Web)" both have an Author that I have set but the "Integration" still shows name@email.com
  
![AE_WFM_Applications_1](images\AE_WFM_Applications_1.png)

You can use the [Application Editor](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=19195da8-6f79-40a5-b020-7932e20a53f4&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to do this.
  
Start &gt; Programs &gt; Symantec &gt; Workflow Designer &gt; Tools &gt; Application Editor

    "[Install Drive]:\Program Files\Symantec\Workflow\Designer\bin\WorkflowAppEditor.exe" 

Open the ".SymWorkflow" file.
  
Amend the Company Name.
  
![AE_Int](images\AE_Int.png)
  
To your own email address.
  
![AE_Int_2](images\AE_Int_2.png)
  
And now we have an Author!
  
![AE_WFM_Applications_3](images\AE_WFM_Applications_3.png)

### Code
  
If you convert the INT into a .zip and extract then open the

    IStorableObject.xml

You will see that there is a "createdBy" value.

    <Value id="createdBy" type="data" val="name@email.com" />

This is changed by the Application Editor.

I'd like this option to be made available in Integration Editor instead.
