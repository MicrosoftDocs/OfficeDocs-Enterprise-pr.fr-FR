---
title: Déplacer un site de OneDrive à une autre géolocalisation
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Découvrez comment déplacer un site de OneDrive à un emplacement géographique différent.
ms.openlocfilehash: 7ce9106fa7d8d144f0f8935713b4df926a73fb6b
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Déplacer un site de OneDrive à une autre géolocalisation 

OneDrive geo déplacer, vous pouvez déplacer les OneDrive d’un utilisateur à un emplacement géographique différent. OneDrive geo déplacer est effectuée par l’administrateur SharePoint Online ou de l’administrateur Office 365. Avant de commencer une OneDrive geo déplacer, veillez à informer l’utilisateur, dont OneDrive est déplacé et vous recommandons de que les ferment tous les fichiers pour la durée du déplacement. (Si l’utilisateur dispose d’un document ouvert à l’aide du client Office pendant le déplacement, puis sur Déplacer achèvement le document devra être enregistré dans le nouvel emplacement.) Le déplacement peut être planifié à une date ultérieure, si vous le souhaitez.

Le service OneDrive utilise le stockage Blob Azure pour stocker le contenu. Le blob de stockage associé à OneDrive l’utilisateur est déplacé de la source à l’emplacement de destination géographique dans les quarante jours de destination OneDrive étant disponible pour l’utilisateur. L’accès à OneDrive l’utilisateur reprend dès que la destination OneDrive est disponible.

Au cours de la fenêtre de déplacer geo OneDrive (environ 2 à 6 heures) OneDrive de l’utilisateur a la valeur en lecture seule. L’utilisateur peut toujours accéder à leurs fichiers via le client de synchronisation de OneDrive ou de leur site de OneDrive dans SharePoint Online. Après déplacement de geo OneDrive, l’utilisateur sera automatiquement connecté à leur OneDrive à l’emplacement géographique de destination lorsqu’ils naviguent sur OneDrive dans le Lanceur d’applications Office 365. Le client de synchronisation commence automatiquement la synchronisation à partir du nouvel emplacement.

Les procédures décrites dans cet article requièrent le [PowerShell Module en ligne de Microsoft SharePoint](https://www.microsoft.com/en-us/download/details.aspx?id=35588).

## <a name="moving-a-onedrive-site"></a>Déplacement d’un site OneDrive

Pour effectuer une OneDrive geo déplacer, l’administrateur doit d’abord définir emplacement de données par défaut (PDL de l’utilisateur) pour l’emplacement géographique appropriée. Une fois le langage PDL, attendez au moins 24 heures pour la mise à jour PDL à synchroniser à travers les emplacements geo avant de commencer le déplacement de geo OneDrive.

Lorsque vous déplacez à l’aide de la zone géographique des applets de commande, se connecter au Service SPO chez l’utilisateur en cours OneDrive géographique, à l’aide de la syntaxe suivante :

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

Par exemple : pour déplacer les OneDrive de l’utilisateur 'Matt@contosoenergy.onmicrosoft.com', de se connecter au centre d’administration de SharePoint euros comme OneDrive de l’utilisateur est dans l’emplacement géographique d’euros :

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a>Validation de l’environnement

Avant de commencer un geo OneDrive déplacer, nous vous recommandons de valider l’environnement.

Pour vous assurer que tous les emplacements de la zone géographique sont compatibles, exécutez :

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

Si un OneDrive est sous scellé ou si elle contient un sous-site, il ne peut pas être déplacé. Vous pouvez utiliser l’applet de commande Start-SPOUserAndContentMove avec le paramètre - ValidationOnly à valider si l’OneDrive est en mesure d’être déplacés :

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

Ceci renverra une réussite si l’OneDrive est prête à être déplacée ou échouer s’il existe un ordre de retenue ou d’un sous-site qui peut empêcher le déplacement. Une fois que vous avez validé que le OneDrive est prêt à passer, vous pouvez démarrer le déplacement.

## <a name="start-a-onedrive-geo-move"></a>Démarrer un déplacement de geo OneDrive

Pour démarrer le déplacement, exécutez :  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

À l’aide de ces paramètres :

-   _UserPrincipalName_ – UPN de l’utilisateur, dont OneDrive est en cours de déplacement.

-   _DestinationDataLocation_ – emplacement géographique où le OneDrive doit être déplacé. Cette valeur doit être identique à l’emplacement de données par défaut de l’utilisateur.

> [!NOTE]
> Nous vous recommandons d’exécution `Get-SPOGeoMoveStateCompatibility` avec `ValidationOnly` avant de lancer OneDrive geo déplacer.

Par exemple, pour déplacer le OneDrive de matt@contosoenergy.onmicrosoft.com d’euros à l’Australie, exécutez :

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

Pour planifier un déplacement geo ultérieurement, utilisez un des paramètres suivants :

-   _PreferredMoveBeginDate_ – la volonté de déplacement susceptibles de commencer en ce moment spécifié. Temps doit être spécifié en temps universel coordonné (UTC).

-   _PreferredMoveEndDate_ – la volonté de déplacement susceptibles d’être terminée à cette heure spécifiée, de mieux. Temps doit être spécifié en temps universel coordonné (UTC). 

## <a name="cancel-a-onedrive-geo-move"></a>Annuler un déplacement de geo OneDrive 

Vous pouvez arrêter le déplacement géographique de, OneDrive l’utilisateur, si le déplacement n’est pas en cours ou complétés à l’aide de l’applet de commande :

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

_UserPrincipalName_ étant le nom UPN de l’utilisateur dont OneDrive déplacer que vous souhaitez arrêter.

## <a name="determining-current-status"></a>Détermination de l’état en cours

Vous pouvez vérifier l’état d’un OneDrive geo déplacer dans ou hors le geo auquel vous êtes connecté à l’aide de l’applet de commande Get-SPOUserAndContentMoveState.

Les statuts de déplacement sont décrits dans le tableau suivant.

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
<td align="left">Le déplacement n’a pas démarré.</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em>n</em>/4)</td>
<td align="left">Le déplacement est en cours dans un des états suivants : Validation (1/4), (2/4) de sauvegarde, restauration (3/4), nettoyage (4/4).</td>
</tr>
<tr class="odd">
<td align="left">Opération réussie</td>
<td align="left">Le déplacement a réussi.</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">Le déplacement a échoué.</td>
</tr>
</tbody>
</table>

