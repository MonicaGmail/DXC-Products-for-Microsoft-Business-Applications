---
# required metadata

title: [EDI Customer]
description: [EDI Customer Documents - Review sales order]
author: [jdutoit2]
manager: Kym Parker
ms.date: 18/10/2021
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

# Review sales order

The Customer EDI module includes modifications to Sales orders. Users can access **All sales orders** page by navigating to **Sales and marketing > Orders > All sales orders**.

## Warnings/Errors
When the sales order validation resulted in a warning or error, the **EDI log** field on the sales order list page can be used to easily identify that there is an issue that might need investigation. <br>
- ![alt text](../IMAGE/Error.png "Error") Error identified with the sales order <br>
- ![alt text](../IMAGE/Warning.png "Warning")  Warning identified with the sales order <br>

To view the actual validation error messages, select the **Log** button available via the **EDI** tab on the Action Pane of the sales order. 

> Note: To setup EDI order validation, see [Setup validation profiles](../SETUP/Validation%20profiles.md) <br>
> Note: For further information relating to validation refer to the validation section(s) in the processing of [Customer purchase order](Customer%20purchase%20order.md).

## Sales order holds
EDI sales orders can be placed on hold for the following reasons. One or more order holds can apply to the sales order.

**Reason**				| **Description**
:--					|:--
Validation errors have been identified  | For further information see the Warnings/Errors section on this document
Purchase order acknowledgement is required for the customer	| Where a purchase order acknowledgement (POA) is required for a customer: <br> • **Customer purchase order acknowledgement** document must be setup on the customer trading partner's Outgoing documents. <br> • **Lock order** field in the **Customer purchase order acknowledgement**'s settings profile must be active. <br> This hold will be released once the purchase order acknowledgement has been sent to the customer.
Purchase order confirmation must be received from the customer after sending the purchase order acknowledgement | Purchase order confirmation requirements are setup via **Customer purchase order acknowledgement** settings profiles **PO confirmation required**. <br> This hold will be released once the purchase order confirmation has been received from the customer.

An order that has been placed on EDI hold will be visible via the **Hold** field on the sales order list page. 

> Note: When an order has been placed on hold, it will not be possible to release the order for picking or posting delivery notes and invoices. 

## List Page
**Field**		| **Description**
:--			|:--
EDI Log			| Used to identify that a warning or error has occurred.
POA Status		| All EDI orders requiring a POA will have an additional status to identify the status of the POA. The EDI **POA status**' available are: <br> •	**Pending** – The purchase order acknowledgement document is enabled and pending for the trading partner (POA document setting **Lock order** is _Yes_) and the order is therefore on hold. <br> • **Sent** - Purchase order acknowledgement has been sent to the customer, and a confirmation is not required (POA document setting **PO confirmation required** is _No_) <br> • **Confirm Pending** – The purchase order acknowledgment has been sent and a confirmation of the purchase order acknowledgement is required by the trading partner and the order is therefore on hold (POA doc setting **PO Confirmation required** is _Yes_ <br> • **POC Received** – The customer has returned a purchase order confirmation for the purchase order acknowledgement. 
**Hold**		| Used to identify the hold status of the EDI order
**Do not process**	| Lock sales order for processing

## Buttons
SALES AND MARKETING > SALES ORDERS > ALL SALES ORDERS > EDI TAB
Field	Description
Validation	
Validate	Select the Validate button to check validation rules for a sales order. 
Log	Select the Log button to view the validation errors that have occurred for the order. 
POA	
Acknowledgement	Option to manually review and/or process the Purchase order acknowledgement to the Customer. The Send to EDI option is also included within this form
Send to EDI	Press this button to manually create the Purchase order acknowledgement staging record. This could also be setup as periodic job.
Reset flag	Select the Reset flag button to reset the EDI status to allow for re-sending of POA to the staging table.
Change order	
Changes	Select to view all pending changes for the sales order and approve/reject each.
The form is filter to Status Pending but can be unfiltered to view automatic or previously processed manual changes. See below for more detail.
Reference	
History	See below for more detail
Trading partners	Link to Trading partner for the Sales order

