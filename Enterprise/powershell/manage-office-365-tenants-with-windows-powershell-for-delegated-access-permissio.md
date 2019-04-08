---
title: Gestion de clients Office 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Résumé : Utilisez Windows PowerShell pour Office 365 pour gérer les locations de votre client.'
ms.openlocfilehash: 4fec058bfd7b7dffa2c29add23d99a144f78decf
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001857"
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="33f32-103">Gestion de clients Office 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué</span><span class="sxs-lookup"><span data-stu-id="33f32-103">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="33f32-104">**Résumé :** Utilisez Windows PowerShell pour Office 365 pour gérer les locations de votre client.</span><span class="sxs-lookup"><span data-stu-id="33f32-104">**Summary:** Use Windows PowerShell for Office 365 to manage your customer tenancies.</span></span>
  
<span data-ttu-id="33f32-p101">Windows PowerShell permet aux Partenaires de syndication et fournisseur de solutions cloud de gérer les paramètres des locations du client qui ne sont pas disponibles dans le Centre d'administration Office 365 et de créer facilement des rapports à partir de ceux-ci. Les autorisations AOBO (Administrer au nom de) sont requises pour que le compte d'administrateur du partenaire puisse se connecter aux locations de son client.</span><span class="sxs-lookup"><span data-stu-id="33f32-p101">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Office 365 admin center. Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="33f32-107">Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud.</span><span class="sxs-lookup"><span data-stu-id="33f32-107">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="33f32-108">Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés.</span><span class="sxs-lookup"><span data-stu-id="33f32-108">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="33f32-109">Ils regroupent les abonnements Office 365 dans leurs offres de services pour les clients.</span><span class="sxs-lookup"><span data-stu-id="33f32-109">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="33f32-110">Lorsqu'ils vendent un abonnement Office 365, ils bénéficient automatiquement des autorisations AOBO (Administrer au nom de) sur les locations clientes et peuvent donc gérer les locations du client et créer des rapports.</span><span class="sxs-lookup"><span data-stu-id="33f32-110">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="33f32-111">Ce qu'il faut savoir avant de commencer</span><span class="sxs-lookup"><span data-stu-id="33f32-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="33f32-p103">Les procédures décrites dans cette rubrique exigent une connexion à Windows PowerShell pour Office 365. Pour plus d'informations, voir [Se connecter à Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="33f32-p103">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="33f32-114">Vous avez aussi besoin des informations d’identification d’administrateur de la location du partenaire.</span><span class="sxs-lookup"><span data-stu-id="33f32-114">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="33f32-115">Que souhaitez-vous faire ?</span><span class="sxs-lookup"><span data-stu-id="33f32-115">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="33f32-116">Répertorier tous les ID de locataire</span><span class="sxs-lookup"><span data-stu-id="33f32-116">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="33f32-p104">Si vous disposez de plus de 500 locataires, définissez la portée de la syntaxe de la cmdlet avec  _-All_ ou _-MaxResultsParameter_. Vous pouvez appliquer cette technique aux autres cmdlets susceptibles de générer de nombreux résultats, comme **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="33f32-p104">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="33f32-119">Pour répertorier tous les ID de locataire auxquels vous avez accès, exécutez cette commande.</span><span class="sxs-lookup"><span data-stu-id="33f32-119">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="33f32-120">Elle affiche la liste de tous les locataires de votre client par **TenantId**.</span><span class="sxs-lookup"><span data-stu-id="33f32-120">This will display a listing of all your customer tenants by **TenantId**.</span></span>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="33f32-121">Obtenir un ID de locataire à l’aide du nom de domaine</span><span class="sxs-lookup"><span data-stu-id="33f32-121">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="33f32-p105">Pour obtenir le code **TenantId** d'une location spécifique du client par nom de domaine, exécutez la commande suivante. Remplacez _<domainname.onmicrosoft.com>_ par le nom de domaine réel du locataire du client que vous voulez obtenir.</span><span class="sxs-lookup"><span data-stu-id="33f32-p105">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="33f32-124">Répertorier tous les domaines pour un locataire</span><span class="sxs-lookup"><span data-stu-id="33f32-124">List all domains for a tenant</span></span>

