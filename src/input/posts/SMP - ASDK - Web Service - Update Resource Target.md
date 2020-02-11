---
title: SMP - ASDK - Web Service - Update Resource Target
tags:
    - SMP
    - ASDK
author: AlexHedley
# description: 
# articleId: 
published: 2016-10-12
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/smp-asdk-web-service-update-r-1?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

I raised an [Idea](https://www.symantec.com/connect/endpoint-management/ideas) on connect - [SMP - ASDK - Web Service - InvalidateTargetMembership](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ecf4247c-6459-4fee-ae38-8528124c4c00&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments) asking for a way to programatically update a Target in an efficient way.
  
There are a number of ways to do this either via SQL or using NScript but none are great.

    exec spResourceTargetDeltaUpdate @resourceTargetGuid='target guid goes here', @flush=1

If you search the forums for **spResourceTargetDeltaUpdate** there are a number of times it's mentioned.
  
In [SMP 8.0 HF4](https://community.broadcom.com/groups/viewthread?MessageKey=c0e4f916-b302-4f6b-add0-b1f6e4b91ecf&amp;CommunityKey=36a652c6-c7e1-4701-af0f-b978f701f102&amp;tab=digestviewer#bmc0e4f916-b302-4f6b-add0-b1f6e4b91ecf) there were 4 new Web Services added to the Resource Model

    URL: http://localhost/altiris/nswebservice/resourcemodel.asmx

Methods:
  
- UpdateResourceTargetMembership
    - targetGuid (guid)
    - fullUpdate (bool)
    - updateDependencies (bool)

- UpdateResourceTargets
    - targetGuids (string)
    - fullUpdate (bool)
    - updateDependencies (bool)

- UpdateResourceTargetsAsync
    - targetGuids (string)
    - fullUpdate (bool)
    - updateDependencies (bool)
    - urgent (bool)

- UpdateResourceTargetsMembership
    - targetGuid (guids [])
    - fullUpdate (bool)
    - updateDependencies (bool)

An update was posted on the Idea from @[Vladimir](https://www.symantec.com/connect/user/vladimir-zelenjak)

> With several months passed since last update here, I can now officially confirm that new ASDK method: ScopingManagementLib.InvalidateTargetMembership(Guid targetGuid, bool invalidateDependencies) added recently and will be available starting 8.1 release.

So take a look at the new method in 8.1

- InvalidateTargetMembership
    - targetGuid (Guid )
    - invalidateDependencies (bool)
