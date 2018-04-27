---
title: Workflow - REST - Response Header
# tags:
#     - 
author: AlexHedley
# description: 
published: 2018-02-09
---

A question from [@epkpej](https://www.symantec.com/connect/user/epkpej) was asked on another of my Articles
  
Using the REST Generator (Response Content) in Workflow 7.6  
[https://www.symantec.com/connect/articles/using-rest-generator-response-content-workflow-76](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70c640bd-f482-4db4-b56b-3770a85df85d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
They wanted to get the "Response Header" from a POST Request.
  
Unfortunately this isn't possible using the REST Generator. It isn't exposed in the components that are generated by the tool.
  
Please vote on the Idea/Feature Request:
  
- [Workflow - Add possibility to retrieve Response Header data using REST Generator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=92aa8f35-4dda-4afd-8639-1452c5e7e666&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

As an alternative you can swap to a **Code (Script) Component**

- [https://www.symantec.com/connect/articles/code-script-component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=17b8ad10-89ff-4552-8a5b-7ab69975efaa&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- https://www.symantec.com/connect/content-external/workflow-id\_LogicBase.Components.Scripting.ScriptedComponent/workflow

Now we need to add a couple of Inputs
  
1. Inputs

- URL - Text
- HeaderValue - Text

2. Result Variable

- Result Variable Type - Text
- Result Variable Name - Header

3. Source Code
  
Namespaces

- System.Net
- System.IO

Now for the code

    HttpWebRequest request = (HttpWebRequest)WebRequest.Create(URL);
    request.Method = "GET";
    request.ServicePoint.Expect100Continue = false;
    request.ContentType = "application/json";
    
    using (WebResponse response = request.GetResponse())
    {
        using (StreamReader reader = new StreamReader(response.GetResponseStream()))
        {
            //responseString = reader.ReadToEnd();
            string header = response.Headers[HeaderValue];
            return header;
        }
    }

As you can see the URL is being used in the first line

    HttpWebRequest request = (HttpWebRequest)WebRequest.Create(URL);

And the Header in a few down

    string header = response.Headers[HeaderValue];

This makes the code a little more resuable but there is lots more you can do.

4. Test Page

Now we need an API to test
  
[https://swapi.co/](https://swapi.co/)
  
If we test it in Postman

    https://swapi.co/api/people/1

There are a number we can chose from, lets use **Etag**.

| Etag | 145c70f4eca80b4752674d42e5bf1bcf |
| --- | --- |

Now you might wish to return the collection of headers and loop through them and find the value you wish either in code or with other WF components.
  
---
  
If you do need to work with REST the Generator should cover most scenarios and I've written a set of Articles:
  
Workflow - REST Generator  
[https://www.symantec.com/connect/articles/workflow-rest-generator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0c51c681-c801-4bcb-a02d-2c9c33c76f78&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

- [Workflow - REST Generator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0c51c681-c801-4bcb-a02d-2c9c33c76f78&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Response Content) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70c640bd-f482-4db4-b56b-3770a85df85d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (PATHs) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c884d3-48d6-4f07-abfa-b6826cf35ae8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - Read Write JSON](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d8050704-5515-4e3c-8f82-0bc67a8260dc&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - REST - Response Header](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=92aa8f35-4dda-4afd-8639-1452c5e7e666&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)