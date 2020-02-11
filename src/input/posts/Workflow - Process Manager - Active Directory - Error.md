---
title: Workflow - Process Manager - Active Directory - Error
tags:
    - Workflow
    - Process Manager
    - Active Directory
    - Error
author: AlexHedley
# description:
# articleId:  
published: 2019-04-09
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-process-manager-active?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

You may notice that Active Directory isn't pulling in new Users or updating existing ones on your Schedule.
  
When you check the logs, you see an error at the time your AD Sync Schedule is set for
  
- [Install Drive]:\Program Files\Symantec\Workflow\Logs\*processmanager.log*

> Cannot connect to the server
> 
> There is no such object on the server.

    Error,11 March 2019 03:30:01,[unknown] Cannot connect to the server
    [unknown] -- error.ToString() --
    [unknown] System.DirectoryServices.DirectoryServicesCOMException (0x80072030): There is no such object on the server.
    [unknown] 
    [unknown]    at System.DirectoryServices.DirectoryEntry.Bind(Boolean throwIfFail)
    [unknown]    at System.DirectoryServices.DirectoryEntry.Bind()
    [unknown]    at System.DirectoryServices.DirectoryEntry.get_AdsObject()
    [unknown]    at System.DirectoryServices.DirectorySearcher.FindAll(Boolean findMoreThanOne)
    [unknown]    at System.DirectoryServices.DirectorySearcher.FindOne()
    [unknown]    at LogicBase.Ensemble.Userman.ServiceCore.ADUtilities.GetDirectorySearcherForServer(ActiveDirectoryServer server, String container)

Or

> There is no such object on the server.

    Error,11 March 2019 03:30:01,[userman] There is no such object on the server.
    [userman] 
    [userman] -- error.ToString() --
    [userman] System.DirectoryServices.DirectoryServicesCOMException (0x80072030): There is no such object on the server.
    [userman] 
    [userman]    at System.DirectoryServices.DirectoryEntry.Bind(Boolean throwIfFail)
    [userman]    at System.DirectoryServices.DirectoryEntry.Bind()
    [userman]    at System.DirectoryServices.DirectoryEntry.get_AdsObject()
    [userman]    at System.DirectoryServices.DirectorySearcher.FindAll(Boolean findMoreThanOne)
    [userman]    at System.DirectoryServices.DirectorySearcher.FindOne()
    [userman]    at LogicBase.Ensemble.Userman.ServiceCore.ADUtilities.GetDirectorySearcherForServer(ActiveDirectoryServer server, String container)
    [userman]    at LogicBase.Ensemble.Userman.ServiceCore.ADUtilities.GetADMembersForOU(ActiveDirectoryServer server, String mainOrgUnit, String baseString, SearchScope searchScope)
    [userman]    at LogicBase.Ensemble.Userman.ServiceCore.ADUtilities.SyncFromOrganizationalUnit(String baseString, ActiveDirectoryServer server)

Looking at the error you see a few methods.

- GetDirectorySearcherForServer
- GetADMembersForOU
- SyncFromOrganizationalUnit

The first thing to check is what you have set your Profile to get.
  
If you have ticked a few OUs and these have been removed from your AD you will need to update the profile.
  
If you have access to the Database run the following query.

    SELECT
      [OrganizationUnits]
    FROM
      [ActiveDirectoryServer]

This will show what OUs you currently have selected.
  
If you change the OUs then they only get appended to the current list and not replaced.
  
An Engineering ticket is currently targeted to 8.5 RU2 (tentative ETA - end of April)
  
At this point, there are two workarounds:

1. Change the AD Sync Profile, change the selection from Organization Units to something else - like Entire Domain, save, then edit it back to Organization Units. Downside here is that you would have to re-select the OUs which may be quite problematic in some of the larger environments.
2. Edit the OU list in ActiveDirectoryServer.OrganizationUnits directly in database and remove the problematic OU. While I would not recommend doing this in general, if you are comfortable enough with SQL to do this backup the db first.

| See | ET4231242 |
| --- | --- |

---
  
Another useful Article is how to merge a User.
  
New Active Directory Users are not being Synchronized to Service Desk

- https://www.symantec.com/connect/forums/new-active-directory-users-are-not-being-synchronized-service-desk

---
  
If you need more information on setting up Active Directory see these Articles (and more)
  
How to configure AD Sync profiles in ServiceDesk 7.1 SP2

- https://support.symantec.com/en\_US/article.HOWTO65717.html

Configuring Active Directory sync profiles

- https://support.symantec.com/en\_US/article.HOWTO84615.html

[![Protirus](images\Protirus.png)](https://www.protirus.com/)​
