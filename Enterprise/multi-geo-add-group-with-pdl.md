---
title: Créer un groupe Office 365 avec un emplacement par défaut des données spécifique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez comment créer un groupe Office 365 avec un emplacement par défaut des données spécifique dans un environnement multigéographique.
ms.openlocfilehash: a46a34d9fd5be9b3acda5ee3859f4eed08797b7c
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30933988"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a>Créer un groupe Office 365 avec un emplacement par défaut des données spécifique

Quand un utilisateur dans un environnement multigéographique crée un groupe Office 365, l’emplacement par défaut des données du groupe est automatiquement défini sur celui de l’utilisateur. Si vous devez créer un groupe avec un emplacement par défaut des données spécifique, vous le pouvez en utilisant la cmdlet Microsoft PowerShell New-UnifiedGroup d’Exchange Online. Lorsque vous procédez de la sorte, la boîte aux lettres de groupe et le site SharePoint associé à celui-ci sont approvisionnés dans l’emplacement par défaut des données spécifié.

Pour faire cela, vous devez être un administrateur général ou un administrateur SharePoint Online ou Exchange Online.

Pour créer un groupe Office 365 avec l’emplacement par défaut des données que vous spécifiez, connectez-vous à Exchange Online PowerShell en transmettant le paramètre *-MailBoxRegion* avec le code d’emplacement géographique.

Par exemple : 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Capture d’écran de la cmdlet PowerShell New-UnifiedGroup avec la syntaxe](media/multi-geo-new-group-with-pdl-powershell.png)

Notez que l’approvisionnement du site du groupe SharePoint est à la demande. Le site est approvisionné la première fois qu’un propriétaire ou un membre du groupe tente d’y accéder.

## <a name="geo-location-codes"></a>Codes d’emplacement géographique

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>Voir aussi

[Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)