Pour connaître l’état du déplacement d’un utilisateur spécifique, utilisez le paramètre UserPrincipalName :

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

Pour connaître l’état de tous les mouvements dans ou hors de l’emplacement géographique auquel vous êtes connecté, utilisez le paramètre MoveState avec l’une des valeurs suivantes : NotStarted, InProgress, réussite, échec, toutes les.

`Get-SPOUserAndContentMoveState -MoveState <value>`

Vous pouvez également ajouter la `-Verbose` paramètre pour obtenir une description plus détaillée de l’état du déplacement.

## <a name="user-experience"></a>Expérience de l'utilisateur

Les utilisateurs de OneDrive Notez perturbant si leur OneDrive est déplacé vers un emplacement géographique différent. En plus d’un état de lecture seule brève au cours du déplacement, les autorisations et les liens existants continueront à fonctionner comme prévu une fois le déplacement terminé.

### <a name="onedrive-for-business"></a>OneDrive for Business

Pendant le déplacement OneDrive de l’utilisateur a la valeur en lecture seule. Une fois le déplacement terminé, l’utilisateur est dirigé vers leur OneDrive dans le nouvel emplacement géographique lorsqu’ils naviguent pour OneDrive le Lanceur d’applications Office 365 ou un navigateur web.

### <a name="permissions-on-onedrive-content"></a>Autorisations sur le contenu de OneDrive

Les utilisateurs disposant d’autorisations sur le contenu de OneDrive continueront d’avoir accès au contenu au cours du déplacement, et une fois celle-ci terminée.

### <a name="onedrive-sync-client"></a>Client de synchronisation OneDrive 

Le client de synchronisation OneDrive détecte automatiquement et transférer en toute transparence la synchronisation vers le nouvel emplacement de OneDrive une fois le déplacement de geo OneDrive est terminé. L’utilisateur n’a pas besoin de signer de nouveau ou exécuter toute autre action.

Si un utilisateur met à jour un fichier alors que le déplacement de geo OneDrive est en cours, le client de synchronisation avertit les que les téléchargements de fichiers sont en attente pendant le déplacement.

### <a name="sharing-links"></a>Partage des liaisons 

Lors de la OneDrive geo déplacer achèvement, redirige automatiquement les liens partagés existants pour les fichiers qui ont été déplacés vers le nouvel emplacement géographique.

### <a name="onenote-experience"></a>Expérience de OneNote 

Client win32 de OneNote et UWP App (universel) détecte automatiquement et OneDrive geo déplacement en toute transparence de synchronisation portables vers le nouvel emplacement de OneDrive. L’utilisateur n’a pas besoin de signer de nouveau ou exécuter toute autre action. L’indicateur visible uniquement à l’utilisateur est la synchronisation de l’ordinateur portable échouent lorsque OneDrive geo déplacement est en cours. Cette expérience est disponible sur les versions de client OneNote suivantes :

-   OneNote win32 : Version 16.0.8326.2096 (ou version ultérieure)

-   OneNote UWP – Version 16.0.8431.1006 (ou version ultérieure)

-   OneNote Mobile Application – Version 16.0.8431.1011 (ou version ultérieure)

### <a name="teams-app"></a>Application des équipes

Lors de la OneDrive geo déplacer l’achèvement, les utilisateurs auront plus accès à leurs fichiers de OneDrive sur les équipes App, fichiers partagés via le chat d’équipes à partir de leur OneDrive avant le déplacement de geo continue de fonctionner après déplacement.

### <a name="onedrive-for-business-mobile-app-ios"></a>OneDrive pour l’entreprise Mobile application (iOS) 

Lors de la OneDrive geo déplacer l’achèvement, l’utilisateur devra se déconnecter et reconnecter sur iOS application Mobile à synchroniser avec le nouvel emplacement de OneDrive.

### <a name="existing-followed-groups-and-sites"></a>Existant suivi des sites et des groupes

Groupes et des sites visités seront afficheront dans la OneDrive de l’utilisateur pour les entreprises, quel que soit leur emplacement géographique. Sites et groupes hébergés dans un autre emplacement géographique seront ouvre dans un onglet séparé.
