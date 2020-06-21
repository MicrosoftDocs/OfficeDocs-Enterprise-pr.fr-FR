---
title: Présentation des fonctionnalités de découverte électronique et de recherche de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
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
- SPO_Content
f1.keywords:
- NOCSH
description: Vue d’ensemble de la fonctionnalité de découverte électronique et d’autres fonctionnalités de recherche dans Microsoft 365 pour l’utilisation et la transparence des audits.
ms.openlocfilehash: d628bc9aa3964ffed671035a1f78f61d9632b87e
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774939"
---
# <a name="microsoft-365-ediscovery-and-search-features-overview"></a>Présentation des fonctionnalités de découverte électronique et de recherche de Microsoft 365 

## <a name="ediscovery"></a>eDiscovery

La fonctionnalité eDiscovery offre un seul emplacement pour les administrateurs, les responsables de la mise en conformité et les autres utilisateurs autorisés à effectuer une enquête complète sur l’activité des utilisateurs de Microsoft 365. Les responsables de la sécurité disposant des autorisations appropriées effectuent des recherches et placent des conservations sur le contenu. Les résultats de la recherche sont les mêmes résultats que ceux obtenus lors d’une recherche de contenu, à l’exception des cas eDiscovery créés pour les conservations appliquées. Les résultats des recherches de découverte électronique sont chiffrés pour la sécurité et vous pouvez analyser les données exportées avec [Advanced eDiscovery](https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20).

## <a name="content-search"></a>Recherche de contenu

