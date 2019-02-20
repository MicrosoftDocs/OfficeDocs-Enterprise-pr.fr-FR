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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Décrit la synchronisation d'annuaires avec Office 365, le nettoyage Active Directory et l'outil Azure Active Directory Connect.
ms.openlocfilehash: 5f380efe3293d25e2e208c5fef836a89f6fa0cc8
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085283"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Planifier la synchronisation d’annuaires pour Office 365
En fonction des besoins de l'entreprise et des exigences techniques, la synchronisation d'annuaires est le choix de mise en service le plus courant pour les clients d'entreprise qui migrent vers Office 365. La synchronisation d'annuaires permet de gérer les identités dans l'annuaire Active Directory local et toutes les mises à jour apportées à cette identité sont synchronisées avec Office 365.
  
Il existe deux éléments à garder à l'esprit lorsque vous planifiez une implémentation de la synchronisation d'annuaires, y compris la préparation d'annuaires, ainsi que les exigences et les fonctionnalités d'Azure Active Directory. La préparation de l'annuaire couvre un certain nombre de domaines. Elles incluent les mises à jour d'attribut, l'audit et la planification du placement des contrôleurs de domaine. La planification et les exigences incluent la détermination des autorisations requises, la planification des scénarios multiforêt/annuaire, la planification de la capacité et la synchronisation bidirectionnelle.
  
## <a name="office-365-identity-models"></a>Modèles d'identité Office 365
Office 365 utilise deux modèles principaux d'authentification et d'identité: l'authentification Cloud et l'authentification fédérée.
  
### <a name="cloud-authentication"></a>Authentification Cloud
[Identité Cloud](about-office-365-identity.md) : créer et gérer des utilisateurs dans le centre d'administration Office 365, vous pouvez également utiliser Windows PowerShell ou Azure Active Directory pour gérer vos utilisateurs. 
  
[Synchronisation de hachage de mot de passe avec authentification unique transparente](about-office-365-identity.md) : le moyen le plus simple d'activer l'authentification pour les objets d'annuaire locaux dans Azure ad. La synchronisation de hachage de mot de passe (hachage) vous permet de synchroniser vos objets de compte d'utilisateur Active Directory sur site avec Office 365 et de gérer vos utilisateurs en local. 
  
[Authentification directe avec authentification unique transparente](about-office-365-identity.md) : fournit une validation de mot de passe simple pour les services d'authentification Azure ad à l'aide d'un agent logiciel exécuté sur un ou plusieurs serveurs locaux afin de valider directement les utilisateurs avec votre Active Directory en local. 
  
### <a name="federated-authentication"></a>Authentification fédérée
[Identité fédérée avec Active Directory Federation Services AD FS](about-office-365-identity.md) -principalement pour les grandes organisations d'entreprise avec des exigences d'authentification plus complexes, les objets d'annuaire locaux sont synchronisés avec Office 365 et les comptes d'utilisateurs sont géré en local. 
  
Les [fournisseurs d'identité et d'authentification tiers](about-office-365-identity.md) -les objets d'annuaire locaux peuvent être synchronisés avec Office 365 et l'accès aux ressources de Cloud est principalement géré par un fournisseur d'identité tiers (IDP). 
  
## <a name="active-directory-cleanup"></a>Nettoyage Active Directory
Pour garantir une transition transparente vers Office 365 à l'aide de la synchronisation, nous vous recommandons vivement de préparer votre forêt Active Directory avant de commencer le déploiement de la synchronisation d'annuaires Office 365.
  
