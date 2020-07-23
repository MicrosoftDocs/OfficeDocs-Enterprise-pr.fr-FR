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
description: 'Résumé : utilisez PowerShell pour Microsoft 365 pour gérer vos locations de client.'
ms.openlocfilehash: 31ce5b9a7bdfa50234c76be65eaeb99d6d199136
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230590"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Gérer les clients Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué

*Cet article s’applique à la fois à Microsoft 365 entreprise et à Office 365 entreprise.*

Windows PowerShell permet aux partenaires de syndication et de fournisseur de solutions Cloud (CSP) d’administrer et de signaler facilement les paramètres de location des clients qui ne sont pas disponibles dans le centre d’administration 365 de Microsoft. Notez que les autorisations administrer de la part de (administrateur) sont requises pour le compte d’administrateur partenaire afin de se connecter à ses clients.
  
Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. Il s’agit souvent de fournisseurs de réseau ou de télécommunication pour d’autres sociétés. Ils regroupent les abonnements Microsoft 365 dans leurs offres de service à leurs clients. Lors de la vente d’un abonnement Microsoft 365, les autorisations d’administration pour le compte de (administrateur) sont automatiquement accordées aux clients pour qu’ils puissent administrer et rendre compte des locations des clients.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

Les procédures décrites dans cette rubrique vous obligent à vous connecter à [Microsoft 365 avec PowerShell](connect-to-office-365-powershell.md).
  
Vous avez aussi besoin des informations d’identification d’administrateur de la location du partenaire.
  
## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

### <a name="list-all-tenant-ids"></a>Répertorier tous les ID de locataire

> [!NOTE]
> Si vous disposez de plus de 500 locataires, définissez la portée de la syntaxe de la cmdlet avec  _-All_ ou _-MaxResultsParameter_. Vous pouvez appliquer cette technique aux autres cmdlets susceptibles de générer de nombreux résultats, comme **Get-MsolUser**.
  
Pour répertorier tous les ID de locataire auxquels vous avez accès, exécutez cette commande.
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

Elle affiche la liste de tous les locataires de votre client par **TenantId**.

>[!Note]
>PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom. Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Obtenir un ID de locataire à l’aide du nom de domaine

Pour obtenir le code **TenantId** d'une location spécifique du client par nom de domaine, exécutez la commande suivante. Remplacez _<domainname.onmicrosoft.com>_ par le nom de domaine réel du locataire du client que vous voulez obtenir.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Répertorier tous les domaines pour un locataire

Pour obtenir la liste de tous les domaines pour un seul des locataires d'un client, exécutez la commande suivante. Remplacez  _<customer TenantId value>_ par la valeur réelle du code TenantId du client.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

Si vous avez enregistré des domaines supplémentaires, tous les domaines associés au code **TenantId** du client seront renvoyés.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Obtenir un mappage de tous les locataires et domaines enregistrés

Les commandes PowerShell précédentes pour Microsoft 365 vous ont permis de récupérer les ID de locataire ou les domaines, mais pas les deux en même temps, et sans aucun mappage clair entre eux. Cette commande génère une liste de tous les ID de locataire du client et leurs domaines.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Obtenir tous les utilisateurs pour un client

Cette commande permet d'afficher **UserPrincipalName**, **DisplayName** et le statut **isLicensed** pour tous les utilisateurs d'une location particulière. Remplacez _<customer TenantId value>_ par la valeur réelle du code TenantId du client.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Obtenir tous les détails sur un utilisateur

Si vous souhaitez voir toutes les propriétés d'un utilisateur particulier, exécutez la commande suivante. Remplacez  _<customer TenantId value>_ par la valeur réelle du code TenantId du client et _<user principal name value>_ par la valeur réelle du nom d'utilisateur principal.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Ajouter des utilisateurs, définir des options et attribuer des licences

La création, la configuration et la gestion des licences en bloc des utilisateurs de Microsoft 365 sont particulièrement efficaces à l’aide de PowerShell pour Microsoft 365. Dans ce processus en deux étapes, vous devez d’abord créer des entrées pour tous les utilisateurs que vous souhaitez ajouter dans un fichier de valeurs séparées par des virgules (CSV), puis importer ce fichier à l’aide de PowerShell pour Microsoft 365. 
  
#### <a name="create-a-csv-file"></a>Créer un fichier CSV

Créez un fichier CSV à l’aide de ce format :
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
oà¹ :
  
- **UsageLocation**: la valeur de ce paramètre est le code ISO de pays/région à deux lettres de l'utilisateur. Les codes de pays/région peuvent être consultés sur la[plateforme de consultation en ligne de l'ISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). Par exemple, le code pour les États-Unis est US et le code pour le Brésil est BR. 
    
- **LicenseAssignment**: la valeur de ce paramètre utilise ce format : `syndication-account:<PROVISIONING_ID>`. Par exemple, si vous affectez des licences O365_Business_Premium à des utilisateurs des locataires du client, la valeur de **LicenseAssignment** ressemble à ceci : **syndication-account:O365_Business_Premium**. Vous trouverez les codes PROVISIONING_ID dans le portail des partenaires de syndication auxquels vous avez accès en tant que partenaire fournisseur de solutions cloud ou de syndication.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>Importer le fichier CSV et créer les utilisateurs

Une fois votre fichier CSV créé, exécutez la commande suivante pour créer des comptes d'utilisateurs avec des mots de passe sans date d'expiration que l'utilisateur doit changer à la première ouverture de session et attribuer la licence que vous spécifiez. Veillez à remplacer le nom de fichier CSV approprié.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Voir aussi

#### 

[Aide pour les partenaires](https://go.microsoft.com/fwlink/p/?LinkId=533477)