<span data-ttu-id="33f32-p106">Pour obtenir la liste de tous les domaines pour un seul des locataires d'un client, exécutez la commande suivante. Remplacez  _<customer TenantId value>_ par la valeur réelle du code TenantId du client.</span><span class="sxs-lookup"><span data-stu-id="33f32-p106">To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="33f32-127">Si vous avez enregistré des domaines supplémentaires, tous les domaines associés au code **TenantId** du client seront renvoyés.</span><span class="sxs-lookup"><span data-stu-id="33f32-127">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="33f32-128">Obtenir un mappage de tous les locataires et domaines enregistrés</span><span class="sxs-lookup"><span data-stu-id="33f32-128">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="33f32-p107">Les commandes Windows PowerShell pour Office 365 précédentes vous ont montré comment récupérer l'ID ou les domaines de locataire, mais pas les deux en même temps, et sans aucun mappage clair entre eux. Cette commande génère une liste de tous les ID de locataire du client et leurs domaines.</span><span class="sxs-lookup"><span data-stu-id="33f32-p107">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="33f32-131">Obtenir tous les utilisateurs pour un client</span><span class="sxs-lookup"><span data-stu-id="33f32-131">Get all users for a tenant</span></span>

<span data-ttu-id="33f32-p108">Cette commande permet d'afficher **UserPrincipalName**, **DisplayName** et le statut **isLicensed** pour tous les utilisateurs d'une location particulière. Remplacez _<customer TenantId value>_ par la valeur réelle du code TenantId du client.</span><span class="sxs-lookup"><span data-stu-id="33f32-p108">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="33f32-134">Obtenir tous les détails sur un utilisateur</span><span class="sxs-lookup"><span data-stu-id="33f32-134">Get all details about a user</span></span>

<span data-ttu-id="33f32-p109">Si vous souhaitez voir toutes les propriétés d'un utilisateur particulier, exécutez la commande suivante. Remplacez  _<customer TenantId value>_ par la valeur réelle du code TenantId du client et _<user principal name value>_ par la valeur réelle du nom d'utilisateur principal.</span><span class="sxs-lookup"><span data-stu-id="33f32-p109">If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="33f32-137">Ajouter des utilisateurs, définir des options et attribuer des licences</span><span class="sxs-lookup"><span data-stu-id="33f32-137">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="33f32-p110">La création, la configuration et la gestion des licences en bloc pour les utilisateurs Office 365 sont particulièrement efficaces en utilisant Windows PowerShell pour Office 365 Dans ce processus en deux étapes, vous commencez par créer des entrées dans un fichier CSV pour tous les utilisateurs que vous souhaitez ajouter, puis vous importez ce fichier à l'aide de Windows PowerShell pour Office 365</span><span class="sxs-lookup"><span data-stu-id="33f32-p110">The bulk creation, configuration, and licensing of Office 365 users is particularly efficient by using Windows PowerShell for Office 365. In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="33f32-140">Créer un fichier CSV</span><span class="sxs-lookup"><span data-stu-id="33f32-140">Create a CSV file</span></span>

<span data-ttu-id="33f32-141">Créez un fichier CSV à l’aide de ce format :</span><span class="sxs-lookup"><span data-stu-id="33f32-141">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="33f32-142">oà¹ :</span><span class="sxs-lookup"><span data-stu-id="33f32-142">where:</span></span>
  
- <span data-ttu-id="33f32-p111">**UsageLocation**: la valeur de ce paramètre est le code ISO de pays/région à deux lettres de l'utilisateur. Les codes de pays/région peuvent être consultés sur la[plateforme de consultation en ligne de l'ISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). Par exemple, le code pour les États-Unis est US et le code pour le Brésil est BR.</span><span class="sxs-lookup"><span data-stu-id="33f32-p111">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="33f32-p112">**LicenseAssignment**: la valeur de ce paramètre utilise ce format : `syndication-account:<PROVISIONING_ID>`. Par exemple, si vous affectez des licences O365_Business_Premium à des utilisateurs des locataires du client, la valeur de **LicenseAssignment** ressemble à ceci : **syndication-account:O365_Business_Premium**. Vous trouverez les codes PROVISIONING_ID dans le portail des partenaires de syndication auxquels vous avez accès en tant que partenaire fournisseur de solutions cloud ou de syndication.</span><span class="sxs-lookup"><span data-stu-id="33f32-p112">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="33f32-149">Importer le fichier CSV et créer les utilisateurs</span><span class="sxs-lookup"><span data-stu-id="33f32-149">Import the CSV file and create the users</span></span>

<span data-ttu-id="33f32-p113">Une fois votre fichier CSV créé, exécutez la commande suivante pour créer des comptes d'utilisateurs avec des mots de passe sans date d'expiration que l'utilisateur doit changer à la première ouverture de session et attribuer la licence que vous spécifiez. Veillez à remplacer le nom de fichier CSV approprié.</span><span class="sxs-lookup"><span data-stu-id="33f32-p113">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="33f32-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33f32-152">See also</span></span>

#### 

[<span data-ttu-id="33f32-153">Aide pour les partenaires</span><span class="sxs-lookup"><span data-stu-id="33f32-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

