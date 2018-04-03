---
title: Ajouter ou supprimer un administrateur de zone géographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Apprenez à ajouter ou supprimer un administrateur de la zone géographique dans OneDrive pour entreprise Multi-Geo.
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>Ajouter ou supprimer un administrateur de la zone géographique dans OneDrive pour Busniess Multi-Geo

Vous pouvez configurer des administrateurs distincts pour chaque emplacement géographique que vous avez dans votre client. Ces administrateurs auront accès aux paramètres de SharePoint Online et OneDrive qui sont spécifiques à leur emplacement géographique.

Certains services - tels que la banque de termes - sont administrés depuis un emplacement central et répliqués dans des endroits de satellite. L’administrateur geo pour l’emplacement central a accès à ceux-ci, alors que les administrateurs geo pour les emplacements de satellites ne.

Les administrateurs globaux et les administrateurs SharePoint Online continuent à accéder aux paramètres dans tous les emplacements de la zone géographique.

## <a name="configuring-geo-administrators"></a>Configuration des administrateurs de geo

Configuration des administrateurs de geo requiert SharePoint Online PowerShell module.

Utilisez [SPOService à la connexion](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) pour vous connecter au centre d’administration de l’emplacement géographique où vous souhaitez ajouter l’administrateur de zone géographique. (Par exemple, se connecter à SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Pour ajouter un utilisateur comme un administrateur de zone géographique, exécuter`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Pour afficher les administrateurs geo existant d’un emplacement, exécutez`Get-SPOGeoAdministrators`

Pour supprimer un utilisateur en tant qu’un administrateur géographique d’un emplacement, exécutez`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

## <a name="see-also"></a>Voir aussi

[Ajouter-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Supprimer-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)