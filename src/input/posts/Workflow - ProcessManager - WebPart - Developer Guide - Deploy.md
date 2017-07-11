---
title: Workflow - ProcessManager - WebPart - Developer Guide - Deploy
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-07-11
---

In this Article I'm going to explain how to deploy a WebPart to your Process Manager.
  
Articles
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=aa0478d7-5f5a-4be4-8369-4c74f963deeb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=36a9f5ee-ab0b-42e7-a75e-590ba4f256ec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a3b54e8a-7492-4397-8512-8828defe25a7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74973282-5d27-4b12-a0d3-9ad29d38a2ce&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments) (this)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c1b3103c-afad-45f8-9f17-244fff752121&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other WebParts
- [Controls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c20f9b40-20f8-4693-937a-7ca431c4d7ce&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) a WebPart
- WF/PM [Connection String](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=849d26ef-084e-426b-a064-fbb86730e6b8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Connecting to [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=77434eb5-7ee1-4bb4-bef1-ef566cce61fb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to retrieve data

- - -
  
Login to your Process Manager as a Administrator.
  
Admin | Portal | Plugin Upload
  
Select 'WebPart' for 'Plugin Type'.
  
Choose your DLL that you've compiled from the VS Project and click upload.
  
![ProcessManager_Admin_Portal_PluginUpload](images\ProcessManager_Admin_Portal_PluginUpload.png)

This may take a few seconds/minutes, wait until the page has completed loading.
  
To confirm it has successfully been deployed you can check it has been added to the following folder:

    [Install Drive]:\Program Files\Symantec\Workflow\ProcessManager\bin

Once the web part has been uploaded it needs to be added to the Web Parts Catalog. You may need to restart IIS for it to appear in the list.
  
Go to "Admin | Portal |Web Parts Catalog"
  
It is probably best to have custom WebParts in their own category. If there is already a category, select it and then press the Edit icon on the right hand side of the category name title bar as shown in the image below.
  
![ProcessManager_Admin_Portal_WebPartsCatalog](images\ProcessManager_Admin_Portal_WebPartsCatalog.png)
  
If there is no category then select the same icon for any category and when the Add WebPart dialog pops up type in 'CategoryName' for the Category field. This will create a new category when you save.
  
Select the custom web part, from the Class Name dropdown list.
  
This will auto populate a **Friendly Name** but this can be changed.
  
![ProcessManager_Admin_Portal_WebPartsCatalog_AddWebPartCatalog](images\ProcessManager_Admin_Portal_WebPartsCatalog_AddWebPartCatalog.png)

| Note. This only has to be done once. If you make changes to the webpart you can simply copy over the dll that is in the *&lt;workflow dir&gt;\ProcessManager\bin* folder. However, after you’ve copied the new dll and refresh the page it can take a while to reload so you may need to close and reopen ProcessManager/ServiceDesk. |
| --- |

The next step is to add the web part onto the required page.
  
Go to "Admin | Portal | Manage Pages" and go to the required page. You may wish to create a clone of a current page and make updates to that first.
  
When the page loads click on "Site Actions | Modify Page".
  
Then press "Site Actions | Add Web Part".
  
Select the previously made category and the required web part as shown in the image below.
  
![ProcessManager_ProcessViewPage_AddWebPart](images\ProcessManager_ProcessViewPage_AddWebPart.png)
  
Select the required zone and then press "Add". The WebPart will be added to the page and look like the image below.
  
![ProcessManager_ProcessViewPage_WebPart](images\ProcessManager_ProcessViewPage_WebPart.png)
  
You can then edit the 'Title' and other default WebPart properties, like any other web part.
  
The new 'ContentText' variable, within the Property Grid section, we added can display any text we wish, I've just added "hello" as an example above.
  
![ProcessManager_ProcessViewPage_WebPart_EditorZone](images\ProcessManager_ProcessViewPage_WebPart_EditorZone.png)
  
Now we can try it in a Process View Page.

- - -
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
