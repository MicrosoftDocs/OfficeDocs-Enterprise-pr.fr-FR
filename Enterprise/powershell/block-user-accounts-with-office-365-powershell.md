---
title: "Bloquer des comptes d’utilisateurs avec Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "Explique comment utiliser Office 365 PowerShell pour bloquer et débloquer l’accès aux comptes d’Office 365."
ms.openlocfilehash: 34d144c982210ddc9d557b6094f71706f8edbb7f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="5fdb9-103">Bloquer des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fdb9-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="5fdb9-104">**Résumé :**  Explique comment utiliser Office 365 PowerShell pour bloquer et débloquer l’accès aux comptes d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="5fdb9-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="5fdb9-p101">Bloque l’accès à un compte Office 365, vous empêchez quiconque de se connecter et d’accéder aux services et aux données de votre organisation d’Office 365 à l’aide du compte. Lorsque vous bloquez l’accès au compte, l’utilisateur reçoit le message d’erreur suivant lorsqu’ils tentent de se connecter :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. When you block access to the account, the user receives the following error message when they attempt to sign in:</span></span>
  
![Compte Office 365 bloqué.](images/o365_powershell_account_blocked.png)
  
<span data-ttu-id="5fdb9-108">Vous pouvez utiliser Office 365 PowerShell pour bloquer l’accès aux différents et plusieurs comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5fdb9-108">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="5fdb9-109">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="5fdb9-109">Before you begin</span></span>

- <span data-ttu-id="5fdb9-p102">Les procédures décrites dans cette rubrique exigent une connexion à Office 365 PowerShell. Pour plus d'informations, reportez-vous à [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="5fdb9-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="5fdb9-112">Lorsque vous bloquez un compte d’utilisateur, il peut prendre jusqu'à 24 heures prennent effet sur les périphériques et les clients de tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5fdb9-112">When you block a user account, it might take as long as 24 hours to take effect on all the user's devices and clients.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="5fdb9-113">Utilisation d'Office 365 PowerShell pour bloquer l'accès à des comptes d'utilisateurs individuels</span><span class="sxs-lookup"><span data-stu-id="5fdb9-113">Use Office 365 PowerShell to block access to individual user accounts</span></span>

<span data-ttu-id="5fdb9-114">Pour bloquer l’accès à un compte d’utilisateur individuel, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-114">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

<span data-ttu-id="5fdb9-115">Cet exemple bloque l’accès au compte d’utilisateur fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="5fdb9-115">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="5fdb9-116">Pour débloquer le compte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-116">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

<span data-ttu-id="5fdb9-117">À tout moment, vous pouvez vérifier le statut bloqué d’un compte d’utilisateur avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a><span data-ttu-id="5fdb9-118">Office 365 PowerShell permet de bloquer l’accès à plusieurs comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="5fdb9-118">Use Office 365 PowerShell to block access to multiple user accounts</span></span>

<span data-ttu-id="5fdb9-119">Tout d’abord, créez un fichier texte qui contient un seul compte sur chaque ligne, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-119">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="5fdb9-p103">Dans les commandes suivantes, l’exemple de fichier texte est C:\My Documents\Accounts.txt. Remplacez ceci par le chemin d’accès et le nom de votre fichier texte.</span><span class="sxs-lookup"><span data-stu-id="5fdb9-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="5fdb9-122">Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="5fdb9-123">Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a><span data-ttu-id="5fdb9-124">Utiliser le module Azure Active Directory V2 PowerShell pour bloquer l’accès à des comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="5fdb9-124">Use the Azure Active Directory V2 PowerShell module to block access to user accounts</span></span>

<span data-ttu-id="5fdb9-p104">Pour utiliser la cmdlet **New-AzureADUser** à partir du module Azure Active Directory V2 PowerShell, vous devez d'abord vous connecter à votre abonnement. Pour obtenir les instructions, reportez-vous à l'article[Se connecter au module Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="5fdb9-p104">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="5fdb9-127">Après vous être connecté, utilisez la syntaxe suivante pour bloquer un compte d’utilisateur individuel :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-127">After you have connected, use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="5fdb9-128">Le paramètre - ObjectID de la cmdlet Set-AzureAD accepte le nom de compte, également appelé Nom d’utilisateur principal, ou l’ID d’objet du compte.</span><span class="sxs-lookup"><span data-stu-id="5fdb9-128">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="5fdb9-129">Cet exemple bloque l’accès au compte d’utilisateur fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="5fdb9-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="5fdb9-130">Pour débloquer ce compte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-130">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="5fdb9-131">Pour afficher le compte d’utilisateur QU'UPN basé sur le nom complet de l’utilisateur, utilisez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-131">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="5fdb9-132">Cet exemple affiche le compte d’utilisateur UPN de l’utilisateur nommé Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="5fdb9-132">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5fdb9-133">Pour bloquer un compte à partir du nom de l’utilisateur, utilisez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-133">To block an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="5fdb9-134">À tout moment, vous pouvez vérifier le statut bloqué d’un compte d’utilisateur avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-134">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

<span data-ttu-id="5fdb9-135">Pour bloquer l’accès à plusieurs comptes d’utilisateurs, créez un fichier texte qui contient un nom de compte de chaque ligne comme suit :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-135">To block access to multiple user accounts, create a text file that contains one account name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="5fdb9-p105">Dans les commandes suivantes, l’exemple de fichier texte est C:\My Documents\Accounts.txt. Remplacez ceci par le chemin d’accès et le nom de votre fichier texte.</span><span class="sxs-lookup"><span data-stu-id="5fdb9-p105">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="5fdb9-138">Pour bloquer l’accès aux comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-138">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="5fdb9-139">Pour débloquer les comptes indiqués dans le fichier texte, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-139">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="see-also"></a><span data-ttu-id="5fdb9-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fdb9-140">See also</span></span>
<span data-ttu-id="5fdb9-141"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="5fdb9-141"></span></span>

<span data-ttu-id="5fdb9-142">Consultez les rubriques supplémentaires suivantes sur la gestion des utilisateurs avec Office 365 PowerShell :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-142">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="5fdb9-143">Création de comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fdb9-143">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="5fdb9-144">Supprimer et restaurer des comptes d’utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fdb9-144">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="5fdb9-145">Attribuer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fdb9-145">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="5fdb9-146">Supprimer des licences à des comptes d'utilisateurs avec Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fdb9-146">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="5fdb9-147">Pour plus d’informations sur les cmdlets utilisées dans ces procédures, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5fdb9-147">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="5fdb9-148">Get-Content.</span><span class="sxs-lookup"><span data-stu-id="5fdb9-148">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [<span data-ttu-id="5fdb9-149">Set-MsolUser</span><span class="sxs-lookup"><span data-stu-id="5fdb9-149">Set-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [<span data-ttu-id="5fdb9-150">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="5fdb9-150">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

