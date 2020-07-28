---
title: Gérer Microsoft teams avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Résumé : utilisez PowerShell pour gérer Microsoft Teams.'
ms.openlocfilehash: 8958c6ec6f0c17c21461cbee4cb1a6441ceed8d6
ms.sourcegitcommit: 132c97bd5e0dbe469da64356ace5084b71419cea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45429191"
---
# <a name="manage-microsoft-teams-with-powershell"></a><span data-ttu-id="33828-103">Gérer Microsoft teams avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="33828-103">Manage Microsoft Teams with PowerShell</span></span>

<span data-ttu-id="33828-104">*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*</span><span class="sxs-lookup"><span data-stu-id="33828-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="33828-105">Vous pouvez gérer Microsoft teams avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33828-105">You can manage Microsoft Teams with PowerShell.</span></span>
  
<span data-ttu-id="33828-106">Tout d’abord, installez le [module Microsoft teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="33828-106">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="33828-107">Se connecter avec un nom d’utilisateur et un mot de passe</span><span class="sxs-lookup"><span data-stu-id="33828-107">Sign in with a user name and password</span></span>

<span data-ttu-id="33828-108">Pour le Cloud Office 365 Worldwide (+ GCC) :</span><span class="sxs-lookup"><span data-stu-id="33828-108">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="33828-109">Pour le Cloud DoD du gouvernement Office 365, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="33828-109">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="33828-110">Pour le secteur public de la version Office 365 pour le gouvernement américain GCC High :</span><span class="sxs-lookup"><span data-stu-id="33828-110">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="33828-111">Se connecter avec l’authentification multifacteur (MFA)</span><span class="sxs-lookup"><span data-stu-id="33828-111">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="33828-112">Pour le Cloud Office 365 Worldwide (+ GCC) :</span><span class="sxs-lookup"><span data-stu-id="33828-112">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="33828-113">Pour le Cloud DoD du gouvernement Office 365, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="33828-113">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="33828-114">Pour le secteur public de la version Office 365 pour le gouvernement américain GCC High :</span><span class="sxs-lookup"><span data-stu-id="33828-114">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="33828-115">Se déconnecter de Microsoft teams</span><span class="sxs-lookup"><span data-stu-id="33828-115">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="33828-116">Utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="33828-116">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="33828-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33828-117">See also</span></span>

[<span data-ttu-id="33828-118">Vue d’ensemble de PowerShell teams</span><span class="sxs-lookup"><span data-stu-id="33828-118">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="33828-119">Gestion de Microsoft 365 à l’aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="33828-119">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="33828-120">Prise en main de PowerShell pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="33828-120">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

