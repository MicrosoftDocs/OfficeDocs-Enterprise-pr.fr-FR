---
title: 'Circonscrire le contenu des sites '
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez comment circonscrire des sites SharePoint à un emplacement géographique spécifique dans un environnement multigéographique.
ms.openlocfilehash: ca63f46ba45d1b3ddfdf4f676b678d62387b801f
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "41973956"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>Circonscrire le contenu des sites 

Dans certaines circonstances, vous pouvez imposer qu’un site et les fichiers qu’il contient restent dans l’emplacement géographique où le site a été créé, soit en empêchant le déplacement du site, soit en empêchant la mise en cache des fichiers qu’il contient dans un autre emplacement géographique.

Pour ce faire, vous pouvez utiliser la cmdlet [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) avec le paramètre **RestrictedToGeo**. La valeur par défaut de ce paramètre est NULL, mais vous pouvez la remplacer par l’une des valeurs suivantes :

|Restriction|Description|
|:----------|:----------|
|NoRestriction|Le site peut être déplacé vers un autre emplacement géographique.|
|BlockMoveOnly|Le site ne peut pas être déplacé vers un autre emplacement géographique, mais son contenu peut être mis en cache dans d’autres emplacements géographiques.|
|BlockFull|Le site ne peut pas être déplacé vers un autre emplacement géographique, et les fichiers qu’il contient ne sont pas mis en cache dans d’autres emplacements géographiques. Les titres (extraits du contenu), les noms et d’autres propriétés des fichiers peuvent toujours être mis en cache dans d’autres emplacements géographiques.<br>Le contenu stocké sur le site avant la définition du paramètre RestrictedToGeo sur BlockFull peut rester en cache dans d’autres emplacements géographiques.|

Utilisez la syntaxe suivante :

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

Par exemple :

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
