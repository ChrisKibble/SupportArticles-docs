---
title: VDS Basic Provider event ID 1
description: Describes an issue in a Hyper-V guest operating system of Windows Server 2008 R2 or of Windows 7 in which the VDS Basic Provider event ID 1 is logged.
ms.date: 10/21/2020
author: Deland-Han
ms.author: delhan
manager: dscontentpm
audience: itpro
ms.topic: troubleshooting
ms.prod: windows-server
localization_priority: medium
ms.reviewer: kaushika, tyagi, adityah
ms.prod-support-area-path: Configuration of virtual machine settings
ms.technology: HyperV 
---
# VDS Basic Provider event ID 1 is logged in a Hyper-V guest operating system

This article discusses an issue in a Hyper-V guest operating system where Virtual Disk Service (VDS) Basic Provider event ID 1 is logged.

_Original product version:_ &nbsp; Windows 7 Service Pack 1, Windows Server 2008 R2 Service Pack 1  
_Original KB number:_ &nbsp; 979391

## Symptoms

Consider the following scenario:

- You have a Hyper-V guest operating system that is running Windows Server 2008 R2 or Windows 7.
- The guest operating system has a disk that is connected to a SCSI controller.

In this scenario, the following event is logged in the System log:

> Event Type: Error  
Event Source: Virtual Disk Service  
Event Category: None  
Event ID: 1  
Date:Date  
Time:Time  
User: N/A  
Computer:computer name  
Description: Unexpected failure. Error code:exception code

## Cause

The VDS looks for the Location paths property of the controller. The value of this property is the path location of the disk. However, a virtual controller doesn't have this property.

## Resolution

This event can be safely ignored.