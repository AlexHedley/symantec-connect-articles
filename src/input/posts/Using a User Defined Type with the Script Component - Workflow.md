---
title: Using a User Defined Type with the Script Component - Workflow
# tags:
#     - 
author: AlexHedley
# description: 
published: 2015-05-21
---

In this Article I will show you how to use a custom data type within the Script Component.
  
So you've created a "User Defined Type" from the **Authoring** section in a ![Int.png](images\article-3419801-files_Int.png) Workflow Integration Component
  
![Create Generator (UDT).png](images\Create%2520Generator%2520%2528UDT%2529.png)
  
![Property.png](images\article-3419801-files_Property.png) UserDefinedType  
  ![Property (2).png](images\Property%2520%25282%2529.png) TextProperty (Text)  
  ![Property (2).png](images\Property%2520%25282%2529.png) IntegerProperty (Number (integer))
  
![1. Type Designer.png](images\article-3419801-files_1.+Type+Designer.png)

![2. Settings.png](images\article-3419801-files_2.+Settings.png)
  
Make sure to note the Namespace:

| Generated.POC\_Scripting\_INT |
| --- |

![C# Generators.png](images\C%2523%2520Generators.png) Generators  
  ![C#.png](images\C%2523.png) UserDefinedType  
    ![Property.png](images\article-3419801-files_Property.png) UserDefinedType
  
![Generators Management (UDT) (2).png](images\Generators%2520Management%2520%2528UDT%2529%2520%25282%2529.png)

Now create a Workflow.
  
Use an ![Data_Add.png](images\article-3419801-files_Data_Add.png) Add Data Element and create a element of your new Data Type.

| DataType | UserDefinedType |
| --- | --- |
| Variable Name | UserDefinedType |

Add some values

| Integer Property | 1 |
| --- | --- |
| Text Property | Alex Hedley |

Search for a ![Code (Script) Component.png](images\Code%2520%2528Script%2529%2520Component.png) Script Component. The Library may not have been added so should show in the ![Search.png](images\article-3419801-files_Search.png) Unloaded Libraries section.
  
You could also add "LogicBase.Components.Scripting.dll" in the Libraries tab of the Project section.
  
Join this to your previous component.
  
Double click on this to start up the Wizard.
  
Add your variable name and choose it's Type:
  
![Scripted Component Wizard - 1. Input Parameters.png](images\article-3419801-files_Scripted+Component+Wizard+-+1.+Input+Parameters.png)
  
Click on **<u>E</u>dit Parameter Mappings**.
  
Select the Parameter then choose the Data Source:
  
![End Component Mapping.png](images\article-3419801-files_End+Component+Mapping.png)
  
Click OK then Next.
  
Choose your "Result <u>v</u>ariable type" and "<u>R</u>esult variable name":
  
![Scripted Component Wizard - 2. Result Variable.png](images\article-3419801-files_Scripted+Component+Wizard+-+2.+Result+Variable.png)
  
Now to the Source Code.
  
You can choose which one you prefer. (C#, VB.NET, JScript)
  
Here is where you need to add your previous namespace.

| Using namespaces (one per line): |
| --- |
| System  <br>			Generated.Generated.POC\_Scripting\_INT |

Now you can use your Type in the code:

| return UserDefinedType[0].TextProperty; |
| --- |

![Scripted Component Wizard - 3. Source Code.png](images\article-3419801-files_Scripted+Component+Wizard+-+3.+Source+Code.png)
  
There is a handy test you can perform at the end to check it is working.
  
![Scripted Component Wizard - 4. Test Page.png](images\article-3419801-files_Scripted+Component+Wizard+-+4.+Test+Page.png)
  
Obviously you can do more complex things than just getting a single Property but this explains the initial set up.

* * *

![Protirus.png](images\article-3419801-files_Protirus.png)
