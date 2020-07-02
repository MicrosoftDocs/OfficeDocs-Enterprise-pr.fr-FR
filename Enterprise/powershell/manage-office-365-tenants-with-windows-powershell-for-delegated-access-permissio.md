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
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Gérer les clients Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué

Windows PowerShell permet aux partenaires de syndication et de fournisseur de solutions Cloud (CSP) d’administrer et de signaler facilement les paramètres de location des clients qui ne sont pas disponibles dans le centre d’administration 365 de Microsoft. Les autorisations AOBO (Administrer au nom de) sont requises pour que le compte d’administrateur du partenaire puisse se connecter aux locations de son client.
  
Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés. Ils regroupent les abonnements Microsoft 365 dans leurs offres de service à leurs clients. Lors de la vente d’un abonnement Microsoft 365, les autorisations d’administration pour le compte de (administrateur) sont automatiquement accordées aux clients pour qu’ils puissent administrer et rendre compte des locations des clients.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
Vous avez aussi besoin des informations d’identification d’administrateur de la location du partenaire.
  
## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

### <a name="list-all-tenant-ids"></a>Répertorier tous les ID de locataire

> [!NOTE]
> If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.
  
Pour répertorier tous les ID de locataire auxquels vous avez accès, exécutez cette commande.
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

Elle affiche la liste de tous les locataires de votre client par **TenantId**.

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Obtenir un ID de locataire à l’aide du nom de domaine

To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Répertorier tous les domaines pour un locataire

To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

Si vous avez enregistré des domaines supplémentaires, tous les domaines associés au code **TenantId** du client seront renvoyés.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Obtenir un mappage de tous les locataires et domaines enregistrés

The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Obtenir tous les utilisateurs pour un client

This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Obtenir tous les détails sur un utilisateur

If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Ajouter des utilisateurs, définir des options et attribuer des licences

La création, la configuration et la gestion des licences en bloc des utilisateurs de Microsoft 365 sont particulièrement efficaces grâce à Windows PowerShell pour Office 365. Dans ce processus en deux étapes, vous devez d’abord créer des entrées pour tous les utilisateurs que vous souhaitez ajouter dans un fichier de valeurs séparées par des virgules (CSV), puis importer ce fichier à l’aide de Windows PowerShell pour Office 365. 
  
#### <a name="create-a-csv-file"></a>Créer un fichier CSV

Créez un fichier CSV à l’aide de ce format :
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
oà¹ :
  
- **UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR. 
    
- **LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>Importer le fichier CSV et créer les utilisateurs

After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Voir aussi

#### 

[Aide pour les partenaires](https://go.microsoft.com/fwlink/p/?LinkId=533477)