### EDI Ribbon – Changes
All the EDI changes applicable to the Sales order can be manually approved or rejected on Changes. Where the Customer purchase order changes are set to be processed Manually, these would appear as pending changes on this form. All pending records will be displayed in ascending order.

Header:
Field	Description
EDI number	EDI number and link to the staging record
Status	Status of the Customer purchase order change EDI record.
Filtered to Pending.
Options are:
•	Pending: Where Processing method = Manual and the change hasn’t been approved/rejected
•	Approved: Where Processing method = Manual and the change has been manually approved and the changes applied to Sales order. If POA is required, an Accept POA record will be created.
•	Rejected: Change has been manually rejected. Sales order has not been updated. If POA is required, a Reject POA record will be created.
•	Auto: When the change has automatically been approved and applied to Sales order. Processing method is set to Automatic and all the line order change types received where set with tolerance as ‘Approve’. If POA is required, an Accept POA record will be created.
Where Processing method is set to Automatic and the line order change types received where set with tolerance as ‘Reject with warning log’: the staging record will error. These can still be viewed on Changes, but won’t be applied to Sales order.
Order purpose code	Indicates the purpose of the EDI record. Examples are:
•	Change
Created date and time	The date and time the selected record was created in the staging table
Group control number	Customer’s group control number for the staging record

Lines – contains the details for each line on the Customer purchase order change record.
Lines flagged as ‘No change’ will be ignored in the update.
Field	Description
Order line change type	The Change or Response type code. Code specifying the type of change to the line item.
Line number	The line within the EDI table/file.
Used to find applicable sales line to update. Except where adding new lines.
Item number	The item identifier as sent by the trading partner. Used when Item Id source is:
•	Our item number
External item number
Bar code	The item identifier as sent by the trading partner. Used when Item Id source is:
•	GTIN
Barcode
SKU	SKU for item
Site	Storage dimension - Site
Warehouse	Storage dimension - Warehouse
Configuration	Inventory dimension - Configuration
Colour	Inventory dimension - Colour
Size	Inventory dimension - Size
Style	Inventory dimension - Style
Customer sales quantity	The customer order quantity for this line
Customer inners	The customer’s inners per outer quantity
Customer pack	The customer’s pack quantity
Unit	The customer unit of measure for this line
Unit price	Customer unit price inclusive of discounts (net price)
Line amount excluding tax	The total line amount excluding tax.
Line amount including tax	The total line amount including tax (if provided else 0)
Requested ship date	The requested ship date (delivery window) from the EDI PO is shown here.
Requested receipt date	The requested receipt date (delivery window) from the EDI PO is shown here.
Delivery name	Address for Delivery – Delivery name
Store code	The store code from the EDI PO line is shown here.

### EDI Ribbon – History
All the EDI staging records applicable to the Sales order can be viewed on History
Field	Description
EDI Document type	EDI document type of the staging record
EDI number	EDI number and link to the staging record
Reference	Additional information for the staging record, examples:
Inbound
Original – First Customer Purchase order received. Only available via Customer purchase order document
Change – Subsequent change/s to the order. Only available via Customer purchase order change document
Cancel – Cancellation received. Can be received via Customer purchase order (if ‘EDI parameters > Allow historic PO types’ is enabled) or Customer purchase order change document
Confirmation – Confirmation received. Can be received via Customer purchase order (if ‘EDI parameters > Allow historic PO types’ is enabled) or Customer purchase order change document
Outbound
C - Purchase order acknowledgement response
ASN345435 – D365 Packing slip for the EDI ASN
IN4734743 – D365 Sales Invoice number for the EDI record.
Created date and time	Created date and time of the EDI staging record

