---
title: Workflow - SendCompleteWorkflowMessage - Event Listeners
tags:
    - Workflow
author: AlexHedley
# description: 
# articleId: 
published: 2015-11-30
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-sendcompleteworkflowmess?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I will explain how to use the 'SendCompleteWorkflowMessage' to hook into a Dialog Workflow via the Event Listeners.

I'm assuming that you already have a Workflow written that is creating Tasks via the 'Dialog Workflow' component.

You could then have another Project (Web Forms) that get's a list of User's Tasks and displays them for actioning, or set up an automated method of send these messages, it's your choice.

As a very simple example we have a Workflow with a Task, once we set up an Event Listener that path will then be available to us for actioning, with the Message data for use.

![POC_WorkflowComplete_WF](images\POC_WorkflowComplete_WF.png)

Double click on your Dialog Workflow and click on the 'Message Listeners' tab,

Tick the "Allow Exit Via Message Monitoring"

Next click on **Add**.

![Dialog Workflow Editor - Message Listeners](images\DialogWorkflowEditor-MessageListeners.png)

Give your Path a name. I've called mine the very inventive "MyPath"

![Dialog Workflow Editor - Message Responses - Path](images\DialogWorkflowEditor-MessageResponses-Path.png)

We need some Path Data to work with so click on that tab.

Untick "Empty Message"

I'm just using 'Text' here but yours could be a newly defined type or one from your Workflow Process.

![Dialog Workflow Editor - Message Responses - Path Data](images\DialogWorkflowEditor-Message+Responses-PathData.png)

Now if you close the Dialog Workflow you will now have a new Path coming out of the DW and if you browse the data your 'Message' variable will be available to you. You might want to add a Process Message to your Process or use the data passed to determine an outcome.

Now how do we send this information?

In your other Workflow you add the 'Send Complete Workflow Message'

![POC_WorkflowComplete_WEB](images\POC_WorkflowComplete_WEB.png)

You will need a Task ID that the Process is currently at.  
You then chose the Data Type the Message is expecting, see the Message Listener of the Task.  
Then the Message Data that is used in your Process.

![SendWorkflowCompleteMessage Editor](images\SendWorkflowCompleteMessageEditor.png)

You could change the Server and/or pick the Path you wish to take, you could set the "MyPath". Workflow should know which path based on the message you are sending.

You may find yourself wondering where is this data?

You can obtain it from two places.

Open **Symantec Workflow Explorer**   
(Start Menu\Programs\Symantec\Workflow Designer\Tools\ Symantec.Explorer.exe)

SymQ Explorer   
  AliasExchangeImpl   
    Lbme.workflowresponsequeue

![Symantec Workflow Explorer - SymQ Explorer - LBME.WorkflowResponseQueue](images\SymantecWorkflowExplorer-SymQExplorer-LBME.WorkflowResponseQueue.png)

You can see the TaskID, the Path, the Message, a view useful and easy way to view.

**Files on the Server**  
[Install Drive]:\program files\Symantec\Workflow\Data\MQWorkflowFileStorage\localworkflowfilestorage-workflowresponsequeue

This will be named after the TaskID.

![localworkflowfilestorage-workflowresponsequeue_0](images\localworkflowfilestorage-workflowresponsequeue_0.png)

It's not that easy to read but you can pick out the important info.

![lbemsg2](images\lbemsg2.png)

Sometimes Messages aren't consumed, they can become corrupt, if you notice this become backlogged you can move these files to a back up folder and add a few back in a couple at time until you find the corrupt one.

Now you're ready to send any message you want to your processes.

* * *

<u>Summary Explanation</u>  
You’ve create a Workflow with many Tasks.  
You wish to action these Tasks from another Workflow.  
You expose the Task (Dialog Workflow) with Message Listeners.  
‘Message Listeners’ tab  
Allow Exit Via Message Monitoring ☑  
Message Responses    LogicBase.Core.MessageExchangeResponse

Add/Edit the Object

| **Path** |  |
| --- | --- |
| Path Name | &lt;*Name*&gt; |
| **Path Data** |  |
| Payload Data Type | Text &lt;Data Type&gt; |
| Variable Name | *&lt;variable&gt;* |

* * *
 
<u><strong>Components</strong></u>
  
![Dialog Workflow Component](images\DialogWorkflowComponent.png)

| **Dialog Workflow** |
| --- |
| **Class:** LogicBase.Components.Default.Workflow.DialogWorkflowComponent |
| **Library:** LogicBase.Components.Default.dll |
| **Publisher:** Symantec Corporation |

![SendWorkflowCompleteMessage Component](images\SendWorkflowCompleteMessageComponent.png)

| Send Complete Workflow Message |
| --- |
| **Class:** LogicBase.Components.Default.Workflow.SendCompleteWorkflowMessage |
| **Library:** LogicBase.Components.Default.dll |
| **Publisher:** Symantec Corporation |

* * *
 
**Component Documentation**
  
[https://www-secure.symantec.com/connect/articles/send-complete-workflow-message](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=deaa687f-b521-4b81-bc11-5d50570157de&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
[https://www-secure.symantec.com/connect/articles/dialog-workflow](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=83135cdc-002c-4a75-8943-bcbad89b2e24&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
**Forum**
  
[https://www-secure.symantec.com/connect/forums/send-complete-workflow-message-component](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=bcf85e71-373d-4344-a098-f9e46fcbe5e9&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=digestviewer#bmbcf85e71-373d-4344-a098-f9e46fcbe5e9)
  
[https://www-secure.symantec.com/connect/forums/dialog-workflow-component](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=1773b3b3-3d4f-4dab-b632-e5343fad7130&amp;CommunityKey=492058b4-42be-43e7-991d-986f1ea9ba7f&amp;tab=digestviewer#bm1773b3b3-3d4f-4dab-b632-e5343fad7130)
  
**How To**
  
[https://support.symantec.com/en\_US/article.HOWTO62158.html](https://support.symantec.com/en_US/article.HOWTO62158.html)
  
[https://support.symantec.com/en\_US/article.HOWTO61624.html](https://support.symantec.com/en_US/article.HOWTO61624.html)
  
[https://support.symantec.com/en\_US/article.HOWTO61707.html#v23056327](https://support.symantec.com/en_US/article.HOWTO61707.html#v23056327)

* * *

[![Protirus.png](images\Protirus.png)](https://www.protirus.com/)
