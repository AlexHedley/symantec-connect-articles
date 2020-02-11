---
title: Workflow - Plugins - Protirus
tags:
    - Workflow
    - Plugin
author: AlexHedley
# description: 
# articleId: 
published: 2017-12-06
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-plugins-protirus?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

Symantec ![Workflow](images\Workflow.png) Workflow Manager has a number of Plugins available from install.
  
These are documented: [Workflow Plugins](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=3b4c589a-aaaa-49a3-a610-7a307716dc53&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments).
  
You can download a copy from the following Connect post:

| Download | [Protirus.Workflow.Plugins](https://www.symantec.com/connect/downloads/workflow-plugins-protirus) |
| --- | --- |

I've created a bundle which are listed below, 'Model Info' down,
  
![Workflow - Menu - Plugins - Protirus](images\Workflow-Menu-Plugins-Protirus.png)
  
Each will be explained on their own pages.
  
- [Model Info](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=fa1db8eb-16be-4c74-95ba-2d5ba1de516b&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Recycle App Pools](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f98989b9-e12e-412d-870f-62ba194b9a6a&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Restart IIS](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=398434ef-3182-40ec-8a5c-dd41bfd28d78&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Restart Workflow Services](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2ac8d6c4-e2f6-492b-a8f7-008c86fa6a70&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Powershell](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4cf9dc2d-aa7d-4e94-a3c8-197aa41677d4&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Task Tray Tool](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c81ce6df-ab80-47e8-827e-eb75b67078c2&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow Explorer](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9bc4e726-c60a-4f63-83cf-76f55d576992&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (Running As)
- Open [Workflow Logs Folder](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=7acbf6dd-adc2-412f-a09c-f2efdbf66c9a&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Zip](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=191d3b73-aa1c-4392-82b1-d6ec0c44e91c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) Project

- Protirus
    - This was just to test some basic info about a Project, get it's Icon etc

There are some config options to allow customisation.
  
Included will be an XML file :

    Protirus.Workflow.Plugins.xml

Save this to the Plugins directory

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins

This currently has two sections, one to choose whether to show or hide each plugin in the menu. This is so you only need to have one DLL instead of individual but means you don't have to have a huge list showing.

      <plugins>
        <pluginsDef>
          <name>ModelInfoPlugin</name>
          <show>true</show>
        </pluginsDef>
      ...
      </plugins>

Swap *&lt;show&gt;true&lt;/show&gt;* to *&lt;show&gt;false&lt;/show&gt;* if you wish to not see them.
  
The second section is specifically for the Zip plugin, it sets which Log files will be included, by default, in the list.

      <files>
        <filesDef>
          <name>processmanager.log</name>
          <show>true</show>
        </filesDef>
      ...
      </files>

Swap *&lt;show&gt;true&lt;/show&gt;* to *&lt;show&gt;false&lt;/show&gt;* if you wish to not see them in the list, you can always manually add them.
  
I'm also using a NuGet package "[DotNetZip](https://github.com/haf/DotNetZip.Semverd)", within the Zip Plugin to perform the zip of the Project / Log, this DLL (and XML) will also need to be included in the Plugins directory.

- DotNetZip.dll
- DotNetZip.xml
