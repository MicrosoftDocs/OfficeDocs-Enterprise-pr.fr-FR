---
title: Préparer votre organisation pour Office 365 Entreprise
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Si vous avez choisi de ne pas de déploiement FastTrack et ne sont pas trouver ce que vous avez besoin dans notre étapes de déploiement de base, il s’agit du point de départ.
ms.openlocfilehash: bb522890880ec77969abe6e2559c3d0293aca372
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651198"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>Préparer votre organisation pour Office 365 Entreprise

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>Ce que vous devez faire pour être prêt pour Office 365 ?

La plupart des organisations n’avez pas besoin de faire quoi que ce soit pour préparer pour Office 365. Il s’agit d’une application sur le web et personnes sont en mesure d’utiliser dès qu’ils ont un compte. D’autres organisations ont plusieurs emplacements, les pratiques de sécurité ou connaître les autres exigences créer le besoin de plus de planification. Pour les organisations de niveau entreprise, suivez les éléments de liste de vérification ci-dessous pour prendre en main Office 365.
  
Si vous souhaitez obtenir de l’aide concernant la configuration d’Office 365, [FastTrack](https://fasttrack.microsoft.com/office) est la meilleure façon de déployer Office 365, vous pouvez également connecter et utiliser les [conseillers de déploiement pour les services Office 365](deployment-advisors-for-office-365.md).
  
|**Sélectionnez un ou plusieurs pour commencer :**||
|:-----|:-----|
| [Configuration système requise pour Office](https://products.office.com/office-system-requirements) |-Microsoft Office Professionnel, Office 365, Office 365 ProPlus et chaque application Office pour Windows, Mac, iOS et Android ont spécifique requise. Vérifiez que votre répondent aux configurations matérielle et logicielle de la configuration minimale requise.|
|**La plupart des** clients se connecter à leur annuaire local à Office 365. Gagnez du temps sur la préparation d’un répertoire en [installant et en cours d’exécution IdFix sur votre réseau](https://www.microsoft.com/download/details.aspx?id=36832).<br> Utilisez le [Gestionnaire DAS se connecter](https://aka.ms/aadconnectpwsync) et la [que configurer Azure AD Premium le guide](https://aka.ms/aadpguidance) pour obtenir des conseils personnalisés. <br> |-Automatisée à vérifier votre annuaire à [Valider populaire comptes synchronisera correctement](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> -Recommande des modifications apportées aux objets d’annuaire et propose à automatiser les modifications pour vous. <br> - [Plus d’informations sur l’utilisation de l’outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md). |
|**Lire** notre [Guide des performances du réseau](https://aka.ms/tune) et l’utilisation notre outils afin de vous présentent la configuration de connectivité et de performances nécessaire pour fournir la meilleure expérience des personnes.  <br> | -Assurez-vous que vous pouvez vous connecter à Office 365, si vous filtrez ou analysez le trafic sortant le trafic, vous souhaiterez comprendre quels de [la gestion des points de terminaison Office 365](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) signifie pour votre organisation.  <br>  - [Modèle et tester votre capacité réseau](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) ou les déplacer vers un circuit [ExpressRoute Azure pour Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) pour une expérience plus prévisible.   |
|**Utilisez** notre [liste de contrôle de planification](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) comme point de départ pour la création de votre propre plan de déploiement.  <br> | -Présentation approfondie de domaines possibles, vous devez planifier avec des liens vers des informations de référence ou des procédures pour vous aider à planifier. |
|**Utiliser** le [Script d’élément volumineux Exchange Server](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) pour rechercher des éléments de messagerie qui peuvent être trop volumineux pour la migration.  <br> | -Utilise les Services Web Exchange pour emprunter l’identité, accéder, analyse de la boîte aux lettres pour les tailles de fichier que vous spécifiez et vidages les résultats dans un fichier CSV. Lisez les [instructions détaillées sur la façon d’utiliser le script](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx). |
|**Profitez d' [experts de déploiement de Microsoft](https://go.microsoft.com/fwlink/?LinkId=517115) qui peut vous aider à partir de la planification à tout le monde vous aider à** commencer à utiliser les nouveaux services et applications.  <br> Utiliser les [Assistants de déploiement pour les services Office 365](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) afin d’obtenir des conseils personnalisés.  <br> | -Le centre d’intégration fonctionne directement avec les clients et avec les organisations partenaires. Accordez-leur un appel aujourd'hui. |
|**Utiliser** les [modèles et les ressources dans le centre de réussite d’Office 365](https://www.microsoft.com/fasttrack/resources) à partager votre déploiement et l’intégration des plans avec les personnes dans votre organisation.  <br> | -La communication avec tout le monde avant, pendant et après la transition vers Office 365 est essentielle.  <br> -Utilisez nos modèles, guides et des documents pour améliorer vos communications. |
|**Lire** l’article [Principes de connectivité réseau Office 365](https://aka.ms/o365networkingprinciples) pour comprendre les principes de connectivité pour gérer le trafic d’Office 365 en toute sécurité et d’obtenir les meilleures performances possibles.  <br> | -Cet article vous aideront à comprendre les plus récents conseils pour éliminer en toute sécurité Office 365 la connectivité réseau. |
   
Vous souhaitez obtenir davantage de ressources pour vous aider à intégrer Office 365 à votre stratégie de nuage plus large ? Voici les [ressources d’architecture informatique en nuage Microsoft](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## <a name="want-to-talk-with-support"></a>Vous voulez parler avec prise en charge ?

Nous sommes là pour vous aider, [contactez le support technique](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) pour les produits d’entreprise.
