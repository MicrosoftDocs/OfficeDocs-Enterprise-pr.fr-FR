---
title: "Affectation de stratégies Skype Entreprise Online propres à chaque utilisateur avec Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: "Résumé : Utilisez Office 365 PowerShell pour affecter des paramètres de communication à chaque utilisateur au moyen de stratégies Skype Entreprise Online."
ms.openlocfilehash: 91916b41ba420a204ecabb27eea2e451a91f6f25
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="705f5-103">Affectation de stratégies Skype Entreprise Online propres à chaque utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="705f5-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="705f5-104">**Résumé :** Utilisez Office 365 PowerShell pour affecter des paramètres de communication à chaque utilisateur au moyen de stratégies Skype Entreprise Online.</span><span class="sxs-lookup"><span data-stu-id="705f5-104">Summary: Use Office 365 PowerShell to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
<span data-ttu-id="705f5-105">Office 365 PowerShell est un outil pratique pour affecter des paramètres de communication à chaque utilisateur au moyen de stratégies Skype Entreprise Online.</span><span class="sxs-lookup"><span data-stu-id="705f5-105">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="705f5-106">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="705f5-106">Before you begin</span></span>

<span data-ttu-id="705f5-107">Suivez ces instructions pour exécuter les commandes (sautez les étapes que vous avez déjà effectuées) :</span><span class="sxs-lookup"><span data-stu-id="705f5-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="705f5-108">Téléchargez et installez le [module Connecteur Skype Entreprise Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="705f5-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="705f5-109">Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="705f5-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
<span data-ttu-id="705f5-110">Lorsque vous y êtes invité, entrez le nom utilisateur et le mot de passe de votre compte d'administrateur Skype Entreprise Online.</span><span class="sxs-lookup"><span data-stu-id="705f5-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="705f5-111">Mise à jour des paramètres de communication externe d’un compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="705f5-111">Updating external communication settings for a user account</span></span>

<span data-ttu-id="705f5-p101">Supposons que vous souhaitiez modifier les paramètres de communication externe d’un compte d’utilisateur. Par exemple, vous souhaitez autoriser Alex à communiquer avec les utilisateurs fédérés (EnableFederationAccess est défini sur True), mais pas avec les utilisateurs Windows Live (EnablePublicCloudAccess est défini sur False). Pour cela, vous devez faire deux choses :</span><span class="sxs-lookup"><span data-stu-id="705f5-p101">Suppose you want to change external communication settings on a user account. For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False). To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="705f5-115">Trouver une stratégie d’accès externe qui réponde à nos critères.</span><span class="sxs-lookup"><span data-stu-id="705f5-115">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="705f5-116">Attribuer cette stratégie d’accès externe à Alex.</span><span class="sxs-lookup"><span data-stu-id="705f5-116">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="705f5-p102">Vous ne pouvez pas créer votre propre stratégie personnalisée. Skype Entreprise Online ne permet pas de créer de stratégies personnalisées. Vous devez attribuer l'une des stratégies créées spécifiquement pour Office 365. Les stratégies pré-créées sont les suivantes :  4 stratégies de client différentes,  224 stratégies de conférence différentes,  5 plans de numérotation différents, 5 stratégies d'accès externe différentes, 1 stratégie de messagerie vocale hébergée et 4 stratégies de voix différentes.</span><span class="sxs-lookup"><span data-stu-id="705f5-p102">You can't create a custom policy all our own. That's because Skype for Business Online does not allow you to create custom policies. Instead, you must assign one of the policies that were created specifically for Office 365. Those pre-created policies include:>  4 different client policies>  224 different conferencing policies>  5 different dial plans>  5 different external access policies>  1 hosted voicemail policy>  4 different voice policies</span></span>
  
