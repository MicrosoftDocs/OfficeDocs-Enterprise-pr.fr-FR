---
title: "Afficher des comptes d’utilisateur avec Office 365 PowerShell"
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
- LIL_Placement
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "Résumé : Permet d’afficher, de liste ou afficher vos comptes d’utilisateurs de différentes manières avec Office 365 PowerShell."
ms.openlocfilehash: b27f9045d26d4dabd3ada70766491f722d822a91
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="4a505-103">Afficher des comptes d’utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a505-103">View user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="4a505-104">**Résumé :** Permet d’afficher, de liste ou afficher vos comptes d’utilisateurs de différentes manières avec Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a505-104">**Summary:** View, list, or display your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="4a505-105">Vous pouvez utiliser le centre d’administration d’Office 365 pour afficher les comptes pour vos clients d’Office 365, vous pouvez également utiliser Office 365 PowerShell et faire certaines choses que le centre d’administration d’Office 365 ne peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="4a505-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="4a505-106">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="4a505-106">Before you begin</span></span>

<span data-ttu-id="4a505-p101">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="4a505-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information"></a><span data-ttu-id="4a505-109">Affichage des informations de compte utilisateur Office 365</span><span class="sxs-lookup"><span data-stu-id="4a505-109">Display Office 365 user account information</span></span>

<span data-ttu-id="4a505-110">Pour afficher la liste complète des comptes d’utilisateur, exécutez la commande suivante dans l’invite de commande d’Office 365 PowerShell ou l’environnement de Script intégré (ISE) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a505-110">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="4a505-111">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4a505-111">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="4a505-p102">L’applet de commande **Get-MsolUser** a également un jeu de paramètres pour filtrer le jeu de comptes d’utilisateurs s’affiche. Par exemple, pour la liste des utilisateurs sans licence (les utilisateurs qui ont été ajoutés à Office 365 mais qui n’ont pas encore été concédé sous licence pour utiliser les services), vous devez exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="4a505-p102">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="4a505-114">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4a505-114">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="4a505-115">Pour plus d’informations sur les paramètres supplémentaires pour filtrer l’affichage de l’ensemble des comptes d’utilisateur s’affiche, consultez [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span><span class="sxs-lookup"><span data-stu-id="4a505-115">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span></span>
  
