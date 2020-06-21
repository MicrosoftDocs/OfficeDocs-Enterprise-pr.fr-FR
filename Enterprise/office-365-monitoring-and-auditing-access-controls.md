---
title: Contrôles d’accès de surveillance et d’audit de Microsoft 365
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
description: 'Résumé : Résumé des différents contrôles d’accès aux contrôles et audits disponibles dans Microsoft 365.'
ms.openlocfilehash: aba1a9966cf50735ba3348fe126d7b4c9233b4b2
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774869"
---
# <a name="monitoring-and-auditing-access-controls-in-microsoft-365"></a>Surveillance et audit des contrôles d’accès dans Microsoft 365

Microsoft effectue une surveillance et un audit détaillés de toutes les délégations, privilèges et opérations qui se produisent au sein de Microsoft 365. Le contrôle d’accès Microsoft 365 est un processus automatisé basé sur le principe des privilèges minimum et l’intégration des contrôles d’accès aux données et des audits :

- Tous les accès autorisés sont traçables vers un utilisateur unique. Les administrateurs sont responsables de la gestion du contenu client.
- Les journaux des demandes de contrôle d’accès, les approbations et les opérations d’administration sont capturés pour l’analyse de la sécurité et des événements malveillants.
- Les niveaux d’accès sont examinés en quasi-temps réel en fonction de l’appartenance au groupe de sécurité afin de s’assurer que seuls les utilisateurs qui ont autorisé les justifications professionnelles et satisfont aux exigences d’éligibilité ont accès aux systèmes.
- Microsoft 365, ses contrôles d’accès et ses services de prise en charge, y compris Azure Active Directory et les centres de connaissances physiques, sont régulièrement contrôlés par des tiers indépendants pour la conformité à la [norme ISO/iec 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001), [iso/IEC 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC), [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP)et d’autres [normes](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).
- Les ingénieurs de Microsoft 365 doivent suivre annuellement une formation sur la sécurité, consulter les meilleures procédures d’accès élevé et reconnaître les stratégies de confidentialité et de sécurité de Microsoft pour conserver les habilitations du service.

Déclenchent des alertes automatiques lorsqu’une activité suspecte est détectée, par exemple, plusieurs échecs de connexion au cours d’une courte période. L’équipe de réponse de sécurité Microsoft 365 utilise l’apprentissage automatique et l’analyse des données volumineuses pour examiner et analyser l’activité, Rechercher des modèles d’accès irréguliers et répondre de manière proactive aux activités anormales et illégales. Microsoft utilise également une équipe dédiée de testeurs de pénétration et s’engage dans les exercices de l’équipe rouge périodique et de l’équipe bleue pour rechercher les problèmes de sécurité et de contrôle d’accès dans le service. Les clients peuvent vérifier l’efficacité des systèmes de contrôle d’accès à l’aide de rapports d’audit et de l’API activité de gestion fournie par Microsoft 365.

Pour plus d’informations, voir référence de l' [API activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference) et [audit et création de rapports dans Microsoft 365](office-365-auditing-and-reporting-overview.md).
