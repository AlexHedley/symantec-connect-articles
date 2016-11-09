---
title: Workflow - Component - Developer Guide - SQL
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-11-09
---

In this Article I'm going to explain how to talk to SQL.
  
- [List](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2f07f920-0cbd-4be4-83a8-c6180eee3092&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Setup](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=17aa2b9a-9092-40d0-afab-a6d8316de97d&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Simple Component](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=86d55504-8f8e-41c7-9eff-ad882326a8f7&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Deploy](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=70a9fde5-0d87-4b9d-a3be-0907567ffc00&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Help File](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=80437c69-ccc3-47e6-a850-9cf3f301b340&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Logging](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=63b72a9a-53b8-4d4b-bce3-5f0732b134d5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- Inputs
    - [Checkbox](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=74c56ef7-1119-40fe-9d5f-3c7a1d808d4c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
    - [Dropdown / Combo](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=267159ac-b8e7-45b4-abe4-f85d78e30783&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Inspecting](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=2c3b3a6f-01d7-4157-a143-ba30c9edc930&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) other Components
- [Creating Globals](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=cf54de06-be56-46ff-b937-148efa57eaec&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Creating Project Properties](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=4cfc07c5-404e-49b3-81b6-520d4ea43d5c&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Working with SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f3cf0097-06e7-42f3-a747-d0dff319c1e5&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [Working with a Web Service](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=26368883-708b-4432-999b-7064f2f25794&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

Build a component like previous Articles have shown.

Now we can create a method that gets some information from SQL.
  
I would add a new input to the Component that's a SQL Connection String, this makes it easier to manage and configure.
  
The following could be added to your **Run** method.
  
We need a SQL Connection first.

    using (SqlConnection DbConn = new SqlConnection(dbConnStr))
    {
    }

Where *dbConnStr* is retrieved from the Property.
  
Now declare your SQL string.

    string sql = "SELECT DISTINCT vC.[Guid] [ComputerGuid] ,vC.[Name] [ComputerName] ,vC.[IP Address] [ComputerIPAddress] ,TC.[Subnet Mask] [ComputerSubnetMask] FROM vComputer vC JOIN Inv_AeX_AC_TCPIP TC on vC.Guid = TC._ResourceGuid WHERE Name = @ComputerName";

Your SQL could be anything but here's a string to get some information from a Computer in the SMP.

    SELECT DISTINCT 
      vC.[Guid] [ComputerGuid] 
      ,vC.[Name] [ComputerName] 
      ,vC.[IP Address] [ComputerIPAddress] 
      ,TC.[Subnet Mask] [ComputerSubnetMask] 
    FROM 
      vComputer vC 
      JOIN Inv_AeX_AC_TCPIP TC on vC.Guid = TC._ResourceGuid 
    WHERE 
      Name = @ComputerName

Next we need a *SQLCommand*, pass both the *sql* string and the Connection (*DbConn*)

    using (SqlCommand sqlCommand = new SqlCommand(sql, DbConn))
    {
    }

Set the appropriate properties

    sqlCommand.CommandText = sql.ToString();
    sqlCommand.Connection = DbConn;
    sqlCommand.CommandType = CommandType.Text;

If you have any parameters you can set them here too
  
I've passed in the *computerName* as a parameter.

    sqlCommand.Parameters.Add("@ComputerName", SqlDbType.NVarChar);
    sqlCommand.Parameters["@ComputerName"].Value = computerName;

Finally we need to Open the connection and Execute the command.

    DbConn.Open();
    SqlDataReader dataReader = sqlCommand.ExecuteReader();

If we've opened it we need to close it, good use for a try/catch/finally statement.

    try
    {
    }
    catch (Exception ex)
    {
    }
    finally
    {dataReader.Close();
    }

Inside your try statement let's check for data/records and do something with them.

    if (dataReader.HasRows)
    {
        while (dataReader.Read())
        {
            Guid computerGuid = dataReader.GetGuid(0);
            string strComputerName = dataReader.GetString(1);
            string strComputerIPAddress = dataReader.GetString(2);
            string strComputerSubnetMask = dataReader.GetString(3);
            
            //Do something
        }
    }

Full code

    private void GetComputerInfo(IData data, string dbConnStr, string computerName, bool logAllErrors)
    {using (SqlConnection packageServerDbConn = new SqlConnection(dbConnStr)){	string sql = "SELECT DISTINCT vC.[Guid] [ComputerGuid] ,vC.[Name] [ComputerName] ,vC.[IP Address] [ComputerIPAddress] ,TC.[Subnet Mask] [ComputerSubnetMask] FROM vComputer vC JOIN Inv_AeX_AC_TCPIP TC on vC.Guid = TC._ResourceGuid WHERE Name = @ComputerName";		using (SqlCommand getComputerInfoCommand = new SqlCommand(sql, packageServerDbConn))	{		getComputerInfoCommand.CommandText = sql.ToString();		getComputerInfoCommand.Connection = packageServerDbConn;		getComputerInfoCommand.CommandType = CommandType.Text;
    		getComputerInfoCommand.Parameters.Add("@ComputerName", SqlDbType.NVarChar);		getComputerInfoCommand.Parameters["@ComputerName"].Value = computerName;
    		packageServerDbConn.Open();
    		SqlDataReader dataReader = getComputerInfoCommand.ExecuteReader();
    		try		{			//get data			if (dataReader.HasRows)			{				while (dataReader.Read())				{					//ComputerGuid	                        ComputerName	ComputerIPAddress	ComputerSubnetMask					//3582B4B5-E3BC-41E1-8E18-07A0AA6E848D	PROTIRUS026	    10.10.100.156	    255.255.255.0					Guid computerGuid = dataReader.GetGuid(0);					string strComputerName = dataReader.GetString(1);					string strComputerIPAddress = dataReader.GetString(2);					string strComputerSubnetMask = dataReader.GetString(3);										ComputerType c = new ComputerType();					c.Id = computerGuid;					c.IpAddress = strComputerIPAddress;					c.Subnet = strComputerSubnetMask;					c.Name = strComputerName;					this.computers.Add(c);				}			}			else			{				base.LogError(data, "No rows found.");			}		}		catch (Exception ex)		{			if (logAllErrors)			{				base.LogError(data, ex.Message);			}		}		finally		{			dataReader.Close();		}	}}
    }

![Protirus](images\Protirus.png)
