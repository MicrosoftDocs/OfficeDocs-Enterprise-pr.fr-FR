---
title: Afficher des comptes d’utilisateur avec Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Résumé : Affichez, répertoriez ou affichez vos comptes d’utilisateur de différentes manières avec Office 365 PowerShell.'
ms.openlocfilehash: 0711bf945b863cb89d45a377f61a139b298ca6d7
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748402"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="10ee3-103">Afficher des comptes d’utilisateur avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="10ee3-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="10ee3-104">Bien que vous puissiez utiliser le centre d’administration Microsoft 365 pour afficher les comptes de votre client 365 Office, vous pouvez également utiliser Office 365 PowerShell et effectuer certaines opérations que le centre d’administration ne peut pas faire.</span><span class="sxs-lookup"><span data-stu-id="10ee3-104">Although you can use the Microsoft 365 admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="10ee3-105">Utilisez le module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="10ee3-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="10ee3-106">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="10ee3-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="10ee3-107">Afficher tous les comptes</span><span class="sxs-lookup"><span data-stu-id="10ee3-107">View all accounts</span></span>

<span data-ttu-id="10ee3-108">Pour afficher la liste complète des comptes d’utilisateurs, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="10ee3-108">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="10ee3-109">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="10ee3-109">You should see information similar to this:</span></span>
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="10ee3-110">Afficher un compte spécifique</span><span class="sxs-lookup"><span data-stu-id="10ee3-110">View a specific account</span></span>

<span data-ttu-id="10ee3-111">Pour afficher un compte d’utilisateur spécifique, renseignez le nom du compte d’utilisateur, également appelé nom d’utilisateur principal (UPN), supprimez les caractères « < » et « > », puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="10ee3-111">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="10ee3-112">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="10ee3-112">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="10ee3-113">Afficher des valeurs de propriétés supplémentaires pour un compte spécifique</span><span class="sxs-lookup"><span data-stu-id="10ee3-113">View additional property values for a specific account</span></span>

<span data-ttu-id="10ee3-114">Par défaut, la cmdlet **Get-AzureADUser** affiche uniquement les propriétés ObjectId, DisplayName et userPrincipalName des comptes.</span><span class="sxs-lookup"><span data-stu-id="10ee3-114">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="10ee3-115">Pour être plus sélectif sur la liste des propriétés à afficher, vous pouvez utiliser la cmdlet **Select-Object** en combinaison avec la cmdlet **Get-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="10ee3-115">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="10ee3-116">Pour combiner les deux cmdlets, nous utilisons le caractère « pipe » « | », qui indique à Azure Active Directory PowerShell pour Graph de prendre les résultats d’une commande et de l’envoyer à la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="10ee3-116">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="10ee3-117">Voici un exemple de commande qui affiche les DisplayName, Department et UsageLocation pour chaque compte d’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="10ee3-117">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="10ee3-118">Cette commande demande à PowerShell Office 365 d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="10ee3-118">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="10ee3-119">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-119">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="10ee3-120">Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-120">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="10ee3-121">Pour afficher toutes les propriétés des comptes d’utilisateur, utilisez la cmdlet **Select-Object** et le caractère générique (\*) pour les afficher tous pour un compte d’utilisateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="10ee3-121">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="10ee3-122">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="10ee3-122">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="10ee3-123">Autre exemple : vous pouvez vérifier l’état activé d’un compte d’utilisateur spécifique à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="10ee3-123">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="10ee3-124">Afficher certains comptes en fonction d’une propriété commune</span><span class="sxs-lookup"><span data-stu-id="10ee3-124">View some accounts based on a common property</span></span>

