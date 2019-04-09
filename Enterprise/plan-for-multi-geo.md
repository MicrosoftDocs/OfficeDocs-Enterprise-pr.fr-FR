---
title: Planifier le déploiement d’Office 365 multigéographique
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Découvrez Office 365 multigéographique, comment opèrent les fonctionnalités multigéographiques et les emplacements géographiques disponibles pour le stockage de données.
ms.openlocfilehash: 4f7905c55cbb926978a43d70300a70d451512f6f
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931793"
---
# <a name="plan-for-office-365-multi-geo"></a>Planifier le déploiement d’Office 365 multigéographique

Ce guide est conçu pour les administrateurs d’entreprises multinationales qui préparent le déploiement de leur locataire Office 365 dans des emplacements géographiques supplémentaires en fonction de la présence de l’entreprise pour répondre aux exigences de résidence des données.

Dans une configuration multigéographique, votre locataire Office 365 se compose d’un emplacement central et d’un ou plusieurs emplacements satellites. Il s’agit d’un même locataire s’étendant sur plusieurs emplacements géographiques. Les informations de votre locataire, y compris les emplacements géographiques, sont gérées dans Azure Active Directory (Azure AD).

Voici quelques termes géographiques clés pour vous aider à comprendre les concepts de base de la configuration :

