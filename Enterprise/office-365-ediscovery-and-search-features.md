---
title: Vue d’ensemble des fonctionnalités de recherche et de découverte Office 365
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
description: Une vue d’ensemble de la fonctionnalité eDiscovery et d’autres fonctionnalités de recherche dans Office 365 pour l’utilisation et la transparence de l’audit.
ms.openlocfilehash: e94c8e27c2ddf7bd50dca15eb849337de6f89c1a
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032029"
---
# <a name="ediscovery-and-search-features"></a>eDiscovery et fonctionnalités de recherche 

## <a name="ediscovery"></a>eDiscovery

La fonctionnalité de découverte électronique offre un emplacement unique pour les administrateurs, les responsables de la mise en conformité et les autres utilisateurs autorisés à effectuer une enquête complète sur l’activité utilisateur d’Office 365. Les responsables de la sécurité disposant des autorisations appropriées effectuent des recherches et placent des conservations sur le contenu. Les résultats de la recherche sont les mêmes résultats que ceux obtenus lors d’une recherche de contenu, à l’exception des cas eDiscovery créés pour les conservations appliquées. Les résultats des recherches de découverte électronique sont chiffrés pour la sécurité et vous pouvez analyser les données exportées avec [Advanced eDiscovery](https://support.office.com/article/office-365-advanced-ediscovery-fd53438a-a760-45f6-9df4-861b50161ae4).

## <a name="content-search"></a>Recherche de contenu

La [recherche de contenu](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) est un outil de recherche de découverte électronique qui offre une amélioration de la mise à l’échelle et des performances par rapport aux précédents outils de recherche eDiscovery. Vous utilisez la recherche de contenu pour rechercher des boîtes aux lettres, des dossiers publics, des sites SharePoint Online et des emplacements OneDrive entreprise. La recherche de contenu prend en charge les recherches volumineuses. Il n’existe aucune limite au nombre de boîtes aux lettres et de sites que vous pouvez consulter. Il n’y a pas non plus de limites quant au nombre de recherches exécutées en même temps. Après avoir exécuté une recherche, le nombre de sources de contenu et un nombre estimé de résultats de recherche sont affichés dans le volet d’informations de la page de recherche. Vous pouvez afficher un aperçu des résultats ou les exporter vers un ordinateur local. Si votre organisation dispose d’un abonnement Office 365 entreprise E5, vous pouvez [préparer les résultats](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a#prepare) de l’analyse à l’aide des puissantes fonctionnalités d’analyse d' [Office 365 Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?LinkID=620116).

## <a name="audit-log-search"></a>Recherche dans le journal d'audit

Outre le suivi des modifications dans son organisation 365 Office, vous pouvez afficher les rapports d’audit et exporter les journaux d’audit. Une fois l’audit activé pour un client Office 365, l’activité utilisateur et administrative sont enregistrées dans les journaux des événements et rendues accessibles en recherche. Par exemple, vous pouvez utiliser l’enregistrement d’audit de boîte aux lettres pour suivre les actions exécutées sur une boîte aux lettres par des utilisateurs autres que le propriétaire de la boîte aux lettres. Les responsables de la conformité peuvent utiliser les fonctionnalités de recherche et de filtrage pour des activités utilisateur spécifiques. Par exemple, pour identifier les utilisateurs qui ont affiché ou téléchargé un document spécifique, si les administrateurs ont effectué des activités de gestion des utilisateurs ou pour afficher les modifications apportées à la configuration du client au cours des 90 derniers jours. Les résultats de la recherche contiennent des informations d’expertise précieuse sur des activités spécifiques menées par un utilisateur ou un administrateur. Consultez la rubrique [activités auditées dans office 365](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c#auditlogevents) pour obtenir une description des activités d’utilisateur et d’administration enregistrées dans Office 365.

Les événements provenant de SharePoint Online et OneDrive entreprise apparaissent dans le journal dans les 30 minutes qui survient. Les événements provenant d’Exchange Online apparaissent dans les journaux d’audit dans les 24 heures qui suivent l’événement. Les événements de connexion à partir d’Azure AD sont disponibles dans les minutes qui suivent l’occurrence, et les autres événements d’annuaire provenant d’Azure AD sont disponibles dans les 24 heures qui suivent. Vous pouvez exporter des ventes dans les résultats de recherche du journal d’audit pour une analyse plus poussée. Un maximum de 50 000 entrées à partir d’une recherche de journal d’audit unique sont exportées. Pour exporter plusieurs entrées de cette limite, réduisez la plage de dates ou exécutez plusieurs recherches de journaux d’audit.

Le tableau suivant décrit en détail certaines des informations affichées dans les rapports d’activité. Pour plus d’informations sur les propriétés collectées par chaque charge de travail Office 365, voir les [Propriétés détaillées dans le journal d’audit office 365](https://support.office.com/article/detailed-properties-in-the-office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3) .

| Propriété | Description |
|----------------|----------------------------------------------------------------------------------------------------------------------|
| Date | Date et heure de l’événement |
| Utilisateur | Utilisateur ayant effectué l’action |
| ClientIP | Adresse IPv4 ou IPv6 de l’appareil utilisé lors de l’enregistrement de l’activité. |
| CreationTime | Date et heure au format UTC (temps universel coordonné) lorsque l’utilisateur a effectué l’activité. |
| EventSource | Indique qu’un événement s’est produit. Les valeurs possibles sont SharePoint et ObjectModel. |
| ID | ID de l’entrée de rapport. L’ID identifie de manière unique l’entrée de rapport. |
| Opération | Nom de l’utilisateur ou de l’activité, qui correspond à la valeur sélectionnée dans l’écran afficher les résultats pour cette activité de l’utilisateur. |
| OrganizationId | GUID pour le service Office 365 de l’organisation où l’événement s’est produit. |
| UserAgent | Informations sur le navigateur de l’utilisateur, fournies par le navigateur. |
| UserId | Utilisateur ayant effectué l’action (spécifié dans la propriété Operation) ayant provoqué l’enregistrement journalisé. |
| UserType | Type d’utilisateur qui a effectué l’opération. Les valeurs suivantes indiquent le type d’utilisateur. |
|  | 0 indique un utilisateur normal. |
|  | 2 indique un administrateur de votre organisation Office 365. |
|  | 3 indique un compte d’administrateur ou de système de centre de connaissances Microsoft. |
| Charge de travail | Service Office 365 où l’activité s’est produite. Les valeurs possibles pour cette propriété sont les suivantes : |
|  | Exchange Online |
|  | SharePoint Online |
|  | OneDrive Entreprise |
|  | Rapports Azure Active Directory |

Pour obtenir la procédure détaillée pour effectuer des recherches dans les journaux d’audit Office 365, consultez [la rubrique recherche des journaux d’audit dans le 365 Office](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).

## <a name="search-unified-audit-log"></a>Rechercher dans le journal d’audit unifié

Utilisez la fonctionnalité de recherche du journal d’audit pour rechercher dans le journal d’audit unifié. Office 365 offre également la possibilité d’effectuer des recherches dans ce journal à l’aide de PowerShell à distance. La [cmdlet Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/Search-UnifiedAuditLog?view=exchange-ps) dans Exchange Online PowerShell est utilisée pour effectuer des recherches dans le journal d’audit unifié des événements liés aux opérations de l’utilisateur à partir d’Exchange Online, SharePoint Online, OneDrive entreprise et Azure ad. 

Vous pouvez rechercher tous les événements dans une plage de dates spécifique ou vous pouvez filtrer les résultats en fonction de critères spécifiques, tels qu’une action spécifique, l’utilisateur qui a effectué l’action ou l’objet cible. Les administrateurs peuvent utiliser jusqu’à trois sessions PowerShell Exchange Online simultanément pour fractionner les recherches de plage de dates volumineuses.