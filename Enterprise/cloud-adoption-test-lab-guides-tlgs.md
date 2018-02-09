---
title: "Guides de laboratoire de test d’adoption cloud"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: "Résumé : Utilisez ces adoption du cloud Guides de laboratoires de Test (TLGs) pour définir les démonstration, preuve de concept, ou les environnements de développement/test pour Office 365, la mobilité d’entreprise + sécurité (EMS), Dynamics 365 et produits Office Server."
ms.openlocfilehash: d13012ebbee05eea903d3ae2d6198b503ad2bf39
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a>Guides de laboratoire de test d’adoption cloud

 **Résumé :** Ces Guides de laboratoires de Test (TLGs) adoption du nuage permet de paramétrer de démonstration, la preuve de concept, ou les environnements de développement/test pour Office 365, la mobilité d’entreprise + sécurité (EMS), Dynamics 365 et produits Office Server.
  
TLGs vous aider à obtenir rapidement des informations sur les produits Microsoft. Elles conviennent parfaitement pour les situations où vous devez évaluer une technologie ou une configuration avant de décider si elle est adapté à votre place ou avant que vous le présentez aux utilisateurs. L’expérience pratique « je créés il moi-même et il fonctionne » vous aide à comprendre les exigences de déploiement d’un nouveau produit ou la solution afin de mieux planifier pour qui l’héberge dans la production.
  
Les guides de laboratoire de test créent également des environnements représentatifs pour le développement et le test d’applications, également connus sous le nom d’environnements de développement/test.
  
