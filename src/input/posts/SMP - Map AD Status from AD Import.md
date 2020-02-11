---
title: SMP - Map AD Status from AD Import
tags:
    - SMP
author: AlexHedley
# description: 
# articleId: 
published: 2015-10-08
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/smp-map-ad-status-from-ad-import?CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&tab=librarydocuments
---

In this Article I'm going to show you how to extend the User Resource to include extra properties you can retrieve from the AD Import to gain extra information about your user base. We are going to map the AD Status value (aka UserAccountControl)

First lets create a ![Data Classes](images\DataClasses.png) Data Class to store this information.
  
![Reports Folder](images\ReportsFolder.png) Settings | ![Folder](images\Folder.png) Notification Server | ![Folder](images\Folder.png) Resource and Data Class Settings | ![Folder](images\Folder.png) Data Classes
  
Right-Click | New | Editable Data Class
  
Call it **AD User Details**
  
Add some Fields
  
- ADStatus (Static List)
- UserAccountControl (String/Integer)
- LastUpdated (Date)

For the Static List add the following values

- Active
- Disabled
- Deleted

If we take a look at an AD User to see what value this is:
  
![AD - Account (Disabled)](images\AD-AccountDisabled.png)

![AD - Attribute Editor](images\AD-AttributeEditor.png)
  
![userAccountControl](images\userAccountControl.png)
  
What does 512 equate to?
  
[http://www.netvision.com/ad_useraccountcontrol.php](http://www.netvision.com/ad_useraccountcontrol.php)

| **Value** | **Description** |
| --- | --- |
| 512 | Enabled Account |
| 514 | Disabled Account |
| 544 | Enabled, Password Not Required |
| 546 | Disabled, Password Not Required |
| 66048 | Enabled, Password Doesn't Expire |
| 66050 | Disabled, Password Doesn't Expire |
| 66080 | Enabled, Password Doesn't Expire & Not Required |
| 66082 | Disabled, Password Doesn't Expire & Not Required |
| 262656 | Enabled, Smartcard Required |
| 262658 | Disabled, Smartcard Required |
| 262688 | Enabled, Smartcard Required, Password Not Required |
| 262690 | Disabled, Smartcard Required, Password Not Required |
| 328192 | Enabled, Smartcard Required, Password Doesn't Expire |
| 328194 | Disabled, Smartcard Required, Password Doesn't Expire |
| 328224 | Enabled, Smartcard Required, Password Doesn't Expire & Not Required |
| 328226 | Disabled, Smartcard Required, Password Doesn't Expire & Not Required |

Let's map this value into the new Data Class with the AD Import.
  
![Reports Folder](images\ReportsFolder.png) Settings | ![Folder](images\Folder.png) Notification Server | ![Microsoft Active Directory Import](images\MicrosoftActiveDirectoryImport.png) Microsoft Active Directory Import
  
![Microsoft Active Directory Import - Config](images\MicrosoftActiveDirectoryImport-Config.png)
  
Under "User" click on "specified column mappings"
  
Select the newly created Data Class
  
![AD Import - Coumn Mappings for User](images\ADImport-CoumnMappingsforUser.png)
  
Then click on UserAccountControl "(null)" to select a Field
  
![AD Import - Directory entry attribute](images\ADImport-Directoryentryattribute.png)
  
OK | OK
  
Run the Import Rule ![Run Import Rule](images\RunImportRule.png)

Now let's create a ![CMDB Rule](images\CMDBRule.png) CMDB Rule to map this number to some text.
  
![Reports Folder](images\ReportsFolder.png) Settings | ![Folder](images\Folder.png) Notification Server | ![Folder](images\Folder.png) Connector | ![Folder](images\Folder.png) CMDB Rules
  
![CMDB Rule - Set AD Status](images\CMDBRule-SetADStatus.png)

| Resource Type | User |
| --- | --- |
| Target using | Sql Query |
| SQL query | &lt;below&gt; |

    SELECT 
        rru.[Guid],
        rru.Name,
        iaud.UserAccountControl,
        GetDate() AS CurrentDateTime
    FROM 
        [RM_ResourceUser] rru
    INNER JOIN 
        Inv_AD_User_Details iaud 
        ON iaud._ResourceGuid = rru.Guid

Choose the data class of the one you've just created:

I'm getting the current date from SQL.

| LastUpdated | CurrentDateTime |
| --- | --- |

* * *

Anybody know how to get the current DateTime in an Expression?

I've tried the following

- Now()
- Today()
- DateTime.Today

With and without equals...

- [https://www-secure.symantec.com/connect/forums/cmdb-rule-help](https://community.broadcom.com/symantecenterprise/viewthread?MessageKey=a98001a0-57f5-4d71-851c-cff888119198&amp;CommunityKey=63b01f30-d5eb-43c7-9232-72362b508207&amp;tab=digestviewer#bma98001a0-57f5-4d71-851c-cff888119198)

* * *

In the 'AD Status' column choose "&lt;Expression&gt;" from the dropdown

<u>Articles</u>

- Scriptable fields for modifying Resource Import Export and CMDB rules [https://support.symantec.com/en\_US/article.HOWTO45608.html#v19412924](https://support.symantec.com/en_US/article.HOWTO45608.html#v19412924)
- Expression Functions [https://support.symantec.com/en\_US/article.HOWTO45613.html#v19412948](https://support.symantec.com/en_US/article.HOWTO45613.html#v19412948)
    - **IIF** [https://support.symantec.com/en\_US/article.HOWTO45647.html#v22897377](https://support.symantec.com/en_US/article.HOWTO45647.html#v22897377)

Now we can use a bunch of nested IIFs, it's not eloquent but it works.

    IIF([AD User Details.UserAccountControl]='512','Active',
     IIF([AD User Details.UserAccountControl]='514','Disabled',
      IIF([AD User Details.UserAccountControl]='544','Active',
       IIF([AD User Details.UserAccountControl]='546','Disabled',
        IIF([AD User Details.UserAccountControl]='66048','Active',
         IIF([AD User Details.UserAccountControl]='66050','Disabled',
          IIF([AD User Details.UserAccountControl]='66080','Active',
           IIF([AD User Details.UserAccountControl]='66082','Disabled',
            IIF([AD User Details.UserAccountControl]='262656','Active',
             IIF([AD User Details.UserAccountControl]='262658','Disabled',
              IIF([AD User Details.UserAccountControl]='262688','Active',
               IIF([AD User Details.UserAccountControl]='262690','Disabled',
                IIF([AD User Details.UserAccountControl]='328192','Active',
                 IIF([AD User Details.UserAccountControl]='328194','Disabled',
                  IIF([AD User Details.UserAccountControl]='328224','Active',
                   IIF([AD User Details.UserAccountControl]='328226','Disabled','Deleted'
                    ))))))))))))))))

I tried a CASE statement but it couldn't get it to verify.

Set a Schedule - a Shared one makes sense, match it to the AD Import.

* * *

[![Protirus](images\Protirus.png)](http://www.protirus.com/)
