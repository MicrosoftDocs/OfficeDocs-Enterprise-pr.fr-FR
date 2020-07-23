---
title: Affecter des stratégies Skype entreprise Online par utilisateur avec PowerShell pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Résumé : utilisez PowerShell pour Microsoft 365 pour affecter des paramètres de communication par utilisateur aux stratégies Skype entreprise online.'
ms.openlocfilehash: 4522cfd877355794c32d9b9bdf14fb11cd0e71b4
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229841"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a><span data-ttu-id="ef832-103">Affecter des stratégies Skype entreprise Online par utilisateur avec PowerShell pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ef832-103">Assign per-user Skype for Business Online policies with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="ef832-104">*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="ef832-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="ef832-105">L’utilisation de PowerShell pour Microsoft 365 est un moyen efficace d’affecter des paramètres de communication par utilisateur à des stratégies Skype entreprise online.</span><span class="sxs-lookup"><span data-stu-id="ef832-105">Using PowerShell for Microsoft 365 is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="ef832-106">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="ef832-106">Before you begin</span></span>

<span data-ttu-id="ef832-107">Suivez ces instructions pour exécuter les commandes (sautez les étapes que vous avez déjà effectuées) :</span><span class="sxs-lookup"><span data-stu-id="ef832-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="ef832-108">Téléchargez et installez le [module Connecteur Skype Entreprise Online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="ef832-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="ef832-109">Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ef832-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

<span data-ttu-id="ef832-110">Lorsque vous y êtes invité, entrez le nom utilisateur et le mot de passe de votre compte d'administrateur Skype Entreprise Online.</span><span class="sxs-lookup"><span data-stu-id="ef832-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="ef832-111">Mise à jour des paramètres de communication externe d’un compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="ef832-111">Updating external communication settings for a user account</span></span>

<span data-ttu-id="ef832-p101">Supposons que vous souhaitiez modifier les paramètres de communication externe d’un compte d’utilisateur. Par exemple, vous souhaitez autoriser Alex à communiquer avec les utilisateurs fédérés (EnableFederationAccess est défini sur True), mais pas avec les utilisateurs Windows Live (EnablePublicCloudAccess est défini sur False). Pour cela, vous devez faire deux choses :</span><span class="sxs-lookup"><span data-stu-id="ef832-p101">Suppose you want to change external communication settings on a user account. For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False). To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="ef832-115">Trouver une stratégie d’accès externe qui réponde à nos critères.</span><span class="sxs-lookup"><span data-stu-id="ef832-115">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="ef832-116">Attribuer cette stratégie d’accès externe à Alex.</span><span class="sxs-lookup"><span data-stu-id="ef832-116">Assign that external access policy to Alex.</span></span>
    
<span data-ttu-id="ef832-117">Comment déterminer quelle stratégie d’accès externe attribuer à Alex ?</span><span class="sxs-lookup"><span data-stu-id="ef832-117">How do you determine which external access policy to assign Alex?</span></span> <span data-ttu-id="ef832-118">La commande suivante renvoie toutes les stratégies d’accès externe où EnableFederationAccess a la valeur True et EnablePublicCloudAccess a la valeur False :</span><span class="sxs-lookup"><span data-stu-id="ef832-118">The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="ef832-119">Sauf si vous avez créé des instances personnalisées de ExternalAccessPolicy, cette commande renvoie une stratégie qui répond à nos critères (FederationOnly).</span><span class="sxs-lookup"><span data-stu-id="ef832-119">Unless you have created any custom instances of ExternalAccessPolicy, that command returns one policy that meets our criteria (FederationOnly).</span></span> <span data-ttu-id="ef832-120">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="ef832-120">Here is an example:</span></span>
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

