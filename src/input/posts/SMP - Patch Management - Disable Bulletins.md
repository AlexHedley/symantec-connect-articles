---
title: SMP - Patch Management - Disable Bulletins
# tags:
#     - 
author: AlexHedley
# description: 
published: 2018-11-02
---

## ![SMP](images\smp.png) SMP
  
### Patch Management
  
### Disable Bulletins
  
Patch Management has it's own Web Service.

| http://localhost/altiris/patchmanagementcore/PatchWorkflowSvc.asmx |
| --- |

| SMP |
| --- |
| 8.5.3073 | ✔ |
| 8.1.5844 | ✘ |
| 7.5.# | ✘ |

Looks like 8.5 got a new method.
  
- Disable Bulletins

| http://localhost/altiris/patchmanagementcore/PatchWorkflowSvc.asmx?op=DisableBulletins |
| --- |

This takes two parameters

- bulletinGuids (string)
- deletePolicies (boolean)

bulletinGuids - This is usually a comma separated list of Guids, when the input is a string but plural.
  
---
  
FORUM
  
Automatically "Delete unused Software Update Packages" problem disabling staged bulletins  
https://www.symantec.com/connect/forums/automatically-delete-unused-software-update-packages-problem-disabling-staged-bulletins
  
From @[Sergei Kljujev](https://www.symantec.com/connect/user/sergei-kljujev)

> In order to disable Bulletin you can use attached script, as following:
> 
> 1. Unzip DisableBulletin.zip and copy contents to C:\Program Files\Altiris\Notification Server\Bin.
> 
> NB! Make Sure to merge NSCRIPT.NRF and NSCRIPT.EXE.CONFIG to the existing ones, if you already have them modified.
> 
> 2. Run C:\Program Files\Altiris\Notification Server\Bin\NSCRIPT.EXE DisableBulletin.cs &lt;bulletin\_guid&gt;
> 
> Note that the script is working on Patch Management Solution Versions up to 8.1.*

- DisableBulletin.cs
- NScript.exe.config
- Nscript.nrf

    DisableBulletin.cs

    using System;
    using System.IO;
    using Altiris.NS.ItemManagement;
    using Altiris.NS.Security;
    using Altiris.PatchManagementCore.Policies;
    using Altiris.PatchManagementCore.Resources;
    
    class DisableBulletin
    {
        static int Main(string[] args)
        {
            Guid bulletinGuid;
            if (args.Length != 1)
            {
                Console.WriteLine("Programmatically Disable Bulletin");
                Console.WriteLine("Usage: nscript.exe DisableBulletin.cs <BulletinGuid>");
                return 1;
            }	
            if (!Guid.TryParse(args[0], out bulletinGuid))
            {
                Console.WriteLine("Error: Cannot create guid from '{0}'", args[0]);
                return 1;
            }
    
            SecurityContextManager.SetContextData();
    
            var bulletin = Item.GetItem(bulletinGuid, ItemLoadFlags.Writeable) as SoftwareBulletinResource;
    
            if (bulletin == null)
            {
                Console.WriteLine("Error: Bulletin '{0}' not found.", bulletinGuid);
                return 1;
            }	
            var oldValue = bulletin.RaiseMessage;
            try
            {
                bulletin.RaiseMessage = false;
                bulletin.IsDisabledByUser = true;
                bulletin.Enabled = false;
                bulletin.setAdvertStagedState(false);
                bulletin.deleteAllPendingUpdates();
                bulletin.Save();
            } 
            catch (Exception ex)
            {
                Console.WriteLine("Error: Bulletin '{0}' could not be disabled. Exception: {1}", bulletin.Name, ex);
               return 1;
            }
            finally 
            {
                bulletin.RaiseMessage = oldValue;
            }
            
            Console.WriteLine("Bulletin '{0}' Disabled.", bulletin.Name);
            return 0;
        }
    }

    NScript.exe.config

    <?xml version="1.0" encoding="utf-8"?>
    <!--
    SYMANTEC:     Copyright (c) 2018 Symantec Corporation. All rights reserved.
    
    THIS SOFTWARE CONTAINS CONFIDENTIAL INFORMATION AND TRADE SECRETS OF SYMANTEC CORPORATION. USE, 
    DISCLOSURE OR REPRODUCTION IS PROHIBITED WITHOUT THE PRIOR EXPRESS WRITTEN PERMISSION OF SYMANTEC
    CORPORATION.
    
    The Licensed Software and Documentation are deemed to be commercial computer software as defined
    in FAR 12.212 and subject to restricted rights as defined in FAR Section 52.227-19 "Commercial
    Computer Software - Restricted Rights" and DFARS 227.7202, Rights in "Commercial Computer Software
    or Commercial Computer Software Documentation", as applicable, and any successor regulations,
    whether delivered by Symantec as on premises or hosted services.  Any use, modification, reproduction
    release, performance, display or disclosure of the Licensed Software and Documentation by the U.S.
    Government shall be solely in accordance with the terms of this Agreement.
    -->
    <configuration><runtime>	<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">		<qualifyAssembly partialName="Altiris.Common" fullName="Altiris.Common,version=7.1.0.0,publicKeyToken=d516cb311cfb6e4f,culture=neutral"/>		<qualifyAssembly partialName="Altiris.Common.UI" fullName="Altiris.Common.UI,version=7.1.0.0,publicKeyToken=d516cb311cfb6e4f,culture=neutral"/>		<qualifyAssembly partialName="Altiris.NS" fullName="Altiris.NS,version=7.1.0.0,publicKeyToken=d516cb311cfb6e4f,culture=neutral"/>		<qualifyAssembly partialName="Altiris.NS.StandardItems" fullName="Altiris.NS.StandardItems,version=7.1.0.0,publicKeyToken=d516cb311cfb6e4f,culture=neutral"/>		<qualifyAssembly partialName="Altiris.NS.UI" fullName="Altiris.NS.UI,version=7.1.0.0,publicKeyToken=d516cb311cfb6e4f,culture=neutral"/>		<qualifyAssembly partialName="Altiris.Resource" fullName="Altiris.Resource,version=7.1.0.0,publicKeyToken=d516cb311cfb6e4f,culture=neutral"/> 		<qualifyAssembly partialName="Altiris.PatchManagementCore" fullName="Altiris.PatchManagementCore,version=7.1.0.0,publicKeyToken=d516cb311cfb6e4f,culture=neutral"/>		<qualifyAssembly partialName="Altiris.InventoryRuleManagement" fullName="Altiris.InventoryRuleManagement,version=7.1.0.0,publicKeyToken=d516cb311cfb6e4f,culture=neutral"/>		<qualifyAssembly partialName="Altiris.Resource.UI" fullName="Altiris.Resource.UI,version=7.1.0.0,publicKeyToken=d516cb311cfb6e4f,culture=neutral"/>	</assemblyBinding></runtime>
    <startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5.1"/></startup>
    </configuration>

    Nscript.nrf

    Altiris.PatchManagementCore
    Altiris.InventoryRuleManagement

---
  
Or from @[schnyders](https://www.symantec.com/connect/user/schnyders)

    $ReportsMS = New-WebServiceProxy -Uri "http://altiris/Altiris/ASDK.NS/ReportManagementService.asmx" -UseDefaultCredential
    $ConsoleMS = New-WebServiceProxy -Uri "http://altiris/Altiris/NS/console.asmx" -UseDefaultCredential
    
    $Bulletins = $ReportsMS.RunReport("9e5b8923-b02b-4702-9b44-4404fa8b6e43").table | Where-Object { $_.Available_x0020_Packages -gt 0 -and $_.Policies -eq 0 -and $_.Downloaded -eq "Yes" }
    
    ForEach($Bulletin in $Bulletins) {
        $ConsoleMS.ItemCallback($Bulletin._ResourceGuid, "ItemAction:e6e01da7-1f2e-4716-99e0-2738c214d458:")
    }

---
  
Programatically disable the staged bulletins  
https://www.symantec.com/connect/forums/programatically-disable-staged-bulletins
  
---
  
ALTERNATIVE TOOLS
  
![Worklfow](images\Workflow.png) Workflow has it's own Project
  
**Zero Day Patch**

| https://www.symantec.com/connect/videos/workflow-template-zero-day-patch |
| --- |

This is using a previous version of the WebService but could easily be updated to take advantage of this new method.
  
**AutoPatcher**  
https://www.symantec.com/connect/articles/autopatcher
  
**{CWoC} PatchAutomation and ZeroDayPatch builds for 8.0**  
https://www.symantec.com/connect/blogs/cwoc-patchautomation-and-zerodaypatch-builds-80
  
---
  
[![Protirus](images\Protirus.png)](https://www.protirus.com)