## Header fields
SALES AND MARKETING > SALES ORDERS > ALL SALES ORDERS
After selecting the applicable sales order, the following fields have been added to the Header via the EDI fast tab.
Field	Description	EDI Source
Identification		
Original EDI number	EDI Customer purchase order staging table record id	Original PO
Change EDI number	Latest EDI Customer purchase order change staging table record id	Change PO
Company GLN	The company’s global location number is shown here.	Original PO
Customer GLN	The Customer’s global location number is shown here.	Original PO
General		
Original order date	The purchase order date from the EDI PO is shown here	Original PO
Change order date	The purchase order date from the EDI PO Change is shown here	Change PO
Advertisement Date	The advertisement date applicable for the order	Original PO
Package characteristic code	The code used to for the package contents.	Original PO
Package label code	The code used for the label.	Original PO
Store zone	The store zone from the EDI PO is shown here.	Original PO
Department	The customer’s department from the EDI PO is shown here.	Original PO
Purpose code	The customer’s purpose code from the EDI PO is shown here.	Original PO
Buyer code	The customer’s buyer code from the EDI PO is shown here.	Original PO
Retail buyer location	The customer’s retail buyer location from the EDI PO is shown here.	Original PO
EDI order type	The EDI order type is shown here.	Original PO
Order purpose code	Latest purpose code: Original, Change, Cancellation or Confirmation	Original PO / Change PO
Delivery		
Store code	The store code from the EDI PO is shown here.
Can be updated by PO Change.	Original PO / Change PO
Requested receipt date	The requested receipt date (delivery window) from the EDI PO is shown here.
Can be updated by PO Change.	Original PO / Change PO
Requested ship date	The requested ship date (delivery window) from the EDI PO is shown here.
Can be updated by PO Change.	Original PO / Change PO
Delivery time	The delivery time from the EDI PO is shown here.
Can be updated by PO Change.	Original PO / Change PO
Version		
Original version number	The PO version number from the EDI PO.	Original PO
Change version number	The latest PO version number from the EDI PO change	Change PO
Settings		
Bypass duplicate check	Used to validate the customer purchase order number.
Note: For further information see Duplicate tolerance in settings profiles
EDI > SETUP > DOCUMENT TYPES > EDI DOCUMENTS > CUSTOMER > INBOUND > PO > SETTINGS. Linked to Customer via Trading partner setup for the applicable document type via:
EDI > SETUP > TRADING PARTNERS	Determined by PO document setting
No Backorders	Identify if the trading partner accepts backorders. 
Note: Copied from the trading partner parameter and used on the POA to identify full or partial shipments
EDI > SETUP > TRADING PARTNERS	Determined by Trading partner Option
Status		
POA status	Current purchase order acknowledgement status.
This field is populated by EDI module, not editable.
Options are: 
•	Pending - The POA document setting is set to ‘Lock order’ and the POA is thus required and haven’t been sent yet.
•	Sent - The POA has been sent and a Confirmation is not required.
•	Confirm pending - The POA has been sent and a Confirmation is required. POA document setting ‘PO confirmation required’ is Yes.
•	POC Received - The Confirmation has been received from the Customer	Determined by POA document setting and if POA has been sent and/or PO confirmation received

## Line fields
SALES AND MARKETING > SALES ORDERS > ALL SALES ORDERS (EDI TAB)
After selecting the applicable sales order, the following fields have been added to the Line details via the EDI fast tab.

Field	Description
General	
Line number	EDI line number
Store code	Store code for the individual line
EDI item number	Item number as provided on EDI inbound document

SALES AND MARKETING > SALES ORDERS > ALL SALES ORDERS (POA RESPONSE TAB)
After selecting the applicable sales order, the following summary table of the POA have been added to the Line details via the POA response fast tab.
Example:
	Customer	Acknowledged	Customer code	Auto triggered
Net Price	40	41	PA (Line price – advise)	Yes
Quantity	100	100	IA (Line item – accept)	Yes
Shipment			SF (Line shipment – full)	Yes
Pack		8	PD (Line item – pack difference)	Yes
Inner	6	6	LIA (Line item – inner accept)	Yes
