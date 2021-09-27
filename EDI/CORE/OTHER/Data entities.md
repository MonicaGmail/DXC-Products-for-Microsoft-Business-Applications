---
# required metadata

title: [EDI Core]
description: [EDI Core - Data entities]
author: [jdutoit2]
manager: Kym Parker
ms.date: 27/09/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: [Application User]
# ms.devlang: 
ms.reviewer: [jdutoit2]
ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [author's Microsoft alias]
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# Data entities

The following is a summary of data entities available for the core EDI module:

## Parameters

**Order**         | **Entity**
:-----------------|:------------------------------------
1                 | EDI parameters
2                 | EDI Shared Parameters

## Connections

**Order**         | **Entity**
:-----------------|:------------------------------------
1		  | EDI FTP sites

## Core setup

**Order**         | **Entity**
:-----------------|:------------------------------------
1		  | UOM mapping
2	          | UOM mapping lines
3		  | Cleanup profile
4		  | Cleanup profile line
5		  | Functional acknowledgement document type mapping
6		  | Functional acknowledgement document type mapping lines
7		  | Reset status profile

## Core document setting profiles

**Order**         | **Entity**
:-----------------|:------------------------------------
1		  | EDI settings - Functional acknowledgement inbound
2		  | EDI settings - Functional acknowledgement outbound

## Document types

**Order**         | **Entity**				
:-----------------|:------------------------------------
1		  | EDI Template file
2		  | EDI Template file section
3		  | EDI Template file line section
4		  | EDI Template XSLT
5		  | EDI template XSLT collection
6		  | EDI template JSON
7		  | EDI template JSON collection
8		  | EDI template code transformation
9		  | EDI Validation profile
10		  | EDI Validation profile line
11		  | EDI Outbound file names
12		  | EDI Field metadata


The following entities are applicable to all EDI - Standard format module:
**Section** 	                  | **Order**         | **Entity**		 	    | **Description**
:-------------------------------- |:------------------|:------------------------------------
**Document type**		  | 1	                               | EDI Template EDIFACT         | Create new **EDIFACT** template and setup
	2	                               | EDI Template EDIFACT section | Section details for the **EDIFACT** template
3	                               | EDI Template EDIFACT element | Element details for each section for the **EDIFACT** template