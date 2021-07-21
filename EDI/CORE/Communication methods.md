---
# required metadata

title: [EDI Communication methods]
description: [Overview of the EDI communication methods]
author: [jdutoit2]
manager: Kym Parker
ms.date: 21/07/2021
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

# Communication methods

## Communication methods overview
Various communication methods (FTP, FTPS, SFTP, Azure cloud blob storage and web services) can be used to:
- Import EDI documents from the VAN or Trading partner and/or
- Export EDI documents generated within D365to the VAN or Trading partner.

### Setting up FTP Sites
**EDI > Setup > Connection setup > FTP sites**
FTP is a communication method that can be used for this module. FTPS and FTP protocols are supported. 
The FTP sites setup form holds the information required to connect to, retrieve and create files in/from FTP sites as well as the EDI document paths in the FTP site.

#### Create a new site configuration
To begin, create a new FTP site record and fill out the connection parameters
| **Field**                         | **Description**                      | 
| :-------------------------------- |:-------------------------------------| 
| Site name                 | Specify a **Name** for the FTP site |
| Active                    | Indicates if the site is active. <br> To activate, select the **Activate** button available in the ribbon. <br> To deactivate, select the **Deactivate** button available in the ribbon. |
| **Connection**            |  |
| Host                 		| Specify the **Host** for the FTP site <br> *Note: FTP:// is not required* |
| Port                 		| Specify the **Port** for the FTP site|
| Enable TLS          		| Select to enable FTPS using TLS |
| **Credentials**      		|  |
| User                 		| Specify the **Username** used for authentication to the FTP site |
| Password                  | Specify the Password used for authentication to the FTP site. <br> *Note: this is encrypted and displayed as ……. within the form.* |

*Note: Select **Test Connection** to confirm that a connection can be made with the FTP site specified.*

#### Site paths
It is possible to configure a different FTP site path per EDI document type.
A common way to configure this is to setup a FTP site for the UAT environment versus the PROD environment so the PROD database can easily be rolled over into the UAT environment by simply changing the active site.
Incoming documents have 2 paths that are required to be defined:
- Inbound
- Archive

Select **Populate paths** on the Action pane, to create the incoming and outgoing paths for all the licensed documents.

| **Field**                         | **Description**                      | 
| :-------------------------------- |:-------------------------------------| 
| EDI document type                 | Specify the **Document type** the path relates to |
| Type                				| The type of path: <br> **Inbound** - The path the EDI document files will be retrieved from <br> **Archive** - Once the file has been pulled from the inbound path it will be moved to this path |
| Search mode		                | Specify to use either the Trading partner’s **Search mask** as prefix or suffix to identify ‘who’ the file is from. <br> Options: <br> **File name must start with** – Filename must start with Trading partner’s Search mask <br> **File name must end with** – Filename must end with Trading partner’s Search mask |
| Path			                    | Specify the FTP path |

Outgoing documents have a single path that is required to be defined

| **Field**                         | **Description**                      | 
| :-------------------------------- |:-------------------------------------| 
| EDI document type                 | Specify the **Document type** the path relates to |
| Path			                    | Specify the FTP path where the outbound file will be saved |

*Note: Each site path can be tested to ensure it is valid by selecting the path records to be tested and pressing the **Test path connection** button on the Incoming and/or Outgoing path's toolbar. <br> The results will be shown on the far right of the grid.*

### Setting up SFTP Sites
**EDI > Setup > Connection setup > SFTP sites**
The SFTP sites setup form holds the information required to connect to, retrieve and create files in/from SFTP sites as well as the EDI document paths in the SFTP site.

#### Create a new site configuration
To begin, create a new SFTP site record and fill out the connection parameters

| **Field**                         | **Description**                      | 
| :-------------------------------- |:-------------------------------------| 
| Site name                 	| Specify a **Name** for the SFTP site |
| Active                   	    | Indicates if the site is active. <br> To activate, select the **Activate** button available in the ribbon. <br> To deactivate, select the **Deactivate** button available in the ribbon. |
| **Connection**            	|  |
| Host                 			| Specify the **Host** for the SFTP site <br> *Note: SFTP:// is not required* |
| Port                 			| Specify the **Port** for the SFTP site|
| **Credentials**      			|  |
| User                 			| Specify the **Username** used for authentication to the SFTP site |
| Password                  	| Specify the **Password** used for authentication to the SFTP site. <br> *Note: this is encrypted and displayed as ……. within the form.* |
| **Proxy** (where applicable)  	|  |
| Proxy type                 	| Select the applicable **Proxy type**, options <br> - Socks4 <br> - Socks5 <br> - Http |
| Proxy host 	             	| Specify the **Proxy host** for the SFTP site |
| Proxy port                 	| Specify the **Proxy port** for the SFTP site |
| Proxy user name              	| Specify the **Proxy username** used for authentication to the SFTP site |
| Proxy password               	| Specify the **Proxy password** used for authentication to the SFTP site. <br> *Note: this is encrypted and displayed as ……. within the form.* |
| **Private key** (where applicable) 	|  |
| Private key                 	| Specify the **Private key** used for authentication to the SFTP site |
| Pass phrase                 	| Specify the **Pass phrase** used for authentication to the SFTP site |

*Note: Select Test Connection to confirm that a connection can be made with the SFTP site specified.*

#### Site paths
It is possible to configure a different SFTP site path per EDI document type.
A common way to configure this is to setup a SFTP site for the UAT environment versus the PROD environment so the PROD database can easily be rolled over into the UAT environment by simply changing the active site. 
Incoming documents have 2 paths that are required to be defined:
- Inbound
- Archive

Select **Populate paths** on the Action pane, to create the incoming and outgoing paths for all the licensed documents.

| **Field**                         | **Description**                      | 
| :-------------------------------- |:-------------------------------------| 
| EDI document type                 | Specify the **Document type** the path relates to |
| Type                				| The type of path: <br> **Inbound** - The path the EDI document files will be retrieved from <br> **Archive** - Once the file has been pulled from the inbound path it will be moved to this path |
| Search mode		                | Specify to use either the Trading partner’s **Search mask** as prefix or suffix to identify ‘who’ the file is from. <br> Options: <br> **File name must start with** – Filename must start with Trading partner’s Search mask <br> **File name must end with** – Filename must end with Trading partner’s Search mask |
| Path			                    | Specify the SFTP path |

Outgoing documents have a single path that is required to be defined

| **Field**                         | **Description**                      | 
| :-------------------------------- |:-------------------------------------| 
| EDI document type                 | Specify the **Document type** the path relates to |
| Path			                    | Specify the SFTP path where the outbound file will be saved |

*Note: Each site path can be tested to ensure it is valid by selecting the path records to be tested and pressing the **Test path connection** button on the Incoming and/or Outgoing path's toolbar. <br> The results will be shown on the far right of the grid.*
