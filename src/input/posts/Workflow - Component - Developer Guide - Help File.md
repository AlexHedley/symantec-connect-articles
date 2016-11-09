---
title: Workflow - Component - Developer Guide - Help File
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-11-09
---

In this Article I'm going to explain how to create an accompanying Help file with added information to display to the User when they open and configure the component.
  
Table of Contents[​](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=17aa2b9a-9092-40d0-afab-a6d8316de97d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70a9fde5-0d87-4b9d-a3be-0907567ffc00&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Help File](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80437c69-ccc3-47e6-a850-9cf3f301b340&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Logging](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63b72a9a-53b8-4d4b-bce3-5f0732b134d5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Inputs
    - [Checkbox](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74c56ef7-1119-40fe-9d5f-3c7a1d808d4c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [Dropdown / Combo](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=267159ac-b8e7-45b4-abe4-f85d78e30783&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2c3b3a6f-01d7-4157-a143-ba30c9edc930&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other Components
- [Creating Globals](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=cf54de06-be56-46ff-b937-148efa57eaec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Creating Project Properties](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4cfc07c5-404e-49b3-81b6-520d4ea43d5c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f3cf0097-06e7-42f3-a747-d0dff319c1e5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with a Web Service](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=26368883-708b-4432-999b-7064f2f25794&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

These are located:

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Help\

When creating a Component using the ![Int](images\Int.png) Integration Project type when you Compile and close the Help Editor loads and allows you to make changes.
  
If you have created a custom component this file won't exist.
  
The File name is usally the DLL name with the ".libconfig" file extension.
  
To create a new Help file for a custom dll open the Help Editor

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\bin\WorkflowHelpEditor.exe

Select **File** | **New**
  
![Help Editor - File New](images\HelpEditor-FileNew.png)
  
Select **Browse**
  
![Help Editor - New File](images\HelpEditor-NewFile.png)
  
Find the dll in the customlib folder
  
![Help Editor - New File - From Assembly](images\HelpEditor-New+File-FromAssembly.png)
  
Now we have the Component to work with.
  
If we compare what data we have to what Attributes we provided in code:

    [Serializable,
    ComponentCategory("Protirus"),
    ComponentImage("Protirus.Workflow.Protirus.png"),
    ComponentName("Protirus Concat"),
    ComponentDescription("This component joins two Strings."),
    ComponentHelp("http://www.protirus.com/components/"),
    ComponentUsage("Requires two strings."),
    ComponentExample("String a = 'Hello' String b = 'World', this will return 'Hello World', if Add Space is True."),
    ComponentPublisher("Protirus", "www.protirus.com")]
    [PropertyPageOrder("General", "Configuration", "Settings")]

![Help Editor - Protirus.Components.Concat (Anno)](images\HelpEditor-Protirus.Components.ConcatAnno.png)
  
If you click on ![Property (2)](images\Property2.png) Properties we can then add extra information and group them by tabs.
  
Data annotations in code are now deprecated so the help file is the only way to add it and show in the Help file within Workflow.
  
![Help Editor - Protirus.Components.Concat - Properties](images\HelpEditor-Protirus.Components.Concat-Properties.png)
  
As we see the Component Properties don't have any information and aren't grouped by tabs.
  
To add the Published add the Company name in the Assembly Info of the component in Visual Studio.
  
![Protirus.Concat Help (Anno)](images\Protirus.ConcatHelpAnno.png)
  
I annotate my variables in code, these can then be copied to help

    [VariableType(typeof(string), false), 
      PropertyIndex(3), 
      DisplayName("String 1"), 
      Category("Configuration"), 
      ComponentDescription("The first String to be merged")]      

You can create new Categories or groupings within a tab,
  
![Help Editor - Protirus.Components.Concat - Properties - New Category.png](images\HelpEditor-Protirus.Components.Concat-Properties-NewCategory.png)
  
Give it a name
  
![Help Editor - Protirus.Components.Concat - Properties - New Category - Name](images\HelpEditor-Protirus.Components.Concat+-Properties-NewCategory-Name.png)
  
Drag the Properties into the Category, then add your information.
  
![Help Editor - Protirus.Components.Concat - Properties - Category - Configuration.png](images\HelpEditor-Protirus.Components.Concat-Properties-Category-Configuration.png)
  
Save this file.
  
Reload your Workflow.
  
![Protirus.Concat General (Updated)](images\Protirus.ConcatGeneralUpdated.png)
  
You may notice the Icon has changed back to the default.
  
![cubes.png](images\article-3610721-files_cubes.png)
  
Back to the Help file.
  
Click on the Component, then click ![Icon](images\Icon.png) Icon
  
Click **Add** then search for your image, choose and click OK.
  
![Help Editor - Protirus.Components.Concat - Icon](images\HelpEditor-Protirus.Components.Concat-Icon.png)
  
Now you might want Tabs aswell as grouping items in the General tab.
  
![Help Editor - Protirus.Components.Concat - Properties - New Page](images\HelpEditor-Protirus.Components.Concat-Properties-NewPage.png)
  
Drag the Category into the new tab
  
![Help Editor - Protirus.Components.Concat - Properties - Page](images\Help+Editor-Protirus.Components.Concat-Properties-Page.png)
  
Now save and reload the WF.
  
![Protirus.Concat Configuration (Filled In)](images\Protirus.ConcatConfigurationFilledIn.png)
  
If we click the Help ?
  
![Protirus.Concat Help (Updated)](images\Protirus.ConcatHelpUpdated.png)
  
If we'd filled in the Help and Example etc they would show here too.

[![Protirus](images\Protirus.png)](https://www.protirus.com/)
