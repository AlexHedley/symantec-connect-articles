---
title: Workflow - ProcessManager - WebPart - Developer Guide - SQL
# tags:
#     - 
author: AlexHedley
# description: 
published: 2017-07-11
---

In this Article we will see how to connect to the Process Manager Database to retrieve data to display in a WebPart.
  
Articles
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=aa0478d7-5f5a-4be4-8369-4c74f963deeb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=36a9f5ee-ab0b-42e7-a75e-590ba4f256ec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a3b54e8a-7492-4397-8512-8828defe25a7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74973282-5d27-4b12-a0d3-9ad29d38a2ce&amp;CommunityKey=a067504a-9710-492c-bbef-18d2ed6b44af&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c1b3103c-afad-45f8-9f17-244fff752121&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other WebParts
- [Controls](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=c20f9b40-20f8-4693-937a-7ca431c4d7ce&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) a WebPart
- WF/PM [Connection String](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=849d26ef-084e-426b-a064-fbb86730e6b8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Connecting to [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=77434eb5-7ee1-4bb4-bef1-ef566cce61fb&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) to retrieve data (this)

- - -
  
Until I find a way to connect directly to the PM DB using Symantec libs we will need to create our own DAL (DataAccessLayer).
  
This example will use information from the following Article: [ServiceDesk - WebPart - Assignments and Audit Info](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=fc22d82f-994d-4b69-b692-e8cc63684308&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
  
As explained in the [Connection String](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=849d26ef-084e-426b-a064-fbb86730e6b8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) Article there are a number of ways we can set this.
  
There are three main parts we need to complete.

- Connect
- Retrieve
- Display

We will need a Data Source, we can use an [SqlDataSource](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.sqldatasource%28v=vs.110%29.aspx). This is part of the 'System.Web.UI.WebControls' lib.
  
This will need a Connection String, we can get this from our previous [Article](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=849d26ef-084e-426b-a064-fbb86730e6b8&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments). and a ProviderName

    SqlDataSource PMDBDataSource = new SqlDataSource();
    WorkflowSQLConnectionString connectionString = new WorkflowSQLConnectionString();
    PMDBDataSource.ConnectionString = connectionString.GetConnectionString();
    PMDBDataSource.ProviderName = "System.Data.SqlClient";

Next we need a way to run a Query.
  
I suggest creating a StoredProcedure as this can be configured outside of the WebPart.
  
Return this data in a DataView for use within the WebPart.

    public DataView RunQuery(string inQuery, SqlDataSourceCommandType inCmdType, ParameterCollection inParams)
    {
        PMDBDataSource.SelectCommandType = inCmdType;
    
        PMDBDataSource.SelectParameters.Clear();
        if (inParams != null)
        {
            foreach (Parameter parameter in inParams)
            {
                PMDBDataSource.SelectParameters.Add(parameter);
            }
        }
    
        PMDBDataSource.SelectCommand = inQuery;
        DataView QueryData = (DataView)PMDBDataSource.Select(DataSourceSelectArguments.Empty);
        
        return QueryData;
    }

This has 3 arguments.

- string inQuery
- SqlDataSourceCommandType inCmdType
- ParameterCollection inParams

With an example of running it we can discuss these inputs.

    protected DataView GetAuditProcessInfoData(string inTicketId)
    {
        ParameterCollection ParamCollection = new ParameterCollection();
        ParamCollection.Add("sessionid", TypeCode.String, inTicketId);
        return ProtirusDAL.RunQuery("[sp_SD_AuditProcessInfo]", SqlDataSourceCommandType.StoredProcedure,
            ParamCollection);
    }

The first is the StoredProcedureName.
  
The second is the type of command you wish to run.
  
This is an enum 'SqlDataSourceCommandType'

- Text = 0
- StoredProcedure = 1

Finally we create a *ParameterCollection* and add in the *SessionId* of the Ticket, as this is what the StoredProcedure expects. You might have other parameters you need here, just add them all.
  
We have a DataView now but we need to display it on the WebPart.
  
We can convert the DataView into a DataTable.
  
We may not need all the columns from the SP, just add the ones you need.

    public DataTable GeAuditProcessInfo(string inTicketId)
    {
        DataTable SDAuditProcessInfoTable = new DataTable();
        //SDAuditProcessInfoTable.Columns.Add("audit_process_info_id", typeof(Guid));
        //SDAuditProcessInfoTable.Columns.Add("incident_session_id", typeof(Guid));
        SDAuditProcessInfoTable.Columns.Add("Service Queue", typeof(string));
        SDAuditProcessInfoTable.Columns.Add("Date Assigned", typeof(string));
        SDAuditProcessInfoTable.Columns.Add("Date Re-Assigned", typeof(string));
        SDAuditProcessInfoTable.Columns.Add("Length Of Assignment", typeof(string));
        //SDAuditProcessInfoTable.Columns.Add("current_assignment", typeof(bool));
    
        DataView SDAuditProcessInfoData = GetAuditProcessInfoData(inTicketId);
    
        foreach (DataRowView ProcessRow in SDAuditProcessInfoData)
        {
            DataRow rowData = ProcessRow.Row;
            
            SDAuditProcessInfoTable.Rows.Add(
                //rowData["audit_process_info_id"].ToString(),
                //rowData["incident_session_id"].ToString(),
                rowData["assigned_to_queue_name"].ToString(),
                rowData["assigned_on_date"].ToString(),
                rowData["assigned_away_date"].ToString(),
                convertToWords(rowData["time_in_queue"].ToString())
                //rowData["current_assignment"].ToString()
                );
        }
        SDAuditProcessInfoTable = SDAuditProcessInfoTable.DefaultView.ToTable(true);
        return SDAuditProcessInfoTable;
    }

Finally we can use this method to get the DataTable to create our WebPart.
  
The [Styling](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=ef6ee8c6-01c1-4ff5-ac42-5df52d46df04&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) Article explains how to generate a Table, so you can use what what is shown there to loop your DT and create a HTML Table displaying the information returned from the Query.
  
---
  
Currently the Process Info WebPart supplied by Symantec assumes a Profile has been created in Process Manager which can then be used to display related data. Related data is assumed to be a 1-to-1 relationship as set out when the DBDT was created. Examples of this are ReportProcess data that have ImIncidentTicket data so single Fields can be added.
  
If we were to have multiple rows relating to a Process this can't be displayed in a WebPart, you would have to create a ![Forms (Web)](images\FormsWeb.png) WebForms Project and then have a Process Type Action added to the page to open the Form.
  
To create a WebPart for each Table would be combersome so I'm looking to develop a WebPart which allows you to pick a Table, then choose your Fields and display it that way. Look out for this soon.
  
- - -
  
[![Protirus](images\Protirus.png)](https://www.protirus.com/)
