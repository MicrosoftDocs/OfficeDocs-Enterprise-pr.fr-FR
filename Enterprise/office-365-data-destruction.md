---
title: Destruction des données Office 365
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
description: Vue d’ensemble des stratégies Microsoft relatives au recyclage, à la suppression ou à la destruction des lecteurs de disque et serveurs des centres de données Office 365.
ms.openlocfilehash: 1fca278dd23e84db2c6591eefc45d0b75265cf17
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032089"
---
# <a name="office-365-data-destruction"></a>Destruction des données Office 365

## <a name="physical-data-destruction"></a>Destruction de données physiques

Microsoft propose des stratégies standard de gestion des données qui traite du recyclage et de la suppression des disques durs et des serveurs ayant échoué ou remis à niveau. Avant de réutiliser des lecteurs de disque Office 365, Microsoft effectue un processus de nettoyage physique compatible avec le National Institute of Standards and Technology Special Publication 800-88 ([NIST SP 800-88 Guidelines for Media assainiing](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-88r1.pdf)). Étant donné que tous les lecteurs de disque dans Office 365 sont chiffrés à l’aide du chiffrement au niveau du volume BitLocker, l’effacement compatible avec NIST SP 800-88 n’est pas techniquement nécessaire. Néanmoins, Microsoft procède à ce processus.

Les disques défaillants utilisés dans les centres de 365 Office sont physiquement détruits et audités via le processus ISO. Le type d’élément détermine les moyens de destruction appropriés. Pour les disques durs qui ne peuvent pas être effacés, Microsoft utilise un processus de destruction pour détruire le support et rendre impossible la récupération des informations. Par exemple, les disques sont physiquement détruits, pulvérisés ou incinérés. Microsoft conserve tous les enregistrements de la destruction et effectue un processus de nettoyage similaire sur les serveurs réutilisés dans Office 365. Ces instructions englobent la désinfection électronique et physique.

Chaque centre de session utilise un processus de destruction physique sur site pour supprimer ses disques. Les bacs sécurisés pour le support de stockage désigné pour la suppression de disque se trouvent dans chaque zone du centre de donnée. Chaque station de casier sécurisée est dotée d’une surveillance vidéo. Une fois qu’un casier de suppression atteint environ 50% de capacité, l’équipe des services de site contacte l’équipe de sécurité physique pour coordonner la suppression. Personnel des services de site et un bureau de sécurité supprimez le bac de suppression sécurisé et placez-le dans une zone de stockage sécurisée désignée. Les stratégies et les procédures régissant le traitement des appareils de données pendant la destruction sont régulièrement testées, y compris les procédures pour garantir l’état des machines approuvées pour la destruction.

Dans le processus de destruction des données, les disques sont effacés conformément à l’Institut NIST 800-88 (si possible), puis placés dans un broyeur industriel et physiquement Demolished. Microsoft gère les responsabilités pour les biens quittant le centre de recherche à l’aide de l’Institut NIST SP 800-88 cohérent de nettoyage/Purge des ressources, de destruction des biens, de chiffrement, d’inventaire, de suivi et de protection de la chaîne de conservation pendant le transport. Ce processus est contrôlé via une télévision de circuit fermé et un certificat de destruction est émis au terme de l’opération.

Microsoft utilise les unités d’effacement des données des protocoles EPS ( [Extreme Protocol solutions](https://www.enterprisedataerasure.com/) ). Le logiciel EPS prend en charge la configuration requise pour le SP 800-88 pour le nettoyage et la purge et l’effacement sécurisé. Avant de procéder au nettoyage ou à la destruction, un inventaire est créé par le gestionnaire de ressources Microsoft. Si un fournisseur est utilisé pour la destruction, le fournisseur fournit un certificat de destruction pour chaque ressource détruite, qui est validée par le gestionnaire des biens.

## <a name="virtual-data-destruction"></a>Destruction de données virtuelles

Microsoft possède des stratégies de gestion de données et des procédures qui traitent de la destruction virtuelle efficace des données afin de se protéger contre le partage possible des données entre les locataires de services ou être accessibles après suppression définitive du service. Les données supprimées du service dans un seul client ne sont pas accessibles à un autre client de service, même si l’un des stockages physiques sous-jacents est réaffecté. Il s’agit d’un résultat des effets composés de plusieurs technologies de virtualisation et de fragmentation utilisées pour mettre à l’évolution des environnements virtuels, les comportements de suppression actifs des applications au sein de chaque client de service (par exemple, la mise à [zéro de page](https://docs.microsoft.com/office365/securitycompliance/office-365-exchange-online-data-deletion#page-zeroing)), ainsi que les processus de chiffrement de contenu multimédia et d’application requis.