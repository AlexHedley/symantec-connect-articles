---
title: Workflow - ProcessManager - WebPart - Developer Guide - Styling
tags:
    - Workflow
    - Process Manager
    - WebPart
    - Developer Guide
author: AlexHedley
# description: 
# articleId: 
published: 2017-07-11
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/workflow-processmanager-webpart-3?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this Article we will see how to style a WebPart to match the Process Manager (PM) theme.
  
Articles
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=aa0478d7-5f5a-4be4-8369-4c74f963deeb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=36a9f5ee-ab0b-42e7-a75e-590ba4f256ec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a3b54e8a-7492-4397-8512-8828defe25a7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74973282-5d27-4b12-a0d3-9ad29d38a2ce&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c1b3103c-afad-45f8-9f17-244fff752121&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other WebParts
- [Controls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c20f9b40-20f8-4693-937a-7ca431c4d7ce&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) a WebPart (this)
- WF/PM [Connection String](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=849d26ef-084e-426b-a064-fbb86730e6b8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Connecting to [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=77434eb5-7ee1-4bb4-bef1-ef566cce61fb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to retrieve data

- - -
  
Open Process Manager and navigate to a Ticket.
  
Right Click on the "Description & Resolution" and Inspect Element, use the Developer Tools of your Web Browser of choice but we wish to get the HTML used to render this section.
  
After some careful extraction we can get the HTML we need.

    <table border="0" width="100%" class="pv_h_tbl1" cellspacing="0" cellpadding="0"><tr>	<td valign="top" class="pv_h_pad0">		<table cellspacing="0" cellpadding="0" class="dg_tbl" width="100%">			<tr>			</tr>			<tr class="dg_row_first">				<td class="dg_label" width="100px">					<span>Description</span>				</td>				<td class="dg_data">					Blah Blah				</td>			</tr>		</table>								</td>							</tr>								
    </table>

We need the classes used

- pv_h_tbl1
- pv_h_pad0
- dg_tbl
- dg_row_first
- dg_label
- dg_data

This is part of the following 'LogicBase.Ensemble.dll'. (Using the methods described in the [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c1b3103c-afad-45f8-9f17-244fff752121&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) Article let's take a look.).

- ​LogicBase.Ensemble.dll
    - ​LogicBase.Ensemble.Reports.WebParts
        - LogicBase.Ensemble.Reports.WebParts.ProcessInfo
- LogicBase.Ensemble.Webparts.Default.dll
- Symantec.ServiceDesk.WebParts.dll

Check the *OnPreRender* method.
  
As you can see from the below we have all the classes used to build up a *Table*.
  
First create a Table and set some properties:

    HtmlTable htmlTable1 = new HtmlTable();
    htmlTable1.Border = 0;
    htmlTable1.Width = "100%";
    htmlTable1.Attributes["class"] = "pv_h_tbl1";
    htmlTable1.CellPadding = htmlTable1.CellSpacing = 0;

Add a Row and a Cell.

    HtmlTableRow row1 = new HtmlTableRow();
    htmlTable1.Rows.Add(row1);
    HtmlTableCell cell1 = new HtmlTableCell();
    cell1.VAlign = "top";
    cell1.Attributes["class"] = "pv_h_pad0";
    row1.Cells.Add(cell1);

Create another Table to hold the information.

    HtmlTable htmlTable2 = new HtmlTable();
    cell1.Controls.Add((Control)htmlTable2);
    htmlTable2.CellPadding = htmlTable2.CellSpacing = 0;
    htmlTable2.Attributes["class"] = "dg_tbl";
    htmlTable2.Width = "100%";

Add a Row.

    HtmlTableRow row2 = new HtmlTableRow();
    htmlTable2.Rows.Add(row2);

Add some cells and set some classes based on the row number.

    HtmlTableRow htmlTableRow = new HtmlTableRow();
    
    cell1 = new HtmlTableCell();
    cell1.Attributes["class"] = "dg_label";
    cell1.Width = "100px";
    cell1.InnerText = "Username";
    
    HtmlTableCell cell2 = new HtmlTableCell();
    cell2.Attributes["class"] = "dg_data";
    cell2.InnerText = UserName;
    
    htmlTableRow.Visible = true;
    htmlTableRow.Attributes["class"] = "dg_row_first";
    htmlTable2.Rows.Add(htmlTableRow);
    htmlTableRow.Cells.Add(cell1);
    htmlTableRow.Cells.Add(cell2);

Finally add the Table to the WebPart.

    this.Controls.Add((Control)htmlTable1);

This adds the UserName to a row.

- Table

There are the original items from previous Articles

- ContentText
- Label

![ProcessManager_ProcessViewPage_WebPart_2.png](images\ProcessManager_ProcessViewPage_WebPart_2.png)
  
If you compile the Project and add it to PM following the steps in the [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74973282-5d27-4b12-a0d3-9ad29d38a2ce&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments) Article you can then inspect the webpage and check the HTML and see it matches the **ProcessInfo** WebPart.
  
- - -
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
