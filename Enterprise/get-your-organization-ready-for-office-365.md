---
title: Préparer votre organisation pour Office 365 Entreprise
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Si vous avez opté pour le déploiement de FastTrack et que vous ne trouvez pas ce dont vous avez besoin dans nos étapes de déploiement de base, il s'agit du point de départ.
ms.openlocfilehash: a15bd73efe2fd2e2dfd13b3a444f77b9d0bfc764
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085373"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>Préparer votre organisation pour Office 365 Entreprise

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>Que devez-vous faire pour vous préparer à Office 365?

La plupart des organisations n'ont rien besoin de faire quoi que ce soit pour préparer Office 365. Il s'agit d'une application sur le Web et les utilisateurs peuvent l'utiliser dès qu'ils disposent d'un compte. D'autres organisations ont des emplacements, des pratiques de sécurité ou d'autres exigences supplémentaires qui nécessitent une planification plus grande. Pour les organisations de niveau entreprise, suivez les éléments de la liste de contrôle ci-dessous pour commencer à utiliser Office 365.
  
Si vous souhaitez obtenir de l’aide concernant la configuration d’Office 365, [FastTrack](https://fasttrack.microsoft.com/office) est la meilleure façon de déployer Office 365, vous pouvez également connecter et utiliser les [conseillers de déploiement pour les services Office 365](deployment-advisors-for-office-365.md).
  
|**Choisissez une ou plusieurs pour commencer:**||
|:-----|:-----|
| [Configuration système requise pour Office](https://products.office.com/office-system-requirements) |-Microsoft Office Professionnel, Office 365, Office 365 proPlus et chaque application Office pour Windows, Mac, iOS et Android ont des exigences système spécifiques. Assurez-vous que votre matériel et vos logiciels sont conformes à la configuration système minimale requise.|
|**La plupart des** clients connectent leur annuaire local à Office 365. Commencez par la préparation de l'annuaire en [installant et en exécutant IdFix sur votre réseau](https://www.microsoft.com/download/details.aspx?id=36832).<br> Utilisez le [conseiller de connexion AAD](https://aka.ms/aadconnectpwsync) et le Guide de configuration d' [Azure ad Premium](https://aka.ms/aadpguidance) pour obtenir des conseils de configuration personnalisés. <br> |-Les vérifications automatisées par rapport à votre annuaire pour [valider les comptes des personnes sont synchronisées correctement](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> -Recommande des modifications apportées aux objets d'annuaire et propose d'automatiser les modifications pour vous. <br> - [Pour plus d'informations sur l'utilisation de l'outil IdFix](prepare-directory-attributes-for-synch-with-idfix.md). |
|**Lisez** nos conseils en matière de [performances réseau](https://aka.ms/tune) et utilisez nos outils pour vous assurer que vous disposez de la configuration de connectivité et de performances nécessaire pour offrir aux utilisateurs la meilleure expérience.  <br> | -Vérifiez que vous pouvez vous connecter à Office 365, si vous filtrez ou analysez le trafic sortant, vous voudrez comprendre ce que signifie la [gestion des points de terminaison 365 Office](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) pour votre organisation.  <br>  - [Modélisez et testez la capacité de votre réseau](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) ou accédez à un circuit [Azure ExpressRoute pour Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) pour une expérience plus prévisible.   |
|**Utilisez** notre [liste de vérification de planification](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) comme point de départ pour créer votre propre plan de déploiement.  <br> | -Vue d'ensemble des domaines possibles à planifier avec des liens vers des informations de référence ou des procédures pour vous aider à planifier. |
|**Utilisez** le [script de grand élément Exchange Server](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) pour rechercher les éléments de courrier qui peuvent être trop volumineux pour être migrés.  <br> | -Utilise les services Web Exchange pour emprunter l'identité, accéder à la boîte aux lettres pour rechercher les tailles de fichiers que vous spécifiez et vide les résultats dans un fichier CSV. Lisez les [instructions détaillées sur l'utilisation du script](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx). |
|**Tirez** parti des [experts de déploiement Microsoft](https://go.microsoft.com/fwlink/?LinkId=517115) qui peuvent vous aider à commencer à utiliser les nouveaux services et applications.  <br> Utilisez les [assistants de déploiement pour les services Office 365](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) pour obtenir des instructions de configuration personnalisées.  <br> | -Le centre d'intégration fonctionne directement avec les clients et les organisations partenaires. Donnez-leur un appel dès aujourd'hui. |
|**Utilisez** les [modèles et les ressources du centre de réussite Office 365](https://www.microsoft.com/fasttrack/resources) pour partager votre déploiement et les plans d'intégration avec les membres de votre organisation.  <br> | -La communication avec tout le monde avant, pendant et après la transition vers Office 365 est essentielle.  <br> -Utilisez nos modèles, guides et documents pour améliorer vos communications. |
|**Lisez** l'article [principes de connectivité réseau Office 365](https://aka.ms/o365networkingprinciples) pour comprendre les principes de connectivité permettant de gérer le trafic Office 365 en toute sécurité et d'obtenir les meilleures performances possibles.  <br> | -Cet article vous aidera à comprendre les instructions les plus récentes pour optimiser en toute sécurité la connectivité réseau Office 365. |
   
Vous souhaitez plus de ressources pour intégrer Office 365 à votre stratégie de Cloud plus large? Voici les ressources sur l' [architecture informatique du Cloud Microsoft](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## <a name="want-to-talk-with-support"></a>Vous souhaitez parler de la prise en charge?

Nous sommes là pour vous aider, [Contactez le support technique](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) pour les produits professionnels.