Lorsque vous configurez la [synchronisation d'annuaires dans Office 365](set-up-directory-synchronization.md), l'une des étapes consiste à [Télécharger et à exécuter l'outil IdFix](install-and-run-idfix.md). Vous pouvez utiliser l'outil IdFix pour faciliter le [nettoyage d'annuaire](prepare-directory-attributes-for-synch-with-idfix.md).
  
Le nettoyage de votre annuaire doit se concentrer sur les tâches suivantes:

- Supprimez les attributs **ProxyAddress** et **userPrincipalName** en double.
- Mettez à jour les attributs **userPrincipalName** vides ou non valides avec des attributs **userPrincipalName** valides.
- Supprimer les caractères non valides et douteables dans les attributs **GivenName**, Surname ( **sn** ), **sAMAccountName**, **DisplayName**, **mail**, **proxyAddresses**, **mailnickname**et **userPrincipalName** ceux. Pour plus d'informations sur la préparation des attributs, voir [liste des attributs synchronisés par l'outil de synchronisation Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).
    
    > [!NOTE]
    > Il s'agit des mêmes attributs que ceux qui sont synchronisés avec Azure AD Connect. 
  
## <a name="multiforest-deployment-considerations"></a>Considérations relatives au déploiement à forêts multiples
Pour plusieurs forêts et options d'authentification unique, utilisez [l'installation personnalisée d'Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Si votre organisation dispose de plusieurs forêts pour l'authentification (forêts d'ouverture de session), nous vous recommandons vivement les suivants:
  
- **Évaluez la consolidation de vos forêts.** En règle générale, il y a plus de charge nécessaire pour gérer plusieurs forêts. À moins que votre organisation n'ait des contraintes de sécurité qui dictent le besoin de forêts distinctes, envisagez de simplifier votre environnement local.
- **Utilisez uniquement dans votre forêt d'ouverture de session principale.** EnVisagez de déployer Office 365 uniquement dans votre forêt d'ouverture de session principale pour le déploiement initial d'Office 365. 
    
Si vous ne pouvez pas consolider votre déploiement Active Directory à forêts multiples ou si vous utilisez d'autres services d'annuaire pour gérer les identités, vous pourrez peut-être les synchroniser avec l'aide de Microsoft ou d'un partenaire.
  
Pour plus d'informations, reportez-vous à la rubrique [multi-Forest Directory Sync with Single Sign-on Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321).
  
## <a name="directory-integration-tools"></a>Outils d'intégration d'annuaire
La synchronisation d'annuaires est la synchronisation des objets d'annuaire (utilisateurs, groupes et contacts) à partir de votre environnement Active Directory local vers l'infrastructure d'annuaire Office 365. Consultez la rubrique [Outils d'intégration d'annuaire](https://go.microsoft.com/fwlink/p/?LinkID=510956) pour obtenir la liste des outils disponibles et leur fonctionnalité. L'outil recommandé est [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).
  
Lorsque les comptes d'utilisateur sont synchronisés avec le répertoire Office 365 pour la première fois, ils sont marqués comme non activés. Ils ne peuvent pas envoyer ou recevoir des courriers électroniques, et ils ne consomment pas de licences d'abonnement. Lorsque vous êtes prêt à affecter des abonnements Office 365 à des utilisateurs spécifiques, vous devez les sélectionner et les activer en affectant une licence valide.
  
La synchronisation d'annuaires est requise pour les fonctionnalités et fonctionnalités suivantes:
  
- SSO
    
- Coexistence Lync
    
- Déploiement Exchange hybride, notamment:
    
  - Liste d'adresses globale (GAL) entièrement partagée entre votre environnement Exchange local et Office 365.
  - Synchronisation des informations GAL provenant de différents systèmes de messagerie.
  - Possibilité d'ajouter et de supprimer des utilisateurs des offres de services Office 365. Cette opération requiert les éléments suivants:
  - La synchronisation bidirectionnelle doit être configurée lors de la configuration de la synchronisation d'annuaires. Par défaut, les outils de synchronisation d'annuaires écrivent des informations d'annuaire uniquement dans le Cloud. Lorsque vous configurez la synchronisation bidirectionnelle, vous activez la fonctionnalité d'écriture différée de sorte qu'un nombre limité d'attributs d'objets soient copiés à partir du Cloud, puis réécrits dans votre service Active Directory local. L'écriture différée est également appelée mode hybride Exchange. 
  - Un déploiement Exchange hybride local
  - Possibilité de déplacer certaines boîtes aux lettres utilisateur vers Office 365 tout en conservant les autres boîtes aux lettres utilisateur en local.
  - Les expéditeurs approuvés et les expéditeurs bloqués en local sont répliqués vers Office 365.
  - Fonctionnalité de délégation de base et d’envoi de courrier « de la part de ».
  - Vous disposez d'une solution d'authentification multifacteur ou de carte à puce sur site intégrée.
    
- Synchronisation de photos, de miniatures, de salles de conférence et de groupes de sécurité