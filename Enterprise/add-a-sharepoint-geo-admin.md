---
title: Ajouter ou supprimer un administrateur géographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: Découvrez comment ajouter ou supprimer un administrateur géographique dans Office 365 multigéographique.
ms.openlocfilehash: 54850252d133e3e26b02cabe3ead0900287e832c
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490910"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a>Ajouter ou supprimer un administrateur géographique dans Office 365 multigéographique

Vous pouvez configurer des administrateurs distincts pour chaque emplacement géographique disponible dans votre client. Ces administrateurs ont accès aux paramètres SharePoint Online et OneDrive spécifiques de leur emplacement géographique.

Certains services (par exemple, le magasin de termes) sont administrés à partir de l’emplacement central et répliqués vers des emplacements satellites. L’administrateur géographique de l’emplacement central a accès à ces fonctionnalités, au contraire des administrateurs géographiques des emplacements satellites.

Les administrateurs généraux et les administrateurs SharePoint Online ont toujours accès aux paramètres dans l’emplacement central et dans tous les emplacements satellites.

## <a name="configuring-geo-administrators"></a>Configuration des administrateurs géographiques

La configuration des administrateurs géographiques nécessite un module SharePoint Online PowerShell.

Pour vous connecter au centre d’administration de l’emplacement géographique auquel vous voulez ajouter l’administrateur géo, utilisez la cmdlet [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) (par exemple, Connect-SPOService https://ContosoEUR-admin.sharepoint.com.)

Pour afficher les administrateurs géographiques existants d’un emplacement, exécutez la cmdlet `Get-SPOGeoAdministrator`.

### <a name="adding-a-user-as-a-geo-admin"></a>Ajout d’un utilisateur en tant qu’administrateur géographique

Pour ajouter un utilisateur en tant qu’administrateur géographique, exécutez la cmdlet `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`.

Pour supprimer un utilisateur administrateur géographique d’un emplacement, exécutez la cmdlet `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`.

### <a name="adding-a-group-as-a-geo-admin"></a>Ajout d’un groupe en tant qu’administrateur géographique

Vous pouvez ajouter un groupe de sécurité ou un groupe de sécurité à extension courrier en tant qu’administrateur géographique (les groupes de distribution et les groupes Office 365 ne sont pas pris en charge).

Pour ajouter un groupe en tant qu’administrateur géographique, exécutez la cmdlet `Add-SPOGeoAdministrator -GroupAlias <alias>`.

Pour supprimer un groupe administrateur géographique, exécutez la cmdlet `Remove-SPOGeoAdministrator -GroupAlias <alias>`.

Notez que certains groupes de sécurité n’ont pas d’alias de groupe. Si vous voulez ajouter un groupe de sécurité dépourvu d’alias, exécutez la cmdlet [MsolGroup Get](https://docs.microsoft.com/fr-FR/powershell/module/msonline/get-msolgroup) pour récupérer une liste de groupes, recherchez l’ObjectID de votre groupe de sécurité, puis exécutez la cmdlet suivante :

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Pour supprimer un groupe à l’aide de l’ObjectID, exécutez la cmdlet `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`.

## <a name="see-also"></a>Voir aussi

[Add-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Définir un alias (MailNickName) pour un groupe de sécurité](https://docs.microsoft.com/fr-FR/powershell/module/azuread/set-azureadgroup)