<span data-ttu-id="10ee3-125">Pour être plus sélectif à propos de la liste des comptes à afficher, vous pouvez utiliser la cmdlet **Where-Object** en combinaison avec la cmdlet **Get-AzureADUser**.</span><span class="sxs-lookup"><span data-stu-id="10ee3-125">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="10ee3-126">Pour combiner les deux cmdlets, nous utilisons le caractère « pipe » « | », qui indique à Azure Active Directory PowerShell pour Graph de prendre les résultats d’une commande et de l’envoyer à la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="10ee3-126">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="10ee3-127">Voici un exemple de commande qui affiche uniquement les comptes utilisateur dont l’emplacement d’utilisation n’est pas spécifié :</span><span class="sxs-lookup"><span data-stu-id="10ee3-127">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="10ee3-128">Cette commande demande à Azure Active Directory PowerShell pour Graph d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="10ee3-128">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="10ee3-129">Obtenir toutes les informations sur les comptes d’utilisateur ( **Get-AzureADUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-129">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="10ee3-130">Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié ( **Where-Object\_{$. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-130">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="10ee3-131">À l’intérieur des accolades, la commande indique à Office 365 PowerShell de trouver uniquement le jeu de comptes dans lequel la propriété de compte d’utilisateur UsageLocation ( \*\* $ \_. UsageLocation\*\* ) n’est pas spécifié ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-131">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="10ee3-132">La propriété **UsageLocation** n’est que l’une des nombreuses propriétés associées à un compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="10ee3-132">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="10ee3-133">Pour afficher toutes les propriétés des comptes d’utilisateur, utilisez la cmdlet **Select-Object** et le caractère générique (\*) pour les afficher tous pour un compte d’utilisateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="10ee3-133">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="10ee3-134">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="10ee3-134">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="10ee3-p106">Par exemple, dans cette liste, **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour obtenir la liste des comptes d’utilisateur pour les utilisateurs qui habitent à Londres :</span><span class="sxs-lookup"><span data-stu-id="10ee3-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="10ee3-137">La syntaxe de l’applet de commande **Where-Object** présentée dans ces exemples est **Where-Object\_{$.**</span><span class="sxs-lookup"><span data-stu-id="10ee3-137">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="10ee3-138">[nom de la propriété du compte d’utilisateur] [opérateur de comparaison] valeur **}**. > [opérateur de comparaison] est **-EQ** pour Equals, **-** ne pour « différent de », **-lt** pour inférieur à, **-gt** pour supérieur à, et autres.</span><span class="sxs-lookup"><span data-stu-id="10ee3-138">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="10ee3-139">[valeur] est généralement une chaîne (une séquence de lettres, de chiffres et d’autres caractères), une valeur numérique ou **$null** pour les> non spécifiés pour plus d’informations, voir [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) .</span><span class="sxs-lookup"><span data-stu-id="10ee3-139">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="10ee3-140">Utilisez le Module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10ee3-140">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="10ee3-141">Tout d’abord, [connectez-vous à votre client Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="10ee3-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="10ee3-142">Afficher tous les comptes</span><span class="sxs-lookup"><span data-stu-id="10ee3-142">View all accounts</span></span>

<span data-ttu-id="10ee3-143">Pour afficher la liste complète des comptes d’utilisateurs, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="10ee3-143">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

<span data-ttu-id="10ee3-144">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="10ee3-144">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="10ee3-145">La cmdlet **Get-MsolUser** dispose également d’un jeu de paramètres pour filtrer l’ensemble de comptes utilisateur affichés.</span><span class="sxs-lookup"><span data-stu-id="10ee3-145">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="10ee3-146">Par exemple, pour la liste des utilisateurs sans licence (utilisateurs qui ont été ajoutés à Office 365 mais qui n’ont pas encore été concédés sous licence pour utiliser l’un des services), exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="10ee3-146">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="10ee3-147">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="10ee3-147">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="10ee3-148">Pour plus d’informations sur les paramètres supplémentaires permettant de filtrer l’affichage de l’ensemble des comptes d’utilisateur affichés, consultez la rubrique [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="10ee3-148">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="10ee3-149">Afficher un compte spécifique</span><span class="sxs-lookup"><span data-stu-id="10ee3-149">View a specific account</span></span>

<span data-ttu-id="10ee3-150">Pour afficher un compte d’utilisateur spécifique, renseignez le nom de connexion du compte d’utilisateur, également appelé nom d’utilisateur principal (UPN), supprimez les caractères « < » et « > », puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="10ee3-150">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="10ee3-151">Afficher certains comptes en fonction d’une propriété commune</span><span class="sxs-lookup"><span data-stu-id="10ee3-151">View some accounts based on a common property</span></span>

<span data-ttu-id="10ee3-152">Pour être plus sélectif à propos de la liste des comptes à afficher, vous pouvez utiliser la cmdlet **Where-Object** en combinaison avec la cmdlet **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="10ee3-152">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="10ee3-153">Pour combiner les deux cmdlets, nous utilisons le caractère « pipe » « | », qui indique à Office 365 PowerShell de prendre les résultats d’une commande et de l’envoyer à la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="10ee3-153">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="10ee3-154">Voici un exemple de commande qui affiche uniquement les comptes utilisateur dont l’emplacement d’utilisation n’est pas spécifié :</span><span class="sxs-lookup"><span data-stu-id="10ee3-154">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="10ee3-155">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="10ee3-155">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="10ee3-156">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-156">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="10ee3-157">Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié ( **Where-Object\_{$. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-157">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="10ee3-158">À l’intérieur des accolades, la commande indique à Office 365 PowerShell de trouver uniquement le jeu de comptes dans lequel la propriété de compte d’utilisateur UsageLocation ( \*\* $ \_. UsageLocation\*\* ) n’est pas spécifié ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-158">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="10ee3-159">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="10ee3-159">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="10ee3-160">La propriété **UsageLocation** n’est que l’une des nombreuses propriétés associées à un compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="10ee3-160">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="10ee3-161">Pour afficher toutes les propriétés des comptes d’utilisateur, utilisez la cmdlet **Select-Object** et le caractère générique (\*) pour les afficher tous pour un compte d’utilisateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="10ee3-161">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="10ee3-162">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="10ee3-162">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="10ee3-p112">Par exemple, dans cette liste, **Ville** est le nom d’une propriété de compte d’utilisateur. Cela signifie que vous pouvez utiliser la commande suivante pour obtenir la liste des comptes d’utilisateur pour les utilisateurs qui habitent à Londres :</span><span class="sxs-lookup"><span data-stu-id="10ee3-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="10ee3-165">La syntaxe de l’applet de commande **Where-Object** présentée dans ces exemples est **Where-Object\_{$.**</span><span class="sxs-lookup"><span data-stu-id="10ee3-165">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="10ee3-166">[nom de la propriété du compte d’utilisateur] [opérateur de comparaison] valeur **}**.</span><span class="sxs-lookup"><span data-stu-id="10ee3-166">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="10ee3-167">[opérateur de comparaison] est **-EQ** pour Equals, **-** ne pour « différent de », **-lt** pour inférieur à, **-gt** pour supérieur à, et autres.</span><span class="sxs-lookup"><span data-stu-id="10ee3-167">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="10ee3-168">[valeur] est généralement une chaîne (une séquence de lettres, de chiffres et d’autres caractères), une valeur numérique ou **$null** pour non spécifié.</span><span class="sxs-lookup"><span data-stu-id="10ee3-168">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="10ee3-169">Pour plus d’informations, voir [Where-Object](https://technet.microsoft.com/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="10ee3-169">See [Where-Object](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="10ee3-170">Vous pouvez vérifier l’État bloqué d’un compte d’utilisateur à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="10ee3-170">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="10ee3-171">Afficher les valeurs des propriétés supplémentaires des comptes</span><span class="sxs-lookup"><span data-stu-id="10ee3-171">View additional property values for accounts</span></span>

<span data-ttu-id="10ee3-172">La cmdlet **Get-MsolUser** affiche par défaut trois propriétés des comptes d’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="10ee3-172">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="10ee3-173">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="10ee3-173">UserPrincipalName</span></span>
    
- <span data-ttu-id="10ee3-174">DisplayName</span><span class="sxs-lookup"><span data-stu-id="10ee3-174">DisplayName</span></span>
    
- <span data-ttu-id="10ee3-175">isLicensed</span><span class="sxs-lookup"><span data-stu-id="10ee3-175">isLicensed</span></span>
    
<span data-ttu-id="10ee3-176">Si vous avez besoin de propriétés supplémentaires, telles que le service pour lequel l’utilisateur travaille pour et le pays/la région où l’utilisateur utilise les services Office 365, vous pouvez exécuter **Get-MsolUser** en combinaison avec la cmdlet **Select-Object** pour spécifier la liste des propriétés du compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="10ee3-176">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="10ee3-177">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="10ee3-177">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="10ee3-178">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="10ee3-178">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="10ee3-179">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-179">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="10ee3-180">Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-180">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="10ee3-181">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="10ee3-181">You should see information similar to this:</span></span>
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="10ee3-182">La cmdlet **Select-Object** vous permet de sélectionner et de sélectionner les propriétés que vous souhaitez qu’une commande affiche.</span><span class="sxs-lookup"><span data-stu-id="10ee3-182">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="10ee3-183">Pour afficher toutes les propriétés des comptes d’utilisateur, utilisez le caractère générique (\*) pour les afficher tous pour un compte d’utilisateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="10ee3-183">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="10ee3-184">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="10ee3-184">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="10ee3-p116">Pour être plus sélectif dans la liste des comptes à afficher, vous pouvez également utiliser la cmdlet **Where-Object**. Voici un exemple de commande qui affiche uniquement les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié :</span><span class="sxs-lookup"><span data-stu-id="10ee3-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="10ee3-187">Cette commande demande à Office 365 PowerShell d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="10ee3-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="10ee3-188">Obtenir toutes les informations sur les comptes utilisateur ( **Get-MsolUser** ) et les envoyer à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-188">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="10ee3-189">Recherchez tous les comptes d’utilisateur dont l’emplacement d’utilisation n’est pas spécifié ( **Where-Object\_{$. UsageLocation-EQ $Null}** ) et envoyer les informations obtenues à la commande suivante ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-189">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="10ee3-190">À l’intérieur des accolades, la commande indique à Office 365 PowerShell de trouver uniquement le jeu de comptes dans lequel la propriété de compte d’utilisateur UsageLocation ( \*\* $ \_. UsageLocation\*\* ) n’est pas spécifié ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-190">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="10ee3-191">Afficher uniquement le nom du compte d’utilisateur, le service et l’emplacement d’utilisation ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="10ee3-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="10ee3-192">Les informations affichées devraient être semblables à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="10ee3-192">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="10ee3-193">Si vous utilisez la synchronisation d’annuaires pour créer et gérer vos utilisateurs Office 365, vous pouvez afficher le compte local à partir duquel un utilisateur d’Office 365 a été projeté.</span><span class="sxs-lookup"><span data-stu-id="10ee3-193">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="10ee3-194">Les éléments suivants supposent qu’Azure AD Connect a été configuré pour utiliser l’ancre source par défaut d’ObjectGUID (pour plus d’informations sur la configuration d’une ancre source, reportez-vous à la rubrique [Azure ad Connect : Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) et suppose que le module Active Directory pour PowerShell a été installé (voir [outils RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)) :</span><span class="sxs-lookup"><span data-stu-id="10ee3-194">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a><span data-ttu-id="10ee3-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10ee3-195">See also</span></span>

[<span data-ttu-id="10ee3-196">Gérer les comptes d'utilisateurs et les licences avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="10ee3-196">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="10ee3-197">Gérer Office 365 avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="10ee3-197">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="10ee3-198">Mise en route d'Office 365 Powershell</span><span class="sxs-lookup"><span data-stu-id="10ee3-198">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

