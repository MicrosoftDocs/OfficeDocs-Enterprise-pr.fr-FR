---
title: Planifier la synchronisation d’annuaires pour Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Décrit la synchronisation d’annuaires avec Office 365, nettoyage d’Active Directory et l’outil d’Azure Active Directory se connecter.
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540482"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Planifier la synchronisation d’annuaires pour Office 365
En fonction des besoins de l’entreprise et les exigences techniques, la synchronisation d’annuaires est le choix de mise en service les plus courants pour les entreprises qui passent à Office 365. Permet à la synchronisation d’annuaires identités à gérer dans Active Directory sur site et toutes les mises à jour à cette identité sont synchronisés avec Office 365.
  
Il existe quelques éléments à prendre en compte lorsque vous planifiez une implémentation de la synchronisation d’annuaires, y compris la préparation d’un répertoire et les exigences et les fonctionnalités d’Azure Active Directory. Préparation d’annuaire traite de plusieurs zones. Elles incluent les mises à jour d’attribut, l’audit et la planification du placement des contrôleurs de domaine. Configuration requise et les fonctionnalités de planification inclut l’identification des autorisations requises, la planification de scénarios de répertoire/multiforest, la planification de capacité et la synchronisation bidirectionnelle.
  
## <a name="office-365-identity-models"></a>Modèles d’identité Office 365
Office 365 utilise deux modèles d’authentification et identité principales : l’authentification et l’authentification fédérée en nuage.
  
### <a name="cloud-authentication"></a>Authentification dans le nuage
[Identité de nuage](about-office-365-identity.md) - créer et gérer des utilisateurs dans le centre d’administration d’Office 365, vous pouvez également utiliser Windows PowerShell ou Azure Active Directory pour gérer vos utilisateurs. 
  
[Hachage de mot de passe de synchronisation avec transparente unique-](about-office-365-identity.md) - la façon la plus simple pour activer l’authentification pour les objets d’annuaire local dans Azure AD. Avec la synchronisation de hachage de mot de passe (pH), vous synchronisez vos objets compte d’utilisateur Active Directory local avec Office 365 et gérer vos utilisateurs locaux. 
  
[L’authentification directe avec transparente unique-](about-office-365-identity.md) - fournit une validation de mot de passe simple pour les services d’authentification Azure AD à l’aide d’un agent logiciel s’exécutant sur un ou plusieurs serveurs locaux pour valider les utilisateurs directement avec votre Active Directory sur site. 
  
### <a name="federated-authentication"></a>Authentification fédérée
[Identité fédérée avec Active Directory Federation Services AD FS](about-office-365-identity.md) - principalement pour les grandes organisations d’entreprise avec des exigences d’authentification plus complexes, objets d’annuaire sont synchronisés avec Office 365 et locaux sont des comptes d’utilisateurs géré local. 
  
[Fournisseurs d’authentification et d’identité tiers](about-office-365-identity.md) - annuaire local objets peuvent être synchronisés avec Office 365 et l’accès aux ressources en nuage est principalement géré par un fournisseur d’identité de tiers (IdP). 
  
## <a name="active-directory-cleanup"></a>Nettoyage Active Directory
Pour garantir une transition transparente vers Office 365 à l’aide de la synchronisation, nous vous recommandons de préparer votre forêt Active Directory avant de commencer votre déploiement de la synchronisation d’annuaire Office 365.
  
Lorsque vous [configurer la synchronisation d’annuaires dans Office 365](set-up-directory-synchronization.md), une des étapes consiste à [télécharger et exécuter l’outil IdFix](install-and-run-idfix.md). Vous pouvez utiliser l’outil IdFix pour faciliter le [nettoyage d’annuaire](prepare-directory-attributes-for-synch-with-idfix.md).
  
Nettoyage de votre annuaire doit se concentrer sur les tâches suivantes :

- Supprimez les attributs **proxyAddress** et **userPrincipalName** en double.
- Mettez à jour les attributs **userPrincipalName** vides ou non valides avec des attributs **userPrincipalName** valides.
- Supprimer les caractères non valides et suspects dans le **prénom**, nom ( **sn** ), **sAMAccountName**, **displayName**, **messagerie**, **proxyAddresses**, **mailNickname**et **userPrincipalName** attributs. Pour plus d’informations sur la préparation des attributs, consultez la [liste des attributs qui sont synchronisés par l’outil de synchronisation Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).
    
    > [!NOTE]
    > Ce sont les mêmes attributs Azure AD Connect est synchronisé. 
  
