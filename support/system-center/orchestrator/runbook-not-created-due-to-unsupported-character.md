---
title: An Orchestrator runbook isn't created
description: Describes an issue in which an Orchestrator runbook isn't created when a Service Manager service request passes an unsupported character.
ms.date: 08/04/2020
ms.prod-support-area-path:
---
# An Orchestrator runbook isn't created when users submit a Service Manager service request form

This article helps you fix an issue where an Orchestrator runbook isn't created when a Service Manager service request passes an unsupported character.

_Original product version:_ &nbsp; System Center 2016 Orchestrator, Microsoft System Center 2012 R2 Orchestrator, Microsoft System Center 2012 Orchestrator, System Center 2016 Service Manager, System Center 2012 R2 Service Manager, System Center 2012 Service Manager  
_Original KB number:_ &nbsp; 2993719

## Symptoms

When users submit a Microsoft System Center Service Manager service request form that calls a Microsoft System Center Orchestrator runbook, a runbook seems to run. However, a runbook is not created or processed.

Additionally, you may see the following error in the Orchestrator Runbook Service trace log:

> \<MsgCode>_com_error\</MsgCode>  
> \<Params>  
> \<Param>IDispatch error #3092\</Param>  
> \<Param>The XML parse error 0xc00ce513 occurred on line number 1, near the XML text "\<Data>\<Parameter>\<ID>{80a3059b-1226-4870-aa85-6613e19f1119}\</ID>\<Value>**nnnn nnn nnn**\</Value>\</Parameter>\<Parameter>\<ID>{5760f6bd-348a-4560-834c-db71ad080863}\</ID>\<Value>**JobTitle**\</Value>\</Parameter>\<Parameter>\<ID>{52065c75-76ed-4a9d-aacc-abc0c5f80e6c}\</ID>\<Value>Servers & Clients\</Value>\</Parameter>\<Parameter>\<ID>{2bf229ae-fe93-49d9-966e-4895c9685e50}\</ID>\<Value>**LastName**\</Value>\</Parameter>\<Parameter>\<ID>{2bf8e7e5-039e-45ba-8b94-f07d258cc703}\</ID>\<Value>\</Value>\</Parameter>\<Parameter>\<ID>{3c10a408-87ac-40dc-a95a-fe679824f9f1}\</ID>\<Value>11/28/2014 12:00:00 AM\</Value>\</Parameter>\<Parameter>\<ID>{dd2138dc-116d-4453-9af6-d42202c74827}\</ID>\<Value>AB49362\</Value>\</Parameter>\<Parameter>\<ID>{908fc0b5-b9b4-4d8c-bce7-970ca314a90d}\</ID>\<Value>**FirstName**\</Value>\</Parameter>\</Data>".\</Param>  
>
> \<Param>-2147217900\</Param>  
>
> \</Params>

## Cause

This issue can occur if the XML file that is transferred from Service Manager contains an ampersand (&). This is one of the predefined entity references in XML and is not valid as a runbook input parameter.

## Resolution

To prevent this issue from occurring, use the following regular expression to limit the characters that can be input. This makes sure that an ampersand cannot be input.

> [!NOTE]
> There is a space after the question mark.

`^[a-zA-Z0-9~!@#$%*()-=+;:,.? ]+$`