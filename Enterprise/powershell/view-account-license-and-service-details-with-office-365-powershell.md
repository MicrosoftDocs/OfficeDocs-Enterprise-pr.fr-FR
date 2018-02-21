---
title: "Afficher les détails de service et de licence de compte avec Office 365 PowerShell"
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
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: "Explique comment utiliser Office 365 PowerShell pour déterminer les services Office 365 qui ont été affectées aux utilisateurs."
ms.openlocfilehash: 69784b43e6e2b24f776d07a937877e5ae0c74888
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="6b259-103">Afficher les détails de service et de licence de compte avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b259-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="6b259-104">**Résumé :** Explique comment utiliser Office 365 PowerShell pour déterminer les services Office 365 qui ont été affectées aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6b259-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="6b259-p101">Dans Office 365, les licences à partir de plans de gestion de licences (également appelé SKU ou Office 365 plans) donner aux utilisateurs d’accéder aux services Office 365 définies pour ces plans. Toutefois, un utilisateur ne peut pas avoir accès à tous les services qui sont disponibles dans une licence qui leur est actuellement assignée. Vous pouvez utiliser Office 365 PowerShell pour afficher l’état des services sur des comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6b259-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="6b259-108">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="6b259-108">Before you begin</span></span>
<span data-ttu-id="6b259-109"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="6b259-109"></span></span>

- <span data-ttu-id="6b259-p102">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6b259-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="6b259-112">Utilisez les commandes `Get-MsolAccountSku` et `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` pour trouver les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6b259-112">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="6b259-113">Plans de gestion de licences disponibles dans votre organisation.</span><span class="sxs-lookup"><span data-stu-id="6b259-113">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="6b259-114">Services disponibles dans chaque plan de gestion de licences et l’ordre dans lequel ils sont répertoriés (numéro d’index).</span><span class="sxs-lookup"><span data-stu-id="6b259-114">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="6b259-115">Pour plus d’informations sur les licences de plans, de licence et de services, voir [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6b259-115">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="6b259-116">Utilisez la commande `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` pour rechercher les licences attribuées à un utilisateur et l’ordre dans lequel ils sont répertoriés (le numéro d’index).</span><span class="sxs-lookup"><span data-stu-id="6b259-116">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="6b259-117">Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _All_, seuls les 500 premiers comptes sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="6b259-117">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="6b259-118">La version courte (instructions sans explications)</span><span class="sxs-lookup"><span data-stu-id="6b259-118">The short version (instructions without explanations)</span></span>
<span data-ttu-id="6b259-119"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="6b259-119"></span></span>

<span data-ttu-id="6b259-120">Pour afficher tous les services Office 365 PowerShell auxquelles un utilisateur a accès, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="6b259-120">To view all the Office 365 PowerShell services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="6b259-p103">Cet exemple montre les services auxquels l’utilisateur BelindaN@litwareinc.com a accès. Affiche les services qui sont associés à toutes les licences sont attribuées à son compte.</span><span class="sxs-lookup"><span data-stu-id="6b259-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="6b259-123">Cet exemple montre les services auxquels cet utilisateur BelindaN@litwareinc.com a accès à partir de la première licence attribuée à son compte (le numéro d’index est égal à 0).</span><span class="sxs-lookup"><span data-stu-id="6b259-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="6b259-124">Pour rechercher tous les utilisateurs sous licence qui ont été activés ou désactivés pour des services spécifiques, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="6b259-124">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="6b259-125">Ces exemples utilisent les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6b259-125">These examples use the following information:</span></span>
  
