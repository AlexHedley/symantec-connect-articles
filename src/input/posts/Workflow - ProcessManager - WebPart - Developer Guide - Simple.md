---
title: Workflow - ProcessManager - WebPart - Developer Guide - Simple
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
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-processmanager-webpart-5?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I'm going to explain how to create a simple WebPart and display some data on the Process Page inkeeping with the PM theme.
  
Articles
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=aa0478d7-5f5a-4be4-8369-4c74f963deeb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=36a9f5ee-ab0b-42e7-a75e-590ba4f256ec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a3b54e8a-7492-4397-8512-8828defe25a7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74973282-5d27-4b12-a0d3-9ad29d38a2ce&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c1b3103c-afad-45f8-9f17-244fff752121&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other WebParts
- [Controls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c20f9b40-20f8-4693-937a-7ca431c4d7ce&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) a WebPart
- WF/PM [Connection String](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=849d26ef-084e-426b-a064-fbb86730e6b8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Connecting to [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=77434eb5-7ee1-4bb4-bef1-ef566cce61fb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to retrieve data

- - -
  
If you open the '**Symantec™ Workflow 8.1 Component Developer Guide**' ([https://support.symantec.com/en\_US/article.DOC9626.html](https://support.symantec.com/en_US/article.DOC9626.html)) and navigate to

- Chapter 9
    - Extending Workflow Process Manager .................................... 190
        - About writing webparts for Process Manager ............... 198
        - Writing webparts for Process Manager ......................... 198

Unfortunately there are only a couple of pages on how to create a Webpart.
  
---
  
### **About writing webparts for Process Manager**
  
Process Manager is an ASP.NET 4.0 compliant portal (ASP.NET webpart host). You can host any ASP.NET 4.0 webparts in it.
  
Webparts are part of the ASP.NET 4.0 specification. Process Manager hosts basic ASP.NET 4.0 webparts.
  
If you are unfamiliar with ASP.NET webparts, you can find help in an abundance of online articles. We recommend familiarizing yourself before attempting to build ASP.NET 4.0 webparts. Because Process Manager is a compliant webpart host, nothing special has to be specified to build controls that will reside in Process Manager.
  
Process Manager has an integrated catalog mechanism, so, when you have finished building your webpart, you can load it into the Process Manager using the integrated plugin loading mechanism, then register it with the webpart catalog.
  
See “Uploading a plugin into Process Manager” on page 197.
  
**Writing webparts for Process Manager**
  
**Creating a webpart**
  
For creating a new webpart, you can use following code sample:

    using System;
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    
    namespace Sample
    {
       public class SampleWebPart : WebPart
       {
           [Personalizable, WebBrowsable]
           public String ContentText { get; set; }
           protected override void CreateChildControls()
           {
               Controls.Add(new Label {
                   Text = ContentText
               }); 
           }
       }
    }

**Accessing session ID**
  
When your webpart requires access to the session ID, you have two options: include a separate login on the webpart, or implement the functionality of Logicbase.ensemble.core so the webpart can retrieve the session ID.

    namespace LogicBase.Ensemble.Core
    {
        public class EnsembleHelper
        {
            ensembleHelper()
            {
            }
    
            public string EnsembleUrl
            {
                get
                {
                    return HttpContext.Current.Request.ApplicationPath;
                }
            }
    
            public static string CurrentSessionID
            {
                get
                {
                    if (HttpContext.Current.User is AbstractEnsemblePrincipal)
                        return (HttpContext.Current.User as AbstractEnsemblePrincipal).SessionID;
                    else
                        return null;
                }
            }
    
            static EnsembleHelper helper = new EnsembleHelper();
            public static EnsembleHelper GetInstance()
            {
                return helper;
            }
        }
    }

All access to Process Manager service functionality should come through web references. These web references enable the webparts to be hosted in other portals (like SharePoint).
  
The URL in the EnsembleURL property is the base URL to Process Manager. If you want to access docman, use this URL + "/docman/docman.asmx".
  
The CurrentSessionID represents the current user and is passed to the Process Manager services (as most services require the session as a parameter).
  
---
  
Once you've added the '*CreateChildControls()*' build your component.
  
Check the output path

    E:\Dev\WF\Protirus.ProcessManager.WebParts\..\bin\Debug\Protirus.ProcessManager.WebParts.dll

Copy the dll and add it to a folder on your WF Server.
  
You could create a Build Rule in VS to copy this to a holding folder ready for upload.
  
- - -
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
