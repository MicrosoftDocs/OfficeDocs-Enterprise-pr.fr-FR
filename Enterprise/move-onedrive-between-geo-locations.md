---
title: Déplacer un site OneDrive vers un autre emplacement géographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez comment déplacer un site OneDrive vers un autre emplacement géographique.
ms.openlocfilehash: 1197d23bdf94fe38ba24138ddde7c1f1fb92b41f
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931823"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Déplacer un site OneDrive vers un autre emplacement géographique 

Avec le déplacement géographique OneDrive, vous pouvez déplacer le site OneDrive d’un utilisateur vers un autre emplacement géographique. Le déplacement géographique OneDrive est effectué par l’administrateur SharePoint Online ou l’administrateur général Office 365. Avant de commencer un déplacement géographique OneDrive, veillez à informer l’utilisateur dont le site OneDrive va être déplacé et conseillez-lui de fermer tous les fichiers pendant la durée du déplacement. (Si l’utilisateur a un document ouvert à l’aide du client Office lors du déplacement, à la fin du déplacement, le document devra être enregistré dans le nouvel emplacement.) Le déplacement peut être planifié à un autre moment, le cas échéant.

Le service OneDrive utilise un Stockage Blob Azure pour stocker du contenu. Le blob Stockage associé au site OneDrive de l’utilisateur est déplacé de la source à l’emplacement géographique de destination dans les 40 jours qui suivent la mise à disposition du site OneDrive de destination à l’utilisateur. L’accès au site OneDrive de l’utilisateur est restauré dès que le site OneDrive de destination est disponible.

Pendant la durée du déplacement géographique du site OneDrive (environ 2 à 6 heures), le site OneDrive de l’utilisateur est défini en lecture seule. L’utilisateur peut toujours accéder à ses fichiers via le client de synchronisation OneDrive  ou son site OneDrive dans SharePoint Online. Une fois le déplacement géographique du site OneDrive terminé, l’utilisateur est connecté automatiquement à son site OneDrive à l’emplacement géographique de destination lorsqu’il navigue vers OneDrive dans le lanceur d’applications Office 365. Le client de synchronisation commence automatiquement la synchronisation à partir du nouvel emplacement.