- <span data-ttu-id="6b259-126">La licence qui permet d’accéder aux services Office 365 qui nous intéresse est la première qui est affecté à tous les utilisateurs (le numéro d’index est égal à 0).</span><span class="sxs-lookup"><span data-stu-id="6b259-126">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="6b259-p104">Les services Office 365 qui nous intéressent sont Skype pour Business Online et Exchange Online. Pour les licences associées avec le plan de gestion des licences, Skype pour Business Online est le service 6 (le numéro d’index est 5), et Exchange Online est le service 9e répertoriés (le numéro d’index est 8).</span><span class="sxs-lookup"><span data-stu-id="6b259-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="6b259-129">Cet exemple renvoie tous les titulaires qui sont activés pour Skype pour Business Online et Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="6b259-129">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="6b259-130">Cet exemple retourne tous les utilisateurs sous licence qui ne sont pas activés pour Skype pour Business Online ou Exchange en ligne.</span><span class="sxs-lookup"><span data-stu-id="6b259-130">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="6b259-131">La version longue (instructions avec des explications détaillées)</span><span class="sxs-lookup"><span data-stu-id="6b259-131">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="6b259-132"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="6b259-132"></span></span>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a><span data-ttu-id="6b259-133">Rechercher des services Office 365 PowerShell auxquelles un utilisateur a accès</span><span class="sxs-lookup"><span data-stu-id="6b259-133">Find the Office 365 PowerShell services that a user has access to</span></span>

<span data-ttu-id="6b259-p105">Il est évidemment important de savoir quels utilisateurs ont été des licences Office 365 et les utilisateurs qui n’ont pas. (Voir l’article [Afficher les utilisateurs sous licence ou non avec Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) pour plus d’informations). Toutefois, simplement disposer d’une licence de Office 365 ne vous indique pas quoi que ce soit sur ce que cet utilisateur peut réellement faire avec Office 365. Il permet de Exchange Online ou Skype pour entreprise en ligne ? Cet utilisateur peut accéder à SharePoint Online ? Il a accès à Office Professionnel Plus ? Disposer d’une licence signifie simplement que l’utilisateur a la possibilité d’accéder à ces services. Toutefois, les fonctionnalités disponibles à un utilisateur dépendent des services qui ont été activées sur la licence sa.</span><span class="sxs-lookup"><span data-stu-id="6b259-p105">It's obviously important for you to know which users have been issued Office 365 licenses and which users haven't. (See the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) for more information). However, simply having an Office 365 license doesn't tell you anything about what that user can actually do with Office 365. Can he or she use Exchange Online or Skype for Business Online? Can this user access SharePoint Online? Does he or she have access to Office Professional Plus? Having a license simply means that the user has the potential to access these services. However, the capabilities available to a user depend on the services that have been enabled on his or her license.</span></span>
  
<span data-ttu-id="6b259-p106">Comment pouvons-nous nous déterminer les fonctionnalités d’Office 365 un utilisateur a accès à ? Pour effectuer une opération que nous avons besoin exécuter une commande similaire à celui-ci :</span><span class="sxs-lookup"><span data-stu-id="6b259-p106">So how can we determine which Office 365 features a user has access to? To do that we need to run a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

<span data-ttu-id="6b259-144">Dans cette commande, nous utilisons la cmdlet **Get-MsolUser** pour renvoyer des informations sur le compte BelindaN@litwareinc.com. Une fois que nous avons renvoyé ces informations, nous les données de compte vers la cmdlet **Select-Object** de tuyau et demander **Select-Object** « développer » la valeur de la propriété de **licences** :</span><span class="sxs-lookup"><span data-stu-id="6b259-144">In this command, we're using the **Get-MsolUser** cmdlet to return information about the account BelindaN@litwareinc.com. Once we've returned that information, we then pipe the account data to the **Select-Object** cmdlet and ask **Select-Object** to "expand" the value of the **Licenses** property:</span></span>
  
 `Select-Object -ExpandProperty Licenses`
  
<span data-ttu-id="6b259-p107">Pourquoi faisons-nous cela ? Ainsi, par défaut les **licences** de propriété uniquement nous indique le nom de la licence pack d'où proviennent les licences de Belinda :</span><span class="sxs-lookup"><span data-stu-id="6b259-p107">Why do we do that? Well, by default the **Licenses** property only tells us the name of the licensing pack where Belinda's license came from:</span></span>
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

<span data-ttu-id="6b259-147">« Extension » de la propriété de **licences** nous donne un peu plus d’informations :</span><span class="sxs-lookup"><span data-stu-id="6b259-147">"Expanding" the **Licenses** property gives us a little more information:</span></span>
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

<span data-ttu-id="6b259-148">Et puis en développant la propriété de **l’état du service** nous pouvons obtenir encore plus d’informations :</span><span class="sxs-lookup"><span data-stu-id="6b259-148">And then by expanding the **ServiceStatus** property we can get back even more information:</span></span>
  
