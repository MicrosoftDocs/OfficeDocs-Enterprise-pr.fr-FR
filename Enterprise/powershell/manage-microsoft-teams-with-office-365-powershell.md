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
# <a name="manage-microsoft-teams-with-powershell"></a>Gérer Microsoft teams avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez gérer Microsoft teams avec PowerShell.
  
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


## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de PowerShell teams](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-office-365-powershell.md)