-   **Locataire** : représentation d’une organisation dans Office 365 à laquelle sont généralement associés un ou plusieurs domaines (par exemple, http://contoso.sharepoint.com)). 

-   **Emplacements géographiques** : emplacements géographiques disponibles pour héberger des données dans un locataire Office 365.

-   **Emplacements satellites** : emplacements géographiques supplémentaires que vous avez configurées pour héberger des données dans votre locataire Office 365. Les locataires multigéographiques s’étendent sur plus d’un emplacement géographique, par exemple, l’Amérique du Nord et l’Europe.

-   **Emplacement par défaut des données** : emplacement géographique où sont stockées les données Exchange et OneDrive d’un utilisateur individuel. L’administrateur peut définir cette valeur sur l’un des emplacements géographiques configurés pour le locataire. Notez que si vous modifiez l’emplacement par défaut des données pour un utilisateur disposant déjà d’un site OneDrive, les données OneDrive de celui-ci ne sont déplacées automatiquement vers le nouvel emplacement géographique. Pour plus d’informations, voir [Déplacer une bibliothèque OneDrive vers un autre emplacement géographique](move-onedrive-between-geo-locations.md). Si l’utilisateur dispose d’une boîte aux lettres Exchange, celle-ci est automatiquement déplacée vers le nouvel emplacement par défaut des données.

L’activation Multi-Géo requiert quatre étapes principales :

1.  Travailler avec votre équipe de compte pour ajouter le plan de services des _fonctionnalités multigéographiques dans Office 365_.

2.  Choisir des emplacements satellites et les ajouter à votre client.

3.  Définir l’emplacement par défaut des données de vos utilisateurs sur l’emplacement satellite souhaité. Lors de l’approvisionnement d’un nouveau site OneDrive ou d’une nouvelle boîte aux lettres Exchange pour un utilisateur, ces éléments sont approvisionnés à l’emplacement par défaut des données de cet utilisateur.

4.  Migrer les sites OneDrive existants de vos utilisateurs de l’emplacement central vers leurs emplacements par défaut des données, selon les besoins (les boîtes aux lettres Exchange sont migrées automatiquement lors de la définition de l’emplacement par défaut des données d’un utilisateur).

Pour plus d’informations sur chacune de ces étapes, voir [Configurer Office 365 multigéographique](multi-geo-tenant-configuration.md).

> [!IMPORTANT]
> Notez qu’Office 365 multigéographique n’est pas conçu pour optimiser les performances, mais pour répondre aux exigences de résidence des données. Pour plus d’informations sur l’optimisation des performances pour Office 365, voir [Planification réseau et optimisation des performances pour Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) ou contacter votre groupe de support.

Vous pouvez configurer n’importe lequel des emplacements suivants en tant qu’emplacements satellite dans lequel héberger des sites OneDrive et SharePoint, ainsi que des boîtes aux lettres Exchange. Lorsque vous planifiez une configuration multigéographique, dressez la liste des emplacements que vous voulez ajouter à votre locataire Office 365. Nous vous recommandons de commencer avec un ou deux emplacements satellites, puis d’étendre progressivement la configuration à d’autres emplacements géographiques si nécessaire.

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

Lorsque vous configurez Multi-Géo, envisagez de consolider votre infrastructure locale lors de la migration vers Office 365. Par exemple, si vous avez des batteries de serveurs locales à Singapour et en Malaisie, vous pouvez les consolider avec l’emplacement satellite APC, à condition que les exigences de résidence des données vous permettent de le faire.

## <a name="best-practices"></a>Meilleures pratiques

Nous vous recommandons de créer un utilisateur de test dans Office 365 pour effectuer certains tests initiaux. Nous allons effectuer quelques étapes de test et de vérification avec cet utilisateur avant de passer aux utilisateurs en production dans Office 365 multigéographique.

Une fois les tests avec l’utilisateur de test terminés, sélectionnez un groupe pilote (par exemple, dans votre service informatique) qui sera le premier à utiliser OneDrive et Exchange dans un nouvel emplacement géographique. Pour ce premier groupe, sélectionnez des utilisateurs qui n’ont pas encore de OneDrive. Nous vous recommandons de limiter ce groupe initial à cinq personnes et de l’étoffer progressivement en suivant une approche de déploiement par lots.

Chaque utilisateur doit disposer d’un *emplacement par défaut des données* défini afin qu’Office 365 puisse déterminer l’emplacement géographique dans lequel approvisionner leur OneDrive. L’emplacement par défaut des données de l’utilisateur doit correspondre à l’un de vos emplacements satellites choisis ou à votre emplacement central. Si le champ d’emplacement par défaut des données n’est pas obligatoire, nous vous recommandons de définir un emplacement par défaut des données pour tous les utilisateurs. Les charges de travail d’un utilisateur dépourvu d’emplacement par défaut des données sont approvisionnées dans l’emplacement central.

Dressez la liste de vos utilisateurs en incluant leur nom d’utilisateur principal (UPN) et le code de l’emplacement par défaut des données approprié. Incluez votre utilisateur de test et votre groupe pilote initial. Vous aurez besoin de cette liste pour les procédures de configuration.

Si vos utilisateurs sont synchronisés à partir d’un système Active Directory local sur Azure Active Directory, vous devez définir l’emplacement par défaut des données en tant qu’attribut Active Directory et le synchroniser à l’aide d’Azure Active Directory Connect. Vous ne pouvez pas configurer directement l’emplacement par défaut des données pour des utilisateurs synchronisés à l’aide d’Azure AD PowerShell. Les étapes de configuration d’un emplacement par défaut des données et de synchronisation de celui-ci dans Active Directory sont décrites dans [Synchronisation Azure Active Directory Connect : Configurer un emplacement de données par défaut pour les ressources Office 365](https://docs.microsoft.com/fr-FR/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

L’administration d’un client multigéographique peut être différente de celle d’un client non multigéographique, car de nombreux services et paramètres SharePoint et OneDrive sont adaptés à un environnement multigéographique. Nous vous recommandons de consulter l’article relatif à l’[administration d’un environnement multi-géographique](administering-a-multi-geo-environment.md) avant de poursuivre votre configuration.

Pour plus d’informations sur l’expérience de vos utilisateurs finaux dans un environnement multigéographique, voir [Expérience utilisateur dans un environnement multigéographique](multi-geo-user-experience.md).

Pour commencer à configurer Office 365 multigéographique, voir [Configurer Office 365 multigéographique](multi-geo-tenant-configuration.md).

Une fois que vous avez terminé la configuration, n’oubliez pas de [migrer les bibliothèques OneDrive de vos utilisateurs](move-onedrive-between-geo-locations.md) pour permettre à ceux-ci de travailler à partir de leur emplacement par défaut des données.