|<span data-ttu-id="6b259-149">Plan de service \*\*\*</span><span class="sxs-lookup"><span data-stu-id="6b259-149">****Service plan****</span></span>|<span data-ttu-id="6b259-150">Description \*\*\*</span><span class="sxs-lookup"><span data-stu-id="6b259-150">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="6b259-151">Sway</span><span class="sxs-lookup"><span data-stu-id="6b259-151">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="6b259-152">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6b259-152">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="6b259-153">Yammer</span><span class="sxs-lookup"><span data-stu-id="6b259-153">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="6b259-154">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="6b259-154">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="6b259-155">Office Professionnel Plus</span><span class="sxs-lookup"><span data-stu-id="6b259-155">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="6b259-156">Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="6b259-156">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="6b259-157">Office Online</span><span class="sxs-lookup"><span data-stu-id="6b259-157">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="6b259-158">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6b259-158">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="6b259-159">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="6b259-159">Exchange Online Plan 2</span></span>  <br/> |
   
> [!NOTE]
> <span data-ttu-id="6b259-p108">Vous dites qui est trop tapant ? De même, si vous pouvez placer avec un peu obtuseness de Windows PowerShell, vous pouvez exécuter cette version condensée de la commande à la place : >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span><span class="sxs-lookup"><span data-stu-id="6b259-p108">You say that's too much typing? Well, if you can put up with a little Windows PowerShell obtuseness, you can run this condensed version of the command instead: >  `(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span></span>
  
<span data-ttu-id="6b259-p109">Dans le cas où vous vous poseriez la question, nous pouvons « développer » la propriété **licences** **licences** étant une propriété à valeurs multiples : il s’agit d’une seule propriété qui peut stocker plusieurs valeurs. Nous allons développer une valeur de propriété que nous avons simplement le détail obtenir ces valeurs supplémentaires qui, par défaut, ne sont pas affichées à l’écran.</span><span class="sxs-lookup"><span data-stu-id="6b259-p109">In case you're wondering, we can "expand" the **Licenses** property because **Licenses** is a multivalued property: it's a single property that can store multiple values. When we expand a property value we simply drill down to get at these additional values that, by default, are not displayed onscreen.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6b259-p110">Comment êtes-vous supposé savoir qu’une valeur est une propriété à valeurs multiples ? Ainsi, pour trouver des, essayez exécutant une commande similaire à celle-ci : > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> la cmdlet **Get-member** renvoie des informations sur l’objet lui-même ; Dans ce cas, les informations sur la propriété valeurs constituant un objet compte d’utilisateur. Voici ce que **Get-Member** a à dire sur la propriété de **licences** : > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> Si la définition de propriété disant quelque chose sur les collections (dans ce cas, `System.Collections.Generic.List`) vous savez que vous avez affaire à une propriété à valeurs multiples.</span><span class="sxs-lookup"><span data-stu-id="6b259-p110">So how are you supposed to know that a value is a multivalued property? Well, to find that out, try running a command similar to this: >  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> The **Get-member** cmdlet returns information about the object itself; in this case, information about the property values that make up a user account object. Here's what **Get-Member** has to say about the **Licenses** property:>  `Licenses Property System.Collections.Generic.List[Microsoft.On...`> If the property definition says something about collections (in this case,  `System.Collections.Generic.List`) then you know you're dealing with a multivalued property.</span></span> 
  
<span data-ttu-id="6b259-p111">Ainsi que tout cela signifie-t-il ? Pour répondre à cette question, nous allons tout d’abord examiner une nouvelle les informations retournées par l’applet de commande **Get-MsolUser** :</span><span class="sxs-lookup"><span data-stu-id="6b259-p111">So what does all this mean? To answer that, let's first take another look at the information returned by the **Get-MsolUser** cmdlet:</span></span>
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

<span data-ttu-id="6b259-169">Et également Examinons un un tableau expliquant ce que ces plans de service de façon étrange nommé représentent vraiment :</span><span class="sxs-lookup"><span data-stu-id="6b259-169">And let's also take a look at a table that explains what these oddly-named service plans really represent:</span></span>
  
