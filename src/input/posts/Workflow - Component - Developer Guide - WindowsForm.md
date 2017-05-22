---
title: Workflow - Component - Developer Guide - WindowsForm
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-05-22
---

In this Article I'm going to explain how to add a Form to your Plugin to allow user interaction.
  
Table of Contents
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=016f70af-1c51-438b-bbae-f98e86164f26&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=84ee5f15-df6c-44c7-8acd-e2764f0c4717&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Plugin](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=8aeca32a-9a00-4d91-b618-f6af07957e71&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2e508788-3a83-4a91-8e5b-18b28ca1cc02&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Advanced Plugin](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=5076bfd9-0b26-408c-b957-3bb5fb0b59c2&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=6d54d145-537c-40e6-86ca-b5dec2b1e972&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [WindowsForm](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80b95a29-8a1a-44ce-a616-87cf8e001dbd&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)

Right Click | Add | Windows Form
  
![VS-RC-Add-WindowsForm](images\VS-RC-Add-WindowsForm.png)
  
Give it a name "*x*Form"
  
Change some Properties

| Property | Value |
| --- | --- |
| Text | Protirus |
| TopMost | True |
| MaxamizeBox | False |
| MinimizeBox | False |
| Icon | Set to one you've added or the default WF one. |
| FormBorderSize | FixedSingle |
| SizeGripStyle | Hide |

Add some labels and textboxes.
  
Set the Textboxes

| Property | Value |
| --- | --- |
| Enabled | False |

Add some buttons to copy the values to the clipboard.

Add a 'StatusStrip' and add a 'StatusLabel' to the Form, we've already set the properties on the Form.

| Property | Value |
| --- | --- |
| SizingGrip | False |

Add an PictureBox to display the Project Type.

Final Form
  
![ProtirusForm](images\ProtirusForm.png)

We will need a key from the ![Regedit [S]](images\RegeditS.png)Registry.
  
It's a ![String Value](images\StringValue.png) String Value

    Software\Wow6432Node\TransparentLogic.com\LogicBase Shared

Which returns

    [Install Drive]:\Program Files\Symantec\Workflow\Shared\

| We can't hardcode the imagePath, as the install drive might be different, so use some code to get a RegKey instead. |
| --- |

We need to add the following folders to the path.

    \logicbaselib\ProjectTypes\

To get the image
  
![WebForm_48](images\WebForm_48.png)
  
Full path

    E:\Program Files\Symantec\Workflow\Shared\logicbaselib\ProjectTypes\WebForm_48.png

| Note | There are some interesting files in this folder, if you look in the XML you will see the 'OldProjectType' name listed. |
| --- | --- |

    Monitoring.xml
    ...
    <OldProjectType>Metronome</OldProjectType>

As we are displaying information about the Project in the Form we need to pass the Project as an input.

    public ProtirusForm(AbstractOrchestrationProject project)
    {
        InitializeComponent();
        _project = project;
    }

Code

    using System.Windows.Forms;
    using LogicBase.Core;
    
    private AbstractOrchestrationProject _project;
    private string imagePath = @"E:\Program Files\Symantec\Workflow\Shared\logicbaselib\ProjectTypes\";
    
    public ProtirusForm(AbstractOrchestrationProject project)
    {
        InitializeComponent();
        _project = project;
    }
    
    private void ProtirusForm_Load(object sender, EventArgs e)
    {
        string filePath = string.Format(@"{0}{1}", imagePath, _project.ProjectSetupData.ProjectType.ImageFileName);
        pbProjectImage.Image = Image.FromFile(filePath);
        txtProjectName.Text = _project.MainFile.FullName;
        txtProjectDirectory.Text = _project.MainFile.DirectoryName;
    }
    
    #region <Button Clicks>
    
    private void btnCopyProjectName_Click(object sender, EventArgs e)
    {
        Clipboard.SetText(txtProjectName.Text);
        //Clipboard.SetDataObject(txtProjectName.Text, true);
        toolStripStatusLabel1.Text = @"Copied 'Project Name' to Clipboard.";
    }
    
    private void btnCopyProjectDirectory_Click(object sender, EventArgs e)
    {
        Clipboard.SetText(txtProjectDirectory.Text);
        //Clipboard.SetDataObject(txtProjectDirectory.Text, true);
        toolStripStatusLabel1.Text = @"Copied 'Project Directory' to Clipboard.";
    }
    
    #endregion <Button Clicks>

To show the Form from the Plugins menu update the *PerformAction* method:

    public void PerformAction(AbstractOrchestrationProject project)
    {
        ProtirusForm pF = new ProtirusForm(project);
        pF.Show();
    }

- - -
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
