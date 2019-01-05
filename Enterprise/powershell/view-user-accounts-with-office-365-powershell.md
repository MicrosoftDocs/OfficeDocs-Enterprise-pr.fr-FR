---
title: Afficher des comptes d’utilisateur avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Résumé : Permet d’afficher, de liste ou d’afficher vos comptes d’utilisateurs de différentes manières avec Office 365 PowerShell.'
ms.openlocfilehash: e95353602b96babe5c80f7d57462370636dd26fa
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730319"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="374c7-103">Afficher des comptes d’utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="374c7-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="374c7-104">**Résumé :** Afficher vos comptes d’utilisateurs de différentes manières avec Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="374c7-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="374c7-105">Bien que vous pouvez utiliser le centre d’administration d’Office 365 pour afficher les comptes de votre client Office 365, vous pouvez également utiliser Office 365 PowerShell et faire des choses que le centre d’administration d’Office 365 ne peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="374c7-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="374c7-106">Utilisez Azure Active Directory PowerShell pour le module de graphique</span><span class="sxs-lookup"><span data-stu-id="374c7-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="374c7-107">Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="374c7-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="374c7-108">Afficher tous les comptes</span><span class="sxs-lookup"><span data-stu-id="374c7-108">View all accounts</span></span>

<span data-ttu-id="374c7-109">Pour afficher la liste complète des comptes d’utilisateur, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="374c7-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="374c7-110">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="374c7-110">You should see information similar to this:</span></span>
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="374c7-111">Afficher un compte spécifique</span><span class="sxs-lookup"><span data-stu-id="374c7-111">View a specific account</span></span>

<span data-ttu-id="374c7-112">Pour afficher un compte d’utilisateur spécifique, renseignez le nom de compte de connexion du compte d’utilisateur, également connu sous le nom d’utilisateur principal (UPN), supprimez le « < » et « > » caractères et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="374c7-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="374c7-113">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="374c7-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="374c7-114">Afficher les valeurs de propriété supplémentaires pour un compte spécifique</span><span class="sxs-lookup"><span data-stu-id="374c7-114">View additional property values for a specific account</span></span>

<span data-ttu-id="374c7-115">Par défaut, l’applet de commande **Get-AzureADUser** affiche uniquement les propriétés UserPrincipalName, DisplayName et ObjectID de comptes.</span><span class="sxs-lookup"><span data-stu-id="374c7-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="374c7-p101">Pour être plus sélective sur la liste des propriétés à afficher, vous pouvez utiliser la cmdlet **Select-Object** en combinaison avec l’applet de commande **Get-AzureADUser** . Pour combiner les deux applets de commande, nous utilisons le caractère « canal » « | », qui indique à Windows Azure Active Directory PowerShell graphique prendre les résultats d’une commande et l’envoyer à la commande suivante. Voici un exemple de commande qui affiche le DisplayName, le service et UsageLocation pour chaque compte d’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="374c7-p101">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="374c7-119">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="374c7-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="374c7-120">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="374c7-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="374c7-121">Afficher uniquement l’utilisateur nom, le service et utilisation emplacement du compte ( **Select-Object DisplayName, département, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="374c7-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="374c7-p102">Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez la cmdlet **Select-Object** et le caractère générique (\*) pour toutes les afficher pour un compte d’utilisateur spécifique. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="374c7-p102">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="374c7-124">Autre exemple, vous pouvez vérifier l’état activé d’un compte d’utilisateur spécifique avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="374c7-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="374c7-125">Afficher des comptes basées sur une propriété courantes</span><span class="sxs-lookup"><span data-stu-id="374c7-125">View some accounts based on a common property</span></span>

