---
title: ServiceDesk - API - Configuring
tags:
    - ServiceDesk
    - API
author: AlexHedley
# description: 
# articleId: 
published: 2018-10-01
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-api-configuring?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

- [Index](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=d54b726c-cf91-42f3-a0fe-436a3d559c14&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Configuring](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=becb0e82-72b6-40da-ad93-e5f3aad8afcd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Extending](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=6d994fd8-1056-49a7-8228-488a03300d41&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Endpoints
    - [Authorization](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=30d60bd5-f273-41b4-a1ff-67a40becd4dd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [ChangeRequest](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=9a8c56d0-0069-49df-8f18-a4228bddd4a8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [Incident](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=bf651a3b-b5a6-4054-b348-3aa2c4414826&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Demo](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=739bf091-178b-4fd7-b214-0b62f4db987c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

| ServiceDesk Version: | 8.5 |
| --- | --- |

> ## Configuring the API
> 
> 
> Prior to first use, some setup is necessary. You’ll have to configure some settings in the Web.config file in the root folder. These settings have comments explaining what they are. Many of the settings should be left alone but a few will need to be provided. Note that changes to the web config are picked up automatically by IIS and resetting IIS after editing the config is not necessary.
> 
> 
> Note that, by default, the web config setting which enables the API for use (ApiEnabled) is set to 'false'. All requests will result in a 403 (Forbidden) response until this setting is set to 'true'.
> 
> 
> ###   
> 	Authentication and Security
> 
> 
> This API passes through authentication from ProcessManager. The API consumer is responsible for providing credentials to the authentication endpoint of this API and for storing and managing the resulting authentication token. The token must be provided on all subsequent requests as the Authorization header in the following format.
> 
> 
> 
>     {
>         "key": "Authorization",
>         "value": "token tokenvalue"
>     }
> 
> 
> 
> Obviously, for production environments you should only allow secure (https) connections.
> 
> 
> ProcessManager sessions are cached at the API level. The API uses its own session timeout value, found in Web.config, which should be set to a value less than or equal to the ProcessManager session timeout. With each request, the expiration datetime for the session is extended. Still, it is possible that the API consumer may make a request on a session that is active in the API but has expired in ProcessManager. If this occurs, it is simply necessary to reauthenticate and retry the request.

### Web.config

    [Install Drive]:\Program Files\Symantec\Workflow\ServiceDesk API\Web.config

As said above, make sure to change "ApiEnabled" to "true"

    <add key="ApiEnabled" value="true"/>

Settings

    <appSettings>
        <!-- ServiceDesk settings (Be careful here. Some of these should most likely not be changed. It's
                recommended to run this API project within the same IIS environment as ServiceDesk -->
    
        <!-- All API calls will be rejected with a 403 Not Authorized until this flag is set to true -->
        <add key="ApiEnabled" value="true"/>
        <!--The url, including scheme prefix, of the root of the ServiceDesk host server for http traffic -->    
        <add key="ServiceDeskBaseUrl" value="http://localhost" />
        <!--The relative url to the processmanager portal -->
        <add key="ProcessManagerBaseUrl" value="processmanager" />
        <!--The relative url of the Incident Management workflow's virtual directory -->
        <add key="IncidentManagementBaseUrl" value="SD.IncidentManagementSimple" />
        <!--The Service ID of the Incident Management workflow project (Very unlikely this should change) -->
        <add key="IncidentManagementServiceId" value="INCIDENT-MGMT" />
        <!-- The relative url of the Change Management workflow's virtual directory -->
        <add key="ChangeManagementBaseUrl" value="SD.ChangeManagementSimple"/>
        <!-- The Service ID of the Change Management workflow project (Very unlikely this should change) -->
        <add key="ChangeManagementServiceId" value="CHANGE-MGMT"/>
        <!--The base url (NOT including scheme prefix) of the server running SymQ (Usually the same as ServiceDesk server) -->
        <add key="SymQServerName" value="localhost" />
        <!--The name of the ORM message queue in SymQ. This can be found in Workflow Explorer. It should almost always be left 'local.orm' -->
        <add key="OrmMessageQueue" value="local.orm" />
        <!--The name of the workflow response queue in SymQ. This can be found in Workflow Explorer. -->
        <add key="WorkflowResponseQueue" value="LBME.WorkflowResponseQueue" />
        <!--Timeout for all ProcessManager web service requests (in milliseconds)-->
        <add key="ServiceRequestTimeout" value="90000" />
        <!--Time before the API will refresh its ProcessManager session. This value should <= the workflow server's session timeout -->
        <add key="ProcessManagerSessionDuration" value="20" />
        <!--The GUID of the ServiceDeskSettings application profile. Highly unlikely this should ever change -->
        <add key="ServiceDeskAppProfileId" value="4811A757-6FA3-4759-822B-86611331CF85" />
    </appSettings>

### Log

    E:\Program Files\Symantec\Workflow\ServiceDesk API\ServiceDeskApi.log

---
  
### Note
  
Currently a change in the web.config is needed to display the individual methods, backup the web.config and make the following change under the "system.web" section from

      <system.web>
        <authentication mode="None" />
        <compilation debug="true" targetFramework="4.5.2" />
        <httpRuntime targetFramework="4.5.2" />
      </system.web>

to

      <system.web>
        <authentication mode="None" />
        <compilation debug="true" targetFramework="4.5.2">
            <assemblies>
                <add assembly="System.Collections, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />
            </assemblies>
        </compilation>
        <httpRuntime targetFramework="4.5.2" />
      </system.web>

[![Protirus](images\Protirus.png)](https://www.protirus.com/)