<span data-ttu-id="4a505-p103">Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser l’applet de commande **Where-Object** en combinaison avec l’applet de commande **Get-MsolUser** . Pour combiner les deux applets de commande, nous utilisons le caractère « pipe » « | », qui indique à Office 365 PowerShell utilisent les résultats d’une commande et l’envoyer à la commande suivante. Voici un exemple de commande qui n'affiche que les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifiée :</span><span class="sxs-lookup"><span data-stu-id="4a505-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="4a505-119">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a505-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="4a505-120">Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-MsolUser** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-120">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="4a505-p104">Rechercher tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifiée ( **Where-Object {$\_. UsageLocation - eq $Null}** ). À l’intérieur d’accolades, la commande indique à Office 365 PowerShell uniquement rechercher l’ensemble des comptes, dans laquelle l’utilisateur UsageLocation compte de propriété ( ** $ \_. UsageLocation** ) n’est pas spécifié ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="4a505-123">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4a505-123">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="4a505-p105">La propriété **UsageLocation** n'est qu’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez l’applet de commande **Select-Object** et le caractère générique (*) pour afficher tous les pour un compte d’utilisateur spécifique. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="4a505-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="4a505-p106">Par exemple, à partir de cette liste, **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour répertorier tous les comptes d’utilisateurs pour les utilisateurs vivant à Londres :</span><span class="sxs-lookup"><span data-stu-id="4a505-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="4a505-p107">La syntaxe de l’applet de commande **Where-Object** présenté dans ces exemples est **Where-Object {$\_.** [nom de propriété de compte utilisateur] [opérateur de comparaison] [valeur] **}**. > [comparaison] est **-eq** pour equals, **ne -** pour non égal à, **lt -** pour moins de **-gt** de plus d’et d’autres > [valeur] est généralement une chaîne (une séquence de lettres, de chiffres et d’autres caractères), un valeur numérique, ou **$Null** pour non spécifié > Pour plus d’informations, reportez-vous à la section [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="4a505-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="4a505-131">Vous pouvez vérifier le statut de blocage d’un compte d’utilisateur avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4a505-131">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="4a505-132">Sélection des propriétés de compte utilisateur à afficher</span><span class="sxs-lookup"><span data-stu-id="4a505-132">Select the user account properties to display</span></span>

<span data-ttu-id="4a505-133">L’applet de commande [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) par défaut affiche les trois propriétés de comptes d’utilisateurs :</span><span class="sxs-lookup"><span data-stu-id="4a505-133">The [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="4a505-134">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="4a505-134">UserPrincipalName</span></span>
    
- <span data-ttu-id="4a505-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4a505-135">DisplayName</span></span>
    
- <span data-ttu-id="4a505-136">isLicensed</span><span class="sxs-lookup"><span data-stu-id="4a505-136">isLicensed</span></span>
    
<span data-ttu-id="4a505-p108">Si vous avez besoin des propriétés supplémentaires, telles que le département travaille pour et le pays/la région où l’utilisateur utilise les services d’Office 365, vous pouvez exécuter **Get-MsolUser** en combinaison avec l’applet de commande **Select-Object** pour spécifier la liste des comptes d’utilisateur Propriétés. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="4a505-p108">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="4a505-139">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a505-139">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="4a505-140">Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-MsolUser** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-140">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="4a505-141">Afficher uniquement l’utilisateur compte nom, le service et l’utilisation de l’emplacement ( **Select-Object DisplayName, département, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-141">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="4a505-142">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4a505-142">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

<span data-ttu-id="4a505-p109">L’applet de commande **Select-Object** vous permet de choisir les propriétés à une commande à afficher. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez le caractère générique (*) pour afficher tous les pour un compte d’utilisateur spécifique. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="4a505-p109">The **Select-Object** cmdlet allows you to pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="4a505-p110">Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez également utiliser l’applet de commande **Where-Object** . Voici un exemple de commande qui n'affiche que les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifiée :</span><span class="sxs-lookup"><span data-stu-id="4a505-p110">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="4a505-148">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a505-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="4a505-149">Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-MsolUser** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-149">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="4a505-p111">Rechercher tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifiée ( **Where-Object {$\_. UsageLocation - eq $Null}** ) et envoyer les informations obtenues à la commande suivante ( **|** ). À l’intérieur d’accolades, la commande est demandant uniquement rechercher l’ensemble des comptes, dans laquelle l’utilisateur UsageLocation de propriété compte Office 365 PowerShell ( ** $ \_. UsageLocation** ) n’est pas spécifié ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="4a505-152">Afficher uniquement l’utilisateur compte nom, le service et l’utilisation de l’emplacement ( **Select-Object DisplayName, département, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-152">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="4a505-153">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4a505-153">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a><span data-ttu-id="4a505-154">Utilisation du module Azure Active Directory V2 PowerShell pour afficher des comptes d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="4a505-154">Use the Azure Active Directory V2 PowerShell module to display user accounts</span></span>

<span data-ttu-id="4a505-p112">Pour afficher les propriétés des comptes d’utilisateurs avec le module PowerShell de Azure Active Directory V2, vous utilisez l’applet de commande [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) . Mais tout d’abord, vous devez vous connecter à votre abonnement. Pour les instructions, voir[se connecter avec le module PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="4a505-p112">To display properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet. But first, you must connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="display-office-365-user-account-information"></a><span data-ttu-id="4a505-158">Affichage des informations de compte utilisateur Office 365</span><span class="sxs-lookup"><span data-stu-id="4a505-158">Display Office 365 user account information</span></span>

<span data-ttu-id="4a505-159">Pour afficher la liste complète des comptes d’utilisateur, exécutez la commande suivante dans l’invite de commande d’Office 365 PowerShell ou l’environnement de Script intégré (ISE) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a505-159">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="4a505-160">L’applet de commande **Get-AzureADUser** par défaut affiche les trois propriétés de comptes d’utilisateurs :</span><span class="sxs-lookup"><span data-stu-id="4a505-160">The **Get-AzureADUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="4a505-161">ObjectID</span><span class="sxs-lookup"><span data-stu-id="4a505-161">ObjectID</span></span>
    
- <span data-ttu-id="4a505-162">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4a505-162">DisplayName</span></span>
    
- <span data-ttu-id="4a505-163">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="4a505-163">UserPrincipalName</span></span>
    
<span data-ttu-id="4a505-p113">Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez utiliser l’applet de commande **Where-Object** en combinaison avec l’applet de commande **Get-AzureADUser** . Pour combiner les deux applets de commande, nous utilisons le caractère « pipe » « | », qui indique à Office 365 PowerShell utilisent les résultats d’une commande et l’envoyer à la commande suivante. Voici un exemple de commande qui n'affiche que les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifiée :</span><span class="sxs-lookup"><span data-stu-id="4a505-p113">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="4a505-167">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a505-167">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="4a505-168">Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-AzureADUser** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-168">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="4a505-p114">Rechercher tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifiée ( **Where-Object {$\_. UsageLocation - eq $Null}** ). À l’intérieur d’accolades, la commande indique à Office 365 PowerShell uniquement rechercher l’ensemble des comptes, dans laquelle l’utilisateur UsageLocation compte de propriété ( ** $ \_. UsageLocation** ) n’est pas spécifié ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-p114">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="4a505-p115">La propriété **UsageLocation** n'est qu’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez l’applet de commande **Select-Object** et le caractère générique (*) pour afficher tous les pour un compte d’utilisateur spécifique, une page à la fois ( **plusieurs** ). Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="4a505-p115">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (*) to display them all for a specific user account, one page at a time ( **More** ). Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

<span data-ttu-id="4a505-p116">Par exemple, la **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour répertorier tous les comptes d’utilisateurs pour les utilisateurs vivant à Londres :</span><span class="sxs-lookup"><span data-stu-id="4a505-p116">For example, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="4a505-p117">La syntaxe de l’applet de commande **Where-Object** présenté dans ces exemples est **Where-Object {$\_.** [nom de propriété de compte utilisateur] [opérateur de comparaison] [valeur] **}**. > [comparaison] est **-eq** pour equals, **ne -** pour non égal à, **lt -** pour moins de **-gt** de plus d’et d’autres > [valeur] est généralement une chaîne (une séquence de lettres, de chiffres et d’autres caractères), un valeur numérique, ou **$Null** pour non spécifié > Pour plus d’informations, reportez-vous à la section[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="4a505-p117">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
### <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="4a505-178">Sélection des propriétés de compte utilisateur à afficher</span><span class="sxs-lookup"><span data-stu-id="4a505-178">Select the user account properties to display</span></span>

<span data-ttu-id="4a505-p118">L’applet de commande **Get-AzureADUser** par défaut affiche les propriétés des comptes d’utilisateurs de UserPrincipalName, DisplayName et ObjectID. Si vous avez besoin des propriétés supplémentaires, telles que le département travaille pour et le pays/la région où l’utilisateur utilise les services d’Office 365, vous pouvez exécuter **Get-AzureADUser** en combinaison avec l’applet de commande **Select-Object** pour spécifier la liste des utilisateurs Propriétés du compte. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="4a505-p118">The **Get-AzureADUser** cmdlet by default displays the ObjectID, DisplayName, and UserPrincipalName properties of user accounts. If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-AzureADUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="4a505-182">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a505-182">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="4a505-183">Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-AzureADUser** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-183">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="4a505-184">Afficher uniquement l’utilisateur compte nom, le service et l’utilisation de l’emplacement ( **Select-Object DisplayName, département, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-184">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="4a505-p119">Pour être plus sélectif sur la liste des comptes à afficher, vous pouvez également utiliser l’applet de commande **Where-Object** . Voici un exemple de commande qui n'affiche que les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifiée :</span><span class="sxs-lookup"><span data-stu-id="4a505-p119">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="4a505-187">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a505-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="4a505-188">Obtenir toutes les informations sur les comptes d’utilisateurs ( **Get-AzureADUser** ) et l’envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-188">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="4a505-p120">Rechercher tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifiée ( **Where-Object {$\_. UsageLocation - eq $Null}** ) et envoyer les informations obtenues à la commande suivante ( **|** ). À l’intérieur d’accolades, la commande est demandant uniquement rechercher l’ensemble des comptes, dans laquelle l’utilisateur UsageLocation de propriété compte Office 365 PowerShell ( ** $ \_. UsageLocation** ) n’est pas spécifié ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-p120">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="4a505-191">Afficher uniquement l’utilisateur compte nom, le service et l’utilisation de l’emplacement ( **Select-Object DisplayName, département, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="4a505-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
## <a name="new-to-office-365"></a><span data-ttu-id="4a505-192">Vous débutez avec Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="4a505-192">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="4a505-p121">![L’icône court pour l’apprentissage de LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **nouveau vers Office 365 ?**         Découvrez la vidéo gratuits pour les [professionnels de l’informatique et les administrateurs d’Office 365](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), proposée par formation de LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="4a505-p121">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="4a505-195">See also</span><span class="sxs-lookup"><span data-stu-id="4a505-195">See also</span></span>

#### 

[<span data-ttu-id="4a505-196">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a505-196">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="4a505-197">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a505-197">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4a505-198">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="4a505-198">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

