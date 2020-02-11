---
title: Workflow - Component - Developer Guide - Inputs - Checkbox
tags:
    - Workflow
    - Component
    - Developer Guide
author: AlexHedley
# description: 
# articleId: 
published: 2016-11-09
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-component-developer-gu-2?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article I'm going to explain how to add a Input of a Checkbox to gather more configuration from the User.
  
Table of Contents[​](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=17aa2b9a-9092-40d0-afab-a6d8316de97d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70a9fde5-0d87-4b9d-a3be-0907567ffc00&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Help File](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80437c69-ccc3-47e6-a850-9cf3f301b340&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Logging](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63b72a9a-53b8-4d4b-bce3-5f0732b134d5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Inputs
    - [Checkbox](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74c56ef7-1119-40fe-9d5f-3c7a1d808d4c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
    - [Dropdown / Combo](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=267159ac-b8e7-45b4-abe4-f85d78e30783&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2c3b3a6f-01d7-4157-a143-ba30c9edc930&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other Components
- [Creating Globals](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=cf54de06-be56-46ff-b937-148efa57eaec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Creating Project Properties](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4cfc07c5-404e-49b3-81b6-520d4ea43d5c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f3cf0097-06e7-42f3-a747-d0dff319c1e5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with a Web Service](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=26368883-708b-4432-999b-7064f2f25794&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

Currently our Component Concatenates two strings together with a space.

    public override void Run(IData data)
    {
        data[_variableName] = _string1.GetValue<String>(data) + " " + _string2.GetValue<String>(data);
    }

It would be nice to give the user the option to say whether they would like a space or not.
  
A Checkbox would be a good choice here.
  
First we can declare a variable to hold our choice.
  
Since it's either going to be Yes or No we can use a Boolean.

    private bool _addSpace;

Next to create the Getter and Setter

    [VariableType(typeof(Boolean), false), 
      PropertyIndex(3), 
      DisplayName("Add Space"), 
      Category("Configuration"), 
      ComponentDescription("Add a space between the two strings")
    ]
    public bool AddSpace
    {
        get
        {
            return this._addSpace;
        }
        set
        {
            this._addSpace = value;
            ((AbstractOrchestrationComponent)this).IsValid(true);
        }
    }

As we are setting the VariableType this can be used in the Component back in Workflow.
  
Now to add the necessary code to the previous methods.
  
**ReadFromStream**

    public override void ReadFromStream(ObjectReadStream info) {
        ...
        this._addSpace = (bool)info.GetValue("_addSpace", typeof(bool), (object)false);
    }

**WriteToStream**

    public override void WriteToStream(ObjectWriteStream info) {
        ...
        info.AddValue("_addSpace", _addSpace);
    }

And finally we can use it in our Run method:

    public override void Run(IData data) {
        bool space = this._addSpace;
        //if (_addSpace.GetValue<bool>(data)) {
        if (space) {
            data[_variableName] = _string1.GetValue<String>(data) + " " + _string2.GetValue<String>(data);
        } else {
            data[_variableName] = _string1.GetValue<String>(data) + _string2.GetValue<String>(data);
        }
    }

[![Protirus.png](images\Protirus.png)](https://www.protirus.com/)
