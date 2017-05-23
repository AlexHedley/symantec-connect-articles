---
title: Workflow - Plugins - License Status
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-05-23
---

## License Status
  
The License Status Manager lets you view licensing information about Workflow and Workflow-related applications (such as ServiceDesk). This tool also lets you run tests on your license to verify that it works properly. The tool does not create or manage licensing. The Symantec Management Platform manages all licensing. The tool communicates with the Symantec Management Platform to determine licensing information.
  
This checks a webservice on your ![smp](images\smp.png) SMP box
  
- http://&lt;SMP\_SERVER&gt;/Altiris/ServiceDesk/Licensing.asmx
- http://&lt;SMP\_SERVER&gt;/Altiris/ServiceDesk/Licensing.asmx?op=GetLicenseCount

Check the default in 'Credentials Manager'.
  
### Component icon
  
N/A
  
### Author
  
![Symantec](images\Symantec.png) Symantec

### Perform Action
  
A new window will open which displays the License Status.
  
![Workflow-LicenseStatus](images\Workflow-LicenseStatus.png)
  
### Alternative
  
'License Status View' can be opened as an AppLication from the Start Menu.
  
"[Install Drive]:\Program Files\Symantec\Workflow\Tools\Symantec.LicenseStatus.Editor.exe"

### Location

    [Install Drive]:\Program Files\Symantec\Workflow\Designer\Plugins\

### DLL

- Symantec.Workflow.Plugins.LicenseTest.dll

### Code
  
N/A

### Documentation

- Symantec™ Workflow 8.1 User Guide [https://support.symantec.com/en\_US/article.DOC9625.html](https://support.symantec.com/en_US/article.DOC9625.html)
    - Chapter 34

### Support

- ServiceDesk 7.x Licensing Error Messages and Troubleshooting Ideas
    - [https://support.symantec.com/en\_US/article.HOWTO50304.html](https://support.symantec.com/en_US/article.HOWTO50304.html)
