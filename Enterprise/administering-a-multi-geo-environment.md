---
title: Administration d’un environnement multigéographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez comment administrer des services SharePoint et OneDrive dans un environnement multigéographique.
ms.openlocfilehash: 823b3a4c1d063a4d398b7f734c2171e856ee1244
ms.sourcegitcommit: 4a1d6c43da44b559136f2bf422a531bea5f48dbb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2018
ms.locfileid: "27210122"
---
# <a name="administering-a-multi-geo-environment"></a>Administration d’un environnement multigéographique

Découvrez le fonctionnement des services OneDrive et SharePoint dans un environnement multigéographique.

#### <a name="onedrive-administrator-experience"></a>Expérience de l’administrateur OneDrive

Dans le [Centre d’administration OneDrive](https://admin.onedrive.com), l’onglet **Emplacements géographiques** dans le volet de navigation gauche présente une carte où vous pouvez afficher et gérer vos emplacements géographiques. Utilisez cette page pour ajouter ou supprimer des emplacements géographiques pour votre client.

#### <a name="taxonomy"></a>Taxonomie

Nous prenons en charge une [taxonomie](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unifiée pour gérer les métadonnées dans l’entreprise à différents emplacements géographiques ; les données de référence étant hébergées à l’emplacement central de votre entreprise. Nous vous recommandons de gérer votre taxonomie globale à partir de l’emplacement central et d’ajouter uniquement des termes spécifiques à la taxonomie de l’emplacement satellite. Les termes de la taxonomie globale sont synchronisés avec les emplacements satellites.

#### <a name="sharing"></a>Partage

Les administrateurs peuvent définir et gérer les stratégies de partage pour chaque emplacement. Les sites OneDrive de chaque emplacement géographique respectent uniquement les paramètres de partage associés à un emplacement géographique précis. (Par exemple, vous pouvez autoriser le [partage externe](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) pour votre emplacement central, mais pas pour votre emplacement satellite, et inversement.) Notez que les paramètres de partage ne vous permettent pas de configurer les limites de partage entre emplacements géographiques.

Pour OneDrive Multi-Géo, vos paramètres de partage doivent être gérés à chaque emplacement géographique car ils ne sont pas synchronisés sur le client. Pour gérer les paramètres de partage, rendez-vous sur le [Centre d’administration OneDrive](https://admin.onedrive.com/?v=SharingSettings). Par défaut, le partage externe est activé pour Tout le monde, dans chaque emplacement satellite.

#### <a name="user-profile-application"></a>Application de profil utilisateur

Il existe une [application de profil utilisateur](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) dans chaque emplacement géographique. Les informations de chaque profil utilisateur sont hébergées dans leur emplacement géographique et accessibles par l’administrateur de cet emplacement.

Si vous avez des propriétés de profil personnalisées, nous vous recommandons d’utiliser le même schéma de profil dans toutes les zones géographiques et de remplir vos propriétés de profil personnalisées dans tous les emplacements géographiques ou dans les emplacements requis. Pour savoir comment remplir les données de profil utilisateur par programme, consultez l’[API de mise à jour en bloc de profil utilisateur](https://docs.microsoft.com/fr-FR/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

#### <a name="bcs-secure-store-apps"></a>BCS, service Banque d’informations sécurisé, applications

BCS, le service Banque d’informations sécurisé et les applications ont des instances distinctes dans chaque emplacement satellite. Ainsi, l’administrateur SharePoint Online doit gérer et configurer ces services séparément à partir de chaque emplacement satellite.

#### <a name="security-and-compliance-admin-center"></a>Centre de sécurité et conformité

Il existe un centre de conformité central pour le client multigéographique : [Centre de sécurité et conformité Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Stratégies de protection contre la perte de données (DLP) et de protection des informations (IP)

Vous pouvez définir vos stratégies DLP et IP pour OneDrive Entreprise dans le Centre de sécurité et conformité, en configurant l’étendue de vos stratégies selon vos besoins, pour tout le client ou pour certains utilisateurs. Par exemple, pour sélectionner une stratégie à appliquer à un utilisateur OneDrive dans un emplacement satellite, sélectionnez la stratégie et entrez l’URL OneDrive de l’utilisateur. Pour en savoir plus sur la création des stratégies DLP, consultez l’article [Vue d’ensemble des stratégies de protection contre la perte de données](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e).

Les stratégies DLP sont synchronisées automatiquement en fonction de leurs conditions d’application à chaque emplacement géographique.

Dans l’interface utilisateur, il est impossible d’appliquer des stratégies de protection contre la perte de données et de protection des informations à tous les utilisateurs d’un emplacement géographique. À la place, sélectionnez les comptes OneDrive concernés par la stratégie ou appliquez la stratégie globalement à tous les comptes OneDrive.

#### <a name="ediscovery"></a>eDiscovery 

Par défaut, un gestionnaire ou un administrateur eDiscovery d’un client multigéographique peut mettre en place un processus eDiscovery uniquement dans l’emplacement central de ce client. Pour pouvoir mettre en place un processus eDiscovery dans les emplacements satellites, il existe un nouveau paramètre Filtre de sécurité de conformité appelé « Région » dans PowerShell.

L’administrateur général Office 365 doit affecter les autorisations de gestionnaire eDiscovery pour autoriser d’autres personnes à mettre en place un processus eDiscovery, et affecter un paramètre « Région » dans le filtre de sécurité de conformité correspondant pour définir la région concernée par le processus comme emplacement satellite. Sinon, aucun processus eDiscovery n’est mis en place à l’emplacement satellite.

Quand un gestionnaire ou un administrateur eDiscovery est défini pour un emplacement satellite particulier, ce gestionnaire ou cet administrateur eDiscovery peut uniquement effectuer des actions de recherche eDiscovery dans les sites SharePoint et OneDrive situés dans cet emplacement satellite. Si un gestionnaire ou un administrateur eDiscovery tente de rechercher des sites SharePoint ou OneDrive en dehors de l’emplacement satellite spécifié, aucun résultat n’est renvoyé. Par ailleurs, lorsque le gestionnaire ou l’administrateur eDiscovery d’un emplacement satellite déclenche une exportation, les données sont exportées vers l’instance Azure de cette région. Ainsi, les entreprises respectent les règles de conformité en interdisant l’exportation de contenu au-delà de frontières contrôlées.

> [!NOTE]
> Si un gestionnaire eDiscovery doit effectuer des recherches dans plusieurs emplacements satellites SharePoint, un autre compte d’utilisateur doit être créé pour ce gestionnaire, lequel doit indiquer un autre emplacement satellite où sont situés les sites OneDrive ou SharePoint.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Emplacements multigéographiques pris en charge</strong></th>
<th align="left"><strong>Emplacement Blob Azure où les données eDiscovery pour SharePoint exportées seront stockées</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">Centres de données situés en Asie de l’Est ou du Sud-Est</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUS</strong></td>
<td align="left">Centres de données situés en Asie de l’Est ou du Sud-Est</td>
</tr>
<tr class="even">
<td align="left"><strong>CAN</strong></td>
<td align="left">Centres de données situés aux États-Unis</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">Centres de données situés en Europe</td>
</tr>
<tr class="odd">
<td align="left"><strong>FRA</strong></td>
<td align="left">Centres de données situés en Europe</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">Centres de données situés en Europe</td>
</tr>
<tr class="even">
<td align="left"><strong>IND</strong></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">Centres de données situés en Asie de l’Est ou du Sud-Est</td>
</tr>
<tr class="even">
<td align="left"><strong>JPN </strong></td>
<td align="left">Centres de données situés en Asie de l’Est ou du Sud-Est</td>
</tr>
<tr class="odd">
<td align="left"><strong>NAM</strong></td>
<td align="left">Centres de données situés aux États-Unis</td>
</tr>
</tbody>
</table>

Pour définir le filtre de sécurité de conformité pour une région :

1.  Ouvrez Windows PowerShell

2.  Entrez   
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName

    Par exemple : **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

Consultez l’article [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) pour en savoir plus sur la syntaxe et les paramètres supplémentaires.

#### <a name="audit-log-search"></a>Recherche de journal d’audit

Un [journal d’audit](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) unifié pour tous vos emplacements satellites est disponible sur la page de recherche du journal d’audit Office 365. Vous pouvez voir toutes les entrées du journal d’audit de plusieurs emplacements géographiques. Par exemple, les activités des utilisateurs dans les régions NAM et EUR apparaissent dans un seul affichage et vous pouvez appliquer les filtres existants pour afficher les activités de certains utilisateurs uniquement.
