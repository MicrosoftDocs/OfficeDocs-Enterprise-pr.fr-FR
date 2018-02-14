---
title: "Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell"
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Explique comment utiliser Office 365 PowerShell attribuer une licence Office 365 pour les utilisateurs sans licence.
ms.openlocfilehash: 688e2775e7a028cd9dbe0c8ea27a7f3a453b5279
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="81f51-103">Attribuer des licences à des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81f51-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="81f51-104">**Résumé :**  Explique comment utiliser Office 365 PowerShell attribuer une licence Office 365 pour les utilisateurs sans licence.</span><span class="sxs-lookup"><span data-stu-id="81f51-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="81f51-p101">Gestionnaire de licences des comptes d’utilisateurs dans Office 365 est important, car les utilisateurs ne peuvent pas utiliser des services Office 365 jusqu'à ce que son compte a été concédé sous licence. Vous pouvez utiliser Office 365 PowerShell à attribuer efficacement des licences à des comptes sans licence, en particulier de plusieurs comptes.</span><span class="sxs-lookup"><span data-stu-id="81f51-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="81f51-107">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="81f51-107">Before you begin</span></span>
<span data-ttu-id="81f51-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="81f51-108"></span></span>

- <span data-ttu-id="81f51-p102">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="81f51-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="81f51-p103">L’applet de commande **Get-MsolAccountSku** permet d’afficher les plans de gestion des licences disponibles et le nombre de licences disponibles dans chaque plan dans votre organisation. Le nombre de licences disponibles dans chaque plan est **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Pour plus d’informations sur les licences des plans, les licences et les services, reportez-vous à la section [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="81f51-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="81f51-114">Pour rechercher les comptes sans licence dans votre organisation, exécutez la commande`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="81f51-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="81f51-p104">Vous pouvez attribuer des licences qu’aux comptes utilisateurs qui ont la propriété **UsageLocation** pour un valide ISO 3166-1 alpha-2 régional. Par exemple, US pour les États-Unis et FR pour la France. Certains services Office 365 ne sont pas disponibles dans certains pays. Pour plus d’informations, consultez [à propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="81f51-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="81f51-p105">Pour rechercher les comptes qui n’ont pas une valeur **UsageLocation** , exécutez la commande `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Pour définir la valeur de **UsageLocation** sur un compte, utilisez la syntaxe `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Par exemple, `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="81f51-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="81f51-122">Si vous utilisez l’applet de commande **Get-MsolUser** sans utiliser le `-All` paramètre, seuls les 500 premiers comptes de sont retournés.</span><span class="sxs-lookup"><span data-stu-id="81f51-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="81f51-123">La version courte (instructions sans explications)</span><span class="sxs-lookup"><span data-stu-id="81f51-123">The short version (instructions without explanations)</span></span>
<span data-ttu-id="81f51-124"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="81f51-124"></span></span>

