---
title: Workflow - MultiStateColor Component
tags:
    - Workflow
author: AlexHedley
# description: 
# articleId: 
published: 2015-06-25
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-multistatecolor-componen?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this article I will show you how to use the 'MultiStateColor' component in the ![Forms (Web).png](images\Forms%2520%2528Web%2529.png) Forms (Web) Project Type
  
This allows you to change a panel on a Web Form to a specific colour.
  
This can be handy for a RAG Status or Traffic light system.
  
In a Form under ![Components.png](images\Components.png)Dashboard Components there is:
  
### ![MultiStateColor.png](images\MultiStateColor.png) **MultiStateColor**

| Class: | LogicBase.Components.FormBuilder.Components.MultiStateColor.MultiStateColorComponent |
| --- | --- |
| Library: | LogicBase.Components.FormBuilder.dll |
| Publisher: | Symantec Corporation |

![Form MSC.gif](images\FormMSC.gif)

Drag this onto your Form.
  
The Theme Style will be set to Panel.

![Edit Component - Appearance MSC.png](images\EditComponent-AppearanceMSC.png)
  
Add in your 'Color States'
  
You can use the Color Picker here to choose a more accurate one.
  
![Edit Component - Configuration MSC.png](images\EditComponent-ConfigurationMSC.png)
  
Click on the "..." next to the 'Color Selection Model':
  
Add in a Matches rule that uses your variable to check - here being color:
  
![Edit Embedded Decision Model MSC.png](images\EditEmbeddedDecisionModelMSC.png)
  
Add you manual comparisons:
  
![Matches Rule Editor MSC.png](images\MatchesRuleEditorMSC.png)
  
Duplicate your ![ColorStateSelectionEndComponent.png](images\ColorStateSelectionEndComponent.png) 'ColorStateSelectionEndComponent' and chose a **Selected Output** from the previously configured list.
  
![ColorStateSelectionEndComponent Editor MSC.png](images\ColorStateSelectionEndComponentEditorMSC.png)
  
Now you can run your Form and see the colour change accordingly.
  
![Workflow MSC.png](images\WorkflowMSC.png)
  
![Form MSC.gif](images\FormMSC.gif)

Watch out when using a Theme
  
Change the Background to nothing or it doesn't work.
  
![Theme Editor MSC.png](images\ThemeEditorMSC.png)
  
Original I tried 3 panels, one of each colour, with visibility rules given the matching value but this way gives more flexibility for more colour choices too.

* * *

[![Protirus](images\Protirus.png)](http://www.protirus.com/)
