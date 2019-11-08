---
title: Limites des sites portail modernes SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/9/2019
audience: Admin
ms.topic: interactive-tutorial
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
description: Découvrez les recommandations en matière de performances pour les sites modernes dans SharePoint Online.
ms.openlocfilehash: 2ff7f76a943563644403f3df2b6b0a6ee9b28d53
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031269"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>Limites des sites portail modernes SharePoint Online

Cet article fournit des recommandations en matière de performances pour les sites portail modernes dans SharePoint Online. Utilisez les instructions de cet article pour optimiser les performances modernes du site portail et éviter les problèmes de performances courants.

## <a name="performance-considerations-for-modern-portal-sites"></a>Considérations relatives aux performances des sites portail modernes

Du point de vue de l’optimisation des performances, il existe quelques caractéristiques qui rendent les sites portail modernes uniques. La principale différence entre les sites de collaboration et de portail dans SharePoint Online est évolutive. Il est généralement prévu que les sites portails fournissent davantage de vues de page à un plus grand nombre d’utilisateurs que les sites de collaboration et qu’ils contiennent vraisemblablement plus de contenu statique et moins de ressources modifiables. En outre, l’architecture des sites modernes diffère des sites classiques dans la plupart du traitement impliqué dans le rendu des pages et l’exécution du code sur le client plutôt que sur le serveur.

L’optimisation des performances pour les sites portail modernes est principalement axée sur quelques objectifs globaux :

- Réduire la taille totale des composants de chaque page de site
- Déchargement de l’hébergement de fichiers statiques courants tels que des images, des feuilles de style et des scripts pour le CDN
- Limiter les appels à SharePoint et aux points de terminaison externes uniquement à ce qui est nécessaire
- Éviter les demandes en double pour le même contenu

La plupart des instructions de cet article se concentrent sur la minimisation et l’optimisation des appels vers SharePoint Online. Effectuer des appels répétitifs chaque fois qu’une page est chargée a un impact sur les performances pour les utilisateurs, car les informations seront extraites du service à chaque fois, même si elles n’ont pas changé. En tant que telles, les demandes à SharePoint peuvent être classées comme des appels communs à tous les utilisateurs ou appels requis pour chaque utilisateur individuel. Les résultats de ces deux catégories d’appels doivent être mis en cache pour optimiser l’expérience utilisateur.

>[!NOTE]
>Utilisez l' [outil Diagnostics de la page pour SharePoint](https://aka.ms/perftool) comme point de départ pour analyser des mesures de performances spécifiques sur les pages de site SharePoint Online.

## <a name="modern-portal-site-limits-and-recommendations"></a>Limites et recommandations des sites portail modernes

