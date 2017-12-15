---
title: "Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
- DecEntMigration
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Explique comment utiliser Office 365 PowerShell pour supprimer des licences Office 365 qui a été précédemment affectés aux utilisateurs."
ms.openlocfilehash: 90cae603a7a7cda0b7318571d3eb045f750fd58d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="5001a-103">Supprimer des licences à des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5001a-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="5001a-104">**Résumé :** Explique comment utiliser Office 365 PowerShell pour supprimer des licences Office 365 qui a été précédemment affectés aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5001a-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="5001a-105">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="5001a-105">Before you begin</span></span>

- <span data-ttu-id="5001a-p101">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="5001a-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="5001a-108">Pour afficher les informations de licence plan ( **AccountSkuID** ) dans votre organisation, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5001a-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="5001a-109">Afficher les licences et les services avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5001a-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="5001a-110">Afficher les détails de service et de licence de compte avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5001a-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="5001a-111">Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le _-tous les_ paramètre, seuls les 500 premiers comptes de sont retournés.</span><span class="sxs-lookup"><span data-stu-id="5001a-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="5001a-112">La version courte (instructions sans explications)</span><span class="sxs-lookup"><span data-stu-id="5001a-112">The short version (instructions without explanations)</span></span>
<span data-ttu-id="5001a-113"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="5001a-113"></span></span>

<span data-ttu-id="5001a-p102">Cette section présente les procédures sans explication superflue ou alambiquée. Si vous avez des questions ou que vous souhaitez plus d'informations, vous pouvez lire le reste de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="5001a-p102">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="5001a-116">Pour supprimer des licences à partir d’un compte d’utilisateur existant, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="5001a-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="5001a-117">Cet exemple supprime la `litwareinc:ENTERPRISEPACK` licence (Office 365 entreprise E3) à partir du compte d’utilisateur BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="5001a-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="5001a-118">Pour supprimer des licences d’un groupe d’utilisateurs sous licence existants, appliquez l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5001a-118">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="5001a-119">**Filtrer les comptes basés sur un attribut de compte existant** Pour ce faire, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="5001a-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="5001a-120">Cet exemple supprime la `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3) des licences de tous les comptes d’utilisateurs dans le service des ventes aux États-Unis.</span><span class="sxs-lookup"><span data-stu-id="5001a-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="5001a-121">**Utilisation d’une liste de comptes spécifiques** Pour ce faire, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5001a-121">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="5001a-122">Créez et enregistrez un fichier texte contenant un seul compte sur chaque ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="5001a-122">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="5001a-123">Utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="5001a-123">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="5001a-124">Cet exemple supprime la `litwareinc:ENTERPRISEPACK` licence (Office 365 entreprise E3) à partir des comptes d’utilisateur défini dans le fichier texte C:\My Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="5001a-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="5001a-125">Pour supprimer des licences de tous les comptes d’utilisateurs existants, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="5001a-125">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="5001a-126">Cet exemple supprime la `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3) licence tout sous licence des comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5001a-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="5001a-127">La version longue (instructions avec des explications détaillées)</span><span class="sxs-lookup"><span data-stu-id="5001a-127">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="5001a-128"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="5001a-128"></span></span>

<span data-ttu-id="5001a-p103">Rien ne dure toujours, et qui inclut des licences Office 365 : tôt ou tard, il arrivera un moment lorsque vous devez supprimer une licence d’un compte d’utilisateur. Peut-être que l’utilisateur va sur le congé ; peut-être l’utilisateur n’a plus besoin de la licence ; peut-être - il y a évidemment autant de raisons pourquoi vous pouvez souhaiter supprimer une licence utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5001a-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span></span>
  
