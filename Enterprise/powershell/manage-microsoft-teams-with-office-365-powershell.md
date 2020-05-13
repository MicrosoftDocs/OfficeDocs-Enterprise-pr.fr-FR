---
title: Gérer Microsoft teams avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Résumé : utilisez Office 365 PowerShell pour gérer votre équipe Microsoft Teams.'
ms.openlocfilehash: 0f15d71558ddb5166090b067da06e0a6321a2b99
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209120"
---
# <a name="manage-microsoft-teams-with-office-365-powershell"></a><span data-ttu-id="3bf0e-103">Gérer Microsoft teams avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bf0e-103">Manage Microsoft Teams with Office 365 PowerShell</span></span>

<span data-ttu-id="3bf0e-104">Vous pouvez gérer Microsoft teams avec Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3bf0e-104">You can manage Microsoft Teams with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="3bf0e-105">Tout d’abord, installez le [module Microsoft teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="3bf0e-105">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="3bf0e-106">Se connecter avec un nom d’utilisateur et un mot de passe</span><span class="sxs-lookup"><span data-stu-id="3bf0e-106">Sign in with a user name and password</span></span>

<span data-ttu-id="3bf0e-107">Pour le Cloud Office 365 Worldwide (+ GCC) :</span><span class="sxs-lookup"><span data-stu-id="3bf0e-107">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="3bf0e-108">Pour le Cloud DoD du gouvernement Office 365, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3bf0e-108">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="3bf0e-109">Pour le secteur public de la version Office 365 pour le gouvernement américain GCC High :</span><span class="sxs-lookup"><span data-stu-id="3bf0e-109">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="3bf0e-110">Se connecter avec l’authentification multifacteur (MFA)</span><span class="sxs-lookup"><span data-stu-id="3bf0e-110">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="3bf0e-111">Pour le Cloud Office 365 Worldwide (+ GCC) :</span><span class="sxs-lookup"><span data-stu-id="3bf0e-111">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="3bf0e-112">Pour le Cloud DoD du gouvernement Office 365, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3bf0e-112">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="3bf0e-113">Pour le secteur public de la version Office 365 pour le gouvernement américain GCC High :</span><span class="sxs-lookup"><span data-stu-id="3bf0e-113">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="3bf0e-114">Se déconnecter de Microsoft teams</span><span class="sxs-lookup"><span data-stu-id="3bf0e-114">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="3bf0e-115">Utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3bf0e-115">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="3bf0e-116">Articles associés</span><span class="sxs-lookup"><span data-stu-id="3bf0e-116">See also</span></span>

[<span data-ttu-id="3bf0e-117">Vue d’ensemble de PowerShell teams</span><span class="sxs-lookup"><span data-stu-id="3bf0e-117">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="3bf0e-118">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bf0e-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3bf0e-119">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="3bf0e-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