<span data-ttu-id="374c7-p103">Pour être plus sélective sur la liste des comptes à afficher, vous pouvez utiliser la cmdlet **Where-Object** en combinaison avec l’applet de commande **Get-AzureADUser** . Pour combiner les deux applets de commande, nous utilisons le caractère « canal » « | », qui indique à Windows Azure Active Directory PowerShell graphique prendre les résultats d’une commande et l’envoyer à la commande suivante. Voici un exemple de commande qui affiche uniquement les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifié :</span><span class="sxs-lookup"><span data-stu-id="374c7-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="374c7-129">Cette commande indique à Windows Azure Active Directory PowerShell graphique pour :</span><span class="sxs-lookup"><span data-stu-id="374c7-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="374c7-130">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="374c7-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="374c7-p104">Trouver tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifié ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Les accolades, la commande indique à Office 365 PowerShell pour trouver uniquement l’ensemble des comptes dans laquelle l’utilisateur UsageLocation compte de la propriété ( \*\* $ \_. UsageLocation\*\* ) n’est pas spécifié ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="374c7-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="374c7-p105">La propriété **UsageLocation** n’existe qu’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez la cmdlet **Select-Object** et le caractère générique (\*) pour toutes les afficher pour un compte d’utilisateur spécifique. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="374c7-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="374c7-p106">Par exemple, dans cette liste, **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour obtenir la liste des comptes d’utilisateur pour les utilisateurs qui habitent à Londres :</span><span class="sxs-lookup"><span data-stu-id="374c7-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="374c7-p107">La syntaxe de la cmdlet **Where-Object** indiquée dans ces exemples est **Where-Object {$\_.** [nom de la propriété compte utilisateur] [opérateur de comparaison] [valeur] **}**. > [opérateur de comparaison] est **-eq** pour est égal à, **-ne** pour pas égal à **-lt** pour inférieure à **-gt** pour supérieure et d’autres personnes.  [valeur] est généralement une chaîne (une séquence de lettres, chiffres et autres caractères), une valeur numérique ou **$Null** pour n’est pas spécifié > Pour plus d’informations, consultez [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) .</span><span class="sxs-lookup"><span data-stu-id="374c7-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="374c7-141">Utiliser le Module d’Active Directory de Microsoft Azure pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="374c7-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="374c7-142">Tout d’abord, [se connecter à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="374c7-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="374c7-143">Afficher tous les comptes</span><span class="sxs-lookup"><span data-stu-id="374c7-143">View all accounts</span></span>

<span data-ttu-id="374c7-144">Pour afficher la liste complète des comptes d’utilisateur, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="374c7-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="374c7-145">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="374c7-145">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="374c7-p108">L’applet de commande **Get-MsolUser** a également un jeu de paramètres pour filtrer l’ensemble des comptes d’utilisateur affiché. Par exemple, la liste des utilisateurs sans licence (les utilisateurs qui ont été ajoutés à Office 365, mais n’ont pas encore été une licence pour utiliser un des services), exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="374c7-p108">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="374c7-148">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="374c7-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="374c7-149">Pour plus d’informations sur les paramètres supplémentaires pour filtrer l’affichage de l’ensemble des comptes d’utilisateurs affichés, voir [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="374c7-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="374c7-150">Afficher un compte spécifique</span><span class="sxs-lookup"><span data-stu-id="374c7-150">View a specific account</span></span>

<span data-ttu-id="374c7-151">Pour afficher un compte d’utilisateur spécifique, renseignez le nom de connexion du compte d’utilisateur du compte d’utilisateur, également connu sous le nom d’utilisateur principal (UPN), supprimez le « < » et « > » caractères et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="374c7-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="374c7-152">Afficher des comptes basées sur une propriété courantes</span><span class="sxs-lookup"><span data-stu-id="374c7-152">View some accounts based on a common property</span></span>

<span data-ttu-id="374c7-p109">Pour être plus sélective sur la liste des comptes à afficher, vous pouvez utiliser la cmdlet **Where-Object** en combinaison avec l’applet de commande **Get-MsolUser** . Pour combiner les deux applets de commande, nous utilisons le caractère « canal » « | », qui indique à Office 365 PowerShell pour prendre les résultats d’une commande et l’envoyer à la commande suivante. Voici un exemple de commande qui affiche uniquement les comptes d’utilisateur qui ont un emplacement d’utilisation non spécifié :</span><span class="sxs-lookup"><span data-stu-id="374c7-p109">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="374c7-156">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="374c7-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="374c7-157">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="374c7-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="374c7-p110">Trouver tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifié ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Les accolades, la commande indique à Office 365 PowerShell pour trouver uniquement l’ensemble des comptes dans laquelle l’utilisateur UsageLocation compte de la propriété ( \*\* $ \_. UsageLocation\*\* ) n’est pas spécifié ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="374c7-p110">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="374c7-160">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="374c7-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="374c7-p111">La propriété **UsageLocation** n’existe qu’une des nombreuses propriétés associées à un compte d’utilisateur. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez la cmdlet **Select-Object** et le caractère générique (\*) pour toutes les afficher pour un compte d’utilisateur spécifique. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="374c7-p111">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="374c7-p112">Par exemple, dans cette liste, **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour obtenir la liste des comptes d’utilisateur pour les utilisateurs qui habitent à Londres :</span><span class="sxs-lookup"><span data-stu-id="374c7-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="374c7-p113">La syntaxe de la cmdlet **Where-Object** indiquée dans ces exemples est **Where-Object {$\_.** [nom de la propriété compte utilisateur] [opérateur de comparaison] [valeur] **}**.  [opérateur de comparaison] est **-eq** pour est égal à **-ne** pour différent, **-lt** pour inférieure à **-gt** pour supérieure et d’autres personnes.  [valeur] est généralement une chaîne (une séquence de lettres, chiffres et autres caractères), une valeur numérique ou **$Null** pour n’est pas spécifié. Pour plus d’informations, voir [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="374c7-p113">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified. See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="374c7-171">Vous pouvez vérifier l’état bloqué d’un compte d’utilisateur avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="374c7-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="374c7-172">Afficher les valeurs de propriété supplémentaires pour les comptes</span><span class="sxs-lookup"><span data-stu-id="374c7-172">View additional property values for accounts</span></span>

<span data-ttu-id="374c7-173">L’applet de commande **Get-MsolUser** par défaut affiche trois propriétés des comptes d’utilisateurs :</span><span class="sxs-lookup"><span data-stu-id="374c7-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="374c7-174">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="374c7-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="374c7-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="374c7-175">DisplayName</span></span>
    
- <span data-ttu-id="374c7-176">isLicensed</span><span class="sxs-lookup"><span data-stu-id="374c7-176">isLicensed</span></span>
    
<span data-ttu-id="374c7-p114">Si vous avez besoin des propriétés supplémentaires, telles que le service fonctionne de l’utilisateur pour et la pays/la région où l’utilisateur utilise les services Office 365, vous pouvez exécuter **Get-MsolUser** en combinaison avec la cmdlet **Select-Object** pour spécifier la liste du compte d’utilisateur Propriétés. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="374c7-p114">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="374c7-179">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="374c7-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="374c7-180">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="374c7-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="374c7-181">Afficher uniquement l’utilisateur nom, le service et utilisation emplacement du compte ( **Select-Object DisplayName, département, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="374c7-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="374c7-182">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="374c7-182">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="374c7-p115">La cmdlet **Select-Object** vous permet de choisir les propriétés que vous souhaitez afficher une commande. Pour afficher toutes les propriétés des comptes d’utilisateurs, utilisez le caractère générique (\*) pour afficher tous les pour un compte d’utilisateur spécifique. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="374c7-p115">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="374c7-p116">Pour être plus sélectif dans la liste des comptes à afficher, vous pouvez également utiliser la cmdlet **Where-Object**. Voici un exemple de commande qui affiche uniquement les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié :</span><span class="sxs-lookup"><span data-stu-id="374c7-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="374c7-188">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="374c7-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="374c7-189">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="374c7-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="374c7-p117">Trouver tous les comptes d’utilisateurs qui ont un emplacement d’utilisation non spécifié ( **Where-Object {$\_. UsageLocation - eq $Null}** ) et envoyer les informations obtenues à la commande suivante ( **|** ). Les accolades, la commande est indiquer à Office 365 PowerShell pour trouver uniquement l’ensemble des comptes dans laquelle l’utilisateur UsageLocation compte de la propriété ( \*\* $ \_. UsageLocation\*\* ) n’est pas spécifié ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="374c7-p117">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="374c7-192">Afficher uniquement l’utilisateur nom, le service et utilisation emplacement du compte ( **Select-Object DisplayName, département, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="374c7-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="374c7-193">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="374c7-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="374c7-p118">Si vous utilisez la synchronisation d’annuaires pour créer et gérer vos utilisateurs Office 365, vous pouvez afficher le compte local, un utilisateur Office 365 a été prévu à partir de. La procédure suivante suppose que Azure AD Connect a été configuré pour utiliser l’ancre de source par défaut du GUID d’objet (pour plus d’informations sur la configuration d’un point d’ancrage de la source, voir [Azure AD Connect : concepts de conception](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) et de la part du principe que le module d’Active Directory pour powershell a été installée (voir [Outils RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)) :</span><span class="sxs-lookup"><span data-stu-id="374c7-p118">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from. The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a><span data-ttu-id="374c7-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="374c7-196">See also</span></span>

[<span data-ttu-id="374c7-197">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="374c7-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="374c7-198">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="374c7-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="374c7-199">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="374c7-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

