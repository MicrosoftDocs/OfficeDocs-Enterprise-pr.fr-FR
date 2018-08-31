---
title: Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
description: Si vous avez activé hybride modernes d’authentification (zone) uniquement pour rechercher qu'il convient pour votre environnement actuel, vous pouvez désactiver la zone. Cet article explique comment.
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540567"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange

Si vous avez activé hybride modernes d’authentification (zone) uniquement pour rechercher qu'il convient pour votre environnement actuel, vous pouvez désactiver la zone. Cet article explique comment.
  
## <a name="who-is-this-article-for"></a>Qui est destiné cet article ?

Si vous avez activé authentification moderne dans Skype pour Business en ligne ou sur site, et/ou Exchange Online ou sur site et vous devez désactiver la zone de trouver, ces étapes sont pour vous.
  
 **Important** Consultez l’article « [Skype pour les topologies d’entreprise pris en charge avec l’authentification moderne](https://technet.microsoft.com/en-us/library/mt803262.aspx)» si vous êtes dans Skype pour Business en ligne ou sur site, ont une zone topologie mixte et à examiner les topologies prises en charge avant de commencer.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Comment faire pour désactiver l’authentification moderne hybride (Exchange)

1. **Exchange local**: ouvrez Exchange Management Shell et exécutez la commande suivante. 
    
1. Set-OrganizationConfig-OAuth2ClientProfileEnabled $false
    
2. Set-AuthServer-Identity evoSTS IsDefaultAuthorizationEndpoint - $false
    
2. **Exchange Online**: se connecter à Exchange Online PowerShell à distance. Exécutez la commande suivante pour activer l’indicateur *OAuth2ClientProfileEnabled* sur « false ». 
    
1. Set-OrganizationConfig-OAuth2ClientProfileEnabled : $false
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Comment faire pour désactiver l’authentification moderne hybride (Skype pour les entreprises)

1. **Skype pour Business local**: exécutez les commandes suivantes dans Skype pour Business Management Shell.
    
1. Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity « »
    
2. **Skype pour les entreprises en ligne**: se connecter à Skype pour les entreprises en ligne avec PowerShell à distance. Exécutez la commande suivante pour désactiver l’authentification moderne. 
    
1. Set-CsOAuthConfiguration - ClientAdalAuthOverride interdit
    
[Lien vers la vue d’ensemble de l’authentification moderne](hybrid-modern-auth-overview.md) . 
  
