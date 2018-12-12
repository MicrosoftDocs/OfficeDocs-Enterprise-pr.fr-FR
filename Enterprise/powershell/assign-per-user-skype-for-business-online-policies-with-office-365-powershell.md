---
title: Affectation de stratégies Skype Entreprise Online propres à chaque utilisateur avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Résumé : Utilisez Office 365 PowerShell pour affecter des paramètres de communication à chaque utilisateur au moyen de stratégies Skype Entreprise Online.'
ms.openlocfilehash: 7f819b619c5b3607c98c10791fe30c3944e862a4
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
ms.locfileid: "17114809"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>Affectation de stratégies Skype Entreprise Online propres à chaque utilisateur avec Office 365 PowerShell

 **Résumé :** Utilisez Office 365 PowerShell pour affecter des paramètres de communication à chaque utilisateur au moyen de stratégies Skype Entreprise Online.
  
Office 365 PowerShell est un outil pratique pour affecter des paramètres de communication à chaque utilisateur au moyen de stratégies Skype Entreprise Online.
  
## <a name="before-you-begin"></a>Avant de commencer

Suivez ces instructions pour exécuter les commandes (sautez les étapes que vous avez déjà effectuées) :
  
1. Téléchargez et installez le [module Connecteur Skype Entreprise Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366).
    
2. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes : 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
Lorsque vous y êtes invité, entrez le nom utilisateur et le mot de passe de votre compte d'administrateur Skype Entreprise Online.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Mise à jour des paramètres de communication externe d’un compte d’utilisateur

Supposons que vous souhaitiez modifier les paramètres de communication externe d’un compte d’utilisateur. Par exemple, vous souhaitez autoriser Alex à communiquer avec les utilisateurs fédérés (EnableFederationAccess est défini sur True), mais pas avec les utilisateurs Windows Live (EnablePublicCloudAccess est défini sur False). Pour cela, vous devez faire deux choses :
  
1. Trouver une stratégie d’accès externe qui réponde à nos critères.
    
2. Attribuer cette stratégie d’accès externe à Alex.
    
> [!NOTE]
>  Vous ne pouvez pas créer votre propre stratégie personnalisée. Skype Entreprise Online ne permet pas de créer de stratégies personnalisées. Vous devez attribuer l'une des stratégies créées spécifiquement pour Office 365. Les stratégies pré-créées sont les suivantes :  4 stratégies de client différentes,  224 stratégies de conférence différentes,  5 plans de numérotation différents, 5 stratégies d'accès externe différentes, 1 stratégie de messagerie vocale hébergée et 4 stratégies de voix différentes.
  
Comment savoir alors quelle stratégie d’accès externe attribuer à Alex ? La commande suivante renvoie toutes les stratégies d’accès externe où EnableFederationAccess a la valeur True et EnablePublicCloudAccess a la valeur False :
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

Le rôle de la commande consiste à renvoyer toutes les stratégies qui répondent aux deux critères suivants : la propriété EnableFederationAccess est définie sur True et la stratégie EnablePublicCloudAccess sur False. Ensuite, cette commande renvoie une stratégie (FederationOnly) qui répond à nos critères. Voici un exemple :
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> L’identité de la stratégie indique Tag:FederationOnly. Ce préfixe Tag: est issu de nos travaux préliminaires sur Microsoft Lync 2013. Pour attribuer des stratégies aux utilisateurs, vous devez supprimer le préfixe Tag: et utiliser uniquement le nom de stratégie : FederationOnly. 
  
Maintenant que vous savez quelle stratégie attribuer à Alex, vous pouvez le faire à l'aide de la cmdlet [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974). Voici un exemple :
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Affecter une stratégie est la simplicité même : il vous suffit de spécifier l’identité de l’utilisateur et le nom de la stratégie à attribuer. 
  
Concernant les stratégies et leur attribution, vous n'êtes pas obligé de gérer les comptes d'utilisateur séparément. Supposons que vous ayez besoin d'une liste de tous les utilisateurs autorisés à communiquer avec les partenaires fédérés et les utilisateurs de Windows Live. Nous savons déjà que la stratégie d'accès utilisateur externe FederationAndPICDefault a été attribuée à ces utilisateurs. Sachant cela, vous pouvez afficher une liste de tous ces utilisateurs en exécutant une commande simple, que voici :
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

En d'autres termes, afficher tous les utilisateurs dont la propriété ExternalAccessPolicy est définie sur FederationAndPICDefault. (En outre, afin de limiter la quantité d'informations affichées à l'écran, utilisez la cmdlet Select-Object pour n'afficher que le nom d'affichage de chaque utilisateur.) 
  
Pour configurer tous vos comptes d’utilisateur de manière à ce qu’ils utilisent la même stratégie, procédez comme suit :
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

Cette commande utilise Get-CsOnlineUser pour renvoyer une collection de tous les utilisateurs qui ont été activés pour Lync, puis transmet toutes ces informations à la cmdlet Grant-CsExternalAccessPolicy, laquelle attribue la stratégie FederationAndPICDefault à chaque utilisateur de la collection.
  
Autre exemple : supposons que vous ayez déjà attribué la stratégie FederationAndPICDefault à Alex, mais que vous ayez changé d'avis et que vous souhaitiez désormais qu'il soit géré par la stratégie d'accès externe globale. Vous ne pouvez pas attribuer explicitement la stratégie globale à un utilisateur. Elle est uniquement utilisée si aucune autre stratégie spécifique n'est affectée à un utilisateur. Cela signifie que, si nous voulons qu'Alex soit géré par la stratégie globale, nous devons lui  *désattribuer*  toutes les stratégies spécifiques qui lui sont affectées. Voici un exemple de commande :
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Cette commande définit le nom de la stratégie d'accès externe attribuée à Alex sur une valeur nulle ($Null). En d'autres termes, aucune stratégie d'accès externe n'est attribuée à Alex. Or, en l'absence de stratégie d'accès externe attribuée à un utilisateur, ce dernier est géré par la stratégie globale.
  
Pour désactiver un compte d’utilisateur à l’aide de Windows PowerShell, utilisez les cmdlets Azure Active Directory pour supprimer la licence Skype Entreprise Online d’Alex. Pour plus d’informations, consultez la rubrique [Désactiver l’accès aux services avec Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Voir aussi

#### 

[Gestion de Skype Entreprise Online avec Office 365 PowerShell](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

