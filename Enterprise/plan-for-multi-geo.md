---
title: Plan de OneDrive pour l’entreprise Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Obtenir des informations sur les OneDrive pour les professionnels Multi-Geo, fonctionne multi-geo et quels emplacements de geo sont disponibles pour le stockage de données.
ms.openlocfilehash: d7d6cfbbff4cf0ec2516f2506946c2832d96b3f2
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>Plan de OneDrive pour l’entreprise Multi-Geo

Ce guide est conçu pour les administrateurs de sociétés nationales multiples (MNCs) qui préparent leurs clients SharePoint Online soit étendue à d’autres régions, conformément à la présence de l’entreprise afin de répondre aux exigences en matière de délégation de compétences de données.

Dans une configuration Multi OneDrive-Geo, vos clients Office 365 se compose d’un emplacement central (également connu sous le nom, l’emplacement par défaut) et un ou plusieurs emplacements de geo satellite. Il s’agit d’un client unique qui s’étend sur plusieurs emplacements de la zone géographique. Dans la OneDrive Multi-Geo, vos informations clients, notamment les sites géo, sont gravées dans Azure Active Directory (DAS). 

Voici quelques termes clés multi-geo pour vous aider à comprendre les concepts de base de la configuration :

-   **Clients** – représentation d’une entreprise dans le nuage Office 365 ayant généralement un ou plusieurs domaines lui sont associés (par exemple, http://contoso.sharepoint.com). 

-   **Emplacements de Geo** – les sites géographiques hébergeant les données de vos clients. Les locataires multi-geo s’étendent sur plus d’un emplacement géographique, par exemple, en Amérique du Nord et en Europe.

-   **Emplacements de données autorisé (ADL)** – l’emplacement géographique pour laquelle votre client a été configuré pour héberger des données OneDrive et SharePoint.

-   **Emplacement de données par défaut (LDP)** – l’emplacement géographique où sont stockées les données de OneDrive d’un utilisateur individuel. Cette option peut être définie par l’administrateur pour les emplacements de données autorisés qui ont été configurés pour le client. Notez que si vous modifiez le langage PDL pour un utilisateur qui possède déjà un site de OneDrive, leurs données OneDrive ne sont pas déplacées vers le nouvel emplacement géographique automatiquement. Pour plus d’informations, voir [déplacer une bibliothèque OneDrive géo - ailleurs](move-onedrive-between-geo-locations.md) .

L’activation Multi-Geo nécessite quatre étapes principales :

1.  Travailler avec votre équipe de compte à ajouter le plan de service _Multi-Geo des fonctionnalités dans Office 365_ .

2.  Choisissez votre souhaité de satellite géo emplacements et de les ajouter à vos clients.

3.  Définir l’emplacement de données par défaut de vos utilisateurs à l’emplacement géographique de satellite souhaité. Lorsqu’un nouveau site de OneDrive est fourni pour un utilisateur, il est mis en service à leur langage PDL.

4.  Migrer des sites OneDrive existants de vos utilisateurs à partir de l’emplacement d’origine vers leur emplacement par défaut des données en fonction des besoins.

Pour plus d’informations sur chacune de ces étapes, reportez-vous à la section [Configurer OneDrive pour entreprise Multi-Geo](multi-geo-tenant-configuration.md) .

> [!IMPORTANT]
> Notez que les fonctionnalités Multi-Geo d’Office 365 ne sont pas conçues pour les cas de l’optimisation des performances, ils sont conçus pour répondre aux exigences en matière de délégation de compétences de données. Pour plus d’informations sur l’optimisation des performances pour Office 365, voir [planification de réseau et de réglage des performances pour Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) , ou contactez votre service de support.

Vous pouvez configurer un des emplacements suivants soient satellite des emplacements géographique où vous pouvez héberger les fichiers OneDrive. Lorsque vous planifiez pour multi-geo, dressez la liste des emplacements que vous souhaitez ajouter à vos clients d’Office 365. Nous vous recommandons commençant par un ou deux emplacements de satellite, puis en développant progressivement à plusieurs emplacements de la zone géographique, si nécessaire.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Emplacement</strong></th>
<th align="left"><strong>Code</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Asie-Pacifique</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Europe / Moyen-Orient / Afrique</td>
<td align="left">EUROS</td>
</tr>
<tr class="odd">
<td align="left">Amérique du Nord</td>
<td align="left">NAM</td>
</tr>
<tr class="even">
<td align="left">Australie</td>
<td align="left">AUSTRALIE</td>
</tr>
<tr class="odd">
<td align="left">Canada</td>
<td align="left">POUVEZ</td>
</tr>
<tr class="odd">
<td align="left">Japon</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">Corée</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">Royaume-Uni</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

Emplacements géographiques à venir :
  
- France
- Inde

Lorsque vous configurez multi-geo, prenez permettent de consolider votre infrastructure sur site lors de la migration vers Office 365. Par exemple, si vous avez des batteries de serveurs sur site en Singapour et en Malaisie, puis vous pouvez consolider les à l’emplacement de satellite APC, sous réserve des exigences en matière de délégation de compétences de données permettent de le faire.

## <a name="best-practices"></a>Meilleures pratiques

Nous vous conseillons de créer un utilisateur test dans Office 365 pour procéder à des tests initiaux. Nous traiterons des étapes de test et la vérification avec cet utilisateur avant de procéder à des utilisateurs de production intégrée à la fonctionnalité OneDrive Multi-Geo.

Une fois que vous avez terminé les tests avec l’utilisateur test, sélectionnez un groupe pilote – par exemple à partir de votre service informatique – pour être le premier à utiliser OneDrive dans une nouveau géolocalisation. Pour ce premier groupe, sélectionnez les utilisateurs qui ne disposent pas encore d’un OneDrive. Nous vous recommandons de pas plus de cinq personnes de ce groupe initial et que vous développer progressivement le suivant une approche de déploiement par lot.

Chaque utilisateur doit disposer d’un *emplacement de données par défaut* (PDL) que Office 365 peut déterminer dans quel emplacement géographique à provisionner leur OneDrive. Emplacement de données par défaut de l’utilisateur doit correspondre à une de vos emplacements choisis satellite ou votre site central. Alors que le champ PDL n’est pas obligatoire, nous vous recommandons de définir que PDL pour tous les utilisateurs. Charges de travail d’un utilisateur sans PDL seront déployés dans l’emplacement central basé sur la logique de Multi-Geo.   

Créer une liste de vos utilisateurs et inclure leur nom d’utilisateur principal (UPN) et le code magasin de l’emplacement des données par défaut approprié. Inclure votre utilisateur de test et de votre groupe pilote initial commence. Vous aurez besoin de cette liste pour les procédures de configuration.

Si vos utilisateurs sont synchronisées à partir d’un système de Active Directory (AD) sur site pour Azure Active Directory (DAS), vous devez définir l’emplacement de données par défaut pour les utilisateurs synchronisés à l’aide d’Azure Active Directory se connecter. Impossible de configurer directement l’emplacement de données par défaut pour des utilisateurs synchronisés à l’aide de PowerShell d’AD Azure. Les étapes pour définir le langage PDL dans Active Directory et de le synchroniser sont couvertes dans [sync d’Azure Active Directory se connecter : configurer l’emplacement de données par défaut pour les ressources d’Office 365](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

L’administration d’un client multi-geo peut différer d’un client non-multi-geo, comme de nombreux paramètres SharePoint et OneDrive et les services sont multi-geo prenant en charge. Nous vous conseillons d’étudier [administration d’un environnement multi-geo](administering-a-multi-geo-environment.md) avant de poursuivre la configuration.

Pour plus d’informations sur l’expérience de vos utilisateurs finaux dans un environnement multi-geo, lire [l’expérience de l’utilisateur dans un environnement multgeo](multi-geo-user-experience.md) .

Pour démarrer la configuration OneDrive de Business Multi-Geo, consultez [Configurer OneDrive pour entreprise Multi-Geo](multi-geo-tenant-configuration.md).

Une fois que vous avez terminé la configuration, n’oubliez pas de [migration de bibliothèques de OneDrive vos utilisateurs](move-onedrive-between-geo-locations.md) que nécessaire pour que vos utilisateurs à partir de leurs emplacements de données par défaut.
