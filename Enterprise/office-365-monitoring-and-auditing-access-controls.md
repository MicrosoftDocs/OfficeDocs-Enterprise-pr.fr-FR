---
title: Office 365 surveillance et audit des contrôles d’accès
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
f1.keywords:
- NOCSH
description: 'Résumé : Résumé des différents contrôles d’accès au contrôle et à l’audit disponibles dans Office 365.'
ms.openlocfilehash: 300d5efa2b448e8e5219eb88f3d736eeba66f2d6
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41842604"
---
# <a name="monitoring-and-auditing-access-controls-in-office-365"></a>Surveillance et audit des contrôles d’accès dans Office 365

Microsoft effectue une surveillance et un audit détaillés de toutes les délégations, privilèges et opérations qui se produisent dans Office 365. Le contrôle d’accès Office 365 est un processus automatisé basé sur le principe des privilèges minimum et l’incorporation des contrôles d’accès aux données et des audits :

- Tous les accès autorisés sont traçables vers un utilisateur unique. Les administrateurs sont responsables de la gestion du contenu client.
- Les journaux des demandes de contrôle d’accès, les approbations et les opérations d’administration sont capturés pour l’analyse de la sécurité et des événements malveillants.
- Les niveaux d’accès sont examinés en quasi-temps réel en fonction de l’appartenance au groupe de sécurité afin de s’assurer que seuls les utilisateurs qui ont autorisé les justifications professionnelles et satisfont aux exigences d’éligibilité ont accès aux systèmes.
- Office 365, ses contrôles d’accès et les services de prise en charge, y compris Azure Active Directory et les centres de documents physiques, sont régulièrement contrôlés par des tiers indépendants pour la conformité à la [norme ISO/iec 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001), [iso/IEC 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC), [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP)et d’autres [normes](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).
- Les ingénieurs Office 365 doivent suivre annuellement une formation sur la sécurité, consulter les meilleures procédures d’accès élevé et reconnaître les stratégies de sécurité et de confidentialité de Microsoft pour conserver les habilitations du service.

Déclenchent des alertes automatiques lorsqu’une activité suspecte est détectée, par exemple, plusieurs échecs de connexion au cours d’une courte période. L’équipe de sécurité de la sécurité d’Office 365 utilise l’apprentissage automatique et l’analyse des données volumineuses pour examiner et analyser l’activité, Rechercher des modèles d’accès irréguliers et répondre de manière proactive aux activités anormales et illégales. Microsoft utilise également une équipe dédiée de testeurs de pénétration et s’engage dans les exercices de l’équipe rouge périodique et de l’équipe bleue pour rechercher les problèmes de sécurité et de contrôle d’accès dans le service. Les clients peuvent vérifier l’efficacité des systèmes de contrôle d’accès à l’aide de rapports d’audit et de l’API activité de gestion fournies par Office 365.

Pour plus d’informations, voir référence de l' [API activité de gestion office 365](https://msdn.microsoft.com/library/office/mt227394.aspx) et [audit et création de rapports dans Office 365](office-365-auditing-and-reporting-overview.md).
