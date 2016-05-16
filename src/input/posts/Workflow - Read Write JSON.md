---
title: Workflow - Read Write JSON
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-05-16
---

There was a question on the Forums from @[Lark](https://www-secure.symantec.com/connect/user/lark) about Reading/Writing JSON in Workflow
  
[https://www-secure.symantec.com/connect/forums/write-object-json-and-read-object-json](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=47441a32-16c6-41ef-823f-db8640f68b0d&amp;CommunityKey=492058b4-42be-43e7-991d-986f1ea9ba7f&amp;tab=digestviewer#bm47441a32-16c6-41ef-823f-db8640f68b0d)
  
I made a couple of suggestions on the post but thought it would be useful as a article.
  
- [Workflow - REST Generator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0c51c681-c801-4bcb-a02d-2c9c33c76f78&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Response Content) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70c640bd-f482-4db4-b56b-3770a85df85d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (PATHs) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c884d3-48d6-4f07-abfa-b6826cf35ae8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - Read Write JSON](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d8050704-5515-4e3c-8f82-0bc67a8260dc&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - REST - Response Header](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=92aa8f35-4dda-4afd-8639-1452c5e7e666&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

Say you have some local JSON you need to work with, the REST Generator can still be of use to turn this into an Object to work with in Workflow.
  
I explained about the new feature they added in a later release that allowed "Create From Sample"

- [Using the REST Generator (Response Content) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70c640bd-f482-4db4-b56b-3770a85df85d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

A couple of things to note here, on the first page of the Generator this asks for a **Namespace** (Protirus), take a note of it as we will need to work with this later.
  
You will need to add a URL here too but it won't be used.
  
Grab the JSON you are wanting to work with and paste it here.
  
![REST Generator - Create From Sample](images\RESTGenerator-CreateFromSample.png)
  
Depending on the name of your Method you will get the Data Type (DT) called this, click on **Edit Type** and rename if necessary.
  
![REST Generator - Create From Sample - Data Type](images\RESTGenerator-CreateFromSample-DataType.png)
  
Close and compile this.
  
Now add this Library to your Workflow Project.
  
Also add the

- Newtonsoft.Json.dll
    - E:\Program Files\Symantec\Workflow\Shared\lib\

There is an issue outstanding with that not being used throughout workflow - [Forum](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=5571b718-8919-4367-8eea-1548ec0cad29&amp;CommunityKey=492058b4-42be-43e7-991d-986f1ea9ba7f&amp;tab=digestviewer#bm5571b718-8919-4367-8eea-1548ec0cad29)
  
In the Workflow use an **Add Data Element** (LogicBase.Components.Default.Process.InsertDataComponent) and set it to your new Date Type (DT).
  
![JSON Data Type.png](images\JSONDataType.png)
  
Then a **Read File** (LogicBase.Components.Default.IO.ReadFile) to locate the JSON file you want to read.
  
A **ByteArray To Text** (LogicBase.Components.Default.EncodingComponents.ByteArrayToText)****to convert the .Contents[] of the Read File.
  
You now have a String you can work with.
  
Add a **Script Component** (LogicBase.Components.Scripting.ScriptedComponent)
  
Map your variable to the input.
  
Set your Result variable type to "Protirus.User"
  
Add in the Namespaces you saved earlier

    Newtonsoft.Json
    Protirus

Now add your code to deserialise the string/json to your new object

    Protirus.User u = JsonConvert.DeserializeObject<Protirus.User>(json);
    return u;

To do the reverse is a little simplier.
  
You already have your Data Type (DT), that you've retrieved and mapped in.
  
Grab a scripting component
  
Add the Namespace

    System.Web.Script.Serialization

Pass it in as an input of your DataType (DT) (obj) and return a string. obj is the name of the input, this could be anything you name it.

    var json = new JavaScriptSerializer().Serialize(obj);
    return json;

Then you can write to a file or use however you want.
  
[![Protirus](images\Protirus.png)](https://protirus.com/)