![Guides de laboratoire de test dans le cloud de Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Avant de plonger, consultez ces ressources supplémentaires :
  
- Permet d’afficher la session de Microsoft Virtual Academy [expérience le Cloud de Microsoft avec les Guides de laboratoires de Test Adoption Cloud](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) (22 minutes seulement).
    
- Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.
    
## <a name="office-365-devtest-environment"></a>Environnement de développement/test Office 365
<a name="O365"> </a>

Utilisez les articles suivants pour créer votre environnement de développement/test Office 365 :
  
- [Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
    
    Créez un intranet simplifié s’exécutant dans les services d’infrastructure Microsoft Azure. Cette étape est facultative si vous souhaitez créer une configuration d’entreprise simulée.
    
- [Environnement de développement/test Office 365](office-365-dev-test-environment.md)
    
    Créer un abonnement d’évaluation d’Office 365 entreprise E5, ce que vous pouvez faire à partir de votre ordinateur ou à partir d’un intranet simplifié en cours d’exécution dans les services d’infrastructure Azure.
    
- [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
    Installez et configurez Azure AD Connect pour la synchronisation d’annuaires avec synchronisation de mot de passe. Cette étape est facultative si vous souhaitez créer une configuration d’entreprise simulée.
    
Pour votre environnement de développement/test Office 365, utiliser ces articles pour démontrer les fonctionnalités d’entreprise de Office 365 :
  
- [Plusieurs facteurs d’authentification pour votre environnement de développement/test d’Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Configurez et testez l’authentification secondaire à l’aide d’un message texte envoyé à votre smartphone pour un compte de votre abonnement Office 365.
    
- [Identité fédérée pour votre environnement de développement/test Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Configurez l’authentification fédérée et effectuez-en des démonstrations avec les comptes d’un domaine Active Directory Windows Server.
    
- [Application du nuage sécurité pour votre environnement de développement/test d’Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Configurer et illustrer l’Office 365 nuage App sécurité, ce qui vous permet de créer des stratégies pour surveillent et vous informent des activités suspectes dans votre abonnement à Office 365.
    
- [Avancées de protection contre les menaces pour votre environnement de développement/test d’Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Configurez et démontrez la protection avancée contre les menaces Office 365, qui est une fonctionnalité d’Exchange Online Protection (EOP) qui vous permet de lutter contre les programmes malveillants dans votre environnement de messagerie.
    
- [E-Discovery avancée pour votre environnement de développement/test d’Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Ajoutez des exemples de données et démontrez Advanced eDiscovery, ce qui vous permet de trouver et d’analyser rapidement les données stockées dans Office 365, notamment la messagerie et les documents.
    
- [Protection des fichiers sensibles dans l’environnement de développement/test d’Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    Montrez comment utiliser la gestion des droits relatifs à l’information d’Office 365 pour protéger les données dans des documents sensibles, même si elles sont publiées par inadvertance dans des dossiers de documents incorrects.
    
- [La classification des données et le marquage de l’environnement de développement/test d’Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Montrez comment le client de Protection d’informations Azure (AIP) peut servir à classer les documents avec différents niveaux de sécurité.
    
- [Environnement de développement/test isolé de SharePoint Online équipe site](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Montrez comment créer un site d’équipe SharePoint en ligne qui est isolé du reste de l’organisation des ressources hautement confidentielles ou sensibles.
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a>Environnement de développement/test Microsoft 365 Entreprise
<a name="O365"> </a>

Créer un environnement de développement/test pour les scénarios [d’Entreprise de Microsoft 365](https://docs.microsoft.com/microsoft-365-enterprise/) avec ces articles :
  
- [L’environnement de développement/test Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
    
    Créez l’environnement initial qui comprend un ordinateur exécutant Windows 10 entreprise, Office 365 E5 et EMS E5.
    
- [Stratégies MAM pour votre environnement de développement/test Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    Créez des groupes d’utilisateurs et des stratégies de gestion des applications mobiles pour les appareils ioS et Android.
    
- [Inscrire les périphériques iOS ou Android dans votre environnement de développement/test Microsoft Enterprise 365](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    Inscrivez des appareils iOS ou Android et gérez-les à distance.
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Environnement de développement/test Office 365 et Dynamics 365
<a name="O365_D365"> </a>

Ajoutez un abonnement à la version d’évaluation de Dynamics 365, et testez des scénarios et fonctionnalités intégrés Office 365 et Dynamics 365 à l’aide des rubriques suivantes :
  
- [Environnement de développement/test Office 365 et Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
    
    Ajoutez un abonnement à la version d’évaluation de Dynamics 365, ainsi que des licences Dynamics 365 et des autorisations à vos comptes d’utilisateur.
    
- [Intégration d’Exchange Online pour votre environnement de développement/test Office 365 et Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    Configurer, puis montrez comment Office 365 et Dynamics 365 fonctionnent ensemble des boîtes aux lettres dans Exchange Online.
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>Environnement de développement/test Microsoft Cloud unique
<a name="O365_D365"> </a>

Créer un environnement de développement/test qui inclut toutes les offres en nuage de Microsoft : Office 365, Azure, EMS et Dynamics 365. Pour les instructions étape par étape, consultez [environnement de développement/test l’un nuage de Microsoft](the-one-microsoft-cloud-dev-test-environment.md) .
  
## <a name="simulated-cross-premises-devtest-environments"></a>Environnements de développement/test intersites
<a name="O365_D365"> </a>

Vous pouvez créer un environnement de développement/test intersite, qui comprend un réseau virtuel Azure et un réseau local simulé, avec les articles suivants :
  
- [Réseau virtuel de coexistence simulé dans Azure](simulated-cross-premises-virtual-network-in-azure.md)
    
    Créez un intranet simulé connecté à un réseau virtuel Azure dans une configuration de cloud hybride.
    
- [Intranet SharePoint Server 2016 dans l’environnement de développement/test Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Créez une batterie de serveurs SharePoint Server 2016 à un seul serveur dans le réseau virtuel Azure et testez la connectivité et l’administration à partir du réseau local simulé.
    
## <a name="additional-cloud-based-devtest-environments"></a>Autres environnements de développement/test dans le cloud
<a name="ADD_TLGs"> </a>

Voici les autres environnements de développement/test dans le cloud que vous pouvez créer dans des services d’infrastructure Azure :
  
- [Environnement de développement/test SharePoint Server 2016 dans Azure](https://technet.microsoft.com/library/mt723354.aspx)
    
    Créez une batterie de serveurs SharePoint Server 2016 à un seul serveur dans des services d’infrastructure Azure.
    
- [Environnement de développement/test Exchange 2016 dans Azure](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    Créez un seul serveur Exchange 2016 dans des services d’infrastructure Azure.
    
- [Environnements de développement/test de SharePoint Server 2013 dans Azure](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    Créez des batteries de serveurs SharePoint Server 2013 de base et haute disponibilité dans des services d’infrastructure Azure.
    
**Participer à la discussion**

|**Contactez-nous**|**Description**|
|:-----|:-----|
|**De quelles solutions avez-vous besoin ?** <br/> |Nous sommes en train de créer du contenu pour les solutions qui s'étendent sur plusieurs produits et services Microsoft. Donnez-nous votre avis sur nos solutions entre serveurs ou demandez des solutions spécifiques en envoyant un courrier électronique à [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).<br/> |
|**Participer à la discussion sur les solutions** <br/> |Si vous êtes passionné par les solutions basées sur le cloud, rejoignez le conseil consultatif de l’adoption cloud (CAAB) pour interagir avec une communauté vaste et dynamique de développeurs de contenu Microsoft, de professionnels du secteur et de clients venant du monde entier. Pour participer, ajoutez-vous en tant que membre de l’espace [CAAB (Conseil consultatif de l’adoption cloud)](https://aka.ms/caab) de la communauté Microsoft Tech et envoyez-nous un message électronique à l’adresse [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Tout le monde peut lire le contenu lié à la communauté sur le [blog CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Toutefois, les membres CAAB reçoivent des invitations à des webinaires privés qui décrivent les nouvelles solutions et ressources relatives à l’adoption cloud.<br/> |
|**Obtenir l'image que vous voyez ici** <br/> |Si vous voulez obtenir une copie modifiable de l’image que vous voyez dans cet article, nous serons ravis de vous l’envoyer. Envoyez-nous votre demande par courrier électronique, en incluant l’URL et le titre de l’illustration, à [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).<br/> |
   
## <a name="see-also"></a>Voir aussi

<a name="ADD_TLGs"> </a>

[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Modèles architecturaux pour SharePoint, Exchange, Skype Entreprise et Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Solutions hybrides](hybrid-solutions.md)


