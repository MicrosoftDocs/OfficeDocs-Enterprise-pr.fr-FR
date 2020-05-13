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
# <a name="manage-microsoft-teams-with-office-365-powershell"></a>Gérer Microsoft teams avec Office 365 PowerShell

Vous pouvez gérer Microsoft teams avec Office 365 PowerShell.
  
Tout d’abord, installez le [module Microsoft teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).
    
## <a name="sign-in-with-a-user-name-and-password"></a>Se connecter avec un nom d’utilisateur et un mot de passe

Pour le Cloud Office 365 Worldwide (+ GCC) :

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

Pour le Cloud DoD du gouvernement Office 365, procédez comme suit : 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

Pour le secteur public de la version Office 365 pour le gouvernement américain GCC High :

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a>Se connecter avec l’authentification multifacteur (MFA)

Pour le Cloud Office 365 Worldwide (+ GCC) :

```powershell
Connect-MicrosoftTeams
```

Pour le Cloud DoD du gouvernement Office 365, procédez comme suit : 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

Pour le secteur public de la version Office 365 pour le gouvernement américain GCC High :

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a>Se déconnecter de Microsoft teams

Utilisez la commande suivante :

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a>Articles associés

[Vue d’ensemble de PowerShell teams](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

