---
# required metadata

title: [DXC Item Creation Wizard ]
description: [DXC Item Creation Wizard - Update item status  ]
author: [Liam Coll]
manager: Kym Parker
ms.date: 02/03/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [DXC Item Creation Wizard ]
audience: [Application User]
# ms.devlang: 
ms.reviewer: [helenho]
ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [helenho]
ms.search.validFrom: [September 2017]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

## Update item status

A periodic job is available that can update the item status with a specified effective date, this can be run for a range of items. Category hierarchy can be used to help select these products to be included. This allows for item status to be planned and updated prior to the effective date. The periodic job can be accessed from **Item creation > Periodic tasks > Update item status**.

1.	Select the *From Status*, only the selected items matching this status will be updated.
2.	Select the *To Status*.
3.	Enter an *Effective date* if required.  
    * To make effective immediately, leave blank.
4.	Select a *Category hierarchy* if required to filter down to a group of products.
5.	Select the items to be updated. 
6.	Select OK.

*Note: Optionally select the Run in the background tab to run in batch processing. Please see [Microsoft User Guides](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/batch-processing-overview) for further information*
