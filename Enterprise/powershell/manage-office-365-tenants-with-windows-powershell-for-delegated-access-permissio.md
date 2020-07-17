---
title: Gérer les clients Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Résumé : utilisez Windows PowerShell pour Microsoft 365 pour gérer vos locations de client.'
ms.openlocfilehash: a57f66ec02f5ba69006c17a9cf734e622017b8fb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998230"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="9d052-103">Gérer les clients Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="9d052-103">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="9d052-104">Windows PowerShell permet aux partenaires de syndication et de fournisseur de solutions Cloud (CSP) d’administrer et de signaler facilement les paramètres de location des clients qui ne sont pas disponibles dans le centre d’administration 365 de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9d052-104">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="9d052-105">Les autorisations AOBO (Administrer au nom de) sont requises pour que le compte d’administrateur du partenaire puisse se connecter aux locations de son client.</span><span class="sxs-lookup"><span data-stu-id="9d052-105">Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="9d052-106">Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud.</span><span class="sxs-lookup"><span data-stu-id="9d052-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="9d052-107">Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés.</span><span class="sxs-lookup"><span data-stu-id="9d052-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="9d052-108">Ils regroupent les abonnements Microsoft 365 dans leurs offres de service à leurs clients.</span><span class="sxs-lookup"><span data-stu-id="9d052-108">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="9d052-109">Lors de la vente d’un abonnement Microsoft 365, les autorisations d’administration pour le compte de (administrateur) sont automatiquement accordées aux clients pour qu’ils puissent administrer et rendre compte des locations des clients.</span><span class="sxs-lookup"><span data-stu-id="9d052-109">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="9d052-110">Ce qu'il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="9d052-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="9d052-p103">Les procédures décrites dans cette rubrique exigent une connexion à Windows PowerShell pour Office 365. Pour plus d'informations, voir [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9d052-p103">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="9d052-113">Vous avez aussi besoin des informations d’identification d’administrateur de la location du partenaire.</span><span class="sxs-lookup"><span data-stu-id="9d052-113">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="9d052-114">Que souhaitez-vous faire ?</span><span class="sxs-lookup"><span data-stu-id="9d052-114">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="9d052-115">Répertorier tous les ID de locataire</span><span class="sxs-lookup"><span data-stu-id="9d052-115">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="9d052-p104">Si vous disposez de plus de 500 locataires, définissez la portée de la syntaxe de la cmdlet avec  _-All_ ou _-MaxResultsParameter_. Vous pouvez appliquer cette technique aux autres cmdlets susceptibles de générer de nombreux résultats, comme **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="9d052-p104">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="9d052-118">Pour répertorier tous les ID de locataire auxquels vous avez accès, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="9d052-118">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="9d052-119">Elle affiche la liste de tous les locataires de votre client par **TenantId**.</span><span class="sxs-lookup"><span data-stu-id="9d052-119">This will display a listing of all your customer tenants by **TenantId**.</span></span>

>[!Note]
><span data-ttu-id="9d052-120">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="9d052-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="9d052-121">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d052-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="9d052-122">Obtenir un ID de locataire à l’aide du nom de domaine</span><span class="sxs-lookup"><span data-stu-id="9d052-122">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="9d052-p106">Pour obtenir le code **TenantId** d'une location spécifique du client par nom de domaine, exécutez la commande suivante. Remplacez _<domainname.onmicrosoft.com>_ par le nom de domaine réel du locataire du client que vous voulez obtenir.</span><span class="sxs-lookup"><span data-stu-id="9d052-p106">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="9d052-125">Répertorier tous les domaines pour un locataire</span><span class="sxs-lookup"><span data-stu-id="9d052-125">List all domains for a tenant</span></span>

<span data-ttu-id="9d052-p107">Pour obtenir la liste de tous les domaines pour un seul des locataires d'un client, exécutez la commande suivante. Remplacez  _<customer TenantId value>_ par la valeur réelle du code TenantId du client.</span><span class="sxs-lookup"><span data-stu-id="9d052-p107">To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="9d052-128">Si vous avez enregistré des domaines supplémentaires, tous les domaines associés au code **TenantId** du client seront renvoyés.</span><span class="sxs-lookup"><span data-stu-id="9d052-128">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="9d052-129">Obtenir un mappage de tous les locataires et domaines enregistrés</span><span class="sxs-lookup"><span data-stu-id="9d052-129">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="9d052-p108">Les commandes Windows PowerShell pour Office 365 précédentes vous ont montré comment récupérer l'ID ou les domaines de locataire, mais pas les deux en même temps, et sans aucun mappage clair entre eux. Cette commande génère une liste de tous les ID de locataire du client et leurs domaines.</span><span class="sxs-lookup"><span data-stu-id="9d052-p108">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="9d052-132">Obtenir tous les utilisateurs pour un client</span><span class="sxs-lookup"><span data-stu-id="9d052-132">Get all users for a tenant</span></span>

<span data-ttu-id="9d052-p109">Cette commande permet d'afficher **UserPrincipalName**, **DisplayName** et le statut **isLicensed** pour tous les utilisateurs d'une location particulière. Remplacez _<customer TenantId value>_ par la valeur réelle du code TenantId du client.</span><span class="sxs-lookup"><span data-stu-id="9d052-p109">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="9d052-135">Obtenir tous les détails sur un utilisateur</span><span class="sxs-lookup"><span data-stu-id="9d052-135">Get all details about a user</span></span>

<span data-ttu-id="9d052-p110">Si vous souhaitez voir toutes les propriétés d'un utilisateur particulier, exécutez la commande suivante. Remplacez  _<customer TenantId value>_ par la valeur réelle du code TenantId du client et _<user principal name value>_ par la valeur réelle du nom d'utilisateur principal.</span><span class="sxs-lookup"><span data-stu-id="9d052-p110">If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="9d052-138">Ajouter des utilisateurs, définir des options et attribuer des licences</span><span class="sxs-lookup"><span data-stu-id="9d052-138">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="9d052-139">La création, la configuration et la gestion des licences en bloc des utilisateurs de Microsoft 365 sont particulièrement efficaces grâce à Windows PowerShell pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="9d052-139">The bulk creation, configuration, and licensing of Microsoft 365 users is particularly efficient by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="9d052-140">Dans ce processus en deux étapes, vous devez d’abord créer des entrées pour tous les utilisateurs que vous souhaitez ajouter dans un fichier de valeurs séparées par des virgules (CSV), puis importer ce fichier à l’aide de Windows PowerShell pour Office 365.</span><span class="sxs-lookup"><span data-stu-id="9d052-140">In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="9d052-141">Créer un fichier CSV</span><span class="sxs-lookup"><span data-stu-id="9d052-141">Create a CSV file</span></span>

<span data-ttu-id="9d052-142">Créez un fichier CSV à l’aide de ce format :</span><span class="sxs-lookup"><span data-stu-id="9d052-142">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="9d052-143">oà¹ :</span><span class="sxs-lookup"><span data-stu-id="9d052-143">where:</span></span>
  
- <span data-ttu-id="9d052-p112">**UsageLocation**: la valeur de ce paramètre est le code ISO de pays/région à deux lettres de l'utilisateur. Les codes de pays/région peuvent être consultés sur la[plateforme de consultation en ligne de l'ISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). Par exemple, le code pour les États-Unis est US et le code pour le Brésil est BR.</span><span class="sxs-lookup"><span data-stu-id="9d052-p112">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="9d052-p113">**LicenseAssignment**: la valeur de ce paramètre utilise ce format : `syndication-account:<PROVISIONING_ID>`. Par exemple, si vous affectez des licences O365_Business_Premium à des utilisateurs des locataires du client, la valeur de **LicenseAssignment** ressemble à ceci : **syndication-account:O365_Business_Premium**. Vous trouverez les codes PROVISIONING_ID dans le portail des partenaires de syndication auxquels vous avez accès en tant que partenaire fournisseur de solutions cloud ou de syndication.</span><span class="sxs-lookup"><span data-stu-id="9d052-p113">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="9d052-150">Importer le fichier CSV et créer les utilisateurs</span><span class="sxs-lookup"><span data-stu-id="9d052-150">Import the CSV file and create the users</span></span>

<span data-ttu-id="9d052-p114">Une fois votre fichier CSV créé, exécutez la commande suivante pour créer des comptes d'utilisateurs avec des mots de passe sans date d'expiration que l'utilisateur doit changer à la première ouverture de session et attribuer la licence que vous spécifiez. Veillez à remplacer le nom de fichier CSV approprié.</span><span class="sxs-lookup"><span data-stu-id="9d052-p114">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="9d052-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d052-153">See also</span></span>

#### 

[<span data-ttu-id="9d052-154">Aide pour les partenaires</span><span class="sxs-lookup"><span data-stu-id="9d052-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

