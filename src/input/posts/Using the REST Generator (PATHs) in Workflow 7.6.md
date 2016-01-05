---
title: Using the REST Generator (PATHs) in Workflow 7.6
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-01-05
---

In this Article I will explain how to use the REST Generator (PATHs) within [Workflow](http://www.symantec.com/connect/workflow-servicedesk) 7.6.
  
Follow up articles
  
- [Workflow - REST Generator](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=0c51c681-c801-4bcb-a02d-2c9c33c76f78&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Response Content) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70c640bd-f482-4db4-b56b-3770a85df85d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (PATHs) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c884d3-48d6-4f07-abfa-b6826cf35ae8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - Read Write JSON](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d8050704-5515-4e3c-8f82-0bc67a8260dc&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Workflow - REST - Response Header](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=92aa8f35-4dda-4afd-8639-1452c5e7e666&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

New to me in build Symantec.Workflow.Setup.7.6.4383.**504** (think it was .479 but I'd advise getting the last build) the REST Generator has been updated to allow multiple paths from the response content.

This is a great addition as what if your request fails or returns a StatusCode other than 200, this needs to be handled differently, you won't get the same data type returned,

By default this creates a PATH of 200-299. As of writing there is no way to delete this path, which I believe is incorrect, what about a PUT request that returns a 301.

The 200-299 PATH requires an output type, if none is selected you get the following error:
  
"Error validating info - ResponseContent on component *x*"

If you don't need one you could just set it to text, it's never going to go down that path, so just have a demo component going to end?

Let's use our trusty Star Wars API to see it in action:
  
[http://swapi.co/](http://swapi.co/)

Fill in the usual content and get the Response Content using "Create the Request" option.
  
Now click on "**Paths...**" to see the new path.

![REST Generator - 2 Components - Paths](images\RESTGenerator-2Components-Paths.png)

You can create multiple paths, make sure OK has a Response, this defaults to your response from the previous screen.

You could have individual ones or you can comma separate them if they return the same data type,

![REST Generator - 2 Components - Paths - Multiple](images\RESTGenerator-2Components-Paths-Multiple.png)

I would advise either a path for each OR a range for the same, don't have both, it is likely to pick the first code it matches.

For the Name don't put spaces, or you get the following error
  
![REST Generator - 2 Components - Paths - Compiler Errors](images\article-3554101-files_REST+Generator+-+2+Components+-+Paths+-+Compiler+Errors.png)

It would be nice if the Generator warned you about this when creating a new Path name, as this is when you compile and don't know this is the reason.

Then back in Workflow we have the component with all the Paths,

![REST - Workflow - Paths - Multiple](images\REST-Workflow-Paths-Multiple.png)

You have the data available to you given the chosen path, and you can deal with it accordingly,

**Ideas**

- [Show StatusCode in Path Name](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c884d3-48d6-4f07-abfa-b6826cf35ae8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

Other articles

- [Using the REST Generator in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e7c91120-a123-4625-979d-1734c77e75d7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (GET) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a2dcdd55-e5af-4a79-98fb-20316278b763&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Headers) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9436681a-270e-439f-ae3d-3b20b9a25341&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (POST) in Workflow 7.6 with Mobility Suite](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f63d5608-8e51-43fb-a09e-c38ebca50cff&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Using the REST Generator (Response Content) in Workflow 7.6](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70c640bd-f482-4db4-b56b-3770a85df85d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

[![Protirus](images\Protirus.png)](http://protirus.com/)