<span data-ttu-id="81f51-p106">Cette section présente les procédures sans explications détaillées. Si vous avez des questions ou souhaitez plus d’informations, vous pouvez lire le reste de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="81f51-p106">This section presents the procedures without detailed explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="81f51-127">Pour attribuer une licence à un utilisateur, utilisez la syntaxe suivante dans Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="81f51-127">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="81f51-128">Cet exemple assigne une licence à partir de la `litwareinc:ENTERPRISEPACK` (Office 365 entreprise E3) le plan licence à l’utilisateur sans licence `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="81f51-128">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="81f51-129">Pour attribuer une licence à plusieurs utilisateurs sans licence, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="81f51-129">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="81f51-130">**Notes**</span><span class="sxs-lookup"><span data-stu-id="81f51-130">**Notes**</span></span>
  
- <span data-ttu-id="81f51-131">Vous ne pouvez pas attribuer plusieurs licences à un utilisateur à partir du même plan de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="81f51-131">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="81f51-132">Si vous n’avez pas assez de licences disponibles, les licences sont attribuées aux utilisateurs dans l’ordre dans lequel ils sont renvoyés par l’applet de commande **Get-MsolUser** jusqu'à épuisement des licences disponibles.</span><span class="sxs-lookup"><span data-stu-id="81f51-132">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="81f51-133">Cet exemple affecte les licences à partir de la `litwareinc:ENTERPRISEPACK` plan de gestion des licences (Office 365 entreprise E3) à tous les utilisateurs sans licence.</span><span class="sxs-lookup"><span data-stu-id="81f51-133">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="81f51-134">Dans cet exemple, les mêmes licences sont attribuées à des utilisateurs sans licence du département des ventes aux États-Unis.</span><span class="sxs-lookup"><span data-stu-id="81f51-134">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="81f51-135">La version longue (instructions avec des explications détaillées)</span><span class="sxs-lookup"><span data-stu-id="81f51-135">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="81f51-136"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="81f51-136"></span></span>

<span data-ttu-id="81f51-p107">Comme indiqué dans l’article [permet d’afficher les utilisateurs sous licence et sans licence avec Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), il est possible que les utilisateurs qui disposent d’un compte utilisateur valide Office 365, mais qui n’ont pas reçu d’une licence d’Office 365. Cela signifie que, compte valide ou aucun compte valide, ces utilisateurs ne sera pas en mesure de se connecter à Office 365. Et si vous ne pouvez pas vous connecter, vous ne pouvez pas tirer parti des services Office 365.</span><span class="sxs-lookup"><span data-stu-id="81f51-p107">As noted in the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), it's possible to have users who have valid Office 365 user accounts, but who have not been issued an Office 365 license. That means that, valid account or no valid account, those users will not be able to log on to Office 365. And if you can't log on, you can't take advantage of any Office 365 services.</span></span>
  
<span data-ttu-id="81f51-140">L’article susmentionné indique également que nous pouvons renvoyer une liste de comptes d’utilisateurs sans licence en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="81f51-140">The aforementioned article also noted that we can return a list of unlicensed user accounts by running this command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="81f51-141">Cette commande renvoie des informations sur les utilisateurs qui ne sont pas actuellement une licence pour Office 365 :</span><span class="sxs-lookup"><span data-stu-id="81f51-141">That command returns information about any users who are not currently licensed for Office 365:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="81f51-p108">Comme vous pouvez le voir, nous avons un utilisateur sans licence : Belinda Newman. Par conséquent, comment nous faire sur l’attribution d’une licence Office 365 Belinda ?</span><span class="sxs-lookup"><span data-stu-id="81f51-p108">As you can see, we have one unlicensed user: Belinda Newman. So how do we go about assigning Belinda an Office 365 license?</span></span>
  
<span data-ttu-id="81f51-144">Pour commencer, nous allons exécuter l’applet de commande **Get-MsolAccountSku** décrit dans l’article [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span><span class="sxs-lookup"><span data-stu-id="81f51-144">For starters, we're going to run the **Get-MsolAccountSku** cmdlet discussed in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="81f51-145">Cette commande renvoie des données semblables à ceci :</span><span class="sxs-lookup"><span data-stu-id="81f51-145">That command returns data similar to this:</span></span>
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

<span data-ttu-id="81f51-p109">Pourquoi nous exécuter **Get-MsolAccountSku** ? (« Référence », dans le cas où vous vous poseriez la question, est abréviation de « unité de stock ». Pour nos besoins, qui est simplement business-parlent de « produit ».) Il existe deux raisons pourquoi nous avons exécuté **Get-MsolAccountSku**. Nous devons tout d’abord, assurez-vous que nous disposons d’une licence pour affecter des Belinda. Nous disposons de toutes les licences que nous pouvons affecter ? Pour déterminer, nous prendre la valeur de propriété **d’ActiveUnits** (25) et de soustraire les valeurs des propriétés de **ConsumedUnits** (24) et **WarningUnits** (0) :</span><span class="sxs-lookup"><span data-stu-id="81f51-p109">Why did we run **Get-MsolAccountSku** ? ("Sku," in case you're wondering, is short for "stock-keeping unit." For our purposes, that's just business-speak for "product.") There are two reasons why we ran **Get-MsolAccountSku**. First, we need to make sure we actually have a license to assign Belinda. Do we have any licenses we can assign her? To determine that, we take the value of **ActiveUnits** property (25) and subtract the values of the **WarningUnits** (0) and **ConsumedUnits** (24) properties:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="81f51-p110">La propriété **ActiveUnits** indique le nombre de licences que nous avons acheté, et que la valeur combinée de **WarningUnits** et de **ConsumedUnits** nous indique de combien de licences est en cours d’utilisation. Il faut soustraire le nombre de licences déjà parlé pour le nombre de licences que nous avons achetés, nous de savoir combien de licences est toujours disponibles. Comme vous avez de la chance, nous avons une licence disponible pour distribution :</span><span class="sxs-lookup"><span data-stu-id="81f51-p110">The **ActiveUnits** property tells us how many licenses we've purchased, and the combined value of **WarningUnits** and **ConsumedUnits** tells us how many licenses are currently in use. If we subtract the number of licenses already spoken for from the number of licenses we purchased, we'll know how many licenses are still available. As luck would have it, we have one license available for distribution:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="81f51-p111">La seconde, pour affecter à Belinda une nouvelle licence, nous avons besoin de connaître le nom de notre plan de gestion des licences (autrement dit, nous devons savoir **AccountSkuId** ). Dans ce cas, c’est très simple : nous avons un seul plan de gestion des licences ( `litwareinc:ENTERPRISEPACK`). Notez, toutefois, qu’il est possible qu’une organisation dispose de plusieurs plans de gestion des licences. Dans ce cas, **Get-MsolAccountSku** renvoie différentes deux **AccountSkuIds**, et vous devez choisir le programme de licence approprié lors de l’attribution des licences. Pour le moment, cependant, nous allons Coller avec le cas le plus simple et supposons que nous avons qu’un seul plan de gestion des licences.</span><span class="sxs-lookup"><span data-stu-id="81f51-p111">Second, in order to assign Belinda a new license we need to know the name of our licensing plan (that is, we need to know the **AccountSkuId** ). In this case, that's easy: we only have a single licensing plan ( `litwareinc:ENTERPRISEPACK`). Note, however, that it's possible for an organization to have multiple licensing plans. In that case, **Get-MsolAccountSku** would return two different **AccountSkuIds**, and you would need to pick the appropriate licensing plan when assigning licenses. For now, though, we're going to stick with the simplest case, and assume we have just one licensing plan.</span></span>
  
<span data-ttu-id="81f51-p112">Alors comment *allons* nous affecter Belinda Newman une nouvelle licence ? Comme ça :</span><span class="sxs-lookup"><span data-stu-id="81f51-p112">So then how  *do*  we assign Belinda Newman a new license? Like this:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="81f51-162">C’est également vous faire : il suffit d’appeler l’applet de commande **Set-MsolUserLicense** , assurez-vous que vous spécifiez le paramètre _UserPrincipalName_ pour l’utilisateur et le programme de licence approprié.</span><span class="sxs-lookup"><span data-stu-id="81f51-162">That's also you have to do: just call the **Set-MsolUserLicense** cmdlet, making sure that you specify the _UserPrincipalName_ parameter for the user and the appropriate licensing plan.</span></span>
  
<span data-ttu-id="81f51-163">Lorsque **Set-MsolUserLicense** est terminée, vous verrez quelque chose similaire à celui-ci à l’écran :</span><span class="sxs-lookup"><span data-stu-id="81f51-163">When **Set-MsolUserLicense** finishes running, you'll see something similar to this onscreen:</span></span>
  
 `PS C:\\windows\\system32>`
  
<span data-ttu-id="81f51-p113">En d’autres termes, il ne s’affiche que quelque chose s’est produit. Pour vérifier qu’une licence a été attribuée à l’utilisateur, exécutez une commande semblable à la suivante :</span><span class="sxs-lookup"><span data-stu-id="81f51-p113">In other words, it won't look like anything has happened. To verify that the user has been assigned a license, run a command like the following:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

<span data-ttu-id="81f51-166">Si tout fonctionne comme prévu, vous devez voir qu’isLicensed propriété de Belinda est maintenant définie à True :</span><span class="sxs-lookup"><span data-stu-id="81f51-166">If everything worked as expected, you should see that Belinda's isLicensed property is now set to True:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [! Bonne question de sécurité, NOTE]<span data-ttu-id="81f51-p114"> : que se passe-t-il si vous commis une erreur et que vous essayez d’attribuer une licence à un utilisateur qui possède déjà une licence ? Finissent vous donner deux licences pour un seul utilisateur ? > La réponse rapide ? N° ; Office 365 ne vous permettent d’assigner plusieurs licences pour le même utilisateur. (, Plusieurs licences dans le plan de gestion des licences, il s’agit.) Si vous essayez de faire votre commande échouera avec le message d’erreur suivant : > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> certes, ce message d’erreur est un petit peu trompeur : la licence n’est pas vraiment non valide, il est simplement assignée à un utilisateur qui déjà *a* une licence. Toutefois, le message d’erreur, l’important est qu’un utilisateur ne vous retrouver avec plusieurs licences.</span><span class="sxs-lookup"><span data-stu-id="81f51-p114"> Good question: what if you made a mistake and tried to assign a license to a user who already has a license? Will you end up giving two licenses to a single user? > The quick answer? No; Office 365 won't let you assign more than one license to the same user. (Well, more than one license from the same licensing plan, that is.) If you try to do that your command will fail with the following error message: >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> Admittedly, that error message is a tiny bit misleading: the license isn't really invalid, it's just being assigned to a user who already  *has*  a license. But, error message aside, the important thing is that one user won't end up with multiple licenses.</span></span>
  
<span data-ttu-id="81f51-p115">Comme vous venez de voir, il est très facile à utiliser PowerShell de 365 d’Office pour affecter une seule licence à un utilisateur unique. Et ceci nous mène à une question évidente : il ne serait pas aussi simple, peut-être même plus facile d’utiliser le centre d’administration Office 365 pour attribuer une licence unique pour un seul utilisateur ? Eh bien, peut-être ; qui dépend, en partie, si vous êtes le plus à l’aise en utilisant Windows PowerShell ou plus à l’aise en utilisant le centre d’administration Office 365. Lorsque Windows PowerShell s’avère vraiment utile, cependant, est lorsque vous devez attribuer plusieurs licences à plusieurs utilisateurs. Par exemple, cette commande attribue une licence Office 365 à un de vos utilisateurs n’ayant pas déjà une licence :</span><span class="sxs-lookup"><span data-stu-id="81f51-p115">As you've just seen, it's very easy to use Office 365 PowerShell to assign a single license to a single user. And that leads to an obvious question: wouldn't it be just as easy, maybe even easier, to use the Office 365 admin center to assign a single license to a single user? Well, maybe; that depends, in part, on whether you're more comfortable using Windows PowerShell or more comfortable using the Office 365 admin center. Where Windows PowerShell really shines, however, is when you need to assign multiple licenses to multiple users. For example, this command assigns an Office 365 license to any of your users that don't already have a license:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="81f51-p116">Dans la commande précédente, nous avons utiliser **Get-MsolUser** et le paramètre _UnlicensedUsersOnly_ pour renvoyer une collection de tous les comptes d’utilisateur sans licence. Nous passer ensuite cette collection pour l’applet de commande **Set-MsolUserLicense** ; à son tour, **Ensemble-MsolUserLicense** attribue une licence (pris à partir de la `litwareinc:ENTERPRISEPACK` licence plan) à chaque utilisateur dans la collection.</span><span class="sxs-lookup"><span data-stu-id="81f51-p116">In the preceding command, we use **Get-MsolUser** and the _UnlicensedUsersOnly_ parameter to return a collection of all the unlicensed user accounts. We then pass that collection to the **Set-MsolUserLicense** cmdlet; in turn, **Set-MsolUserLicense** assigns a license (taken from the `litwareinc:ENTERPRISEPACK` licensing plan) to each user in the collection.</span></span>
  
<span data-ttu-id="81f51-p117">AH, mais que se passe-t-il si vous avez 5 utilisateurs sans licence mais qu’une seule licence disponible ? Dans ce cas **Set-MsolUserLicense** donnera lieu à la licence disponible pour le premier utilisateur renvoyé par **Get-MsolUser**. **Ensemble-MsolUserLicense** loyalement tente alors d’attribuer une licence à quatre autres utilisateurs, mais les quatre de ces tentatives échoue avec le message d’erreur suivant :</span><span class="sxs-lookup"><span data-stu-id="81f51-p117">Ah, but what if you have 5 unlicensed users but only one available license? In that case **Set-MsolUserLicense** will give the available license to the first user returned by **Get-MsolUser**. **Set-MsolUserLicense** will then dutifully try to assign a license to the other four users, but all four of those attempts will fail along with the following error message:</span></span>
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
<span data-ttu-id="81f51-p118">En d’autres termes, MsolUserLicense de l’ensemble n’échoue pas seulement. Au lieu de cela, il affecte des licences autant que possible. Puis il échouera.</span><span class="sxs-lookup"><span data-stu-id="81f51-p118">In other words, Set-MsolUserLicense won't just fail. Instead, it will assign as many licenses as it can. Only then will it fail.</span></span>
  
<span data-ttu-id="81f51-p119">Nous allons essayer un autre exemple. Vous souhaitez peut-être attribuer une licence à tous les utilisateurs du service des ventes. Pas de problème :</span><span class="sxs-lookup"><span data-stu-id="81f51-p119">Let's try another example. Maybe you'd like to assign a license to all the users in the Sales department. No problem:</span></span>
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="81f51-189">Ou, si vous voulez vraiment faire cela selon les règles de l’art et que vous souhaitez réduire les messages d’erreur et le traitement informatique au minimum, attribuez une licence à tous les utilisateurs sans licence du département des ventes :</span><span class="sxs-lookup"><span data-stu-id="81f51-189">Or, if you want to get really fancy, and if you want to keep error messages and computing processing to a minimum, just assigned a license to unlicensed users from the Sales department:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="81f51-p120">Après tout, il n’existe aucun point tente de licences les utilisateurs déjà une licence. Comme nous l’avons déjà vu, qui ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="81f51-p120">After all, there's no point trying to license users who already have a license. As we've already seen, that won't work.</span></span>
  
<span data-ttu-id="81f51-p121">Voici un autre exemple. Vous souhaitez peut-être licence tous les utilisateurs qui n’ont actuellement une licence Office 365 aux États-Unis. Dans ce cas :</span><span class="sxs-lookup"><span data-stu-id="81f51-p121">Here's another example. Maybe you'd like to license all the US users who don't currently have an Office 365 license. In that case:</span></span>
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="81f51-195">Et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="81f51-195">And so on and so on.</span></span>
  
> [!NOTE]
> <span data-ttu-id="81f51-p122">Combien de temps faut-il pour exécuter une commande, par exemple, émet des licences pour tous les utilisateurs sans licence ? C’est difficile de dire : elle dépend de fait de tout ce qui est du nombre d’utilisateurs dont vous disposez à la vitesse de votre connexion réseau. Si vous avez quelques centaines d’utilisateurs à licence cela contribuera assez rapidement (autrement dit, il ne devrait pas prendre plus d’une minute ou deux). Si vous avez 10 000 utilisateurs autoriser évidemment prendra un peu plus de temps. Mais, loin de constituer tant que qu’il faudrait pour attribuer des licences à 10 000 utilisateurs en utilisant le centre d’administration Office 365.</span><span class="sxs-lookup"><span data-stu-id="81f51-p122">How long does it take to run a command that, say, issues licenses to all your unlicensed users? That's difficult to say: it depends on everything from the number of users you have to the speed of your network connection. If you have a couple hundred users to license this will go reasonably quickly (that is, it shouldn't take more than a minute or two). If you have 10,000 users to license it will obviously take a little longer. But nowhere near as long as it would take to assign licenses to 10,000 users by using the Office 365 admin center.</span></span> 
  
<span data-ttu-id="81f51-p123">Tant que nous sommes sur le sujet, c’est quelque chose que vous devez prendre en compte lorsque l’attribution des licences : si un utilisateur n’a pas une valeur pour la propriété **UsageLocation** vous ne pourrez pas lui attribuer une licence Office 365. À la place, vous obtenez un message d’erreur semblable à celui-ci :</span><span class="sxs-lookup"><span data-stu-id="81f51-p123">As long as we're on the subject, here's something you need to watch out for when assigning licenses: if a user does not have a value configured for the **UsageLocation** property you won't be able to assign that user an Office 365 license. Instead, you'll get an error message similar to this:</span></span>
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
<span data-ttu-id="81f51-p124">De manière quelque peu rond-point, de ce message d’erreur indique que l’utilisateur en question n'a pas été affecté un **UsageLocation**. Comme vous l’avez peut-être deviné, la propriété **UsageLocation** (qui indique la région ou du pays où l’utilisateur utilise généralement Office 365) est extrêmement importante. Pourquoi ? C’est parce que les services disponibles à un utilisateur dépendent non seulement le pack de licence que vous avez acheté mais également sur la résidence de l’utilisateur : règles locales et réglementaires, certains services peut-être pas disponibles pour certains utilisateurs. Si un utilisateur ne possède pas une **UsageLocation**, Office 365 n’a aucun moyen de savoir quels services peuvent légalement être exposés à cet utilisateur. Par conséquent, Office 365 n’offrent pas tous les services à l’utilisateur, au moins pas jusqu'à ce que l' **UsageLocation** a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="81f51-p124">In somewhat-roundabout fashion, this error message tells us that the user in question has not been assigned a **UsageLocation**. As you might have guessed, the **UsageLocation** property (which indicates the region or country where the user typically uses Office 365) is extremely important. Why? That's because the services available to a user depend not only on the licensing pack that you purchased but also on where the user lives: due to local rules and regulations, some services might not be available to some users. If a user doesn't have a **UsageLocation**, Office 365 has no way of knowing which services can legally be exposed to that user. Therefore, Office 365 can't offer any services to that user, at least not until the **UsageLocation** has been specified.</span></span>
  
> [!NOTE]
> <span data-ttu-id="81f51-p125">Lorsque vous configurez un compte d’utilisateur vous savez immédiatement s’il existe des restrictions de licence associées à la partie spécifiée du monde. Par exemple, si vous modifiez **UsageLocation** d’un utilisateur sous licence en Iran ( `IR`), la commande échouera avec le message d’erreur : `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> c’est parce que Office 365 n’est pas actuellement disponible pour les utilisateurs en Iran. Pour plus d’informations, consultez [à propos des restrictions de licence](https://go.microsoft.com/fwlink/p/?LinkId=691730). Incidemment, Office 365 utilise les codes de pays à deux lettres produites par l’organisation internationale de normalisation (ISO). Vous pouvez trouver ces codes sur le [site web ISO](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span><span class="sxs-lookup"><span data-stu-id="81f51-p125">When you configure a user account you'll know immediately if there are any license restrictions associated with the specified part of the world. For example, if you change the **UsageLocation** for a licensed user to Iran ( `IR`), the command will fail with this error message: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> That's because Office 365 is not currently available to users in Iran. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730). Incidentally, Office 365 uses the two-letter country codes produced by the International Organization for Standardization (ISO). You can find those codes on the [ISO web site](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span></span> 
  
<span data-ttu-id="81f51-214">Si vous souhaitez vérifier si un utilisateur donné a une **UsageLocation** , vous pouvez utiliser une commande similaire à celle-ci :</span><span class="sxs-lookup"><span data-stu-id="81f51-214">If you want to verify that a given user has a **UsageLocation** you can use a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

<span data-ttu-id="81f51-215">Sinon, vous pouvez retourner une liste de tous les utilisateurs qui n’ont pas une **UsageLocation** à l’aide de cette commande :</span><span class="sxs-lookup"><span data-stu-id="81f51-215">Alternatively, you can return a list of all the users who don't have a **UsageLocation** by using this command:</span></span>
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> <span data-ttu-id="81f51-p126">Lorsque vous attribuez une licence à un utilisateur utilisateur, par défaut, aura accès à tous les services que votre organisation dispose de l’accès à Office 365. Par exemple, si vous avez acheté des licences pour Office 365 entreprise E3, votre utilisateur nouvellement disposant d’une licence sera automatiquement avoir accès aux services Exchange Online, Skype pour Business Online et SharePoint Online. Si vous préférez limiter l’accès d’un utilisateur à ces services (par exemple, vous souhaitez un utilisateur d’accéder à SharePoint Online, mais *pas* à Exchange Online et Skype pour Business Online) puis consultez l’article [, désactivation de l’accès aux services avec Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="81f51-p126">When you assign a license to a user that user will, by default, be given access to all the Office 365 services that your organization has access to. For example, if you purchased licenses for Office 365 Enterprise E3, your newly-licensed user will automatically be granted access to services like Exchange Online, Skype for Business Online, and SharePoint Online. If you would prefer to limit a user's access to those services (for example, you might want a user to have access to SharePoint Online but  *not*  to Exchange Online and Skype for Business Online) then see the article [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span></span> 
  
## <a name="new-to-office-365"></a><span data-ttu-id="81f51-219">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="81f51-219">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="81f51-220">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81f51-220">See Also</span></span>
<span data-ttu-id="81f51-221"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="81f51-221"></span></span>

<span data-ttu-id="81f51-222">Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="81f51-222">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="81f51-223">Création de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81f51-223">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="81f51-224">Suppression et restauration de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81f51-224">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="81f51-225">Bloquer des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81f51-225">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="81f51-226">Supprimer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="81f51-226">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="81f51-227">Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="81f51-227">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="81f51-228">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="81f51-228">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="81f51-229">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="81f51-229">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="81f51-230">Ensemble-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="81f51-230">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="81f51-231">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="81f51-231">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="81f51-232">Select-Object</span><span class="sxs-lookup"><span data-stu-id="81f51-232">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="81f51-233">Where-Object</span><span class="sxs-lookup"><span data-stu-id="81f51-233">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

