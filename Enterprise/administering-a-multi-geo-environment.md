---
title: Administration d’un environnement multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Obtenir des informations sur l’administration des services SharePoint et OneDrive dans un environnement multi-geo.
ms.openlocfilehash: 5d423fedc25b6e58ee84a51b01eb3858e6f198bb
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="administering-a-multi-geo-environment"></a>Administration d’un environnement multi-geo

Voici comment les services OneDrive et SharePoint fonctionnent dans un environnement multi-geo.

#### <a name="onedrive-administrator-experience"></a>Expérience de l’administrateur de OneDrive

Le [Centre admin de OneDrive](https://admin.onedrive.com) a un onglet **emplacements de la zone géographique** dans la navigation gauche quelles fonctionnalités un géo-emplacements mappent dans lequel vous pouvez afficher et gérer les emplacements de votre zone géographique. Utilisez cette page pour ajouter ou supprimer des emplacements geo pour vos clients.

#### <a name="taxonomy"></a>Taxonomie

Nous prend en charge une [taxonomie](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) de unifiée de métadonnées d’entreprise géré dans tous les magasins de géo, avec le maître hébergé dans l’emplacement central pour votre société. Nous vous conseillons gérez votre taxonomie globale à partir de l’emplacement central et ajoutez uniquement les termes spécifiques à l’emplacement à la taxonomie de l’emplacement géographique satellite. Termes de taxonomie globale seront synchronisées dans les emplacements de geo satellite.

#### <a name="sharing"></a>Partage

Les administrateurs peuvent définir et gérer les stratégies de partage pour chacun de leurs magasins. Les sites de OneDrive dans chaque emplacement géographique honorera seulement les correspondant geo partage des paramètres spécifiques. Par exemple, vous pouvez autoriser le [partage externe](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) pour votre site central, mais pas pour vos satellites emplacement et inversement. Pour OneDrive Multi-Geo, vous devez gérer vos paramètres de partage à chaque emplacement géographique comme elles ne sont pas synchronisées sur les clients.

Pour gérer le partage visite la page du [Centre d’administration OneDrive paramètres de partage](https://admin.onedrive.com/?v=SharingSettings) . Par défaut le partage externe est activé avec n’importe qui dans chaque emplacement de satellite.

#### <a name="user-profile-application"></a>Application de profil utilisateur

Il existe une [application de profil utilisateur](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) dans chaque emplacement géographique. Les informations de profil de chaque utilisateur sont hébergées dans leur emplacement géographique et est disponible à l’administrateur de cet emplacement géographique.

Si vous avez des propriétés de profil personnalisé, nous vous recommandons d’utiliser le même schéma de profil dans le monde entier et de remplir les propriétés de votre profil personnalisé dans tous les emplacements de la zone géographique ou lorsque cela est nécessaire.

#### <a name="bcs-secure-store-apps"></a>Applications BCS, banque d’informations sécurisé,

BCS, banque d’informations sécurisée et applications possèdent des instances de geo distinct, donc l’administrateur SharePoint Online doit gérer et configurer ces services à partir de chaque instance géographique où ils le souhaitent être présents.

#### <a name="security-and-compliance-admin-center"></a>Centre Admin de mise en conformité et de sécurité

Il existe un centre de conformité centralisé pour le locataire Multi-Geo : [Office 365 sécurité & centre de conformité](https://protection.office.com/?rfr=AdminCenter\#/homepage).

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Information Protection (IP) Prevention (DLP) stratégie DLP

Vous pouvez définir votre DLP IP stratégies de OneDrive pour l’entreprise dans le centre de sécurité et de conformité, portée des stratégies en fonction des besoins au locataire entier ou pour les utilisateurs concernés. Par exemple : Si vous souhaitez sélectionner une stratégie pour un utilisateur de OneDrive dans un emplacement de satellite, sélectionnez cette option pour appliquer la stratégie à un OneDrive spécifique et entrez les url de l’OneDrive. Pour obtenir des instructions générales lors de la création de stratégies DLP, consultez [vue d’ensemble des stratégies de prévention de perte de données](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) .

Les stratégies DLP sont synchronisés automatiquement en fonction de leur applicabilité dans chaque emplacement géographique.

Mise en œuvre de stratégies de prevention de perte de données et de Protection des informations à tous les utilisateurs dans un emplacement géographique n’est pas une option disponible dans l’interface utilisateur, à la place vous devez sélectionner les comptes de OneDrive applicables pour la stratégie ou appliquer globalement à tous les comptes de OneDrive.

#### <a name="ediscovery"></a>eDiscovery 

Par défaut, une e-Discovery Manager ou l’administrateur d’un client multi-geo sera en mesure de conduire eDiscovery uniquement dans l’emplacement central de ce client. Pour prendre en charge la possibilité de mener l’e-Discovery pour les emplacements de satellite, un nouveau paramètre de filtre de sécurité de la conformité, appelé « Region » est disponible via PowerShell.

L’administrateur Office 365 doit affecter des autorisations de gestionnaire d’e-Discovery pour permettre à d’autres utilisateurs à effectuer des e-Discovery et de lui attribuer un paramètre « Région » dans leur filtre de sécurité de la conformité applicables pour spécifier la région de conduite d’e-Discovery comme satellite emplacement, sinon qu'aucun eDiscovery ne se fera pour l’emplacement de satellite.

Lorsque le rôle de responsable ou l’administrateur d’e-Discovery est défini pour un emplacement particulier-geo, l’e-Discovery Manager ou administrateur uniquement pourront effectuer des actions de recherche d’e-Discovery contre les sites SharePoint et les sites de OneDrive que qui se trouve à cet emplacement géo. Si un administrateur ou un gestionnaire eDiscovery tente de rechercher des sites SharePoint ou OneDrive en dehors de la région déterminée, aucun résultats ne seront renvoyés. En outre, lorsque l’e-Discovery responsable ou administrateur pour une région déclenche une exportation, les données sont exportées vers l’instance Azure de cette région. Cela aide les entreprises à respecter les réglementations en ne permettant ne pas de contenu à exporter au-delà des frontières contrôlés.

> [!NOTE]
> S’il est nécessaire pour une e-Discovery Manager pour effectuer une recherche dans plusieurs régions de SharePoint, un autre compte d’utilisateur devez être créé pour l’e-Discovery Manager qui spécifie la zone secondaire où se trouvent les sites OneDrive ou SharePoint.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Prise en charge de multi-Geo Geo emplacements</strong></th>
<th align="left"><strong>e-Discovery pour les données exportées de SharePoint sera dans cet emplacement de données Blob d’Azure...</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>NAM</strong></td>
<td align="left">Les centres de données américains</td>
</tr>
<tr class="even">
<td align="left"><strong>EUROS</strong></td>
<td align="left">Les centres de données en Europe</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">Sud-est ou des centres de données d’Asie orientale</td>
</tr>
<tr class="even">
<td align="left"><strong>POUVEZ</strong></td>
<td align="left">Les centres de données américains</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUSTRALIE</strong></td>
<td align="left">Sud-est ou des centres de données d’Asie orientale</td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">Emplacement de données par défaut du locataire</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">Les centres de données en Europe</td>
</tr>
<tr class="even">
<td align="left"><strong>JPN</strong></td>
<td align="left">Sud-est ou des centres de données d’Asie orientale</td>
</tr>
</tbody>
</table>

Pour définir le filtre de sécurité de la conformité d’une région :

1.  Ouvrir Windows PowerShell

2.  Entrez   
    $s = New-PSSession - ConfigurationName Microsoft.Exchange - ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -$cred des informations d’identification-authentification base - AllowRedirection - SessionOption (nouveau-PSSessionOption - SkipCACheck - SkipCNCheck - SkipRevocationCheck)

    $un = Import-PSSession $s - AllowClobber  

3.  **Nouvelle-ComplianceSecurityFilter** **-Action** Tous les EnterTheNameYouWantToAssign de **NomFiltre -** **-région** EnterTheRegionParameter **-utilisateurs** EnterTheUserPrincipalName

    Par exemple : **ComplianceSecurityFilter-nouvelle-Action** tous les **NomFiltre -** NAMEDISCOVERYMANAGERS **-région** NAM **-utilisateurs** adwood@contosodemosx.onmicrosoft.com

Consultez l’article de la [Nouvelle-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) pour la syntaxe et les paramètres supplémentaires

#### <a name="audit-log-search"></a>Recherche de journal d’audit

Un unifiée [journal d’Audit](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) pour tous les emplacements de votre zone géographique est disponible à partir de la page de recherche de journal d’audit Office 365. Vous pouvez voir toutes les entrées de journal d’audit de sur des zones géographiques, par exemple, euros & nom géographique activités de l’utilisateur seront affiche dans une vue hiérarchique et vous pouvez ensuite appliquer des filtres existants pour voir les activités spécifiques de l’utilisateur.
