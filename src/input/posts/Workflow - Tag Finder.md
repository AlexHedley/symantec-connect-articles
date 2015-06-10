---
title: Workflow - Tag Finder
# tags:
#     - 
author: AlexHedley
# description: 
published: 2015-06-10
---

In this article I will show you how to use the 'Extract Text By Pattern' component in the ![Forms (Web).png](images\Forms%2520%2528Web%2529.png) Forms (Web) Project Type

If you have a need to find a value within string you can use the following:
  
![Extract Text By Pattern.png](images\ExtractTextByPattern.png)

| Extract Text By Pattern |
| --- |
| Class: LogicBase.Components.Default.Process.RegEx.ExtractTextByPattern |
| Library: LogicBase.Components.Default.dll |
| Publisher: Symantec Corporation |

[https://www-secure.symantec.com/connect/articles/extract-text-pattern](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2a1808cb-0dfe-4bc9-9a63-6d5aeb71642e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

Example:
  
{{##\_Retry\_Tag:25}}

| BEGIN | TAG | END |
| --- | --- | --- |
| {{##\_Retry\_Tag: | 25 | }} |

![Tag Finder Workflow.png](images\TagFinderWorkflow.png)

This will find the first occurrence.

![Tag Finder Web (1).png](images\Tag%2520Finder%2520Web%2520%25281%2529.png) ![Tag Finder Web (2).png](images\Tag%2520Finder%2520Web%2520%25282%2529.png)

I created a variable for the Start and End Tag and passed it the data I needed to search in.

![Extract Text By Pattern - Configuration (1).png](images\Extract%2520Text%2520By%2520Pattern%2520-%2520Configuration%2520%25281%2529.png)

If you know the length of the tag, say it’s a GUID you could untick ‘Use Pattern For End’ and hardcode the length. This is similar to how the Email Monitor searches for {IID=} updates in Tickets.

![Extract Text By Pattern - Configuration (2).png](images\Extract%2520Text%2520By%2520Pattern%2520-%2520Configuration%2520%25282%2529.png)

If it doesn’t find a match it continues.
  
You could then use a ‘Get Number from String’ to check it is a Number or do a Length check to be sure.  

* * *

<u><strong>Forum</strong></u>

[https://www-secure.symantec.com/connect/forums/extracting-text-different-variable-email-body](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=9ca4fc07-c285-4dbe-90fd-be7f1938e673&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=digestviewer#bm9ca4fc07-c285-4dbe-90fd-be7f1938e673)
  
[https://www-secure.symantec.com/connect/forums/string-parsing](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=1346a873-3853-4d9c-a70a-8580b7dc813a&amp;CommunityKey=492058b4-42be-43e7-991d-986f1ea9ba7f&amp;tab=digestviewer#bm1346a873-3853-4d9c-a70a-8580b7dc813a)
  
[https://www-secure.symantec.com/connect/forums/parsing-text-email](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=6aa0b251-3b25-4107-a0cb-1de26466791f&amp;CommunityKey=492058b4-42be-43e7-991d-986f1ea9ba7f&amp;tab=digestviewer#bm6aa0b251-3b25-4107-a0cb-1de26466791f)

* * *

[![Protirus](images\Protirus.png)](http://www.protirus.com/)
