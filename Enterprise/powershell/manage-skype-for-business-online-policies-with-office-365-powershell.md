---
title: Gestion des stratégies Skype Entreprise Online avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "Résumé : Utilisez Office 365 PowerShell pour gérer les propriétés de votre compte d'utilisateur Skype Entreprise Online à l'aide de stratégies."
ms.openlocfilehash: 51e402922b2a357ef29e9b2628eb25fc252e5437
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031729"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>Gestion des stratégies Skype Entreprise Online avec Office 365 PowerShell

 **Résumé :** Utilisez Office 365 PowerShell pour gérer les propriétés de votre compte d'utilisateur Skype Entreprise Online à l'aide de stratégies.
  
Pour gérer les nombreuses propriétés du compte d'utilisateur pour Skype Entreprise Online, vous devez les spécifier en tant que propriétés de stratégies avec Office 365 PowerShell.
  
## <a name="before-you-begin"></a>Avant de commencer

Suivez ces instructions pour exécuter les commandes (sautez les étapes que vous avez déjà effectuées) :
  
1. Téléchargez et installez le [module Connecteur Skype Entreprise Online](https://www.microsoft.com/download/details.aspx?id=39366).
    
2. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes : 
    
```
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

Lorsque vous y êtes invité, entrez le nom utilisateur et le mot de passe de votre compte d'administrateur Skype Entreprise Online.
    
## <a name="manage-user-account-policies"></a>Gestion de stratégies de compte d’utilisateur

De nombreuses propriétés de compte d'utilisateur Skype Entreprise Online sont configurées à l'aide de stratégies. Les stratégies sont simplement des ensembles de paramètres qui peuvent être appliqués à un ou plusieurs utilisateurs. Pour voir comment la stratégie a été configurée, vous pouvez exécuter cet exemple de commande, qui porte sur la stratégie FederationAndPICDefault :
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Vous devriez obtenir en retour un élément semblable au suivant :
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

Dans cet exemple, les valeurs de cette stratégie déterminent ce qu’une utilisation peut ou ne peut pas faire lorsqu’il s’agit de communiquer avec des utilisateurs fédérés. Par exemple, la propriété EnableOutsideAccess doit avoir la valeur true pour qu’un utilisateur puisse communiquer avec des personnes extérieures à l’organisation. Notez que cette propriété n’apparaît pas dans le centre d’administration Microsoft 365. Au lieu de cela, la propriété est automatiquement définie sur true ou false en fonction des autres sélections que vous effectuez. Les deux autres propriétés intéressantes sont les suivantes :
  
- **EnableFederationAccess** indique si l'utilisateur peut communiquer avec des personnes à partir de domaines fédérés.
    
- **EnablePublicCloudAccess** indique si l'utilisateur peut communiquer avec des utilisateurs Windows Live.
    
Ainsi, vous ne modifiez pas directement les propriétés liées à la fédération sur les comptes d'utilisateur (par exemple, **Set-CsUser -EnableFederationAccess $True**). Vous attribuez à un compte une stratégie d'accès externe où les valeurs de propriété souhaitées sont déjà préconfigurées. Pour qu'un utilisateur puisse communiquer avec des utilisateurs fédérés et des utilisateurs Windows Live, une stratégie permettant ces types de communication doit être attribuée à son compte.
  
Pour savoir si quelqu’un peut communiquer avec des utilisateurs externes à l’organisation, vous devez :
  
- déterminer la stratégie d’accès externe qui a été attribuée à cet utilisateur ;
    
- déterminer les capacités autorisées ou non par cette stratégie.
    
Pour ce faire, vous pouvez par exemple utiliser la commande suivante :
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Cette commande trouve la stratégie attribuée à l’utilisateur, puis les fonctionnalités activées ou désactivées dans cette stratégie.
  
Pour gérer les stratégies Skype entreprise Online avec PowerShell, consultez les applets de commande pour :

- [Stratégie du client](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [Stratégie de conférence](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [Stratégie mobile](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [Stratégie de messagerie vocale en ligne](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [Stratégie de routage des communications vocales](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> Un plan de numérotation Skype Entreprise Online ne diffère d'une stratégie que par le nom. Le nom « plan de numérotation » a été préféré à « stratégie de numérotation » (par exemple) afin d'assurer la compatibilité descendante avec Office Communications Server et Exchange. 
  
Par exemple, pour voir toutes les stratégies de voix que vous pouvez utiliser, il suffit d’exécuter la commande suivante :
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> Cette action renvoie la liste de toutes les stratégies de voix dont vous disposez. Toutefois, gardez à l'esprit que toutes les stratégies ne peuvent pas être attribuées à tous les utilisateurs, en raison des diverses restrictions impliquant la gestion des licences et l'emplacement géographique (le dénommé « [emplacement d'utilisation](https://msdn.microsoft.com/library/azure/dn194136.aspx) »). Si vous souhaitez connaître les stratégies d'accès externe et les stratégies de conférence qui peuvent être attribuées à un utilisateur particulier, utilisez des commandes semblables à celles-ci : 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

Le paramètre ApplicableTo limite les données renvoyées aux stratégies qui peuvent être attribuées à l’utilisateur indiqué (par exemple, Alex Darrow). Selon les restrictions liées à la gestion des licences et à l’emplacement d’utilisation, cela pourrait représenter un sous-ensemble de toutes les stratégies disponibles. 
  
Dans certains cas, les propriétés de stratégies ne sont pas utilisées avec Office 365, tandis que d’autres utilisateurs peuvent uniquement être gérées par le personnel du support technique Microsoft. 
  
Avec Skype Entreprise Online, les utilisateurs doivent être gérés par une stratégie ou une autre. Si une propriété portant sur les stratégies est vide, cela signifie que l'utilisateur en question est géré par une stratégie globale, c'est-à-dire une stratégie qui est appliquée automatiquement à un utilisateur, sauf si une stratégie individuelle est appliquée à cet utilisateur. Si aucune stratégie de client n'est répertoriée pour un compte d'utilisateur, cela signifie qu'il est géré par la stratégie globale. Vous pouvez déterminer la stratégie de client globale avec cette commande :
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Voir aussi

#### 

[Gestion de Skype Entreprise Online avec Office 365 PowerShell](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Gérer Office 365 avec Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Mise en route d'Office 365 Powershell](getting-started-with-office-365-powershell.md)