La [recherche de contenu](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) est un outil de recherche de découverte électronique qui offre une amélioration de la mise à l’échelle et des performances par rapport aux précédents outils de recherche eDiscovery. Vous utilisez la recherche de contenu pour rechercher des boîtes aux lettres, des dossiers publics, des sites SharePoint Online et des emplacements OneDrive entreprise. La recherche de contenu prend en charge les recherches volumineuses. Il n’existe aucune limite au nombre de boîtes aux lettres et de sites que vous pouvez consulter. Il n’y a pas non plus de limites quant au nombre de recherches exécutées en même temps. Après avoir exécuté une recherche, le nombre de sources de contenu et un nombre estimé de résultats de recherche sont affichés dans le volet d’informations de la page de recherche. Vous pouvez afficher un aperçu des résultats ou les exporter vers un ordinateur local. Si votre organisation dispose d’un abonnement Microsoft 365 E5, vous pouvez [préparer les résultats](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a#prepare) de l’analyse à l’aide des puissantes fonctionnalités d’analyse de [Microsoft 365 Advanced eDiscovery](https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20).

## <a name="audit-log-search"></a>Recherche dans le journal d’audit

Outre le suivi des modifications dans leur organisation Microsoft 365, vous pouvez afficher les rapports d’audit et exporter les journaux d’audit. Une fois l’audit activé pour un client Microsoft 365, l’activité utilisateur et administrative sont enregistrées dans les journaux d’événements et font l’objet de recherches. Par exemple, vous pouvez utiliser l’enregistrement d’audit de boîte aux lettres pour suivre les actions exécutées sur une boîte aux lettres par des utilisateurs autres que le propriétaire de la boîte aux lettres. Les responsables de la conformité peuvent utiliser les fonctionnalités de recherche et de filtrage pour des activités utilisateur spécifiques. Par exemple, pour identifier les utilisateurs qui ont affiché ou téléchargé un document spécifique, si les administrateurs ont effectué des activités de gestion des utilisateurs ou pour afficher les modifications apportées à la configuration du client au cours des 90 derniers jours. Les résultats de la recherche contiennent des informations d’expertise précieuse sur des activités spécifiques menées par un utilisateur ou un administrateur. Consultez [la rubrique Rechercher dans le journal d’audit](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance) une description des activités d’utilisateur et d’administration enregistrées dans Microsoft 365.

Les événements provenant de SharePoint Online et OneDrive entreprise apparaissent dans le journal dans les 30 minutes qui survient. Les événements provenant d’Exchange Online apparaissent dans les journaux d’audit dans les 24 heures qui suivent l’événement. Les événements de connexion à partir d’Azure AD sont disponibles dans les minutes qui suivent l’occurrence, et les autres événements d’annuaire provenant d’Azure AD sont disponibles dans les 24 heures qui suivent. Vous pouvez exporter des ventes dans les résultats de recherche du journal d’audit pour une analyse plus poussée. Un maximum de 50 000 entrées à partir d’une recherche de journal d’audit unique sont exportées. Pour exporter plusieurs entrées de cette limite, réduisez la plage de dates ou exécutez plusieurs recherches de journaux d’audit.

Le tableau suivant décrit en détail certaines des informations affichées dans les rapports d’activité. Pour plus d’informations sur les propriétés collectées par chaque charge de travail Microsoft 365, voir les [Propriétés détaillées dans le journal d’audit](https://docs.microsoft.com/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log) .

| Propriété | Description |
|----------------|----------------------------------------------------------------------------------------------------------------------|
| Date | Date et heure de l’événement |
| Utilisateur | Utilisateur ayant effectué l’action |
| ClientIP | Adresse IPv4 ou IPv6 de l’appareil utilisé lors de l’enregistrement de l’activité. |
| CreationTime | Date et heure au format UTC (temps universel coordonné) lorsque l’utilisateur a effectué l’activité. |
| EventSource | Indique qu’un événement s’est produit. Les valeurs possibles sont SharePoint et ObjectModel. |
| ID | ID de l’entrée de rapport. L’ID identifie de manière unique l’entrée de rapport. |
| Opération | Nom de l’utilisateur ou de l’activité, qui correspond à la valeur sélectionnée dans l’écran afficher les résultats pour cette activité de l’utilisateur. |
| OrganizationId | GUID du service Microsoft 365 de l’organisation où l’événement s’est produit. |
| UserAgent | Informations sur le navigateur de l’utilisateur, fournies par le navigateur. |
| UserId | Utilisateur ayant effectué l’action (spécifié dans la propriété Operation) ayant provoqué l’enregistrement journalisé. |
| UserType | Type d’utilisateur qui a effectué l’opération. Les valeurs suivantes indiquent le type d’utilisateur. |
|  | 0 indique un utilisateur normal. |
|  | 2 indique un administrateur de votre organisation Microsoft 365. |
|  | 3 indique un compte d’administrateur ou de système de centre de connaissances Microsoft. |
| Charge de travail | Service Microsoft 365 où l’activité s’est produite. Les valeurs possibles pour cette propriété sont les suivantes : |
|  | Exchange Online |
|  | SharePoint Online |
|  | OneDrive Entreprise |
|  | Rapports Azure Active Directory |

Pour obtenir la procédure détaillée pour la recherche des journaux d’audit Microsoft 365, consultez la rubrique [Search the audit log dans le centre de sécurité & Compliance Center](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance).

## <a name="search-unified-audit-log"></a>Rechercher dans le journal d’audit unifié

Utilisez la fonctionnalité de recherche du journal d’audit pour rechercher dans le journal d’audit unifié. Microsoft 365 offre également la possibilité d’effectuer des recherches dans ce journal à l’aide de PowerShell à distance. La [cmdlet Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/Search-UnifiedAuditLog?view=exchange-ps) dans Exchange Online PowerShell est utilisée pour effectuer des recherches dans le journal d’audit unifié des événements liés aux opérations de l’utilisateur à partir d’Exchange Online, SharePoint Online, OneDrive entreprise et Azure ad. 

Vous pouvez rechercher tous les événements dans une plage de dates spécifique ou vous pouvez filtrer les résultats en fonction de critères spécifiques, tels qu’une action spécifique, l’utilisateur qui a effectué l’action ou l’objet cible. Les administrateurs peuvent utiliser jusqu’à trois sessions PowerShell Exchange Online simultanément pour fractionner les recherches de plage de dates volumineuses.