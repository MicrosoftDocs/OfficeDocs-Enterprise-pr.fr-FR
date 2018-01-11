---
title: Afficher les utilisateurs avec ou sans licence avec Office 365 PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Explique comment utiliser Office 365 PowerShell pour afficher des comptes d'utilisateurs sous licence ou non.
ms.openlocfilehash: fe4f75d9d8dbc85efbc71856192dbaece3e84fbc
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="08f89-103">Afficher les utilisateurs avec ou sans licence avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="08f89-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="08f89-104">**Résumé :** Explique comment utiliser Office 365 PowerShell pour afficher des comptes d'utilisateurs sous licence ou non.</span><span class="sxs-lookup"><span data-stu-id="08f89-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="08f89-p101">Il se peut que l'intégralité, une partie ou aucune des licences disponibles soit attribuée aux comptes d'utilisateurs de votre organisation Office 365 à partir des plans de gestion des licences disponibles dans votre organisation. Vous pouvez utiliser Office 365 PowerShell pour rechercher rapidement les utilisateurs avec ou sans licence dans votre organisation.</span><span class="sxs-lookup"><span data-stu-id="08f89-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="08f89-107">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="08f89-107">Before you begin</span></span>

- <span data-ttu-id="08f89-p102">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="08f89-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="08f89-110">Si vous utilisez la cmdlet **Get-MsolUser** sans utiliser le paramètre _-All_, seuls les 500 premiers comptes sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="08f89-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="08f89-111">La version courte (instructions sans explications)</span><span class="sxs-lookup"><span data-stu-id="08f89-111">The short version (instructions without explanations)</span></span>

<span data-ttu-id="08f89-p103">Cette section présente les procédures sans explication superflue ou alambiquée. Si vous avez des questions ou que vous souhaitez plus d'informations, vous pouvez lire le reste de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="08f89-p103">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="08f89-114">Pour afficher la liste de tous les comptes d'utilisateurs et leur statut de licence dans votre organisation, exécutez la commande suivante dans Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="08f89-114">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="08f89-115">Pour afficher la liste de tous les comptes d’utilisateurs sans licence dans votre organisation, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="08f89-115">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="08f89-116">Pour afficher la liste de tous les comptes d’utilisateurs avec licence dans votre organisation, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="08f89-116">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="08f89-117">La version longue (instructions avec des explications détaillées)</span><span class="sxs-lookup"><span data-stu-id="08f89-117">The long version (instructions with detailed explanations)</span></span>

<span data-ttu-id="08f89-p104">Les comptes d'utilisateur Office 365 et les licences Office 365 ne requièrent pas de correspondance de 1 à 1 : il est possible que des utilisateurs Office 365 ne possèdent pas de licence Office 365 et que des licences Office 365 n'aient pas été attribuées à un utilisateur. (En fait, un compte d'utilisateur peut même avoir  *plusieurs*  licences Office 365.) Lorsque vous créez un compte d'utilisateur Office 365 (consultez l'article [utilisateurs de licence Office 365 avec Windows PowerShell](http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx) pour obtenir plus d'informations), vous n'avez pas à attribuer de licence à cet utilisateur : le nouvel utilisateur disposera d'un compte valide, mais il ne sera pas en mesure de se connecter à Office 365. S'il essaie de se connecter, il verra quelque chose de semblable à ceci :</span><span class="sxs-lookup"><span data-stu-id="08f89-p104">Office 365 user accounts and Office 365 licenses don't need to have a one-to-one correspondence: it's possible to have Office 365 users who do not have an Office 365 license, and it's possible to have Office 365 licenses that haven't been assigned to a user. (In fact, a single user account can even have  *multiple*  Office 365 licenses.) When you create a new Office 365 user account (see the article [License Office 365 users with Windows PowerShell](http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx) for more information) you don't have to assign that user a license: the new user will have a valid account, but he or she won't be able to sign in to Office 365. If they try to sign in, they'll see something similar to this:</span></span>
  
![Utilisateur sans licence Office 365 valide.](images/o365_powershell_no_license.png)
  
<span data-ttu-id="08f89-p105">De même, un utilisateur peut décider de prendre des congés prolongés, voire une année sabbatique ou un congé de maternité/paternité. Dans ce cas, vous pouvez retirer la licence à l'utilisateur, mais laisser le compte intact (c'est-à-dire laisser toutes les valeurs de propriété, telles que l'adresse et le numéro de téléphone, telles quelles). Ainsi, vous pouvez attribuer sa licence à quelqu'un d'autre (par exemple, un employé qui remplace temporairement la personne en congé). Lorsque l'utilisateur retourne au travail, vous pouvez lui délivrer une nouvelle licence et il sera en mesure de reprendre le travail comme s'il n'était jamais parti.</span><span class="sxs-lookup"><span data-stu-id="08f89-p105">Likewise, you might have a user who will be taking some extended time off, perhaps for a sabbatical or for maternity/paternity leave. In a case like that, you could remove the user's license but leave the user account intact (that is, leave all its property values, such as address and phone number, as-is). By doing that, you can assign their license to someone else (like, say, a temporary worker filling in for the person on leave). When the user returns to work you can issue them a new license and they'll be able to resume working as if they'd never been gone.</span></span>
  
<span data-ttu-id="08f89-p106">Cela signifie tout simplement que vous pouvez avoir des utilisateurs qui ont un compte mais pas de licence. Ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="08f89-p106">Which simply means that, yes, you can have users who have accounts but who don't have licenses. Or vice-versa.</span></span>
  
<span data-ttu-id="08f89-p107">L'article [Afficher les licences et les services avec Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) explique la façon dont vous pouvez déterminer le nombre de licences Office 365 que votre organisation a achetées, ainsi que le nombre de ces licences qui ont été attribuées à des utilisateurs. Il s'agit d'informations importantes. Toutefois, il est tout aussi important de savoir quels utilisateurs possèdent une licence et lesquels n'en ont pas. Cet article va vous indiquer comment procéder.</span><span class="sxs-lookup"><span data-stu-id="08f89-p107">The article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) explains how you can determine the number of Office 365 licenses your organization has purchased as well as how many of those licenses have been assigned to users. That's important information. Equally important, however is knowing which of your users have been assigned these licenses and which ones haven't. And this article will tell you how to do just that.</span></span>
  