|<span data-ttu-id="6b259-170">Plan de service \*\*\*</span><span class="sxs-lookup"><span data-stu-id="6b259-170">****Service plan****</span></span>|<span data-ttu-id="6b259-171">Description \*\*\*</span><span class="sxs-lookup"><span data-stu-id="6b259-171">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="6b259-172">Sway</span><span class="sxs-lookup"><span data-stu-id="6b259-172">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="6b259-173">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6b259-173">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="6b259-174">Yammer</span><span class="sxs-lookup"><span data-stu-id="6b259-174">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="6b259-175">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="6b259-175">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="6b259-176">Office Professionnel Plus</span><span class="sxs-lookup"><span data-stu-id="6b259-176">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="6b259-177">Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="6b259-177">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="6b259-178">Office Online</span><span class="sxs-lookup"><span data-stu-id="6b259-178">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="6b259-179">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6b259-179">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="6b259-180">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="6b259-180">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="6b259-p112">Compris ?  `MCOSTANDARD` est simplement un nom de programmation interne de Skype pour Business Online, tandis que `OFFICESUSBCRIPTION` est simplement le nom de programmation interne pour Office Professionnel Plus. Il n’est pas la chose la plus intuitive dans le monde, mais tant que vous gardez cette table pratique vous n’aurez pas beaucoup de problèmes lorsqu’il s’agit de travailler avec les services d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="6b259-p112">Got all that?  `MCOSTANDARD` is just an internal programming name for Skype for Business Online, while `OFFICESUSBCRIPTION` is just the internal programming name for Office Professional Plus. It's not the most intuitive thing in the world, but as long as you keep this table handy you won't have many problems when it comes to working with Office 365 services.</span></span>
  
<span data-ttu-id="6b259-p113">Mais attendez : il est plus. Comme nous l’avons appris dans l’article, [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), si la **ProvisioningStatus** est définie sur `Success` qui signifie que le service a été entièrement activé ; par exemple si `MCOSTANDARD` est défini sur `Success` qui signifie que l’utilisateur peut accéder à Skype pour l’activité en ligne. Si la **ProvisioningStatus** est définie sur `PendingInput` qui signifie que Office 365 est toujours traitement de la demande de service ; Toutefois, l’utilisateur peut en général une session et accéder au service, tandis que la demande termine le traitement. ( `YAMMER_ENTERPRISE` sont toujours affichés en tant que `PendingInput`, mais c’est OK : qui n’empêchera pas un utilisateur de se connecter à Yammer).</span><span class="sxs-lookup"><span data-stu-id="6b259-p113">But wait: there's more. As we learned in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), if the **ProvisioningStatus** is set to `Success` that means that the service has been fully enabled; for example if `MCOSTANDARD` is set to `Success` that means that the user can access Skype for Business Online. If the **ProvisioningStatus** is set to `PendingInput` that means that Office 365 is still processing the service request; however, the user can typically log on and access the service while the request finishes processing. ( `YAMMER_ENTERPRISE` will always be shown as `PendingInput`, but that's OK: that won't stop a user from logging on to Yammer).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="6b259-188">Les utilisateurs peuvent installer et activer une nouvelle installation d’Office Professionnel Plus lors de la `OFFICESUBSCRIPTION` dans les `PendingInput` état.</span><span class="sxs-lookup"><span data-stu-id="6b259-188">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="6b259-189">Et, en soi, est un service est défini sur `Disabled` qui signifie que le service en question n’est pas disponible pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6b259-189">And, needless to say, is a service is set to  `Disabled` that means that the service in question is not available to the user.</span></span>
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a><span data-ttu-id="6b259-190">Rechercher les utilisateurs qui ont accès à des services Office 365 PowerShell spécifiques</span><span class="sxs-lookup"><span data-stu-id="6b259-190">Find users that have access to specific Office 365 PowerShell services</span></span>