<span data-ttu-id="5001a-p104">Avant d’aller plus loin qu’il est important de noter que la suppression d’une licence, vous devez, bien, supprimez la licence : la désactivation de tous les services sur une licence n’est pas la même chose que la suppression d’une licence. Par exemple, supposons que nous avons utilisé notre licences Office 365 ; en d’autres termes, nous n’avons pas de licences disponibles que ce soit. Vous décidez de suivre la procédure de [désactivation de l’accès aux services Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) pour désactiver tous les services, par exemple, sur le compte de le de Belinda Newman. Après cela, combien de licences va nous disposons nous ? C’est ça : zéro. Oui, la procédure de cette rubrique va *désactiver* tous les services sur les licences de Belinda, mais il ne désactivera pas (c.-à-d. de supprimer) la licence elle-même. La licence sera toujours valide et elle restera affectée à Belinda Newman. Elle ne sera uniquement en mesure d’utiliser cette licence pour accéder aux services Office 365.</span><span class="sxs-lookup"><span data-stu-id="5001a-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span></span>
  
<span data-ttu-id="5001a-p105">Et c’est important : Si vous souhaitez supprimer une licence d’un utilisateur, vous devez *Supprimer* la licence. La désactivation de tous les services empêche l’utilisateur de se connecter à Office 365, mais il ne libérer la licence sa. Si vous souhaitez reprendre une licence qui est actuellement affectée à un utilisateur, que vous devez exécuter une commande semblable à celle-ci, une commande qui utilise le paramètre _RemoveLicenses_ pour supprimer réellement la licence précédemment attribuée à Belinda :</span><span class="sxs-lookup"><span data-stu-id="5001a-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="5001a-142">Exécutez cette commande, et Belinda Newman est n’est plus accordée pour utiliser Office 365.</span><span class="sxs-lookup"><span data-stu-id="5001a-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5001a-p106">Comme vous pouvez le voir, lorsque vous utilisez le paramètre _RemoveLicenses_ , que vous devez spécifier le nom de la licence à supprimer. Si vous ne savez pas quel plan de gestion des licences utilisé pour attribuer une licence à l’utilisateur, il suffit d’exécuter une commande comme suit :`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span><span class="sxs-lookup"><span data-stu-id="5001a-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span></span>
  
<span data-ttu-id="5001a-145">Pour vérifier que la licence a vraiment été supprimée, utilisez la commande Get-MsolUser pour vérifier le compte de l’utilisateur en question :</span><span class="sxs-lookup"><span data-stu-id="5001a-145">To verify that the license really was removed, use the Get-MsolUser to check the user account in question:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

<span data-ttu-id="5001a-146">Si tout se déroule conformément au plan, propriété **d’isLicensed** de Belinda est maintenant fixée à `False`:</span><span class="sxs-lookup"><span data-stu-id="5001a-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span></span>
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

<span data-ttu-id="5001a-p107">Un autre moyen de libérer une licence est en supprimant le compte utilisateur. Pour plus d’informations, voir [Supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="5001a-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5001a-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5001a-149">See also</span></span>

<span data-ttu-id="5001a-150">Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="5001a-150">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="5001a-151">Création de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5001a-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="5001a-152">Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5001a-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="5001a-153">Bloquer des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5001a-153">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="5001a-154">Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5001a-154">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="5001a-155">Pour plus d'informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5001a-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="5001a-156">Get-Content.</span><span class="sxs-lookup"><span data-stu-id="5001a-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="5001a-157">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="5001a-157">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="5001a-158">Ensemble-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="5001a-158">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="5001a-159">ForEach-Object.</span><span class="sxs-lookup"><span data-stu-id="5001a-159">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="5001a-160">Where-Object</span><span class="sxs-lookup"><span data-stu-id="5001a-160">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="5001a-161">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="5001a-161">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="5001a-p108">![L’icône court pour l’apprentissage de LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **nouveau vers Office 365 ?**         Découvrez la vidéo gratuits pour les [professionnels de l’informatique et les administrateurs d’Office 365](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), proposée par formation de LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="5001a-p108">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   

