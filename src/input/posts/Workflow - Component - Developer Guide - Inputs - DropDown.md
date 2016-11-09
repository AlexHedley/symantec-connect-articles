---
title: Workflow - Component - Developer Guide - Inputs - DropDown
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-11-09
---

In this Article I'm going to explain how to add a Input of a Dropdown / Combo to gather more configuration from the User.
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=17aa2b9a-9092-40d0-afab-a6d8316de97d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70a9fde5-0d87-4b9d-a3be-0907567ffc00&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Help File](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80437c69-ccc3-47e6-a850-9cf3f301b340&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Logging](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63b72a9a-53b8-4d4b-bce3-5f0732b134d5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Inputs
    - [Checkbox](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74c56ef7-1119-40fe-9d5f-3c7a1d808d4c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [Dropdown / Combo](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=267159ac-b8e7-45b4-abe4-f85d78e30783&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2c3b3a6f-01d7-4157-a143-ba30c9edc930&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other Components
- [Creating Globals](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=cf54de06-be56-46ff-b937-148efa57eaec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Creating Project Properties](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4cfc07c5-404e-49b3-81b6-520d4ea43d5c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f3cf0097-06e7-42f3-a747-d0dff319c1e5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with a Web Service](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=26368883-708b-4432-999b-7064f2f25794&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

- - -
  
When using the Pad Text component I noticed it used a DropDown to allow a choice of options. This could be useful in a Component I was creating so I thought I'd investigate how this was configured.

| ![transform](images\transform.png)**Pad Text** |
| --- |
| *Class:*LogicBase.Components.Default.Process.PadText |
| *Library:*LogicBase.Components.Default.dll |

![Components - PadText - Configuration](images\Components-PadText-Configuration.png)
  
If you've completed the [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2c3b3a6f-01d7-4157-a143-ba30c9edc930&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) article you will already have this DLL ready, re-open it in your Decompiler of choice.
  
Find 'PadText' under 'Process'.
  
We need to find the **PadType** configuration.
  
First the Declaration

    private PadText.PadTypeEnum _padType;

This is new, it's using an Enum. This is a much better way then an Array of Strings.

    public enum PadTypeEnum
    {
        Left,
        Right
    }

**ReadFromStream**

    public override void ReadFromStream(ObjectReadStream info)
    {
        ...
        this._padType = (PadText.PadTypeEnum)info.GetValue("padType", typeof(PadText.PadTypeEnum));
        ...
    }

**WriteToStream**

    public override void WriteToStream(ObjectWriteStream info)
    {
        ...
        info.AddValue("padType", this._padType);
        ...
    }

Run

    public override void Run(IData data)
    {
        ...
        char value = (char)this._padChar.GetValue(data);
        switch (this._padType)
        {
            case PadText.PadTypeEnum.Left:
            {
                str1 = str1.PadLeft(this._padLength, value);
                break;
            }
            case PadText.PadTypeEnum.Right:
            {
                str1 = str1.PadRight(this._padLength, value);
                break;
            }
        }
        ...
    }

A switch statement is used to consider each choice made.
  
If we want to use a drop down in our own components we can create our own Enum and use that instead.
  
![Protirus](images\Protirus.png)
