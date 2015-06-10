---
title: Workflow - Cookie (using code) - Web App
# tags:
#     - 
author: AlexHedley
# description: 
published: 2015-06-05
---

In this article I will show you how to create and retrieve Cookies in the ![App.png](images\App.png)Web App Project Type
  
The Cookie components aren't available in the Web App Project type.

In a Forms (Web) Project they are under
  
![Components.png](images\Components.png) Input Output
  
![Components.png](images\Components.png) Web Cookies
  
![Clear Cookie.png](images\ClearCookie.png) Clear Cookie
  
![Get From Cookie.png](images\GetFromCookie.png) Get From Cookie
  
![Save To Cookie.png](images\SaveToCookie.png) Save To Cookie
  
**Class:** LogicBase.Components.Default.IO.ClearCookie  
**Library:** LogicBase.Components.Default.dll  
**Publisher:** Symantec Corporation
  
Some of the Default.IO is available but not these.
  
The Dialog Model type is not the same as the ![Forms (Web).png](images\Forms%2520%2528Web%2529.png) Forms (Web) Project Type in a Web Application Project.

Since we can't use the components we will have to use another method.
  
Let's go to the trusty Scripting Component.
  
Add in the Library (**LogicBase.Components.Scripting.dll**) to your Project
  
Find the ![Code (Script) Component.png](images\Code%2520%2528Script%2529%2520Component.png) Code (Script) Component

<u>Set Cookie</u>
  
We will create the 'Set' Component first, this will have 3 parameters:
  
CookieName - Text
  
CookieValue - Text
  
ExpiresMinutes - Number (integer)
  
No **return** type
  
In the namespaces add

    System.Web

<font color="#008000"><font><span class="sc0"><span class="ms-rteThemeFontFace-1">//Cookie Class</span><br class="ms-rteThemeFontFace-1"><span class="ms-rteThemeFontFace-1">//</span></span></font></font>[https://msdn.microsoft.com/en-us/library/system.web.httpcookie(v=vs.71).aspx](https://msdn.microsoft.com/en-us/library/system.web.httpcookie%28v=vs.71%29.aspx)

System.Object  
   System.Web.HttpCookie  
Namespace: System.Web
  
C# code:
```csharp
    HttpCookie myCookie = new HttpCookie(CookieName);
    DateTime now = DateTime.Now;
    
    // Set the cookie value.
    myCookie.Value = CookieValue;
    // Set the cookie expiration date.
    myCookie.Expires = now.AddMinutes(ExpiresMinutes);
    
    // Add the cookie.
    HttpContext.Current.Response.Cookies.Add(myCookie);
```

If you read the MS Articles below you won't see **HttpContext.Current.**
  
This is needed for it to work in Workflow.

<u>Get Cookie</u>
  
For the Get Cookie we need an input of
  
CookieName - Text
  
- 'Result variable type' of **Text**
- 'Result variable name' of **Cookie**

Again add the namespace of **System.Web**
  
Then the following C# code:

    HttpCookie myCookie = new HttpCookie(CookieName);
    myCookie = HttpContext.Current.Request.Cookies[CookieName];
    
    return myCookie.Value;

And now you can use this throughout your project.

* * *
 
To view the Cookies in IE.
  
F12 - Cache | View Cookie Information
  
* * *

<u>Links</u>
  
**Connect Forum**
  
[https://www-secure.symantec.com/connect/forums/need-tutorial-save-cookie-component-usage](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=7b7bd87c-0355-4c18-9553-87cbb6e7ee99&amp;CommunityKey=492058b4-42be-43e7-991d-986f1ea9ba7f&amp;tab=digestviewer#bm7b7bd87c-0355-4c18-9553-87cbb6e7ee99)
  
**MS**
  
<font class="ms-rteThemeFontFace-1"><span class="sc2 ms-rteThemeFontFace-1"><font color="#008000">// Code: Writing a Cookie (Visual C#)</font></span></font>  
[https://msdn.microsoft.com/en-us/library/aa287547%28v=vs.71%29.aspx](https://msdn.microsoft.com/en-us/library/aa287547%28v=vs.71%29.aspx)
  
<font class="ms-rteThemeFontFace-1"><span class="sc2 ms-rteThemeFontFace-1"><font color="#008000">// Code: Reading a Cookie (Visual C#)</font></span></font>  
[https://msdn.microsoft.com/en-us/library/aa287533(v=vs.71).aspx](https://msdn.microsoft.com/en-us/library/aa287533%28v=vs.71%29.aspx)
  
// HttpCookie Properties  
[https://msdn.microsoft.com/en-us/library/System.Web.HttpCookie\_properties(v=vs.110).aspx](https://msdn.microsoft.com/en-us/library/System.Web.HttpCookie_properties%28v=vs.110%29.aspx)

* * *

[![Protirus.png](images\Protirus.png)](http://www.protirus.com/)
