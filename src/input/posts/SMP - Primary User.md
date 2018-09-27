---
title: SMP - Primary User
# tags:
#     - 
author: AlexHedley
# description: 
published: 2018-09-27
---

The Symantec Management Agent (SMA) calculates the Primary User based on the length of time a user has been logged onto a machine.

> How is the primary user calculated?
> 
> - AeXUserMonitorLog.xml stores the history of user sessions
> - SMA calculate primary user prior to basic inventory update
>     - takes all the old sessions from XML, adjusts them to 28 day limit
>     - takes all the current sessions from Windows, adjusts them to 28 day limit
>     - sums up durations of all the sessions for each user and selects the user with the longest duration as the primary user

    AeXUserMonitorLog.xml

- install directory of the Symantec Management Agent
  
This is made up of

    <?xml version="1.0"?>
    <UserLog>
        <Log utc_lastloggedon="2018-09-11 19:18:14 -6:00" utc_year="2018" utc_month="9" utc_day="16" duration="398289" userID="MyDomain\John_Doe"/>
    </UserLog>

This fills in the following Table:

    Evt_AeX_Client_LogOn

The calculations use a value that can be updated in the Registry:
  
Default Value **28**

    HKEY_LOCAL_MACHINE\SOFTWARE\Altiris\Altiris Agent\Inventory\PrimaryUserRecordDays

Another table is then updated via Basic Inventory

    Inv_AeX_AC_Primary_User

| Key | Type | Value (some as example) | Description |
| --- | --- | --- | --- |
| PrimaryUserRecordDays | REG_DWORD | 0x1c | Sets 28 day limit, can be changed at any time. No SMA restart is needed |
| PrimaryUser | REG_SZ | altiris\jdoe48 | Holds the currently selected primary user |

**SQL**
  
You can use this information in your Reports by adding the Data Class 'AeX AC Primary User' or the above 'Inv' table.

    SELECT * FROM Inv_AeX_AC_Primary_User

Example Data

| _id | _ResourceGuid | Domain | Month | User | Server Generated | Year |
| --- | --- | --- | --- | --- | --- | --- |
| # | {Guid} | MyDomain | October | alex.hedley |  | 2018 |

You can use the *_ResourceGuid* to join to the Computer table.
  
---
  
**CMDB Rule**
  
Tasks
  
Many people use this information to then set the "Asset Owner" to be the "Primary User".
  
This has been know to have issues:
  
HOWTO95240  
How the Asset Owner association works  
https://support.symantec.com/en\_US/article.HOWTO95240.html
  
TECH163941  
CMDB task "Assign Computer's Ownership to be the Primary User" fails to work  
https://support.symantec.com/en\_US/article.TECH163941.html
  
---
  
**Tech**
  
TECH251540  
Understanding Primary User Calculation Methods in 8.x  
https://support.symantec.com/en\_US/article.TECH251540.html
  
HOWTO7778  
Primary User Calculation Methods NS 6.0  
https://support.symantec.com/en\_US/article.HOWTO7778.html
  
HOWTO7796  
Understanding Primary User in Notification Server 6.0 SP2 and SP3  
https://support.symantec.com/en\_US/article.HOWTO7796.html
  
---
  
**Forum**
  
Change the primary user  
https://www.symantec.com/connect/forums/change-primary-user
  
When is the Primary User calculated?  
https://www.symantec.com/connect/forums/when-primary-user-calculated
