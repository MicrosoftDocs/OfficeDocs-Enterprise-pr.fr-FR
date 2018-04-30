---
title: Ajouter ou supprimer un administrateur localisés
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Découvrez comment ajouter ou supprimer un administrateur localisés dans OneDrive pour Business Multi-localisés.
ms.openlocfilehash: 7630597654df9ad78619b94fedc9e18d5b0b721e
ms.sourcegitcommit: 886b23f590f6187f7a98c1083a3b49359ec2a5c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>Ajouter ou supprimer un administrateur localisés dans OneDrive pour Busniess Multi-localisés

Vous pouvez configurer des administrateurs distincts pour chaque emplacement géographique que vous avez dans votre client. Ces administrateurs auront accès aux paramètres de SharePoint Online et OneDrive qui sont spécifiques à leur emplacement géographique.

Certains services - telles que le magasin de termes - sont administrés à partir de l’emplacement central et répliquées aux emplacements satellites. L’administrateur localisés pour l’emplacement central a accès à ces derniers, tandis que les administrateurs localisés pour les emplacements satellites ne.

Les administrateurs globaux et les administrateurs SharePoint Online continuent à accéder aux paramètres dans tous les emplacements de géolocalisation.

## <a name="configuring-geo-administrators"></a>Configuration des administrateurs localisés

Configuration des administrateurs localisés nécessite module SharePoint Online PowerShell.

[Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) permet de se connecter au centre d’administration de l’emplacement géographique où vous souhaitez ajouter l’administrateur de géolocalisation. (Par exemple, Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Pour afficher les administrateurs geo existant d’un emplacement, exécutez`Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Ajout d’un utilisateur en tant qu’un administrateur localisés

Pour ajouter un utilisateur en tant qu’un administrateur localisés, exécutez`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Pour supprimer un utilisateur en tant qu’un administrateur géographique d’un emplacement, exécutez`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Ajout d’un groupe en tant qu’un administrateur localisés

Vous pouvez ajouter un groupe de sécurité ou un groupe de sécurité à extension messagerie en tant qu’un administrateur de géolocalisation. (Groupes de distribution et les groupes d’Office 365 ne sont pas pris en charge.)

Pour ajouter un groupe en tant qu’un administrateur localisés, exécutez`Add-SPOGeoAdministrator -GroupAlias <alias>`

Pour supprimer un groupe en tant qu’un administrateur localisés, exécutez`Remove-SPOGeoAdministrator -GroupAlias <alias>`

Notez que pas tous les groupes de sécurité ont un alias de groupe. Si vous souhaitez ajouter un groupe de sécurité qui ne dispose pas d’un alias, exécutez [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) pour récupérer la liste des groupes, trouver ObjectID de votre groupe de sécurité, puis exécutez :

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Pour supprimer un groupe à l’aide de ObjectID, exécutez`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="see-also"></a>Voir aussi

[SPOGeoAdministrator ajouter](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Définir un alias (MailNickName) pour un groupe de sécurité](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)