Les procédures décrites dans cet article nécessitent le [module Microsoft SharePoint Online PowerShell](https://www.microsoft.com/en-us/download/details.aspx?id=35588).

## <a name="communicating-to-your-users"></a>Communication avec vos utilisateurs

Lors du déplacement de sites OneDrive entre différents emplacements géographiques, il est important de communiquer à vos utilisateurs ce à quoi ils doivent s’attendre. Cela peut vous aider à réduire la confusion des utilisateurs et diminuer le nombre d’appels à votre support technique. Prévenez vos utilisateurs par courriel avant le déplacement et faites-leur part des informations suivantes :

- La date de début prévue du déplacement et la durée attendue de l’opération.
- L’emplacement géographique vers lequel est déplacé leur espace OneDrive et l’URL permettant d’accéder au nouvel emplacement.
- Conseillez-leur de fermer leurs fichiers et de ne pas y apporter de modifications lors du déplacement.
- Le partage et les autorisations de fichiers ne sont modifiés par la migration.
- Présentez-leur l’[expérience utilisateur dans un environnement multigéographique](multi-geo-user-experience.md).

N’oubliez pas d’envoyer un courrier électronique à vos utilisateurs une fois le déplacement terminé pour les avertir qu’ils peuvent reprendre leur travail dans OneDrive.

## <a name="scheduling-onedrive-site-moves"></a>Planification de déplacements de site OneDrive

Vous pouvez planifier les déplacements de site OneDrive à l’avance (décrit plus loin dans cet article). Nous vous recommandons de commencer avec un petit nombre d’utilisateurs pour valider vos stratégies de communication et de flux de travail. Une fois que vous êtes habitué au processus, vous pouvez planifier des déplacements comme suit :

- Vous pouvez planifier jusqu’à 4 000 déplacements à la fois.
- Lorsque les déplacements commencent, vous pouvez planifier plus d’informations, avec un maximum de 4 000 déplacements dans la file d’attente et à un moment donné.
- Nous vous recommandons de ne pas planifier plus de 4 000 déplacements par mois.

## <a name="moving-a-onedrive-site"></a>Déplacement d’un site OneDrive

Pour effectuer un déplacement géographique OneDrive, l’administrateur client doit commencer par définir l’emplacement des données par défaut de l’utilisateur sur l’emplacement géographique approprié. Une fois que cet emplacement est défini, patientez au moins 24 heures pendant  la synchronisation de la mise à jour de l’emplacement des données par défaut sur les emplacements géographiques avant de commencer le déplacement géographique OneDrive.

Lorsque vous utilisez les cmdlets de déplacement géographique, connectez-vous au service SPO à l’emplacement géographique OneDrive actuel de l’utilisateur, à l’aide de la syntaxe suivante :

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

Par exemple : pour déplacer le site OneDrive de l’utilisateur ’Matt@contosoenergy.onmicrosoft.com’, connectez-vous au centre d’administration SharePoint EUR car le site OneDrive de l’utilisateur se trouve dans l’emplacement géographique EUR :

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![Capture d’écran d’une fenêtre PowerShell affichant la cmdlet connect-sposervice](media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>Validation de l’environnement

Avant de commencer un déplacement géographique OneDrive, nous vous recommandons de valider l’environnement.

Pour vous assurer que tous les emplacements géographiques sont compatibles, exécutez :

`Get-SPOGeoMoveCrossCompatibilityStatus`

Une liste de vos emplacements géographiques s’affichera et le contenu que vous pourrez déplacer entre ces emplacements sera marqué « Compatible ». Si la commande renvoie « Incompatible », réessayez de valider l’état plus tard.

Si un OneDrive contient, par exemple, un sous-site, il ne peut pas être déplacé. Vous pouvez utiliser la cmdlet Start-SPOUserAndContentMove avec le paramètre -ValidationOnly pour contrôler si le site OneDrive peut être déplacé :

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

Ceci renvoie Opération réussie si le site OneDrive est prêt à être déplacé ou Échec s’il existe une conservation légale ou un sous-site qui empêche le déplacement. Une fois que vous avez contrôlé que le site OneDrive est prêt à être déplacé, vous pouvez commencer le déplacement.

## <a name="start-a-onedrive-geo-move"></a>Démarrer un déplacement géographique OneDrive

Pour démarrer le déplacement, exécutez :  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

À l’aide de ces paramètres :

-   _UserPrincipalName_ : UPN de l’utilisateur dont le site OneDrive est déplacé.

-   _DestinationDataLocation_ : emplacement géographique dans lequel le site OneDrive doit être déplacé. Il doit être identique à l’emplacement des données par défaut de l’utilisateur.

> [!NOTE]
> Nous vous recommandons d’exécuter `Get-SPOGeoMoveStateCompatibility` avec `ValidationOnly` avant de lancer le déplacement géographique du site OneDrive.

Par exemple, pour déplacer le site OneDrive de matt@contosoenergy.onmicrosoft.com de l’emplacement EUR à AUS, exécutez :

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![Capture d’écran de la fenêtre PowerShell affichant la cmdlet Start-SPOUserAndContentMove](media/move-onedrive-between-geo-locations-image2.png)

Pour planifier un déplacement géographique à un autre moment, utilisez l’un des paramètres suivants :

-   _PreferredMoveBeginDate_ : le déplacement commencera probablement à l’heure spécifiée. L’heure doit être spécifiée en Temps universel coordonné (UTC).

-   _PreferredMoveEndDate_ : le déplacement se terminera probablement d’ici l’heure spécifiée, dans la mesure du possible. L’heure doit être spécifiée en Temps universel coordonné (UTC). 

## <a name="cancel-a-onedrive-geo-move"></a>Annuler un déplacement géographique OneDrive 

Vous pouvez arrêter le déplacement géographique du site OneDrive d’un utilisateur tant que le déplacement géographique n’est pas en cours ou terminé, en utilisant la cmdlet :

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

où _UserPrincipalName_ est l’UPN de l’utilisateur dont vous souhaitez arrêter le déplacement du site OneDrive.

## <a name="determining-current-status"></a>Déterminer l’état actuel

Vous pouvez vérifier l’état du déplacement géographique d’un site OneDrive à l’intérieur ou à l’extérieur de l’emplacement géographique auquel vous êtes connecté à l’aide de la cmdlet Get-SPOUserAndContentMoveState.

Ces états de déplacement sont décrits dans le tableau suivant.

<table>
<thead>
<tr class="header">
<th align="left"><strong>État</strong></th>
<th align="left"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">NotStarted</td>
<td align="left">Le déplacement n’a pas commencé.</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em>n</em>/4)</td>
<td align="left">Le déplacement est en cours dans l’un des états suivants : Validation (1/4), Sauvegarde (2/4), Restauration (3/4), Nettoyage (4/4).</td>
</tr>
<tr class="odd">
<td align="left">Opération réussie</td>
<td align="left">Le déplacement a réussi.</td>
</tr>
<tr class="even">
<td align="left">Échec</td>
<td align="left">Le déplacement a échoué.</td>
</tr>
</tbody>
</table>

Pour rechercher l’état du déplacement d’un utilisateur spécifique, utilisez le paramètre UserPrincipalName :

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

Pour rechercher l’état de tous les déplacements à l’intérieur ou à l’extérieur de l’emplacement géographique auquel vous êtes connecté, utilisez le paramètre MoveState avec l’une des valeurs suivantes : NotStarted, InProgress, Success, Failed, All.

`Get-SPOUserAndContentMoveState -MoveState <value>`

Vous pouvez également ajouter le paramètre `-Verbose` pour des descriptions plus détaillées de l’état de déplacement.

## <a name="user-experience"></a>Expérience de l’utilisateur

Les utilisateurs de OneDrive devraient observer des perturbations minimales si leur site OneDrive est déplacé vers un autre emplacement géographique. Excepté un état de lecture seule bref lors du déplacement, les autorisations et liens existants continueront à fonctionner comme prévu une fois le déplacement terminé.

### <a name="onedrive-for-business"></a>OneDrive Entreprise

Lorsque le déplacement est en cours, le site OneDrive de l’utilisateur est défini en lecture seule. Une fois le déplacement terminé, l’utilisateur est dirigé vers son site OneDrive dans le nouvel emplacement géographique lorsqu’il navigue vers OneDrive dans le lanceur d’applications Office 365 ou un navigateur web.

### <a name="permissions-on-onedrive-content"></a>Autorisations sur le contenu OneDrive

Les utilisateurs disposant d’autorisations sur le contenu OneDrive auront toujours accès au contenu pendant le déplacement et une fois qu’il est terminé.

### <a name="onedrive-sync-client"></a>Client de synchronisation OneDrive 

Le client de synchronisation OneDrive détecte automatiquement la synchronisation avec le nouvel emplacement OneDrive et la transfère en toute transparence une fois le déplacement géographique de OneDrive terminé. L’utilisateur n’a pas besoin de se connecter à nouveau, ni d’effectuer une autre action. (Version 17.3.6943.0625 ou ultérieure du client de synchronisation requise.)

Si un utilisateur met à jour un fichier pendant le déplacement géographique de OneDrive, le client de synchronisation l’informe que des téléchargements de fichiers sont en attente pendant le déplacement.

### <a name="sharing-links"></a>Liens de partage 

Lorsque le déplacement géographique de OneDrive est terminé, les liens partagés existants pour les fichiers qui ont été déplacés redirigent automatiquement vers le nouvel emplacement géographique.

### <a name="onenote-experience"></a>Expérience OneNote 

Le client OneNote win32 client et l’application UWP (universelle) détecteront automatiquement et synchroniseront en toute transparence les blocs-notes avec le nouvel emplacement OneDrive à la fin du déplacement géographique de OneDrive. L’utilisateur n’a pas besoin de se connecter à nouveau ou d’effectuer une autre action. Le seul indicateur visible pour l’utilisateur est l’échec de la synchronisation des blocs-notes lorsque le déplacement géographique de OneDrive est en cours. Cette expérience est disponible sur les versions de client OneNote suivantes :

-   OneNote win32 – Version 16.0.8326.2096 (et versions ultérieures)

-   OneNote UWP – Version 16.0.8431.1006 (et versions ultérieures)

-   Application mobile OneNote : Version 16.0.8431.1011 (et versions ultérieures)

### <a name="teams-app"></a>Application Teams

Lorsque le déplacement géographique de OneDrive est terminé, les utilisateurs ont accès à leurs fichiers OneDrive sur l’application Teams. En outre, les fichiers partagés via la conversation Teams de leur site OneDrive avant le déplacement géographique continuent à fonctionner après le déplacement.

### <a name="onedrive-for-business-mobile-app-ios"></a>Application mobile OneDrive Entreprise (iOS) 

Lorsque le déplacement géographique de OneDrive est terminé, l’utilisateur doit se déconnecter et se reconnecter sur l’application mobile iOS pour réaliser la synchronisation avec le nouvel emplacement OneDrive.

### <a name="existing-followed-groups-and-sites"></a>Sites et groupes suivis existants

Les sites et groupes suivis apparaissent dans OneDrive Entreprise de l’utilisateur indépendamment de leur emplacement géographique. Les sites et groupes hébergés dans un autre emplacement géographique s’ouvrent dans un onglet distinct.
