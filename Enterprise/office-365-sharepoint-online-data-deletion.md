---
title: Suppression des données SharePoint Online d’Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Explication de la suppression de données dans SharePoint Online.
ms.openlocfilehash: 44b05ce6c028e79e489a94157f264fcedd63ea1a
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035474"
---
# <a name="sharepoint-online-data-deletion-in-office-365"></a>Suppression des données SharePoint Online dans Office 365

SharePoint Online stocke les objets en tant que code abstrait dans les bases de données d’application. Lorsqu’un utilisateur télécharge un fichier vers SharePoint Online, ce fichier est décomposé et converti en code d’application et stocké dans plusieurs tables sur plusieurs bases de données. Dans SharePoint Online, tout le contenu qu’un client télécharge est divisé en segments, chiffrés (éventuellement avec plusieurs clés AES 256 bits) et distribué dans le centre de données. Pour plus d’informations sur le processus de segmentation et de chiffrement, voir [chiffrement dans le Cloud Microsoft](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview). 

Dans SharePoint Online, les éléments sont conservés pendant 93 jours après leur suppression de leur emplacement d’origine. Elles restent dans la corbeille de site à l’heure entière, sauf si quelqu’un les supprime de cette corbeille ou la vide. Dans ce cas, les éléments sont placés dans la corbeille de la collection de sites, où ils restent pendant les 93 jours. Pour plus d’informations sur la restauration des éléments supprimés, voir [restaurer des éléments dans la corbeille d’un site SharePoint](https://support.office.com/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) et [restaurer des éléments supprimés de la corbeille de la collection de sites](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b). La durée de rétention de la Corbeille n’est pas configurable dans SharePoint Online.

Lorsque vous supprimez une collection de sites, vous supprimez également la hiérarchie des sites de la collection et tout le contenu qu’elles contiennent :

- les documents et bibliothèques de documents ;
- Listes et données de liste
- Paramètres de configuration de site
- Informations de rôle et de sécurité liées au site ou à ses sous-sites
- Sous-sites du site Web de niveau supérieur, leur contenu et les informations utilisateur

Si vous supprimez accidentellement une collection de sites, elle peut être restaurée par un administrateur global ou SharePoint à l’aide du centre d’administration SharePoint. 

La suppression matérielle se produit lorsqu’un utilisateur purge les éléments supprimés de la corbeille de la collection de sites, lorsque les périodes de rétention et de sauvegarde expirent, ou lorsqu’un administrateur supprime définitivement une collection de sites à l’aide de la [cmdlet Remove-spodeletedsit](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps). Quand un utilisateur supprime (supprime définitivement ou purge) le contenu de SharePoint Online, toutes les clés de chiffrement pour les segments supprimés sont également supprimées. Les blocs sur les disques qui stockaient les segments supprimés précédemment sont marqués comme inutilisés et disponibles pour une réutilisation.
