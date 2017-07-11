---
title: Workflow - ProcessManager - WebPart - Developer Guide - Controls
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-07-11
---

In this Article I'm going to explain how to add Controls to your WebPart.
  
Articles
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=aa0478d7-5f5a-4be4-8369-4c74f963deeb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=36a9f5ee-ab0b-42e7-a75e-590ba4f256ec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a3b54e8a-7492-4397-8512-8828defe25a7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74973282-5d27-4b12-a0d3-9ad29d38a2ce&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c1b3103c-afad-45f8-9f17-244fff752121&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other WebParts
- [Controls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c20f9b40-20f8-4693-937a-7ca431c4d7ce&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) a WebPart
- WF/PM [Connection String](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=849d26ef-084e-426b-a064-fbb86730e6b8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Connecting to [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=77434eb5-7ee1-4bb4-bef1-ef566cce61fb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to retrieve data

- - -
  
In previous Articles we've created and deployed a basic WebPart but it doesn't do anything yet.
  
In this Article we will start showing some information on the WebPart.
  
Controls:

- Label
- Input
- Table - shown in the [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) Article
- Literal

---
  
**Label**
  
As we found out before we need to add code to the *CreateChildControls()* method.
  
We can use *WebControls* / *HtmlControls* Assemblies to do this.

    protected override void CreateChildControls()
    {
        Controls.Add(new Label {
            Text = "Hello"
        }); 
    }

But what information can we show?
  
We could show the *UserName* of the logged in User.
  
We could show the *ReportSessionID* of the Ticket we have open.

    string UserName = this.Context.User.Identity.Name;
    Controls.Add(new Label { Text = UserName });
    
    string TrackingId = this.Context.Request["ReportSessionID"];
    Controls.Add(new Label { Text = TrackingId });

This would look like the following.
  
![ProcessManager_ProcessViewPage_WebPart_Example](images\ProcessManager_ProcessViewPage_WebPart_Example.png)
  
---
  
**Input**
  
What if you want to have the User be able to change the Data shown on the WebPart when they edit it?
  
We saw this in the [Simple](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a3b54e8a-7492-4397-8512-8828defe25a7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) Article.
  
If we set some Attributes against a Property we can configure it to do so.

    [Personalizable, WebBrowsable]
    public String ContentText { get; set; }

    [Personalizable]

Its value will be persisted.

    [WebBrowsable]

The end user will be able to modify it in the editor component.

Now if you edit the Control an Input will be available to add the String you wish to display.

![ProcessManager_ProcessViewPage_WebPart](images\ProcessManager_ProcessViewPage_WebPart.png)

---

**Table**

Shown in the [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) Article

---

**Literal**

To add a break between controls you can use the 'Literal' Control and pass in any HTML.

    Controls.Add(new LiteralControl("<br />"));

---

More Controls to be added soon...

- - -

[![Protirus](images\Protirus.png)](https://www.protirus.com/)
