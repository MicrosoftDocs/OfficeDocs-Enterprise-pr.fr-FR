---
title: Ajouter ou supprimer un administrateur géographique
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
localization_priority: Normal
f1.keywords:
- NOCSH
description: Découvrez comment ajouter ou supprimer un administrateur géo dans Microsoft 365 Multi-Geo.
ms.openlocfilehash: 13b730de6b318ddb3a4cf3a084d4b59e56a82dbf
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433605"
---
# <a name="add-or-remove-a-geo-administrator-in-microsoft-365-multi-geo"></a>Ajouter ou supprimer un administrateur géo dans Microsoft 365 Multi-Geo

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

Vous pouvez ajouter un groupe de sécurité ou un groupe de sécurité à extension courrier en tant qu’administrateur géographique (les groupes de distribution et les groupes Microsoft 365 ne sont pas pris en charge).

Pour ajouter un groupe en tant qu’administrateur géographique, exécutez la cmdlet `Add-SPOGeoAdministrator -GroupAlias <alias>`.

Pour supprimer un groupe administrateur géographique, exécutez la cmdlet `Remove-SPOGeoAdministrator -GroupAlias <alias>`.

Notez que certains groupes de sécurité n’ont pas d’alias de groupe. Si vous voulez ajouter un groupe de sécurité dépourvu d’alias, exécutez la cmdlet [MsolGroup Get](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) pour récupérer une liste de groupes, recherchez l’ObjectID de votre groupe de sécurité, puis exécutez la cmdlet suivante :

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Pour supprimer un groupe à l’aide de l’ObjectID, exécutez la cmdlet `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`.

## <a name="see-also"></a>Voir aussi

[Add-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Définir un alias (MailNickName) pour un groupe de sécurité](https://docs.microsoft.com/powershell/module/azuread/set-azureadgroup)