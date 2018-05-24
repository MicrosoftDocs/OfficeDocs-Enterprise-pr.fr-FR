---
title: Planification de OneDrive Entreprise Multi-Géo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez OneDrive Entreprise Multi-Géo, son fonctionnement et les emplacements géographiques disponibles pour le stockage des données.
ms.openlocfilehash: 54efc6092338e505ef44344f9c3d3a7efe9ae498
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>Planification de OneDrive Entreprise Multi-Géo

Ce guide est conçu pour les administrateurs des entreprises multinationales qui préparent le déploiement de leur client SharePoint Online dans des emplacements géographiques supplémentaires en fonction de la présence de l’entreprise pour répondre aux exigences de résidence.

Dans une configuration OneDrive Multi-Géo, votre client Office 365 est constitué d’un emplacement central (également appelé emplacement par défaut) et d’un ou plusieurs emplacements géographiques satellites. Il s’agit d’un client unique déployé sur plusieurs emplacements géographiques. Dans OneDrive Multi-Géo, vos informations de client, y compris les emplacements géographiques, sont gérées dans Azure Active Directory (AAD). 

Voici des termes géographiques clés pour vous aider à comprendre les concepts de base de la configuration :

-   **Client** : représentation d’une organisation dans le cloud Office 365 qui a généralement un ou plusieurs domaines qui lui sont associés (par exemple, http://contoso.sharepoint.com). 

-   **Emplacements géographiques** : emplacements géographiques où sont hébergées les données de votre client. Les clients multigéographiques sont déployés sur plusieurs emplacements géographiques (par exemple, en Amérique du Nord et en Europe).

-   **Emplacements de données autorisés** : les emplacements géographiques pour lesquels votre client a été configuré pour héberger des données OneDrive et SharePoint.

-   **Emplacement de données par défaut** : l’emplacement géographique où les données OneDrive d’un utilisateur individuel sont stockées. Il peut être défini par l’administrateur sur l’un des emplacements de données autorisés configurés pour le client. Notez que si vous changez l’emplacement de données par défaut d’un utilisateur qui possède déjà un site OneDrive, ses données OneDrive ne sont pas déplacées vers le nouvel emplacement géographique automatiquement. Reportez-vous à l’article relatif au [déplacement d’une bibliothèque OneDrive vers un autre emplacement géographique](move-onedrive-between-geo-locations.md) pour plus d’informations.

L’activation Multi-Géo requiert quatre étapes principales :

1.  Travailler avec votre équipe de compte pour ajouter le plan de services des _fonctionnalités multigéographiques dans Office 365_.

2.  Choisir des emplacements géographiques satellites et les ajouter à votre client.

3.  Définir l’emplacement de données par défaut de vos utilisateurs sur l’emplacement géographique satellite souhaité. Lorsqu’un nouveau site OneDrive est configuré pour un utilisateur, il est configuré pour ses emplacements de données par défaut.

4.  Déplacer les sites OneDrive existants de vos utilisateurs de l’emplacement initial vers leur emplacement de données par défaut, selon vos besoins.

Reportez-vous à la [configuration de OneDrive Entreprise Multi-Géo](multi-geo-tenant-configuration.md) pour plus d’informations sur chacune de ces étapes.

> [!IMPORTANT]
> Notez que les fonctionnalités multigéographiques d’Office 365 ne sont pas conçues pour des cas d’optimisation des performances. Elles sont conçues pour répondre aux exigences de résidence des données. Pour plus d’informations sur l’optimisation des performances pour Office 365, reportez-vous à l’article relatif à la [planification réseau et à l’optimisation des performances pour Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou contactez votre groupe de support.

Vous pouvez configurer les emplacements géographiques satellites suivants où vous pouvez héberger les fichiers OneDrive. Lorsque vous planifiez Multi-Géo, créez une liste des emplacements à ajouter à votre client Office 365. Nous vous recommandons de commencer avec un ou deux emplacements satellites puis de déployer progressivement sur d’autres emplacements géographiques, si nécessaire.

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
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">Amérique du Nord</td>
<td align="left">NAM</td>
</tr>
<tr class="even">
<td align="left">Australie</td>
<td align="left">AUS</td>
</tr>
<tr class="odd">
<td align="left">Canada</td>
<td align="left">CAN</td>
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

Lorsque vous configurez Multi-Géo, envisagez de consolider votre infrastructure locale lors de la migration vers Office 365. Par exemple, si vous avez des batteries de serveurs locales à Singapour et en Malaisie, vous pouvez les consolider avec l’emplacement satellite APC, à condition que les exigences de résidence des données vous permettent de le faire.

## <a name="best-practices"></a>Meilleures pratiques

Nous vous recommandons de créer un utilisateur test dans Office 365 pour effectuer des tests initiaux. Nous allons passer en revue quelques étapes de test et de vérification avec cet utilisateur avant d’intégrer des utilisateurs de production dans la fonction OneDrive Multi-Géo.

Une fois que vous avez terminé les tests avec l’utilisateur test, sélectionnez un groupe pilote (éventuellement de votre service informatique) qui sera le premier à utiliser OneDrive dans un nouvel emplacement géographique. Pour ce premier groupe, sélectionnez les utilisateurs qui ne possèdent pas encore un OneDrive. Nous vous recommandons de ne pas sélectionner plus de cinq personnes dans ce groupe initial et de le développer progressivement à l’aide d’une approche de déploiement par lot.

Chaque utilisateur doit disposer d’un *emplacement de données par défaut* (PDL) défini afin qu’Office 365 puisse déterminer dans quel emplacement géographique configurer son OneDrive. L’emplacement de données par défaut de l’utilisateur doit correspondre à l’un de vos emplacements satellites choisis ou à votre emplacement central. Le champ PDL n’est pas obligatoire, mais nous vous recommandons de définir un PDL pour tous les utilisateurs. Les charges de travail d’un utilisateur sans PDL seront configurées dans l’emplacement central en fonction de la logique Multi-Géo.   

Créez une liste de vos utilisateurs et incluez leur nom d’utilisateur principal (UPN) et le code de l’emplacement des données par défaut approprié. Incluez votre utilisateur test et votre groupe pilote initial pour commencer. Vous aurez besoin de cette liste pour les procédures de configuration.

Si vos utilisateurs sont synchronisés à partir d’un système Active Directory (AD) local avec Azure Active Directory (AAD), vous devez définir l’emplacement de données par défaut pour les utilisateurs synchronisés à l’aide d’Azure Active Directory Connect. Vous ne pouvez pas configurer directement l’emplacement des données par défaut pour les utilisateurs synchronisés à l’aide d’Azure AD PowerShell. Les étapes à suivre pour configurer le PDL dans AD et le synchroniser sont décrites dans l’article [Synchronisation Azure Active Directory Connect : configurer un emplacement de données par défaut pour les ressources Office 365](https://docs.microsoft.com/fr-FR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

L’administration d’un client multigéographique peut être différente de celle d’un client non multigéographique, car de nombreux services et paramètres SharePoint et OneDrive sont adaptés à un environnement multigéographique. Nous vous recommandons de consulter l’article relatif à l’[administration d’un environnement multi-géographique](administering-a-multi-geo-environment.md) avant de poursuivre votre configuration.

Lisez l’article [Expérience utilisateur dans un environnement multigéographique](multi-geo-user-experience.md) pour plus d’informations sur l’expérience de vos utilisateurs finaux dans un environnement multigéographique.

Pour démarrer la configuration de OneDrive Entreprise Multi-Géo, reportez-vous à la [configuration de OneDrive Entreprise Multi-Géo](multi-geo-tenant-configuration.md).

Une fois que vous avez terminé la configuration, n’oubliez pas de [migrer les bibliothèques OneDrive de vos utilisateurs](move-onedrive-between-geo-locations.md) pour permettre à vos utilisateurs de travailler depuis leur emplacement de données par défaut.
