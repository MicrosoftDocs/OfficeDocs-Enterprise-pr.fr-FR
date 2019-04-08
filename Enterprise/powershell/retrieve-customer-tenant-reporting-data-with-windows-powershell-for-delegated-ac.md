---
title: Récupération des données des rapports du locataire d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Résumé : Utilisez Remote Windows PowerShell pour Microsoft Exchange Online pour récupérer des rapports à partir de locataires de clients individuels.'
ms.openlocfilehash: 8df88e8b00cbd8e14558e423f41f45ea5f9bf26a
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001757"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Récupération des données des rapports du locataire d’un client avec Windows PowerShell pour les partenaires avec autorisation d’accès délégué

 **Résumé :** Utilisez Remote Windows PowerShell pour Microsoft Exchange Online pour récupérer des rapports à partir de locataires de clients individuels.
  
Partenaires de syndication et fournisseur de solutions cloud peut accéder aux données qui composent les rapports des locataires des clients directement via Remote Windows PowerShell pour Exchange Online. Cela permet aux partenaires de recueillir et d'enregistrer les données des rapports et de s'en servir pour effectuer d'autres opérations. Après avoir ouvert une connexion à distance, la récupération des données de création de rapports sur une location client est identique à l'exécution de n'importe quelle cmdlet sur la location d'un client.
  
Dans cet article, vous utilisez Remote Windows PowerShell pour Exchange Online afin de vous connecter à une location de client unique et récupérer un rapport. Par défaut, Windows PowerShell ne prend pas en charge le regroupement des données des rapports à partir de plusieurs locations de clients. Les rapports que vous récupérez avec cette procédure ne sont destinés qu'aux organisations déléguées ( _DelegatedOrg_) auxquelles vous vous connectez.
  
Si vous voulez récupérer un rapport unique pour toutes les locations de votre client, vous trouverez un exemple de script pour ce faire dans [Regroupement des données des rapports d'un client via Windows PowerShell pour les partenaires avec autorisation d'accès délégué](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md).
  
## <a name="before-you-begin"></a>Avant de commencer

- Vous devez vous connecter à votre locataire Exchange Online à l'aide de Remote Windows PowerShell Pour plus d'informations, voir [Connexion à des locataires Exchange Online avec Remote Windows PowerShell pour les partenaires avec autorisations d'accès délégué](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="run-the-get-stalemailboxreport-sample"></a>Exécution de l’exemple Get-StaleMailboxReport

Une fois que vous avez ouvert une session Exchange Online à distance, exécutez la commande **Get-StaleMailboxReport** pour récupérer le rapport pour la plage de dates du 25/03/2015 au 31/03/2015.
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Il existe plusieurs autres cmdlets que vous pouvez utiliser pour la création de rapports pour Exchange Online, Lync Online et SharePoint Online, ainsi que d'autres cmdlets pour le suivi des messages. Pour en savoir plus sur les cmdlets de création de rapports disponibles et le service web de création de rapports Office 365, voir les rubriques dans la section suivante.
  
## <a name="see-also"></a>Voir aussi

#### 

[Service web de création de rapports Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Cmdlets de création de rapports dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[Aide pour les partenaires](https://go.microsoft.com/fwlink/p/?LinkID=533477)

