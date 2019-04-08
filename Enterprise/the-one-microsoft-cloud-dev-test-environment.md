---
title: Environnement de développement/test Microsoft Cloud unique
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 'Résumé : Utilisez ce guide de laboratoire de test pour créer un environnement de développement/test qui inclut toutes les offres cloud de Microsoft.'
ms.openlocfilehash: b8ffd01c9d129d4537c82f0e1f74bd7c1be1388b
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037948"
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a>Environnement de développement/test Microsoft Cloud unique

 **Résumé : **Utilisez ce guide de laboratoire de test pour créer un environnement de développement/test qui inclut toutes les offres cloud de Microsoft.
  
Les instructions fournies dans cet article vous permettent de créer un intranet simulé dans les services d’infrastructure de Microsoft Azure, puis d’ajouter des abonnements Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS) et Microsoft Dynamics 365. Vous obtenez ainsi une organisation plus simple qui utilise toutes les offres cloud de Microsoft en même temps dans un environnement de développement/test unique.  
  
![Phase 3 de l’environnement de développement/test cloud One Microsoft avec Azure, Office 365, EMS et Dynamics 365](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
Vous pouvez utiliser la configuration obtenue pour :
  
- Bénéficier d’une intégration de toutes les offres cloud de Microsoft, telles que l’infrastructure d’identité commune fournies par Azure Active Directory (AD).
    
- Évaluer des scénarios complets comprenant plusieurs offres Microsoft Cloud.
    
- Créer une démonstration, une preuve de concept ou une configuration de développement/test qui utilise plusieurs offres Microsoft Cloud.
    
- Développer vos compétences sur Microsoft Cloud à des fins de développement professionnel.
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a>Phase 1 : Créer un intranet simulé et y ajouter Office 365

Suivez les instructions fournies dans [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
La figure 1 montre la configuration obtenue, comprenant Office 365, un Intranet simulé dans les services Azure et la synchronisation d’annuaires à partir d’une forêt AD DS (Active Directory Domain Services).
  
**Figure 1 : Intranet simulé dans Azure avec Office 365**

![Environnement de développement/test d’Office 365 avec DirSync](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> La version d’évaluation d’Azure est de 30 jours. L’abonnement à la version d’évaluation d’Office 365 Entreprise E5 est de 30 jours, et peut être facilement étendue de 30 jours supplémentaires. Pour un environnement de développement/test permanent, créez un abonnement payant Azure et un abonnement payant Office 365 Entreprise E5 avec un petit nombre de licences. 
  
## <a name="phase-2-add-ems"></a>Phase 2 : Ajout d’EMS

Dans cette phase, vous vous inscrivez pour l’abonnement d’évaluation EMS et l’ajoutez à la même organisation que votre abonnement d’évaluation Office 365.
  
1. En utilisant un navigateur de votre ordinateur de bureau ou de CLIENT1, connectez-vous au portail Office 365 ([https://www.office.com](https://www.office.com)) à l’aide des informations d’identification de votre compte Administrateur général.
    
2. Cliquez sur la vignette **Administration**.
    
3. Sous l’onglet **Centre d’administration Office** de votre navigateur, dans le volet de navigation gauche, cliquez sur **Facturation > Acheter des services**.
    
4. Dans la page **Acheter des services**, recherchez l’élément **Enterprise Mobility + Security E5**. Pointez votre souris dessus et cliquez sur **Démarrer l’essai gratuit**.
    
5. Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.
    
6. Dans la page **Réception de la commande**, cliquez sur **Continuer**.
    
> [!NOTE]
> L’abonnement à la version d’évaluation d’Enterprise Mobility + Security E5 est de 90 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un nombre réduit de licences. 
  
Ensuite, activez la licence Enterprise Mobility + Security E5 pour tous les comptes d’utilisateur.
  
1. Sous l’onglet **Centre d’administration Office 365** de votre navigateur, dans le volet de navigation gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
2. Cliquez sur votre compte Administrateur général, puis cliquez sur **Modifier** pour les **licences de produit**.
    
3. Dans le volet **Licences de produit**, activez la licence de produit pour **Enterprise Mobility + Security E5** en sélectionnant **Activer**, cliquez sur **Enregistrer**, cliquez deux fois sur **Fermer**.
    
4. Pour tous vos autres comptes (Utilisateur 1, Utilisateur 2, Utilisateur 3, Utilisateur 4 et Utilisateur 5), suivez les étapes 2 et 3.
    
Votre environnement de développement/test comporte maintenant :
  
- Un intranet simulé exécuté dans les services d’infrastructure Azure.
    
- Des abonnements d’évaluation Office 365 E5 Entreprise et EMS qui partagent la même organisation et le même client Azure AD avec votre liste des comptes d’utilisateur.
    
- Tous vos comptes d’utilisateur activés pour utiliser Office 365 Entreprise E5 et EMS.
    
La figure 2 montre la configuration obtenue, qui ajoute EMS.
  
**Figure 2 : Intranet simulé dans Azure avec Office 365 et EMS**

![Phase 2 de l’environnement de développement/test cloud One Microsoft avec Azure, Office 365 et EMS](media/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a>Phase 3 : Ajouter Dynamics 365

Dans cette phase, vous allez souscrire à l’abonnement d’évaluation Dynamics 365 et l’ajouter à la même organisation que vos abonnements d’évaluation Office 365 et EMS.
  
1. En utilisant un navigateur de votre ordinateur de bureau ou de CLIENT1, connectez-vous au portail Office 365 ([https://www.office.com](https://www.office.com)) à l’aide des informations d’identification de votre compte Administrateur général.
    
2. Cliquez sur la vignette **Administration**.
    
3. Dans l’onglet **Centre d’administration Microsoft 365**, dans le volet de navigation de gauche, cliquez sur **Facturation > Acheter des services**.
    
4. Dans la page **Acheter des services**, recherchez l’élément **Dynamics 365 Plan 1 Enterprise Edition**. Placez le curseur de la souris dessus et cliquez sur **Démarrer l’essai gratuit**.
    
5. Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.
    
6. Dans la page **Réception de la commande**, cliquez sur **Continuer**.
    
> [!NOTE]
> L’abonnement d’évaluation Dynamics 365 Plan 1 Enterprise Edition est valide pendant 30 jours. Vous pouvez facilement étendre l’abonnement d’évaluation pour une période supplémentaire de 30 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un nombre réduit de licences. 
  
Procédez comme suit pour affecter des licences Dynamics 365 aux comptes de l’administrateur général, ainsi qu’aux comptes Utilisateur 2 et Utilisateur 3 afin de leur attribuer le rôle d’administrateur système.
  
1. Dans l’onglet **Centre d’administration Microsoft 365**, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
2. Dans la liste des utilisateurs actifs, sélectionnez votre compte Administrateur général, puis cliquez sur **Modifier** pour **Licences de produits**.
    
3. 	Dans le volet **Licences de produit**, activez la licence de produit pour **Dynamics 365 Plan 1 Enterprise Edition** en sélectionnant **Activer**, cliquez sur **Enregistrer**, puis cliquez deux fois sur **Fermer**.
    
4. Suivez les étapes 2 et 3 pour les comptes Utilisateur 2 et Utilisateur 3.
    
5. Fermez l’onglet **Centre d’administration Microsoft 365**.
    
Lors de cette phase, vous allez configurer les comptes Utilisateur 2 et Utilisateur 3 en tant qu’administrateurs système de Dynamics 365.
  
1. Sur l’onglet **Centre d’administration Office** de votre navigateur, cliquez sur **Centres d’administration** dans le volet de navigation de gauche, puis sur **Dynamics 365**.
    
    Vous devrez peut-être attendre la fin de l’approvisionnement de Dynamics 365 avant de le voir apparaître dans le menu.
    
2. Sur l’onglet Dynamics 365, cliquez sur **Toutes ces options**, puis sur **Terminer l’installation**.
    
    Attendez la fin de l’installation.
    
    Une fois l’installation terminée, un tableau de bord Activité de ventes reposant sur des exemples de données inclus dans l’abonnement d’essai est affiché. Visionnez la **vidéo de présentation de l’essai**. Fermez la fenêtre de la vidéo lorsque vous avez terminé.
    
3. Dans la barre d’outils située en haut de l’écran, cliquez sur la flèche vers le bas en regard de **Ventes**, sur **Paramètres** puis sur **Sécurité**.
    
4. Dans la page **Sécurité**, cliquez sur **Utilisateurs**.
    
5. Dans la liste des utilisateurs, cliquez sur **Utilisateur 2**.
    
6. Dans la barre d’outils, cliquez sur **Gérer les rôles**.
    
7. Dans **Gérer les rôles**, cliquez sur **Administrateur système**, puis sur **OK**.
    
8. Dans la barre d’outils en haut de l’écran, cliquez sur **Sécurité**.
    
9. Répétez les étapes 5 à 8 pour le compte Utilisateur 3.
    
10. Fermez l’onglet **Utilisateur :User3**.
    
> [!NOTE]
> Le rôle d’administrateur système Dynamics 365 a été automatiquement attribué à votre compte d’administrateur général Office 365. 
  
Votre environnement de développement/test comporte maintenant :
  
- Un intranet simulé exécuté dans les services d’infrastructure Azure.
    
- Des abonnements à la version d’évaluation d’Office 365 E5 Enterprise, d’EMS et de Dynamics 365 qui partagent la même organisation et le même client Azure AD avec votre liste des comptes d’utilisateur.
    
- Tous vos comptes d’utilisateur activés pour utiliser Office 365 Entreprise E5 et EMS.
    
- Vos comptes d’administrateur général d’entreprise, Utilisateur 2 et Utilisateur 3 peuvent utiliser Dynamics 365, et sont également administrateurs système de Dynamics 365.
    
La figure 3 présente la configuration finale.
  
**Figure 3 : Intranet simulé dans Azure avec Office 365, EMS et Dynamics 365**

![Phase 3 de l’environnement de développement/test cloud One Microsoft avec Azure, Office 365, EMS et Dynamics 365](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a>Étapes suivantes

Vous pouvez maintenant tester différentes configurations avec votre environnement de développement/test Microsoft Cloud. Voici quelques suggestions :
  
- [Stratégies de gestion des applications mobiles pour votre environnement de développement/test Office 365 et EMS](https://technet.microsoft.com/library/mt764059.aspx)
    
- [Intégration d’Exchange Online pour votre environnement de développement/test Office 365 et Dynamics 365](https://technet.microsoft.com/library/mt798313.aspx)
    
- [Créer un réseau simulé intersites dans les services d’infrastructure Azure pour héberger les charges de travail sur serveur](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ressources relatives à l’architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Solutions hybrides](hybrid-solutions.md)
  
[Solutions de sécurité](security-solutions.md)





