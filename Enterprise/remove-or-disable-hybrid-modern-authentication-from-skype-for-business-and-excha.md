---
title: Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: Si vous avez activé uniquement l’authentification moderne hybride (HMA) pour qu’elle ne soit pas appropriée pour votre environnement actuel, vous pouvez désactiver la HMA. Cet article explique comment procéder.
ms.openlocfilehash: 91373adf590ad9a69880de20897795ced23d98b8
ms.sourcegitcommit: c8acfa57a22d7d055500f2e8b84a9ef252c70e82
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "36493321"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange

Si vous avez activé uniquement l’authentification moderne hybride (HMA) pour qu’elle ne soit pas appropriée pour votre environnement actuel, vous pouvez désactiver la HMA. Cet article explique comment procéder.
  
## <a name="who-is-this-article-for"></a>À qui est destiné cet article?

Si vous avez activé l’authentification moderne dans Skype entreprise Online ou en local, et/ou Exchange Online ou en local et que vous avez besoin de désactiver la haute disponibilité, ces étapes sont pour vous.

> [!IMPORTANT]
> Reportez-vous à l’article «[topologies Skype entreprise prises en charge avec l’authentification moderne](https://technet.microsoft.com/en-us/library/mt803262.aspx)» si vous êtes dans Skype entreprise Online ou en local, que vous disposez d’une mémoire HMA mixte et que vous devez consulter les topologies prises en charge avant de commencer.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Désactivation de l’authentification moderne hybride (Exchange)

1. **Exchange local**: Ouvrez l’environnement de commande Exchange Management Shell et exécutez les commandes suivantes: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Connectez-vous à Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) à l’aide de PowerShell à distance. Exécutez la commande suivante pour transformer votre indicateur *OAuth2ClientProfileEnabled* en «false»:

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Procédure de désactivation de l’authentification moderne hybride (Skype entreprise)

1. **Skype entreprise en local**: exécutez les commandes suivantes dans Skype entreprise Management Shell:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype entreprise Online**: [Connectez-vous à Skype entreprise Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) avec PowerShell à distance. Exécutez la commande suivante pour désactiver l’authentification moderne:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Revenez à la vue d’ensemble de l’authentification moderne](hybrid-modern-auth-overview.md) . 
  

