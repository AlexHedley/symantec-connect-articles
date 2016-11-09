---
title: Workflow - Component - Developer Guide - Web Service
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-11-09
---

In this Article I'm going to explain how to connect to a Web Service in your component.
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=17aa2b9a-9092-40d0-afab-a6d8316de97d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70a9fde5-0d87-4b9d-a3be-0907567ffc00&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Help File](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80437c69-ccc3-47e6-a850-9cf3f301b340&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Logging](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63b72a9a-53b8-4d4b-bce3-5f0732b134d5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Inputs
    - [Checkbox](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74c56ef7-1119-40fe-9d5f-3c7a1d808d4c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [Dropdown / Combo](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=267159ac-b8e7-45b4-abe4-f85d78e30783&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2c3b3a6f-01d7-4157-a143-ba30c9edc930&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other Components
- [Creating Globals](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=cf54de06-be56-46ff-b937-148efa57eaec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Creating Project Properties](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4cfc07c5-404e-49b3-81b6-520d4ea43d5c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f3cf0097-06e7-42f3-a747-d0dff319c1e5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Working with a Web Service (this)

We did this in the following [Asset Ownership](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=7e9fe111-ca99-4880-adee-6532190f0eea&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) Component.
  
We will add a reference to an ![smp.png](images\smp.png) SMP Web Service.
  
Build a basic component like we have in previous Articles.
  
How to: Add, Update, or Remove a Service Reference  
[https://msdn.microsoft.com/en-us/library/bb628652.aspx](https://msdn.microsoft.com/en-us/library/bb628652.aspx)

> **Adding a Service Reference**  
> 	  
> 	To add a reference to an external service  
> 	  
> 	1. In **Solution Explorer**, right-click the name of the project that you want to add the service to, and then click **Add Service Reference**.  
> 	The **Add Service Reference** dialog box appears.  
> 	  
> 	2. In the **Address** box, enter the URL for the service, and then click **Go** to search for the service. If the service implements username/password security, you may be prompted for a username and password.  
> 	  
> 	Note  
> 	You should only reference services from a trusted source. Adding references from an untrusted source may compromise security.  
> 	  
> 	Note  
> 	You can also select the URL from a drop-down list that stores the last 15 URLs where valid service metadata was found.  
> 	  
> 	A progress bar is displayed while the search is being performed. You can stop the search at any time by clicking **Stop**.  
> 	  
> 	3. In the **Service** list, expand the node for the service that you want to use and select a service contract.  
> 	  
> 	4. In the **Namespace** box, enter the namespace that you want to use for the reference.  
> 	  
> 	5. Click **OK** to add the reference to the project.  
> 	A service client (proxy) is generated, and metadata describing the service is added to the app.config file.

For the Address we will use the Resource Model

> http://localhost/altiris/nswebservice/resourcemodel.asmx

Replace localhost with the name of your SMP Server.
  
You will have a Using statement in your class that references this new Service.

    using Protirus.AssetOwner.Service.ResourceModelService;

In our Run method we can now connect to our Service and perform actions, in this case SaveDataClass

> http://localhost/altiris/nswebservice/resourcemodel.asmx?op=SaveDataClass

Declare a client to work with.

    public override void Run(IData data)
    {
        using (var client = new ResourceModelService.ResourceModelService())
        {
            client.Timeout = Timeout.GetValue<int>(data);
            client.Url = Url.GetValue<string>(data);
            client.Credentials = CredentialCache.DefaultCredentials;
            
            //Do Stuff
            
            client.SaveDataClass(asset, new[] { dcd });
        }
    }

Here I've set up inputs to the Component to pass properties I don't want to hardwire like Timeout and URL.
  
I could have done the same for Credentials but in this case I'm just going to use the DefaultCredentials that are taken from the ApplicationPool.

You could look in the help file for other methods and services you could interact with

> E:\Program Files\Altiris\Altiris ASDK\Help\ASDK7.6.chm

![Protirus](images\Protirus.png)
