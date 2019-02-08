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
ms.openlocfilehash: 802add6295edffe3ec80e70e9bd70663479ec61a
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25359026"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="d847f-104">Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange</span><span class="sxs-lookup"><span data-stu-id="d847f-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="d847f-p102">Si vous avez activé hybride modernes d’authentification (zone) uniquement pour rechercher qu'il convient pour votre environnement actuel, vous pouvez désactiver la zone. Cet article explique comment.</span><span class="sxs-lookup"><span data-stu-id="d847f-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="d847f-107">Qui est destiné cet article ?</span><span class="sxs-lookup"><span data-stu-id="d847f-107">Who is this article for?</span></span>

<span data-ttu-id="d847f-108">Si vous avez activé authentification moderne dans Skype pour Business en ligne ou sur site, et/ou Exchange Online ou sur site et vous devez désactiver la zone de trouver, ces étapes sont pour vous.</span><span class="sxs-lookup"><span data-stu-id="d847f-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d847f-109">Consultez l’article «[Skype pour les topologies d’entreprise pris en charge avec l’authentification moderne](https://technet.microsoft.com/en-us/library/mt803262.aspx)» si vous êtes dans Skype pour Business en ligne ou sur site, ont une zone topologie mixte et à examiner les topologies prises en charge avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="d847f-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="d847f-110">Comment faire pour désactiver l’authentification moderne hybride (Exchange)</span><span class="sxs-lookup"><span data-stu-id="d847f-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="d847f-111">**Exchange local**: ouvrez Exchange Management Shell et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="d847f-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="d847f-p103">**Exchange Online**: [se connecter à Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) PowerShell à distance. Exécutez la commande suivante pour activer l’indicateur *OAuth2ClientProfileEnabled* sur « false » :</span><span class="sxs-lookup"><span data-stu-id="d847f-p103">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="d847f-114">Comment faire pour désactiver l’authentification moderne hybride (Skype pour les entreprises)</span><span class="sxs-lookup"><span data-stu-id="d847f-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="d847f-115">**Skype pour Business local**: exécutez les commandes suivantes dans Skype pour Business Management Shell :</span><span class="sxs-lookup"><span data-stu-id="d847f-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="d847f-p104">**Skype pour les entreprises en ligne**: [se connecter à Skype pour les entreprises en ligne](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) avec PowerShell à distance. Exécutez la commande suivante pour désactiver l’authentification moderne :</span><span class="sxs-lookup"><span data-stu-id="d847f-p104">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell. Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="d847f-118">[Lien vers la vue d’ensemble de l’authentification moderne](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="d847f-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

