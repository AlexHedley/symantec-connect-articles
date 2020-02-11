---
title: SMP - ASDK - Web Service - Report With Parameter
tags:
    - SMP
    - ASDK
author: AlexHedley
# description: 
articleId: 3841861
published: 2019-07-11
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/smp-asdk-web-service-report-w?CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&tab=librarydocuments
---

There's times you wish to get data from the SMP but don't have access to the DB.
  
Instead you could create a Report that contains this data then use the Report Management Web Services to retrieve this data.
  
One extra option to make the Report more useful is to add parameters so you can pre-filter the data.

I've created a simple report that returns the UserGuid based on a username search.

    SELECT 
      [Guid] AS [UserGuid] 
    FROM 
      [vUser]
    WHERE 
      Name LIKE '%' + '%UserName%' + '%'

We can use the ReportManagement WebService to achieve this.
  
- http://localhost/altiris/asdk.ns/ReportManagementService.asmx?op=RunReportWithParameters

| Parameter | Value |
| --- | --- |
| reportItemGuid |  |
| nameValuePairs |  |

You can see the SOAP request on the webpage

    POST /altiris/asdk.ns/ReportManagementService.asmx HTTP/1.1
    Host: localhost
    Content-Type: text/xml; charset=utf-8
    Content-Length: length
    SOAPAction: "http://Altiris.ASDK.NS.com/RunReportWithParameters"

    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
      <soap:Body>
        <RunReportWithParameters xmlns="http://Altiris.ASDK.NS.com">
          <reportItemGuid>string</reportItemGuid>
          <nameValuePairs>string</nameValuePairs>
        </RunReportWithParameters>
      </soap:Body>
    </soap:Envelope>

Response

    HTTP/1.1 200 OK
    Content-Type: text/xml; charset=utf-8
    Content-Length: length

    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
      <soap:Body>
        <RunReportWithParametersResponse xmlns="http://Altiris.ASDK.NS.com">
          <RunReportWithParametersResult>xml</RunReportWithParametersResult>
        </RunReportWithParametersResponse>
      </soap:Body>
    </soap:Envelope>

If you are on the ![SMP](images\smp.png) SMP server you can test it out.
  
Get the ReportGuid from your ![Report](images\Report.png) Report.
  
Then we need a "Name Value Pair" of our input:

    UserName=Alex.Hedley

Output

    <?xml version="1.0" encoding="UTF-8"?>
    <NewDataSet>
        <xs:schema xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" 
            xmlns:xs="http://www.w3.org/2001/XMLSchema" 
            xmlns="" id="NewDataSet">
            <xs:element msdata:UseCurrentLocale="true" msdata:IsDataSet="true" name="NewDataSet">
                <xs:complexType>-                <xs:choice maxOccurs="unbounded" minOccurs="0">
                        <xs:element name="Table">
                            <xs:complexType>
                                <xs:sequence>
                                    <xs:element name="UserGuid" minOccurs="0" type="xs:string" msdata:DataType="System.Guid, mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
                                </xs:sequence>
                            </xs:complexType>
                        </xs:element>
                    </xs:choice>
                </xs:complexType>
            </xs:element>
        </xs:schema>
        <Table>
            <UserGuid>23f904fe-a273-47e1-a48f-2cf08aa6bbc3</UserGuid>
        </Table>
    </NewDataSet>

As you can see we get a Table that contains the Rows brought back from the SQL we wrote above.

    <Table>
        <UserGuid>23f904fe-a273-47e1-a48f-2cf08aa6bbc3</UserGuid>
    </Table>

Now create a script to get this data remotely, lets use PowerShell
  
Replace the ## with the values you'd need.

    $smpServer = "#SERVERNAME#"
    $UserName = "#USERNAME#"
    
    $reportItemGuid = '#00000000-0000-0000-0000-000000000000#' #UserInfo
    $params = "UserName=$UserName"
    
    $where = "http://$smpServer/altiris/asdk.ns/ReportManagementService.asmx"
                
    $ws = New-WebServiceProxy -uri $where -UseDefaultCredential
    
    $wsResult = $ws.RunReportWithParameters($reportItemGuid, $params)
    if ($wsResult.Errors.length -gt 0){
        $result = $wsResult.Errors[0]
    }
    else
    {     
        $result = $wsResult.Table
    }
    $result

And then the output

    UserGuid                            
    --------                            
    00000000-0000-0000-0000-000000000000

And now we have a way to get data from Altiris with any inputs we need.