<span data-ttu-id="ef832-p104">Maintenant que vous savez quelle stratégie attribuer à Alex, vous pouvez le faire à l'aide de la cmdlet [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974). Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="ef832-p104">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet. Here is an example:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="ef832-123">Affecter une stratégie est la simplicité même : il vous suffit de spécifier l’identité de l’utilisateur et le nom de la stratégie à attribuer.</span><span class="sxs-lookup"><span data-stu-id="ef832-123">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="ef832-p105">Concernant les stratégies et leur attribution, vous n'êtes pas obligé de gérer les comptes d'utilisateur séparément. Supposons que vous ayez besoin d'une liste de tous les utilisateurs autorisés à communiquer avec les partenaires fédérés et les utilisateurs de Windows Live. Nous savons déjà que la stratégie d'accès utilisateur externe FederationAndPICDefault a été attribuée à ces utilisateurs. Sachant cela, vous pouvez afficher une liste de tous ces utilisateurs en exécutant une commande simple, que voici :</span><span class="sxs-lookup"><span data-stu-id="ef832-p105">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time. For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users. We already know that those users have been assigned the external user access policy FederationAndPICDefault. Because we know that, you can display a list of all those users by running one simple command. Here is the command:</span></span>
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="ef832-p106">En d'autres termes, afficher tous les utilisateurs dont la propriété ExternalAccessPolicy est définie sur FederationAndPICDefault. (En outre, afin de limiter la quantité d'informations affichées à l'écran, utilisez la cmdlet Select-Object pour n'afficher que le nom d'affichage de chaque utilisateur.)</span><span class="sxs-lookup"><span data-stu-id="ef832-p106">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault. (And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="ef832-131">Pour configurer tous vos comptes d’utilisateur de manière à ce qu’ils utilisent la même stratégie, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ef832-131">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="ef832-132">Cette commande utilise Get-CsOnlineUser pour renvoyer une collection de tous les utilisateurs qui ont été activés pour Lync, puis transmet toutes ces informations à la cmdlet Grant-CsExternalAccessPolicy, laquelle attribue la stratégie FederationAndPICDefault à chaque utilisateur de la collection.</span><span class="sxs-lookup"><span data-stu-id="ef832-132">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="ef832-133">Autre exemple : supposons que vous ayez déjà attribué la stratégie FederationAndPICDefault à Alex, mais que vous ayez changé d'avis et que vous souhaitiez désormais qu'il soit géré par la stratégie d'accès externe globale.</span><span class="sxs-lookup"><span data-stu-id="ef832-133">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy.</span></span> <span data-ttu-id="ef832-134">Vous ne pouvez pas attribuer explicitement la stratégie globale à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ef832-134">You can't explicitly assign the global policy to anyone.</span></span> <span data-ttu-id="ef832-135">Au lieu de cela, la stratégie globale est utilisée pour un utilisateur donné si aucune stratégie par utilisateur n’est affectée à cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ef832-135">Instead, the global policy is used for a given user if no per-user policy is assigned to that user.</span></span> <span data-ttu-id="ef832-136">Cela signifie que, si nous voulons qu'Alex soit géré par la stratégie globale, nous devons lui  *désattribuer*  toutes les stratégies spécifiques qui lui sont affectées.</span><span class="sxs-lookup"><span data-stu-id="ef832-136">Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him.</span></span> <span data-ttu-id="ef832-137">Voici un exemple de commande :</span><span class="sxs-lookup"><span data-stu-id="ef832-137">Here is an example command:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="ef832-p108">Cette commande définit le nom de la stratégie d'accès externe attribuée à Alex sur une valeur nulle ($Null). En d'autres termes, aucune stratégie d'accès externe n'est attribuée à Alex. Or, en l'absence de stratégie d'accès externe attribuée à un utilisateur, ce dernier est géré par la stratégie globale.</span><span class="sxs-lookup"><span data-stu-id="ef832-p108">This command sets the name of the external access policy assigned to Alex to a null value ($Null). Null means "nothing". In other words, no external access policy is assigned to Alex. When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  

## <a name="managing-large-numbers-of-users"></a><span data-ttu-id="ef832-142">Gestion d’un grand nombre d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="ef832-142">Managing large numbers of users</span></span>

<span data-ttu-id="ef832-143">Pour gérer un grand nombre d’utilisateurs (1000 ou plus), vous devez effectuer un traitement par lots des commandes via un bloc de script à l’aide de la cmdlet [Invoke-Command](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) .</span><span class="sxs-lookup"><span data-stu-id="ef832-143">To manage large numbers of users (1000 or more), you need to batch the commands via a script block using the [Invoke-Command](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) cmdlet.</span></span>  <span data-ttu-id="ef832-144">Dans les exemples précédents, chaque fois qu’une cmdlet est exécutée, elle doit configurer l’appel, puis attendre le résultat avant de l’envoyer à nouveau.</span><span class="sxs-lookup"><span data-stu-id="ef832-144">In previous examples, each time a cmdlet is executed, it must set up the call and then wait for the result before sending it back.</span></span>  <span data-ttu-id="ef832-145">Lors de l’utilisation d’un bloc de script, les cmdlets peuvent être exécutées à distance et, une fois terminées, renvoyer les données.</span><span class="sxs-lookup"><span data-stu-id="ef832-145">When using a script block, this allows the cmdlets to be executed remotely, and once completed, send the data back.</span></span> 

```powershell
Import-Module LyncOnlineConnector
$sfbSession = New-CsOnlineSession
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

<span data-ttu-id="ef832-146">Cela permet de trouver 500 utilisateurs à la fois qui n’ont pas de stratégie client.</span><span class="sxs-lookup"><span data-stu-id="ef832-146">This will find 500 users at a time who do not have a client policy.</span></span> <span data-ttu-id="ef832-147">Il lui accorde la stratégie cliente « ClientPolicyNoIMURL » et la stratégie d’accès externe « FederationAndPicDefault ».</span><span class="sxs-lookup"><span data-stu-id="ef832-147">It will grant them the client policy "ClientPolicyNoIMURL" and the external access policy "FederationAndPicDefault".</span></span> <span data-ttu-id="ef832-148">Les résultats sont regroupés en groupes de 50 et chaque lot de 50 est envoyé à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ef832-148">The results are batched into groups of 50 and each batch of 50 is then sent to the remote machine.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ef832-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef832-149">See also</span></span>

[<span data-ttu-id="ef832-150">Gestion de Skype entreprise Online avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef832-150">Manage Skype for Business Online with PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="ef832-151">Gérer Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef832-151">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ef832-152">Prise en main de PowerShell pour Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ef832-152">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
