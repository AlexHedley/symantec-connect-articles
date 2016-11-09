---
title: Workflow - Component - Developer Guide - Inspecting
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-11-09
---

In this Article I'm going to explain how to inspect other Components.
  
Table of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=17aa2b9a-9092-40d0-afab-a6d8316de97d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70a9fde5-0d87-4b9d-a3be-0907567ffc00&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Help File](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80437c69-ccc3-47e6-a850-9cf3f301b340&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Logging](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63b72a9a-53b8-4d4b-bce3-5f0732b134d5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Inputs
    - [Checkbox](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74c56ef7-1119-40fe-9d5f-3c7a1d808d4c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [Dropdown / Combo](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=267159ac-b8e7-45b4-abe4-f85d78e30783&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2c3b3a6f-01d7-4157-a143-ba30c9edc930&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other Components (this)
- [Creating Globals](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=cf54de06-be56-46ff-b937-148efa57eaec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Creating Project Properties](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4cfc07c5-404e-49b3-81b6-520d4ea43d5c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f3cf0097-06e7-42f3-a747-d0dff319c1e5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with a Web Service](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=26368883-708b-4432-999b-7064f2f25794&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

This is a great way to learn how something is done if there isn't documentation or guides you can follow. Dissecting code is a useful skill to obtain.
  
There are a number of decompilers available, two of which I use are

- ![dotPeek (S).png](images\dotPeekS.png) [dotPeek](https://www.jetbrains.com/decompiler/) from ![JetBrains (S).png](images\JetBrains%2520%2528S%2529.png) [JetBrains](https://www.jetbrains.com/)
- ![JustDecompile.png](images\JustDecompile.png) [JustDecompile](http://www.telerik.com/products/decompiler.aspx) from [Telerik](http://www.telerik.com/)
- An SMP staff member told me about [ILSpy](http://ilspy.net/), I've not tried it yet but useful to add to the list.

Lately I've been favouring JustDecompile over dotPeek but try them out and see which you prefer, or comment below on any others you use and your experience.
  
For an example we will look at the **Add New Data Element**, this has a checkbox for Is Array.
  
The Component Class Name is

    LogicBase.Components.Default.Process.InsertDataComponent

So we need to find this DLL.
  
Open the WF install location and search for

    LogicBase.Components.Default*.dll

And it's in

    E:\Program Files\Symantec\Workflow\Shared\Components

Copy this to your dev folder. I like to create a folder with WF version numbers.
  
We need to find the 'InsertDataComponent' under 'Process'.
  
![JustDecompile - LogicBase.Components.Default](images\JustDecompile-LogicBase.Components.Default.png)
  
Now look for the IsArray information.
  
So we have a declaration.

    private bool _array;

Next the Getter/Setter

    [HideIfPropertyNull("DataType")]
    [PropertyIndex(2)]
    [RefreshProperties(RefreshProperties.All)]
    public bool IsArray
    {
        get
        {
            return this._array;
        }
        set
        {
            if (this._array != value)
            {
                this._array = value;
                this.CreateValue();
                this.IsValid(true);
            }
        }
    }

Then the methods
  
**ReadFromStream**

    this._array = info.GetBoolean("isArray");

If we compare this to how I did it in the Checkbox article, this way is more succinct.

    this._addSpace = (bool)info.GetValue("_addSpace", typeof(bool), (object)false);

**WriteToStream**

    info.AddValue("isArray", this._array);

We can take what we've learnt here and use it in future components.

![Protirus.png](images\Protirus.png)
