---
title: Créer un groupe Microsoft 365 avec un PDL spécifique
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.collection: Strat_SP_gtc
localization_priority: Normal
description: Découvrez comment créer un groupe Microsoft 365 avec un emplacement de données par défaut spécifié dans un environnement multi-géo.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1648a9c974e7d25d989156c5a8e2d6818727a3b6
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606830"
---
# <a name="create-a-microsoft-365-group-with-a-specific-pdl"></a>Créer un groupe Microsoft 365 avec un PDL spécifique

Lorsque les utilisateurs dans un environnement multi-géo créent un groupe Microsoft 365, l’emplacement des données par défaut du groupe est automatiquement défini sur celui de l’utilisateur. Les administrateurs Exchange, SharePoint et généraux peuvent créer des groupes dans n’importe quelle région sélectionnée. 

Si vous devez créer un groupe avec un emplacement par défaut des données spécifique, vous le faire à l’aide de l’applet de commande Microsoft PowerShell New-UnifiedGroup d’Exchange Online ou à partir du Centre d’administration SharePoint. Lorsque vous procédez de la sorte, la boîte aux lettres de groupe et le site SharePoint associé à celui-ci sont configurés dans l’emplacement par défaut des données spécifié.

Pour créer un groupe Microsoft 365 avec le langage PDL que vous spécifiez, accédez au centre d’administration SharePoint à l’emplacement géographique dans lequel vous souhaitez créer le site de groupe.

Par exemple :

Si vous souhaitez créer un site de groupe à partir de votre emplacement en Australie, vous pouvez aller à https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement

1. Sélectionnez **+ Créer**.
2. Suivez le processus pour créer un site de groupe.

Votre site de groupe est configuré dans l’emplacement géographique correspondant au Centre d’administration SharePoint à partir duquel vous avez initié la demande de création de site. 

Utilisation d’Exchange PowerShell 

Connectez-vous à Exchange Online PowerShell en transmettant le paramètre *-MailBoxRegion* avec le code d’emplacement géographique.

Par exemple : 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Capture d’écran de la cmdlet PowerShell New-UnifiedGroup avec la syntaxe](media/multi-geo-new-group-with-pdl-powershell.png)

Notez que l’approvisionnement du site du groupe SharePoint est à la demande. Le site est approvisionné la première fois qu’un propriétaire ou un membre du groupe tente d’y accéder.

## <a name="geo-location-codes"></a>Codes d’emplacement géographique

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="related-topics"></a>Voir aussi

[Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
