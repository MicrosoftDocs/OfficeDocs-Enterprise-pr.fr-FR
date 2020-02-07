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
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "Résumé : Utilisez Office 365 PowerShell pour gérer les propriétés de votre compte d'utilisateur Skype Entreprise Online à l'aide de stratégies."
ms.openlocfilehash: aed7e3929a41dec69803a5b73bdf29fb23b4ba05
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841331"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="a078f-103">Gestion des stratégies Skype Entreprise Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a078f-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

<span data-ttu-id="a078f-104">Pour gérer les nombreuses propriétés du compte d'utilisateur pour Skype Entreprise Online, vous devez les spécifier en tant que propriétés de stratégies avec Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a078f-104">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="a078f-105">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="a078f-105">Before you begin</span></span>

<span data-ttu-id="a078f-106">Suivez ces instructions pour exécuter les commandes (sautez les étapes que vous avez déjà effectuées) :</span><span class="sxs-lookup"><span data-stu-id="a078f-106">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="a078f-107">Téléchargez et installez le [module Connecteur Skype Entreprise Online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="a078f-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="a078f-108">Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a078f-108">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="a078f-109">Lorsque vous y êtes invité, entrez le nom utilisateur et le mot de passe de votre compte d'administrateur Skype Entreprise Online.</span><span class="sxs-lookup"><span data-stu-id="a078f-109">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="a078f-110">Gestion de stratégies de compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="a078f-110">Manage user account policies</span></span>

<span data-ttu-id="a078f-p101">De nombreuses propriétés de compte d'utilisateur Skype Entreprise Online sont configurées à l'aide de stratégies. Les stratégies sont simplement des ensembles de paramètres qui peuvent être appliqués à un ou plusieurs utilisateurs. Pour voir comment la stratégie a été configurée, vous pouvez exécuter cet exemple de commande, qui porte sur la stratégie FederationAndPICDefault :</span><span class="sxs-lookup"><span data-stu-id="a078f-p101">Many Skype for Business Online user account properties are configured by using policies. Policies are simply collections of settings that can be applied to one or more users. To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="a078f-114">Vous devriez obtenir en retour un élément semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="a078f-114">In turn, you should get back something similar to this:</span></span>
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="a078f-115">Dans cet exemple, les valeurs au sein de cette stratégie déterminent ce qu'un utilisateur peut ou ne peut pas faire en matière de communication avec des utilisateurs fédérés.</span><span class="sxs-lookup"><span data-stu-id="a078f-115">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users.</span></span> <span data-ttu-id="a078f-116">Par exemple, la propriété EnableOutsideAccess doit être définie sur True pour qu'un utilisateur puisse communiquer avec des personnes extérieures à l'organisation.</span><span class="sxs-lookup"><span data-stu-id="a078f-116">For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization.</span></span> <span data-ttu-id="a078f-117">Notez que cette propriété n’apparaît pas dans le centre d’administration Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="a078f-117">Note that this property does not appear in the Microsoft 365 admin center.</span></span> <span data-ttu-id="a078f-118">Elle est automatiquement définie sur True ou False en fonction des autres sélections que vous effectuez.</span><span class="sxs-lookup"><span data-stu-id="a078f-118">Instead, the property is automatically set to True or False based on the other selections that you make.</span></span> <span data-ttu-id="a078f-119">Les deux autres propriétés qui vous intéressent sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a078f-119">The other two properties of interest are:</span></span>
  
- <span data-ttu-id="a078f-120">**EnableFederationAccess** indique si l'utilisateur peut communiquer avec des personnes à partir de domaines fédérés.</span><span class="sxs-lookup"><span data-stu-id="a078f-120">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="a078f-121">**EnablePublicCloudAccess** indique si l'utilisateur peut communiquer avec des utilisateurs Windows Live.</span><span class="sxs-lookup"><span data-stu-id="a078f-121">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="a078f-p103">Ainsi, vous ne modifiez pas directement les propriétés liées à la fédération sur les comptes d'utilisateur (par exemple, **Set-CsUser -EnableFederationAccess $True**). Vous attribuez à un compte une stratégie d'accès externe où les valeurs de propriété souhaitées sont déjà préconfigurées. Pour qu'un utilisateur puisse communiquer avec des utilisateurs fédérés et des utilisateurs Windows Live, une stratégie permettant ces types de communication doit être attribuée à son compte.</span><span class="sxs-lookup"><span data-stu-id="a078f-p103">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**). Instead, you assign an account an external access policy that has the desired property values preconfigured. If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="a078f-125">Pour savoir si quelqu’un peut communiquer avec des utilisateurs externes à l’organisation, vous devez :</span><span class="sxs-lookup"><span data-stu-id="a078f-125">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="a078f-126">déterminer la stratégie d’accès externe qui a été attribuée à cet utilisateur ;</span><span class="sxs-lookup"><span data-stu-id="a078f-126">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="a078f-127">déterminer les capacités autorisées ou non par cette stratégie.</span><span class="sxs-lookup"><span data-stu-id="a078f-127">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="a078f-128">Pour ce faire, vous pouvez par exemple utiliser la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a078f-128">For example, you can do that by using this command:</span></span>
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="a078f-129">Cette commande trouve la stratégie attribuée à l’utilisateur, puis les fonctionnalités activées ou désactivées dans cette stratégie.</span><span class="sxs-lookup"><span data-stu-id="a078f-129">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="a078f-130">Pour gérer les stratégies Skype entreprise Online avec PowerShell, consultez les applets de commande pour :</span><span class="sxs-lookup"><span data-stu-id="a078f-130">To manage Skype for Business Online policies with PowerShell, see the cmdlets for:</span></span>

- <span data-ttu-id="a078f-131">[Stratégie du client](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="a078f-131">[Client policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span></span>
- <span data-ttu-id="a078f-132">[Stratégie de conférence](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="a078f-132">[Conferencing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span></span>
- <span data-ttu-id="a078f-133">[Stratégie mobile](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="a078f-133">[Mobile policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span></span>
- <span data-ttu-id="a078f-134">[Stratégie de messagerie vocale en ligne](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="a078f-134">[Online Voicemail policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span></span>
- <span data-ttu-id="a078f-135">[Stratégie de routage des communications vocales](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="a078f-135">[Voice Routing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span></span>


> [!NOTE]
> <span data-ttu-id="a078f-p104">Un plan de numérotation Skype Entreprise Online ne diffère d'une stratégie que par le nom. Le nom « plan de numérotation » a été préféré à « stratégie de numérotation » (par exemple) afin d'assurer la compatibilité descendante avec Office Communications Server et Exchange.</span><span class="sxs-lookup"><span data-stu-id="a078f-p104">A Skype for Business Online dial plan is a policy in every respect except the name. The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="a078f-138">Par exemple, pour voir toutes les stratégies de voix que vous pouvez utiliser, il suffit d’exécuter la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a078f-138">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="a078f-p105">Cette action renvoie la liste de toutes les stratégies de voix dont vous disposez. Toutefois, gardez à l'esprit que toutes les stratégies ne peuvent pas être attribuées à tous les utilisateurs, en raison des diverses restrictions impliquant la gestion des licences et l'emplacement géographique (le dénommé « [emplacement d'utilisation](https://msdn.microsoft.com/library/azure/dn194136.aspx) »). Si vous souhaitez connaître les stratégies d'accès externe et les stratégies de conférence qui peuvent être attribuées à un utilisateur particulier, utilisez des commandes semblables à celles-ci :</span><span class="sxs-lookup"><span data-stu-id="a078f-p105">That returns a list of all the voice policies available to you. Keep in mind, however, that not all policies can be assigned to all users. This is due to various restrictions involving licensing and geographic location. (The so-called "[usage location](https://msdn.microsoft.com/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="a078f-p106">Le paramètre ApplicableTo limite les données renvoyées aux stratégies qui peuvent être attribuées à l’utilisateur indiqué (par exemple, Alex Darrow). Selon les restrictions liées à la gestion des licences et à l’emplacement d’utilisation, cela pourrait représenter un sous-ensemble de toutes les stratégies disponibles.</span><span class="sxs-lookup"><span data-stu-id="a078f-p106">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="a078f-145">Dans certains cas, les propriétés de stratégies ne sont pas utilisées avec Office 365, tandis que d’autres utilisateurs peuvent uniquement être gérées par le personnel du support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a078f-145">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="a078f-p107">Avec Skype Entreprise Online, les utilisateurs doivent être gérés par une stratégie ou une autre. Si une propriété portant sur les stratégies est vide, cela signifie que l'utilisateur en question est géré par une stratégie globale, c'est-à-dire une stratégie qui est appliquée automatiquement à un utilisateur, sauf si une stratégie individuelle est appliquée à cet utilisateur. Si aucune stratégie de client n'est répertoriée pour un compte d'utilisateur, cela signifie qu'il est géré par la stratégie globale. Vous pouvez déterminer la stratégie de client globale avec cette commande :</span><span class="sxs-lookup"><span data-stu-id="a078f-p107">With Skype for Business Online, users must be managed by a policy of some kind. If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy. Because we don't see a client policy listed for a user account, it is managed by the global policy. You can determine the global client policy with this command:</span></span>
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="a078f-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a078f-150">See also</span></span>

[<span data-ttu-id="a078f-151">Gestion de Skype Entreprise Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a078f-151">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="a078f-152">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a078f-152">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a078f-153">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="a078f-153">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

