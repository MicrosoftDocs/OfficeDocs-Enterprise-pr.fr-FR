---
title: Microsoft 365 données immuabilité
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
f1.keywords:
- NOCSH
description: Définit et décrit l’immuabilité des données dans Microsoft 365.
ms.openlocfilehash: 8648060f3036d2f3c81704cf53a817910607263a
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998458"
---
# <a name="immutability-in-microsoft-365"></a>Immuabilité dans Microsoft 365

La conformité réglementaire, les exigences de gouvernance interne ou les risques de contentieux imposent aux organisations de conserver le courrier électronique et les données associées sous une forme découvrable. Toutes les données du système doivent être découvrables et aucune ne peut être détruite ou modifiée. Le terme standard du secteur est « immuabilité ».

Les méthodes traditionnelles d’immuabilité ont généralement fonctionné en déplacant les messages électroniques vers un emplacement de stockage distinct en lecture seule. Bien que ces systèmes visent l’objectif de la conservation des éléments de boîte aux lettres pour la découverte, ils affectent souvent l’expérience utilisateur en supprimant les éléments conservés du flux de travail quotidien personnalisé. Pour les professionnels de l’informatique, cette approche d’immuabilité nécessite le déploiement et la maintenance continue d’une infrastructure de serveur et de stockage distincte. La découverte est effectuée avec des outils externes au système de messagerie et inclut des coûts de déploiement et de maintenance associés.

Les fonctionnalités de stratégie de conservation et de conservation sur place de l’archivage dans Microsoft 365 et ses services vous permettent de conserver et de conserver de nombreuses classes de données entrantes, internes et sortantes. Cela inclut les opérations suivantes :

- Communications par courrier électronique entrant et sortant
- Livres et enregistrements contenus dans un formulaire électronique ou dans des documents en ligne partagés
- Demandes de réunion
- Situées
- Messages instantanés
- Documents partagés pendant les réunions en ligne
- Messages vocaux

De plus, Microsoft a développé des fonctionnalités complémentaires pour permettre [l’archivage des données](https://support.office.com/article/Archiving-third-party-data-in-Office-365-0ce338d5-3666-4a18-86ab-c6910ff408cc) provenant d’autres sources via l’intégration de solutions de capture et de gestion de données tierces. Une fois les données tierces importées, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 aux données, notamment :

- [Conservation pour litige](https://docs.microsoft.com/microsoft-365/compliance/create-a-litigation-hold)
- [Découverte électronique inaltérable et conservation inaltérable](https://docs.microsoft.com/microsoft-365/compliance/manage-legal-investigations)
- [Recherche de conformité](https://docs.microsoft.com/microsoft-365/compliance/search-for-content)
- [Archivage local](https://docs.microsoft.com/microsoft-365/compliance/enable-archive-mailboxes)
- [Audit de boîte aux lettres](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing)
- [Stratégies de rétention](https://docs.microsoft.com/microsoft-365/compliance/retention-policies)

Par exemple, lorsqu’une boîte aux lettres est placée en conservation pour litige, les données tierces sont conservées. Vous pouvez rechercher des données tierces à l’aide de la découverte électronique inaltérable ou de la recherche de conformité. Vous pouvez également appliquer des stratégies d’archivage et de rétention à des données tierces, comme vous pouvez le faire pour Microsoft Data. L’archivage de données tierces dans Microsoft 365 aide votre organisation à respecter les stratégies gouvernementales et réglementaires.

L’archivage dans Microsoft 365 fournit des valeurs mobilières et des commissions Exchange (SEC) pour la règle de stockage compatible 17A -4. Microsoft 365 conserve les fichiers permanents de toutes les données collectées dans un format non réinscriptible et non effaçable en utilisant des stratégies de rétention sur place et des stratégies de conservation, notamment le verrouillage de la conservation.

Notamment :

- Tous les enregistrements stockés à l’aide des stratégies de rétention indiquées ci-dessus sont conservés dans une zone de stockage dédiée à partir de l’PurVIEW de l’utilisateur ordinaire. Seuls les utilisateurs autorisés peuvent accéder à ces enregistrements et les Rechercher, mais ils ne peuvent pas les modifier ou les supprimer.
- Les métadonnées de chaque élément incluent un horodatage utilisé dans le calcul de la durée de rétention. Les horodatages sont appliqués lorsqu’un nouvel élément est reçu ou créé et qu’il ne peut pas être modifié ou supprimé des métadonnées.
- L’archivage dans Microsoft 365 permet aux utilisateurs de combiner différentes stratégies de rétention et des actions de conservation pour créer des stratégies de rétention granulaires. Ces stratégies définissent le type ou l’emplacement des éléments conservés et la durée de conservation.
- La fonctionnalité de verrouillage de conservation permet aux utilisateurs de choisir s’il faut appliquer une stratégie restrictive à la stratégie. Une stratégie restrictive interdit à quiconque de pouvoir supprimer, désactiver ou modifier la stratégie de rétention. Cela signifie que lorsque le verrouillage de conservation est activé, il ne peut pas être désactivé et aucun mécanisme n’existe sous lequel les données provenant de dépositaires existants collectées par les stratégies de rétention en place peuvent être remplacées, modifiées, effacées ou supprimées pendant la période de conservation. De plus, le délai d’attente défini par le verrouillage de conservation ne peut pas être raccourci ou réduit. Elle peut toutefois être allongée, dans le cas d’une obligation légale de continuer la rétention des données stockées, comme indiqué ci-dessus. Le verrouillage de conservation garantit que personne, pas même les administrateurs ou ceux disposant d’un accès de contrôle, ne peut modifier les paramètres ou remplacer ou effacer les données qui ont été stockées, en configurant l’archivage dans Microsoft 365 en fonction des instructions décrites dans la version 2003 de la règle SEC 17A -4.

Pour comprendre comment Microsoft 365 vous aide à respecter les obligations réglementaires, notamment en ce qui concerne les conditions requises pour la réglementation 17A -4, consultez le [livre blanc](https://www.microsoft.com/microsoft-365/blog/wp-content/uploads/2015/11/Microsoft-EOA-White-Paper.pdf) sur l’archivage Exchange Online, SharePoint Online, OneDrive entreprise et Skype entreprise. Le livre blanc fournit également une analyse approfondie des fonctionnalités et des fonctionnalités d’archivage de Microsoft 365 en fonction de chacune des exigences de la norme SEC 17A -4 et démontre aux clients soumis à la façon dont l’archivage Microsoft 365 peut les autoriser à répondre à ces exigences.