|**Limite**|**Valeur maximale recommandée**|**Remarques**|
|:-----|:-----|:-----|:-----|
|Pages et Actualités  <br/> |5 000 par site  <br/> |Nous vous recommandons de limiter le nombre de pages et d’éléments d’actualité dans un site portail moderne à la limite de 5 000.  <br/> |
|Composants WebPart sur une page  <br/> |20 par page  <br/> |Nous vous recommandons d’utiliser au moins 20 composants WebPart totaux par page, y compris les composants WebPart Microsoft et les composants WebPart personnalisés. <br/> Pour plus d’informations, consultez la rubrique [optimiser les performances des composants WebPart dans les pages de site modernes SharePoint Online](modern-web-part-optimization.md).  <br/> |
|Composants WebPart dynamiques sur une page  <br/> |4 par page  <br/> |Les composants WebPart dynamiques qui effectuent une ou plusieurs requêtes vers SharePoint pour extraire les données les plus récentes doivent être limités à 4 par page. Le composant WebPart _News_ est un exemple de composant WebPart dynamique. <br/> Pour plus d’informations, consultez la rubrique [optimiser les performances des composants WebPart dans les pages de site modernes SharePoint Online](modern-web-part-optimization.md).    <br/> |
|Groupes de sécurité  <br/> |20 par site  <br/> |Le nombre de groupes de sécurité affecte l’étendue de nombreuses requêtes dans les sites portail modernes. Nous vous recommandons de limiter le nombre de groupes de sécurité à un ensemble aussi petit que possible, avec un maximum de 20 par site.  <br/> |
|Éléments dans la navigation de site  <br/> |100 par site  <br/> |Nous vous recommandons d’ajouter moins de 100 éléments à la navigation du site et d’utiliser des contrôles de navigation prédéfinis.  <br/> Pour plus d’informations, consultez la rubrique [optimize page Weight in SharePoint Online Modern site pages](modern-page-weight-optimization.md). <br/> |
|Taille maximale de l’image  <br/> |300 Ko par image  <br/> |Nous vous recommandons de limiter la taille des images à 300kb ou plus petite, et d’utiliser un CDN pour héberger des images, des feuilles de style et des scripts. <br/>Pour plus d’informations, consultez la rubrique [optimize images in SharePoint Online Modern site pages](modern-image-optimization.md) et [utilisation du réseau de distribution de contenu (CDN) Office 365 avec SharePoint Online](use-office-365-cdn-with-spo.md).  <br/> |
|Utilisateurs disposant de droits de modification  <br/> |200 utilisateurs par site  <br/> |Les sites portail SharePoint sont optimisés pour l’affichage et l’utilisation de contenu. Les autorisations de modification sur un portail doivent être limitées à un groupe d’utilisateurs restreint car les autorisations de modification téléchargent des contrôles supplémentaires et s’exécutent donc plus lentement pour ces utilisateurs. Un nombre excessif d’utilisateurs disposant d’autorisations de modification a donc une incidence sur l’expérience globale. <br/> |
|IFrames tiers  <br/> |2 par page  <br/> |les iFrames sont lents de manière imprévisible, car ils chargent une page externe distincte, y compris tout le contenu associé tel que JavaScript, CSS et les éléments d’infrastructure. Si vous devez utiliser des iFrames, limitez leur nombre à 2 ou moins par page.<br/> Pour plus d’informations, reportez-vous à la rubrique [optimize iframes in SharePoint Online Modern and Classic Publishing site pages](modern-iframe-optimization.md). <br/> |
|Appels au service UPA  <br/> |1 par utilisateur et par heure  <br/> |Nous vous recommandons de ne pas passer par appel de _requête_ au service UPA (application de profil utilisateur). L' [API Microsoft Graph](https://docs.microsoft.com/graph/call-api) et le [PageContext](https://docs.microsoft.com/javascript/api/sp-page-context/pagecontext?view=sp-typescript-latest) peuvent être utilisés pour rechercher des informations utilisateur.  <br/> Si un appel de service UPA est nécessaire, effectuez un seul appel lorsque cela est nécessaire, puis mettez en cache les informations pour les réutiliser au cours de la même session. |
|Appels au service de taxonomie  <br/> |5 par utilisateur et par heure  <br/> |Nous vous recommandons de ne pas effectuer d’appels _par requête_ vers le service de taxonomie. Si des appels de service de taxonomie sont nécessaires, mettez en cache les informations pour les réutiliser au cours de la même session. <br/> Pour plus d’informations, consultez la rubrique [optimize Call page Calls in SharePoint Online Modern and Classic Publishing site pages](modern-page-call-optimization.md). <br/> |

## <a name="related-topics"></a>Voir aussi

[Création d’un portail SharePoint sain](https://docs.microsoft.com/sharepoint/portal-health)

[Optimisation des performances SharePoint Online](tune-sharepoint-online-performance.md)

[Optimisation des performances Office 365](tune-office-365-performance.md)

[Limites de SharePoint Online](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[Performances offertes par l’expérience moderne de SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[Aide relative aux performances des portails SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-performance)
