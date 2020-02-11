---
title: ServiceDesk - Software Request Process - SQL
tags:
    - ServiceDesk
    - Software Request Process
author: AlexHedley
# description: 
# articleId: 
published: 2017-10-10
# symantecUrl:
broadcomUrl: https://community.broadcom.com/symantecenterprise/viewdocument/servicedesk-software-request-proc-3?CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&tab=librarydocuments
---

In this series of Articles I'm going to explain how the new **Software Request Process** works in [ServiceDesk](https://www.symantec.com/products/service-desk) 8.1, this will cover the new Tables that have been created to store the Software Request data.

Table Of Contents
  
- [Index](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=253f9b2f-045e-4e05-acb9-fcc37005f674&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Overview](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=a5fdba6d-707b-44be-a051-b08e5a5cfe19&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [Config](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=e3acdfdc-8b09-4ca7-afb5-821c9cce9301&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SMP](https://www.symantec.com/connect/articles/servicedesk-software-request-process-smp)
- [Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=24530d5f-01a3-464d-846b-01482ee0c85e&amp;CommunityKey=206bac34-051d-4ea1-b726-4ea8778c1986&amp;tab=librarydocuments)
- [Hidden Reports](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f39346c9-799f-4d1b-ba9b-7f0910cd9c74&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [SQL](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=28879800-dd5e-436b-8f8b-9bc7301fbb1e&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments) (this)
- [WFs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=736fee28-7f45-497e-b208-b3de50cde839&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)
- [DLLs](https://community.broadcom.com/symantecenterprise/viewdocument?DocumentKey=f4cef159-76c3-4b5b-9287-94aee6bec214&amp;CommunityKey=04ead5e9-3643-4118-b853-afa5a58710c6&amp;tab=librarydocuments)

So we all know and love ReportProcess, obviously this is still being used as this is a new Process in SD.
  
There are two new Ticket types

- Software Request
- Software Delivery

They have their own ReportProcess prefixes

- SR-#
- SD-#

And their own Data Types

- RequestTicket = ServiceDesk.SoftwareRequest.Core.DataTypes.SoftwareRequest;
- SoftwareTicket = ServiceDesk.SoftwareRequest.Core.DataTypes.RequestedSoftware;

Each has it's own Process

- ServiceDesk.SoftwareRequest.Approval
- ServiceDesk.SoftwareRequest.Delivery

If you look into the the SQL tables they are called

- SrSoftwareRequest
- SrRequestedSoftware

Everything is Task based so you will still need to be familar with the Task table and how that works.
  
There are also [*ReportProcessRelationship*]s which link the Request to the Delivery.

ServiceIds

- SD-SR-APPROVAL
- SD-SR-DELIVERY

[![Protirus](images\Protirus.png)](https://protirus.com/)