<span data-ttu-id="705f5-p103">Comment savoir alors quelle stratégie d’accès externe attribuer à Alex ? La commande suivante renvoie toutes les stratégies d’accès externe où EnableFederationAccess a la valeur True et EnablePublicCloudAccess a la valeur False :</span><span class="sxs-lookup"><span data-stu-id="705f5-p103">So how do you determine which external access policy to assign Alex? The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="705f5-p104">Le rôle de la commande consiste à renvoyer toutes les stratégies qui répondent aux deux critères suivants : la propriété EnableFederationAccess est définie sur True et la stratégie EnablePublicCloudAccess sur False. Ensuite, cette commande renvoie une stratégie (FederationOnly) qui répond à nos critères. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="705f5-p104">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False. In turn, that command returns one policy - FederationOnly - that meets our criteria. Here is an example:</span></span>
  
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
> <span data-ttu-id="705f5-p105">L’identité de la stratégie indique Tag:FederationOnly. Ce préfixe Tag: est issu de nos travaux préliminaires sur Microsoft Lync 2013. Pour attribuer des stratégies aux utilisateurs, vous devez supprimer le préfixe Tag: et utiliser uniquement le nom de stratégie : FederationOnly.</span><span class="sxs-lookup"><span data-stu-id="705f5-p105">The policy Identity says Tag:FederationOnly. As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013. When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="705f5-p106">Maintenant que vous savez quelle stratégie attribuer à Alex, vous pouvez le faire à l'aide de la cmdlet [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974). Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="705f5-p106">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet. Here is an example:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="705f5-131">Affecter une stratégie est la simplicité même : il vous suffit de spécifier l’identité de l’utilisateur et le nom de la stratégie à attribuer.</span><span class="sxs-lookup"><span data-stu-id="705f5-131">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="705f5-p107">Concernant les stratégies et leur attribution, vous n'êtes pas obligé de gérer les comptes d'utilisateur séparément. Supposons que vous ayez besoin d'une liste de tous les utilisateurs autorisés à communiquer avec les partenaires fédérés et les utilisateurs de Windows Live. Nous savons déjà que la stratégie d'accès utilisateur externe FederationAndPICDefault a été attribuée à ces utilisateurs. Sachant cela, vous pouvez afficher une liste de tous ces utilisateurs en exécutant une commande simple, que voici :</span><span class="sxs-lookup"><span data-stu-id="705f5-p107">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time. For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users. We already know that those users have been assigned the external user access policy FederationAndPICDefault. Because we know that, you can display a list of all those users by running one simple command. Here is the command:</span></span>
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="705f5-p108">En d'autres termes, afficher tous les utilisateurs dont la propriété ExternalAccessPolicy est définie sur FederationAndPICDefault. (En outre, afin de limiter la quantité d'informations affichées à l'écran, utilisez la cmdlet Select-Object pour n'afficher que le nom d'affichage de chaque utilisateur.)</span><span class="sxs-lookup"><span data-stu-id="705f5-p108">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault. (And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="705f5-139">Pour configurer tous vos comptes d’utilisateur de manière à ce qu’ils utilisent la même stratégie, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="705f5-139">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="705f5-140">Cette commande utilise Get-CsOnlineUser pour renvoyer une collection de tous les utilisateurs qui ont été activés pour Lync, puis transmet toutes ces informations à la cmdlet Grant-CsExternalAccessPolicy, laquelle attribue la stratégie FederationAndPICDefault à chaque utilisateur de la collection.</span><span class="sxs-lookup"><span data-stu-id="705f5-140">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="705f5-p109">Autre exemple : supposons que vous ayez déjà attribué la stratégie FederationAndPICDefault à Alex, mais que vous ayez changé d'avis et que vous souhaitiez désormais qu'il soit géré par la stratégie d'accès externe globale. Vous ne pouvez pas attribuer explicitement la stratégie globale à un utilisateur. Elle est uniquement utilisée si aucune autre stratégie spécifique n'est affectée à un utilisateur. Cela signifie que, si nous voulons qu'Alex soit géré par la stratégie globale, nous devons lui  *désattribuer*  toutes les stratégies spécifiques qui lui sont affectées. Voici un exemple de commande :</span><span class="sxs-lookup"><span data-stu-id="705f5-p109">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy. You can't explicitly assign the global policy to anyone. It is only used if no other per-user policy is assigned. Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him. Here is an example command:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="705f5-p110">Cette commande définit le nom de la stratégie d'accès externe attribuée à Alex sur une valeur nulle ($Null). En d'autres termes, aucune stratégie d'accès externe n'est attribuée à Alex. Or, en l'absence de stratégie d'accès externe attribuée à un utilisateur, ce dernier est géré par la stratégie globale.</span><span class="sxs-lookup"><span data-stu-id="705f5-p110">This command sets the name of the external access policy assigned to Alex to a null value ($Null). Null means "nothing". In other words, no external access policy is assigned to Alex. When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="705f5-p111">Pour désactiver un compte d’utilisateur à l’aide de Windows PowerShell, utilisez les cmdlets Azure Active Directory pour supprimer la licence Skype Entreprise Online d’Alex. Pour plus d’informations, consultez la rubrique [Désactiver l’accès aux services avec Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="705f5-p111">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license. For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="705f5-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="705f5-152">See also</span></span>

#### 

[<span data-ttu-id="705f5-153">Gestion de Skype Entreprise Online avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="705f5-153">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="705f5-154">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="705f5-154">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="705f5-155">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="705f5-155">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

