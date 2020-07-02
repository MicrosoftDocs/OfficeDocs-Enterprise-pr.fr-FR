---
title: Récupération des données des rapports du locataire d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Résumé : Utilisez Remote Windows PowerShell pour Microsoft Exchange Online pour récupérer des rapports à partir de locataires de clients individuels.'
ms.openlocfilehash: d4b8d931b6b8ea8c7b8467dd70326e1b0fbfc3d5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998623"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Récupération des données des rapports du locataire d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué

Utilisez Windows PowerShell à distance pour Microsoft Exchange Online pour récupérer des rapports à partir de locataires de clients individuels.
  
Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.
  
In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.
  
 
## <a name="before-you-begin"></a>Avant de commencer

- You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="run-the-get-stalemailboxreport-sample"></a>Exécution de l’exemple Get-StaleMailboxReport

Une fois que vous avez ouvert une session Exchange Online à distance, exécutez la commande **Get-StaleMailboxReport** pour récupérer le rapport pour la plage de dates du 25/03/2015 au 31/03/2015.
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.
  
## <a name="see-also"></a>Voir aussi

#### 

[Service web de création de rapports Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Cmdlets de création de rapports dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[Aide pour les partenaires](https://go.microsoft.com/fwlink/p/?LinkID=533477)

