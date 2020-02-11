---
title: Workflow - Tokens from Listbox
tags:
    - Workflow
author: AlexHedley
# description: 
# articleId: 
published: 2015-06-10
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-tokens-from-listbox?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this article I will show you how to use Javascript in the ![Forms (Web).png](images\Forms%2520%2528Web%2529.png) Forms (Web) Project Type to pass values from a Listbox to a Textarea.

This is similar to how the Email Templates work in ServiceDesk.

Add a Form Builder component to the Workflow.
  
Add a Multiline Textbox to your Form. Name it “Email\_HTML”  
Add a Listbox to your Form, give it an Ouput of “Token\_SEL”

![Web Form Editor (js).png](images\Web%2520Form%2520Editor%2520%2528js%2529.png)

![Web Form Editor - Edit Component - Functionality (js).png](images\Web%2520Form%2520Editor%2520-%2520Edit%2520Component%2520-%2520Functionality%2520%2528js%2529.png)

Add some Tokens to the Listbox Items.
  
- Token1
- Token2
- Token3

Then add a “Custom Event” using the “AttributesKeyValuePair”.

![Web Form Editor - Edit Component (Listbox) - Functionality (js).png](images\Web%2520Form%2520Editor%2520-%2520Edit%2520Component%2520%2528Listbox%2529%2520-%2520Functionality%2520%2528js%2529.png)

Choose “onclick”

![Web Form Editor - Edit Component (Listbox) - Functionality - onclick (js).png](images\Web%2520Form%2520Editor%2520-%2520Edit%2520Component%2520%2528Listbox%2529%2520-%2520Functionality%2520-%2520onclick%2520%2528js%2529.png)

Add the following code:

    var Email_HTML = document.getElementById("Email_HTML");
    var Tokens = document.getElementById("Tokens");
    var selectedValue = Tokens.options[Tokens.selectedIndex].text; //.value;
    Email_HTML.value = Email_HTML.value + ' ${' + selectedValue + '}';

![Web Form Editor - Script (js).png](images\Web%2520Form%2520Editor%2520-%2520Script%2520%2528js%2529.png)

Open the Form.
  
Now click on a Token and it will add it to your textbox.

![Form (js).png](images\Form%2520%2528js%2529.png)

In your code you can now parse the Tokens {} and replace them with any other info.
  
You could use “[Workflow - Tag Finder](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=59d4c016-dd91-49c5-b4e2-09ce3e01765a&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (Extract Text By Pattern)”

* * *

[![Protirus.png](images\Protirus.png)](http://www.protirus.com/)
