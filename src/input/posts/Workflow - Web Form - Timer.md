---
title: Workflow - Web Form - Timer
tags:
    - Workflow
    - WebForm
author: AlexHedley
# description: 
# articleId: 
published: 2015-06-10
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-web-form-timer?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

> ⚠ Missing Images

In this article I will show you how to create a Timer or Countdown in the ![Forms (Web).png](images\FormsWeb.png) Forms (Web) Project Type

Add a Form Builder component to the Workflow.
  
Add a Textbox to the Form.
  
Change the Control ID: “counter”.
  
![Textbox - Functionality (Timer).png](images\Textbox-FunctionalityTimer.png)
  
Now edit the Web Form.
  
Go to the Behaviour tab.
  
Add timer() to the *onload* event for the Body.
  
![Form - Behaviour (Timer).png](images\FormBehaviourTimer.png)

    var count = 30;
    var x;
    function timer() {
        x = setTimeout("timer()",1000);
        count = count-1;
        document.getElementById("counter").value = count;
    }

Change count to the value you wish to count down from.

This could be done with a Label instead of a textbox.

Add a Label to the Form.

Change the Control ID: “counter2”.

    document.getElementById("counter2").innerHTML = count;

* * *

You could then use an [Auto Exit Page On Timer](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ed403596-e91b-4e55-b235-800813a8c26b&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to close the form or go to the next page or whichever route you need to go.

* * *

[![Protirus](images\Protirus.png)](http://www.protirus.com/)