## <a name="multiforest-deployment-considerations"></a>Considérations relatives au déploiement à forêts multiples
Pour plusieurs forêts et les options d’authentification unique, utilisez [personnalisé Installation d’Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Si votre organisation dispose de plusieurs forêts pour l’authentification (forêts d’ouverture de session), nous vous recommandons les éléments suivants :
  
- **Évaluer consolider vos forêts.** En règle générale, il est plus de charge requis pour la maintenance de plusieurs forêts. Sauf si votre organisation a des contraintes de sécurité qui déterminent la nécessité de forêts distinctes, pensez à simplifier votre environnement local.
- **Utilisées uniquement dans votre forêt de connexion principale.** Envisagez de déployer Office 365 uniquement dans votre forêt de connexion principale pour le déploiement initial d’Office 365. 
    
Si vous ne pouvez pas consolider votre déploiement Active Directory à forêts multiples ou utilisez autres services d’annuaire pour gérer des identités, vous pourrez synchroniser ces à l’aide de Microsoft ou d’un partenaire.
  
Pour plus d’informations, voir la [Synchronisation d’annuaire à forêts multiples avec scénario d’authentification unique](https://go.microsoft.com/fwlink/p/?LinkId=525321).
  
## <a name="directory-integration-tools"></a>Outils de l’intégration d’annuaire
La synchronisation d’annuaires est la synchronisation des objets d’annuaire (utilisateurs, groupes et contacts) à partir de votre environnement d’Active Directory sur site à l’infrastructure d’annuaire Office 365. Voir [Outils de l’intégration d’annuaire](https://go.microsoft.com/fwlink/p/?LinkID=510956) pour obtenir la liste des outils disponibles et leurs fonctionnalités. L’outil recommandé d’utiliser est [Azure Active Directory se connecter](https://go.microsoft.com/fwlink/?LinkId=525323).
  
Lorsque les comptes d’utilisateurs sont synchronisées avec l’annuaire Office 365 pour la première fois, elles sont marquées comme non activée. Ils ne peuvent pas envoyer ou recevoir du courrier électronique, et ils n’utilisent pas de licences d’abonnement. Lorsque vous êtes prêt à affecter des abonnements Office 365 à des utilisateurs spécifiques, vous devez sélectionner et les activer en affectant une licence valide.
  
La synchronisation d’annuaires est requise pour les fonctionnalités suivantes :
  
- SSO
    
- Coexistence Lync
    
- Déploiement Exchange hybride, notamment :
    
  - Entièrement partagée liste d’adresses globale (LAG) entre votre environnement Exchange local sur et d’Office 365.
  - Synchronisation des informations GAL provenant de différents systèmes de messagerie.
  - La possibilité d’ajouter et supprimer des utilisateurs d’offres de services Office 365. Cela nécessite les éléments suivants :
  - Synchronisation bidirectionnelle doit être configurée lors de l’installation de la synchronisation de répertoire. Par défaut, outils de synchronisation d’annuaire écrivent les informations d’annuaire uniquement vers le nuage. Lorsque vous configurez la synchronisation bidirectionnelle, vous activez la fonctionnalité d’écriture différée afin qu’un nombre limité d’attributs de l’objet est copié à partir du nuage et puis réécrit les dans votre annuaire Active Directory local. Écriture différée est également appelée le mode Exchange hybride. 
  - Un déploiement sur site Exchange hybride
  - Possibilité de déplacer certaines boîtes aux lettres utilisateur vers Office 365 tout en conservant les autres utilisateurs boîtes aux lettres locales.
  - Les expéditeurs fiables et expéditeurs bloqués locaux sont répliqués vers Office 365.
  - Fonctionnalité de délégation de base et d’envoi de courrier « de la part de ».
  - Vous disposez d’une solution d’authentification intégrée locale carte à puce ou de plusieurs facteurs.
    
- Synchronisation de photos, miniatures, salles de conférence et groupes de sécurité