<span data-ttu-id="6b259-p114">Dans un autre article, nous avons vu comment vous pouvez utiliser Office 365 PowerShell pour désactiver l’accès utilisateur aux services. (Si vous avez manqué de cet article, reportez-vous à la section [désactiver l’accès aux services Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). Qui mène à une question évidente : existe-t-il un moyen pour déterminer quels *utilisateurs* (c'est-à-dire, plusieurs utilisateurs) ont les services activé ou désactivé ?</span><span class="sxs-lookup"><span data-stu-id="6b259-p114">In a separate article, we saw how you can use Office 365 PowerShell to disable user access to services. (If you missed that article, see [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). That leads to an obvious question: is there any way to determine which  *users*  (that is, more than one user) have which services enabled or disabled?</span></span>
  
<span data-ttu-id="6b259-p115">Nous étions en espérant que quelqu'un demande qui. Pour répondre à cette question, examinons le tableau des services que nous avons d’abord étudiés dans l’article [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) pour notre plan de licence disponible uniquement `litwareinc:ENTERPRISEPACK`:</span><span class="sxs-lookup"><span data-stu-id="6b259-p115">We were hoping that someone would ask that. In order to answer that question, let's review the table of services that we first looked at in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) for our only available licensing plan `litwareinc:ENTERPRISEPACK`:</span></span>
  
|<span data-ttu-id="6b259-196">Plan de service \*\*\*</span><span class="sxs-lookup"><span data-stu-id="6b259-196">****Service plan****</span></span>|<span data-ttu-id="6b259-197">Description \*\*\*</span><span class="sxs-lookup"><span data-stu-id="6b259-197">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="6b259-198">Sway</span><span class="sxs-lookup"><span data-stu-id="6b259-198">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="6b259-199">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6b259-199">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="6b259-200">Yammer</span><span class="sxs-lookup"><span data-stu-id="6b259-200">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="6b259-201">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="6b259-201">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="6b259-202">Office Professionnel Plus</span><span class="sxs-lookup"><span data-stu-id="6b259-202">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="6b259-203">Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="6b259-203">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="6b259-204">Office Online</span><span class="sxs-lookup"><span data-stu-id="6b259-204">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="6b259-205">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6b259-205">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="6b259-206">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="6b259-206">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="6b259-p116">Comme vous vous en souvenez peut-être, le plan de service n’est rien de plus que le nom de programmation interne pour un produit ; par exemple, `OFFICESUBSCRIPTION`, au nom d’un, est le nom de programmation interne d’Office Professionnel Plus. Si `OFFICESUBSCRIPTION` s’affiche en tant que `SUCCESS` sur le plan de service d’un utilisateur, puis qui signifie que l’utilisateur est autorisé à accéder à Office Professionnel Plus. Si `EXCHANGE_S_ENTERPRISE` est répertorié en tant que `DISABLED` qui signifie que l’utilisateur ne peut pas utiliser Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="6b259-p116">As you might recall, the service plan is nothing more than the internal programming name for a product; for example,  `OFFICESUBSCRIPTION`, to name one, is the internal programming name for Office Professional Plus. If  `OFFICESUBSCRIPTION` shows up as `SUCCESS` on a user's service plan, then that means that the user is allowed to access Office Professional Plus. If `EXCHANGE_S_ENTERPRISE` is listed as `DISABLED` that means the user can't use Exchange Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="6b259-210">Les utilisateurs peuvent installer et activer une nouvelle installation d’Office Professionnel Plus lors de la `OFFICESUBSCRIPTION` dans les `PendingInput` état.</span><span class="sxs-lookup"><span data-stu-id="6b259-210">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="6b259-p117">Est maintenant le moment où l’ordre dans lequel apparaissent les services est extrêmement importante. Windows PowerShell attribue un numéro d’index à chaque entrée de la liste. La première entrée est 0, l’entrée suivante est 1 et ainsi de suite. Les résultats sont expliqués dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="6b259-p117">Now is the time where the order in which the services appear is extremely important. Windows PowerShell assigns an index number to each entry in the list. The first entry is 0, the next entry is 1, and so on. The results are explained in the following table:</span></span>
  
|<span data-ttu-id="6b259-215">Numéro d’index de \*\*\*</span><span class="sxs-lookup"><span data-stu-id="6b259-215">****Index number****</span></span>|<span data-ttu-id="6b259-216">Plan de service \*\*\*</span><span class="sxs-lookup"><span data-stu-id="6b259-216">****Service plan****</span></span>|
|:-----|:-----|
|<span data-ttu-id="6b259-217">0</span><span class="sxs-lookup"><span data-stu-id="6b259-217">0</span></span>  <br/> | `SWAY` <br/> |
|<span data-ttu-id="6b259-218">1</span><span class="sxs-lookup"><span data-stu-id="6b259-218">1</span></span>  <br/> | `INTUNE_O365` <br/> |
|<span data-ttu-id="6b259-219">2</span><span class="sxs-lookup"><span data-stu-id="6b259-219">2</span></span>  <br/> | `YAMMER_ENTERPRISE` <br/> |
|<span data-ttu-id="6b259-220">3</span><span class="sxs-lookup"><span data-stu-id="6b259-220">3</span></span>  <br/> | `RMS_S_ENTERPRISE` <br/> |
|<span data-ttu-id="6b259-221">4</span><span class="sxs-lookup"><span data-stu-id="6b259-221">4</span></span>  <br/> | `OFFICESUBSCRIPTION` <br/> |
|<span data-ttu-id="6b259-222">5</span><span class="sxs-lookup"><span data-stu-id="6b259-222">5</span></span>  <br/> | `MCOSTANDARD` <br/> |
|<span data-ttu-id="6b259-223">6</span><span class="sxs-lookup"><span data-stu-id="6b259-223">6</span></span>  <br/> | `SHAREPOINTWAC` <br/> |
|<span data-ttu-id="6b259-224">7</span><span class="sxs-lookup"><span data-stu-id="6b259-224">7</span></span>  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|<span data-ttu-id="6b259-225">8</span><span class="sxs-lookup"><span data-stu-id="6b259-225">8</span></span>  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
<span data-ttu-id="6b259-226">Comme vous pouvez le voir, `SWAY` est le premier service répertorié, afin qu’il soit affecté de numéro d’index 0.</span><span class="sxs-lookup"><span data-stu-id="6b259-226">As you can see,  `SWAY` is the first service listed, so it gets assigned index number 0.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="6b259-p118">Pourquoi 0 et non 1 ? C’est une chose de programmation. Dans les langages de programmation indices indiquent où un élément est « décalage » à partir du début du tableau. Le premier élément *est* le début du tableau, son décalage est donc 0. Le deuxième élément est 1 élément à partir du début du tableau, son décalage est donc 1.</span><span class="sxs-lookup"><span data-stu-id="6b259-p118">Why 0 and not 1? That's a programming thing. In programming languages indices tell you how far an item is "offset" from the beginning of the array. The first item  *is*  the beginning of the array, so its offset is 0. The second item is 1 item from the beginning of the array, so its offset is 1.</span></span>
  
<span data-ttu-id="6b259-p119">Nous allons essayer un exemple. Supposons que nous aimerions une liste de tous les utilisateurs sous licence qui n’ont pas été activé pour Exchange Online. Pour ce faire, nous pouvons utiliser la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6b259-p119">Let's try an example. Suppose we'd like a list of all the licensed users who have not been enabled for Exchange Online. To do that, we can use the following command:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="6b259-p120">Certes, qui est une aspect énigmatiques petite commande, donc prenez une minute pour expliquer comment il fonctionne. Il s’agit en fait d’une commande de deux parties, et la première partie est très simple : nous utilisons la cmdlet **Get-MsolUser** pour renvoyer une collection de tous les utilisateurs de notre Office 365 (sous licence ou non) :</span><span class="sxs-lookup"><span data-stu-id="6b259-p120">Admittedly, that's a cryptic-looking little command, so let's take a minute to explain how it works. This is actually a two-part command, and the first part is very simple: we use the **Get-MsolUser** cmdlet to return a collection of all our Office 365 users (both licensed and unlicensed):</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="6b259-p121">Cette information est ensuite transmise à la cmdlet **Where-Object** . **Where-Object** passe par tous les comptes d’utilisateur et de recherche pour ces comptes qui répondent aux deux critères suivants :</span><span class="sxs-lookup"><span data-stu-id="6b259-p121">That information is then piped to the **Where-Object** cmdlet. **Where-Object** goes through all the user accounts and looks for those accounts that meet both of the following criteria:</span></span>
  
- <span data-ttu-id="6b259-p122">La propriété **isLicensed** est égale à ( `-eq`) `True` ( `$true`). Qui nous permet d’éliminer les utilisateurs sans licence.</span><span class="sxs-lookup"><span data-stu-id="6b259-p122">The **isLicensed** property is equal to ( `-eq`)  `True` ( `$true`). That enables us to weed out the unlicensed users.</span></span>
    
- <span data-ttu-id="6b259-p123">La valeur des licences **[0]. État du service [8]. ProvisioningStatus** propriété est égale à ( `-eq`) `Disabled`. Pour nos besoins immédiats, la partie importante de ce nom de propriété complexe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="6b259-p123">The value of the **Licenses[0].ServiceStatus[8].ProvisioningStatus** property is equal to ( `-eq`)  `Disabled`. For our immediate purposes, the important part of this unwieldy property name is this:</span></span>
    
     `ServiceStatus[8]`
    
    <span data-ttu-id="6b259-p124">Le `[8]` représente le numéro d’index pour Exchange Online. (Nous savons que d’après la table il y a quelques minutes). Que se passe-t-il si nous souhaitons rechercher tous les utilisateurs activés pour Skype pour entreprise en ligne ? Ainsi, le numéro d’index pour Skype pour Business Online est 5, nous utiliserait la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="6b259-p124">The  `[8]` represents the index number for Exchange Online. (We know that from looking at the table a few minutes ago). What if we wanted to find all the users enabled for Skype for Business Online? Well, the index number for Skype for Business Online is 5, so we'd use this syntax:</span></span>
    
     `ServiceStatus[5]`
    
    <span data-ttu-id="6b259-247">Etc., etc.</span><span class="sxs-lookup"><span data-stu-id="6b259-247">Etc., etc.</span></span>
    
    <span data-ttu-id="6b259-p125">Incidemment, `Licenses[0]` indique le plan de gestion des licences qui nous intéressent. Étant donné que notre domaine de test n’a qu’un seul plan de gestion des licences Cela importe peu. Mais supposons que nous avons un utilisateur qui a été attribué des licences à partir de deux plans de licences différents. Dans ce cas, `Licenses[0]` représenterait le premier plan de gestion des licences, et `Licenses[1]` représenterait le deuxième plan de licence.</span><span class="sxs-lookup"><span data-stu-id="6b259-p125">Incidentally,  `Licenses[0]` indicates the licensing plan that we want to look at. Since our test domain only has one licensing plan this doesn't matter much. But suppose we had a user who has been assigned licenses from two different licensing plans. In that case, `Licenses[0]` would represent the first licensing plan, and `Licenses[1]` would represent the second licensing plan.</span></span>
    
    <span data-ttu-id="6b259-252">Pour rechercher les licences attribuées à un utilisateur et l’ordre dans lequel elles sont répertoriées, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6b259-252">To find the licenses that are assigned to a user, and the order in which they are listed, run the following command:</span></span>
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

<span data-ttu-id="6b259-p126">Vous voyez comment tout cela fonctionne ? Le numéro d’index d’Office Professionnel Plus est 4 ; Par conséquent, cette commande renvoie une liste de tous les utilisateurs qui n’ont pas été activées pour Office Professionnel Plus :</span><span class="sxs-lookup"><span data-stu-id="6b259-p126">Do you see how this all works? The index number for Office Professional Plus is 4; therefore, this command returns a list of all the users who have not been enabled for Office Professional Plus:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="6b259-p127">Et si nous voulions une liste d’utilisateurs qui ont été *activés* pour Office Professionnel Plus ? Ainsi, si vous avez été activé votre **état du service** sera `PendingInput` ou `Success`; en d’autres termes, votre **état du service** sera *pas* égaux ( `-ne`) `Disabled`. Cela signifie que tout ce que nous devons faire est de prendre notre commande précédente et permuter les `-eq` opérateur pour le `-ne` opérateur :</span><span class="sxs-lookup"><span data-stu-id="6b259-p127">And what if we wanted a list of users who have been  *enabled*  for Office Professional Plus? Well, if you've been enabled then your **ServiceStatus** will either be `PendingInput` or `Success`; in other words, your **ServiceStatus** will *not*  equal ( `-ne`)  `Disabled`. That means all we have to do is take our previous command and swap out the  `-eq` operator for the `-ne` operator:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="6b259-p128">Comme on passe, que code ne probablement gagner de nombreux concours de beauté. Et vérité informé, le code peut obtenir encore plus compliquée. Par exemple, supposons que nous voulons rechercher les utilisateurs qui ont été activés pour les deux Skype pour Business Online et Exchange Online :</span><span class="sxs-lookup"><span data-stu-id="6b259-p128">As the saying goes, that code probably won't win many beauty contests. And, truth be told, the code can get even more tangled. For example, suppose we want to look for users who have been enabled for both Skype for Business Online and Exchange Online:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="6b259-p129">Mais ne vous inquiétez pas trop sur comment plus compliqué qui peut se présenter : l’important est que, avec relativement peu d’effort, vous pouvez récupérer ces informations. Ne peut pas obtenir cette même information à l’aide du centre d’administration de l’Office 365 ? En théorie, Oui mais, en pratique, non. Pour obtenir cette même information à l’aide du centre d’administration de l’Office 365, vous devez consulter les informations de licence pour chaque utilisateur, un seul utilisateur à la fois, et puis manuellement effectuer le suivi de qui a été activé pour *X* et qui n’avaient pas. Qui fonctionnent, mais soyons honnêtes : Si vous avez des utilisateurs de plus de 10 ou 11, vous n’allez pas à effectuer cette opération. Il est bien trop longues et laborieuses.</span><span class="sxs-lookup"><span data-stu-id="6b259-p129">But don't worry too much about how gnarly that might look: the important thing is that, with relatively little effort, you can retrieve this information. Can't you get at this same information using the Office 365 admin center? In theory, yes but, in practical terms, no. To get at this same information using the Office 365 admin center you'd need to look at the licensing information for each user, one user at a time, and then manually keep track of who'd been enabled for  *X*  and who hadn't. That would work, but let's be honest: if you have more than 10 or 11 users, you're not going to do this. It's way too tedious and time-consuming.</span></span>
  
<span data-ttu-id="6b259-267">Qui, bien sûr, est pourquoi nous devons Windows PowerShell : Windows PowerShell vous économisez des tâches longues et laborieuses que.</span><span class="sxs-lookup"><span data-stu-id="6b259-267">Which, of course, is why we have Windows PowerShell: Windows PowerShell helps save you from tedious and time-consuming tasks such as that.</span></span>
  
<span data-ttu-id="6b259-268">Alors que nous sommes dessus, voici la commande ultime pour l’affichage des informations sur le service :</span><span class="sxs-lookup"><span data-stu-id="6b259-268">While we're at it, here's the ultimate command for viewing service information:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[0].ProvisioningStatus}}, @{Name="MDM";Expression={$_.Licenses[0].ServiceStatus[1].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[2].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[3].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[4].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[5].ProvisioningStatus}}, @{Name="OfficeWeb";Expression={$_.Licenses[0].ServiceStatus[6].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[8].ProvisioningStatus}} | ConvertTo-Html > "C:\\My Documents\\Service Info.html"
```

<span data-ttu-id="6b259-p130">Et Oui, c’est une commande très allures étranges. Mais, il crée un fichier CSV affiche tous les utilisateurs et tous ses États de service.</span><span class="sxs-lookup"><span data-stu-id="6b259-p130">And yes, that's a very crazy-looking command. But it creates a CSV file showing all of your users and all of their service statuses.</span></span>

  
## <a name="see-also"></a><span data-ttu-id="6b259-271">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b259-271">See also</span></span>
<span data-ttu-id="6b259-272"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="6b259-272"></span></span>

<span data-ttu-id="6b259-273">Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="6b259-273">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="6b259-274">Création de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b259-274">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6b259-275">Supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b259-275">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6b259-276">Bloquer des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b259-276">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6b259-277">Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b259-277">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6b259-278">Supprimer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b259-278">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="6b259-279">Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="6b259-279">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="6b259-280">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="6b259-280">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="6b259-281">Format-List</span><span class="sxs-lookup"><span data-stu-id="6b259-281">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="6b259-282">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="6b259-282">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="6b259-283">Select-Object</span><span class="sxs-lookup"><span data-stu-id="6b259-283">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="6b259-284">Where-Object</span><span class="sxs-lookup"><span data-stu-id="6b259-284">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="6b259-285">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="6b259-285">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]