<span data-ttu-id="08f89-p108">Comme vous le savez probablement, la cmdlet **Get-MsolUser** renvoie des informations sur tous vos comptes d'utilisateurs Office 365. Vous avez besoin d'informations rapides sur tous vos utilisateurs Office 365 ? Exécutez la commande suivante dans Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="08f89-p108">As you probably know, the **Get-MsolUser** cmdlet returns information about all your Office 365 user accounts. Need some quick info about all your Office 365 users? Then run this command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="08f89-135">Ainsi, Get-MsolUser renvoie des données semblables à ceci :</span><span class="sxs-lookup"><span data-stu-id="08f89-135">In turn, Get-MsolUser returns data similar to this:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BelindaN@litwareinc.com     Belinda Newman                  False
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

<span data-ttu-id="08f89-p109">Comme vous le voyez, l'une des valeurs de propriété renvoyées est celle de la propriété **isLicensed**. Si **isLicensed** a la valeur `False`, cela signifie que l'utilisateur n'a pas de licence pour Office 365. En d'autres termes, vous pouvez simplement faire défiler la liste des utilisateurs et sélectionner ceux pour lesquels la propriété **isLicensed** a la valeur `False`.</span><span class="sxs-lookup"><span data-stu-id="08f89-p109">As you can see, one of the property values returned is for the **isLicensed** property. If **isLicensed** is equal to `False` that means that the user doesn't have a license for Office 365. In other words, and if you wanted to, you could simply scroll through your list of users and pick out the ones where the **isLicensed** property is set to `False`.</span></span>
  
<span data-ttu-id="08f89-p110">Dans tous les cas, faire défiler une liste d'utilisateurs en essayant de repérer ceux sans licence fonctionne tant que vous avez un nombre relativement restreint d'utilisateurs. Cependant, si la liste est longue, il sera, au mieux, extrêmement pénible de la faire défiler jusqu'au bout. (Et, selon la façon dont Windows PowerShell a été configuré, tout bonnement impossible. Ceci est dû au fait qu'il existe une limite quant au nombre de lignes de sortie qui peuvent être affichées sur la console Windows PowerShell à un moment donné.)</span><span class="sxs-lookup"><span data-stu-id="08f89-p110">At any rate, scrolling through a list of users trying to pick out the unlicensed users works as long as you have a relatively small number of users. If you have a large number of users, however, scrolling through that list will be, at best, extremely tedious. (And, depending on how Windows PowerShell has been configured, perhaps downright impossible. That's because there's a limit to the number of lines of output that can be displayed in the Windows PowerShell console at any one time.)</span></span>
  
<span data-ttu-id="08f89-143">Ainsi, il est de loin préférable de dresser la liste des utilisateurs sans licence en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="08f89-143">With that in mind, a much better way to list your unlicensed users is to run this command instead:</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="08f89-p111">Cette commande renvoie uniquement les utilisateurs qui n'ont pas de licence pour Office 365. En d'autres termes :</span><span class="sxs-lookup"><span data-stu-id="08f89-p111">That command returns only those users who don't have a license for Office 365. In other words:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="08f89-p112">Comme vous le voyez, nous avons un utilisateur sans licence. Que faire si nous voulions obtenir uniquement la liste des utilisateurs  *avec licence*  ? C'est légèrement plus compliqué, mais à peine :</span><span class="sxs-lookup"><span data-stu-id="08f89-p112">As you can see we have one unlicensed user. And what is we only wanted a list of the  *licensed*  users? That's a tiny bit more complicated, but only the tiniest bit:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true}
```

<span data-ttu-id="08f89-149">Cette commande, qui recherche tous les comptes d'utilisateurs où la propriété **isLicensed** a la valeur `True`, renvoie des informations semblables à ceci :</span><span class="sxs-lookup"><span data-stu-id="08f89-149">That command, which looks for all the user accounts where the **isLicensed** property is equal to `True`, returns information similar to this:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

<span data-ttu-id="08f89-p113">Comme vous le voyez, les informations ne sont pas renvoyées pour Belinda Newman. Pourquoi ? Vous avez la solution : parce que la propriété **isLicensed** pour le compte de Belinda n'est pas définie sur `True`.</span><span class="sxs-lookup"><span data-stu-id="08f89-p113">As you can see, information is not returned for Belinda Newman. Why not? You got it: because the **isLicensed** property for Belinda's account is not set to `True`.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="08f89-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08f89-153">See also</span></span>
<span data-ttu-id="08f89-154"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="08f89-154"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="08f89-155">Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="08f89-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="08f89-156">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="08f89-156">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="08f89-157">Where-Object</span><span class="sxs-lookup"><span data-stu-id="08f89-157">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

