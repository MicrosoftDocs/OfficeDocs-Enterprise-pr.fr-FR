---
title: Isolation du client dans Office 365
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
description: Résumé de la manière dont Microsoft applique l’isolation du client pour Office 365.
ms.openlocfilehash: a5b8a3e42aa7acc5cebe8ed21a8599fc03b5060f
ms.sourcegitcommit: 67dbbf1a5ec8cc4b10ca10f267f871f0bc045e63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "37375522"
---
# <a name="tenant-isolation-in-office-365"></a>Isolation du client dans Office 365

L’un des principaux avantages du Cloud Computing est le concept d’une infrastructure commune partagée entre plusieurs clients simultanément, conduisant à des économies d’échelle. Ce concept *est appelé architecture mutualisée*. Microsoft continue de s’assurer que l’architecture mutualisée de nos services Cloud prend en charge les normes de sécurité, de confidentialité, de confidentialité, d’intégrité et de disponibilité au niveau de l’entreprise.

En fonction des investissements et de l’expérience considérables collectés dans le [cycle de vie du développement](http://www.microsoft.com/security/sdl/default.aspx)de la sécurité et de l’informatique de [confiance](https://www.microsoft.com/en-us/twc/default.aspx) , les services Cloud Microsoft ont été conçus en partant du principe que tous les clients sont potentiellement hostiles à tous d’autres clients, et nous avons implémenté des mesures de sécurité pour empêcher les actions d’un client d’affecter la sécurité ou le service d’un autre client, ou d’accéder au contenu d’un autre client.

Les deux principaux objectifs du maintien de l’isolation des clients dans un environnement mutualisés sont les suivants :
1.  Empêcher la fuite ou l’accès non autorisé au contenu du client dans les clients ; les
2.  Empêcher les actions d’un client d’affecter le service à un autre client

Plusieurs formes de protection ont été mises en œuvre partout dans Office 365 pour empêcher les clients de commettre des services ou des applications Office 365 ou d’obtenir un accès non autorisé aux informations d’autres clients ou au système Office 365 lui-même, notamment :
- L’isolation logique du contenu client au sein de chaque client pour les services Office 365 est obtenue via le contrôle d’accès basé sur les rôles et l’autorisation Azure Active Directory.
- SharePoint Online fournit des mécanismes d’isolation des données au niveau du stockage.
- Microsoft utilise une sécurité physique rigoureuse, un filtrage en arrière-plan et une stratégie de chiffrement multicouche pour protéger la confidentialité et l’intégrité du contenu du client. Tous les centres de donnees Office 365 ont des contrôles d’accès biométriques, avec la plupart des impressions Palm requises pour obtenir un accès physique. En outre, tous les employés Microsoft américains doivent être tenus de suivre une vérification de fond standard dans le cadre du processus d’embauche. Pour plus d’informations sur les contrôles utilisés pour l’accès administratif dans Office 365, reportez-vous à la rubrique [office 365 administrative Access Controls](office-365-administrative-access-controls-overview.md).
- Office 365 utilise des technologies côté service qui chiffrent le contenu du client au repos et en transit, notamment BitLocker, le chiffrement par fichier, le chiffrement TLS (Transport Layer Security) et la sécurité du protocole Internet (IPsec). Pour plus d’informations sur le chiffrement dans Office 365, consultez la rubrique [technologies de chiffrement de données dans office 365](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview).

Ensemble, les protections mentionnées ci-dessus fournissent des contrôles d’isolation logiques robustes qui fournissent une protection contre les menaces et une atténuation équivalente à celles fournies par l’isolation physique seule.

## <a name="related-links"></a>Liens connexes
- [Isolation et contrôle d’accès dans Azure Active Directory](office-365-isolation-in-azure-active-directory.md)
- [Isolation du client dans Office Graph et Delve](office-365-isolation-in-graph-and-delve.md)
- [Isolation du client dans Office 365 Search](office-365-isolation-in-office-365-search.md)
- [Isolation du client dans Office 365 Video](office-365-isolation-in-office-365-video.md)
- [Limites de ressources](office-365-resource-limits.md)
- [Surveillance et test des limites du client](office-365-monitoring-and-testing.md)
- [Isolation et contrôle d’accès dans Office 365](office-365-isolation-in-office-365.md)
