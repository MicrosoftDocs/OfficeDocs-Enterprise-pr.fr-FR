---
title: Tester Office 365 à l’aide des Guides de laboratoire de test relatifs à l’adoption de Microsoft Cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/09/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Résumé : Utilisez ces guides de laboratoire de test relatifs à l’adoption de Microsoft Cloud pour configurer une démonstration, une étude de faisabilité ou des environnements de développement/test pour Office 365.'
ms.openlocfilehash: 37a99c313339f0894bf6fba0040bf2f7c2160fa6
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162377"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a>Tester Office 365 à l’aide des Guides de laboratoire de test relatifs à l’adoption de Microsoft Cloud

 **Résumé :** Utilisez ces guides de laboratoire de test relatifs à l’adoption de Microsoft Cloud pour configurer une démonstration, une étude de faisabilité ou des environnements de développement/test pour Office 365.
  
Les guides de laboratoire de test vous permettent d’avoir un aperçu rapide des produits Microsoft. Ils sont particulièrement utiles lorsque vous avez besoin d’évaluer une technologie ou une configuration avant de décider si elle vous convient et de lancer la conception, la planification ainsi que le déploiement pour vos utilisateurs. L’expérience pratique, suite à laquelle vous pourrez dire « Je l’ai créé moi-même et ça fonctionne », vous aide à comprendre les exigences de déploiement d’un nouveau produit ou d’une nouvelle solution de façon à garantir une meilleure planification pour son hébergement dans un environnement de production.
  
Les guides de laboratoire de test créent également des environnements représentatifs pour le développement et le test d’applications, également connus sous le nom d’environnements de développement/test.
  
![Guides de laboratoire de test dans Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles dans le Guide de Laboratoire Test Office 365.
    
## <a name="office-365-devtest-environment"></a>Environnement de développement/test Office 365

Utilisez les articles suivants pour créer votre environnement de développement/test Office 365 :
  
- [Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
    
    Créez un intranet simplifié s’exécutant dans les services d’infrastructure Microsoft Azure. Cette étape est facultative si vous souhaitez créer une configuration d’entreprise simulée.
    
- [Environnement de développement/test Office 365](office-365-dev-test-environment.md)
    
    Créez un abonnement d’évaluation Office 365 Entreprise E5 à partir de votre ordinateur ou d’un intranet simplifié exécuté dans des services d’infrastructure Azure.
    
- [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
    Installez et configurez Azure AD Connect pour la synchronisation d’annuaires avec synchronisation de hachage de mot de passe. Cette étape est facultative si vous souhaitez créer une configuration d’entreprise simulée.
    
Pour votre environnement de développement/test Office 365, utilisez les articles suivants pour montrer les fonctionnalités d’entreprise d’Office 365 :
  
- [Authentification multifacteur pour votre environnement de développement/test Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Configurez et testez l’authentification secondaire à l’aide d’un message texte envoyé à votre smartphone pour un compte de votre abonnement Office 365.
    
- [Identité fédérée pour votre environnement de développement/test Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Configurez l’authentification fédérée et effectuez-en des démonstrations avec les comptes d’un domaine AD DS (Active Directory Domain Services).
    
- [Protection avancée contre les menaces pour votre environnement de développement/test Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Configurez et démontrez la protection avancée contre les menaces Office 365, qui est une fonctionnalité d’Exchange Online Protection (EOP) qui vous permet de lutter contre les programmes malveillants dans votre environnement de messagerie.
    
- [Advanced eDiscovery pour votre environnement de développement/test Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Ajoutez des exemples de données et démontrez Advanced eDiscovery, ce qui vous permet de trouver et d’analyser rapidement les données stockées dans Office 365, notamment la messagerie et les documents.
    
- [Protection des fichiers sensibles dans l’environnement de développement/test Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    Montrez comment utiliser la gestion des droits relatifs à l’information d’Office 365 pour protéger les données dans des documents sensibles, même si elles sont publiées par inadvertance dans des dossiers de documents incorrects.
    
- [Classification et étiquetage des données dans l’environnement de développement/test Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Démontrez comment le client Azure Information Protection peut servir à classer des documents avec différents niveaux de sécurité.
    
- [Site d’équipe SharePoint Online isolé dans votre environnement de développement/test](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Démontrez comment créer un site d’équipe SharePoint Online isolé du reste de l’organisation pour les ressources sensibles ou hautement confidentielles.
    

## <a name="simulated-cross-premises-devtest-environments"></a>Environnements de développement/test intersites

Vous pouvez créer un environnement de développement/test intersite, qui comprend un réseau virtuel Azure et un réseau local simulé, avec les articles suivants :
  
- [Réseau virtuel intersites simulé dans Azure](simulated-cross-premises-virtual-network-in-azure.md)
    
    Créez un intranet simulé connecté à un réseau virtuel Azure dans une configuration de cloud hybride.
    
- [Intranet SharePoint Server 2016 dans un environnement de développement/test Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Créez une batterie de serveurs SharePoint Server 2016 à un seul serveur dans le réseau virtuel Azure et testez la connectivité et l’administration à partir du réseau local simulé.
    
## <a name="sharepoint-server-2016-devtest-environments"></a>Environnements de développement/test SharePoint Server 2016

Voici les environnements de développement/test SharePoint Server 2016 que vous pouvez créer dans des services d’infrastructure Azure :
  
- [Environnement de développement/test SharePoint Server 2016 dans Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)
    
    Créez une batterie de serveurs SharePoint Server 2016 à un seul serveur dans des services d’infrastructure Azure.

- [Intranet SharePoint Server 2016 dans un environnement de développement/test Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)
    
    Créez une batterie de serveurs SharePoint Server 2016 à un seul serveur dans des services d’infrastructure Azure et accédez-y à partir d’un intranet simulé.


## <a name="the-microsoft-365-enterprise-devtest-environments"></a>Environnements de développement/test Microsoft 365 Entreprise

Créez un environnement de développement/test pour [Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/) en vous aidant de [ces articles](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).  
    
## <a name="see-also"></a>Voir aussi

[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Ressources relatives à l’architecture informatique Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Solutions hybrides](hybrid-solutions.md)
