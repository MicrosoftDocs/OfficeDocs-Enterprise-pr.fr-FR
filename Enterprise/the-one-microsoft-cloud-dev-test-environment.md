---
title: "Environnement de développement/test Microsoft Cloud unique"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: "Résumé : Utilisez ce Guide de laboratoire de Test pour créer un environnement de développement/test qui inclut toutes les offres en nuage de Microsoft."
ms.openlocfilehash: 8bd3f92abd3752555443534bbe81330727ed3eb5
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a>Environnement de développement/test Microsoft Cloud unique

 **Résumé :** Utilisez ce Guide de laboratoire de Test pour créer un environnement de développement/test qui inclut toutes les offres en nuage de Microsoft.
  
Les instructions fournies dans cet article vous permettent de créer un intranet simulé dans les services d’infrastructure de Microsoft Azure, puis d’ajouter des abonnements Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS) et Microsoft Dynamics 365. Vous obtenez ainsi une organisation plus simple qui utilise toutes les offres cloud de Microsoft en même temps dans un environnement de développement/test unique.  
  
![Phase 3 de l’environnement de développement/test cloud One Microsoft avec Azure, Office 365, EMS et Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
Vous pouvez utiliser la configuration obtenue pour :
  
- Bénéficier d’une intégration de toutes les offres cloud de Microsoft, telles que l’infrastructure d’identité commune fournies par Azure Active Directory (AD).
    
- Évaluer des scénarios complets comprenant plusieurs offres Microsoft Cloud.
    
- Créer une démonstration, une preuve de concept ou une configuration de développement/test qui utilise plusieurs offres Microsoft Cloud.
    
- Développer vos compétences sur Microsoft Cloud à des fins de développement professionnel.
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a>Phase 1 : Créer un intranet simulé et y ajouter Office 365

Suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
La figure 1 illustre votre configuration qui en résulte, ce qui inclut Office 365 et un intranet simulé en cours d’exécution dans les services d’infrastructure Azure et la synchronisation d’annuaire à partir d’une forêt de Windows Server Active Directory (AD) sur site.
  
**Figure 1 : L’intranet simulé dans Azure avec Office 365**

![Environnement de développement/test d’Office 365 avec DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> La version d’essai Azure est de 30 jours. L’abonnement d’évaluation de Office 365 entreprise E5 est de 30 jours, ce qui peut être facilement étendus pour un autre 30 jours. Pour un environnement de développement/test permanent, créer un nouveau payé l’abonnement Azure et un nouvel abonnement Office 365 entreprise E5 payé avec un petit nombre de licences. 
  
## <a name="phase-2-add-ems"></a>Phase 2 : Ajouter EMS

Dans cette phase, vous vous inscrivez pour l’abonnement d’évaluation EMS et l’ajoutez à la même organisation que votre abonnement d’évaluation Office 365.
  
1. Avec un navigateur soit sur votre ordinateur de bureau ou à partir de CLIENT1, ouvrez une session sur le portail Office 365 à [https://portal.office.com](https://portal.office.com) avec les informations d’identification de votre compte d’administrateur global.
    
2. Cliquez sur la mosaïque de **l’Admin** .
    
3. Dans l’onglet **Centre d’administration d’Office** dans votre navigateur, dans la navigation de gauche, cliquez sur **de facturation > acheter les services**.
    
4. Dans la page **services d’achat** , trouver la **mobilité d’entreprise + E5 de la sécurité** . Placez le pointeur de la souris sur elle et cliquez sur **Démarrer la version d’évaluation gratuite**.
    
5. Dans la page **Confirmer votre commande** , cliquez sur **Essayer maintenant**.
    
6. Dans la page **reçu de commande** , cliquez sur **Continuer**.
    
> [!NOTE]
> L’abonnement à la version d’évaluation d’Enterprise Mobility + Security E5 est de 90 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un nombre réduit de licences. 
  
Ensuite, activez la licence Enterprise Mobility + Security E5 pour tous les comptes d’utilisateur.
  
1. Dans l’onglet **Centre d’administration d’Office 365** dans votre navigateur, dans la navigation de gauche, cliquez sur **les utilisateurs > utilisateurs actifs**.
    
2. Cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.
    
3. Dans le volet des **licences** , activer la licence du produit de **mobilité d’entreprise + sécurité E5** **on**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .
    
4. Pour tous vos autres comptes (Utilisateur 1, Utilisateur 2, Utilisateur 3, Utilisateur 4 et Utilisateur 5), suivez les étapes 2 et 3.
    
Votre environnement de développement/test comporte maintenant :
  
- Un intranet simulé exécuté dans les services d’infrastructure Azure.
    
- Des abonnements d’évaluation Office 365 E5 Entreprise et EMS qui partagent la même organisation et le même client Azure AD avec votre liste des comptes d’utilisateur.
    
- Tous vos comptes d’utilisateur activés pour utiliser Office 365 Entreprise E5 et EMS.
    
La figure 2 montre la configuration obtenue, qui ajoute EMS.
  
**Figure 2 : L’intranet simulé dans Azure avec Office 365 et EMS**

![Phase 2 de l’environnement de développement/test cloud One Microsoft avec Azure, Office 365 et EMS](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a>Phase 3 : Ajoutez Dynamics 365

Dans cette phase, vous allez souscrire à l’abonnement d’évaluation Dynamics 365 et l’ajouter à la même organisation que vos abonnements d’évaluation Office 365 et EMS.
  
1. À l’aide d’un navigateur soit sur votre ordinateur de bureau ou à partir de CLIENT1, connectez-vous au portail Office 365 à [https://portal.office.com](https://portal.office.com) avec les informations d’identification de votre compte d’administrateur global.
    
2. Cliquez sur la mosaïque de **l’Admin** .
    
3. Dans l’onglet **Centre admin** , dans la navigation de gauche, cliquez sur **de facturation > acheter les services**.
    
4. Dans la page **services d’achat** , trouver l’élément de **Dynamics 365 Plan 1 Enterprise Edition** . Placez le pointeur de la souris sur elle et cliquez sur **Démarrer la version d’évaluation gratuite**.
    
5. Dans la page **Confirmer votre commande** , cliquez sur **Essayer maintenant**.
    
6. Dans la page **reçu de commande** , cliquez sur **Continuer**.
    
> [!NOTE]
> L’abonnement d’évaluation Dynamics 365 Plan 1 Enterprise Edition est valide pendant 30 jours. Vous pouvez facilement étendre l’abonnement d’évaluation pour une période supplémentaire de 30 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un nombre réduit de licences. 
  
Procédez comme suit pour affecter des licences Dynamics 365 aux comptes de l’administrateur général, ainsi qu’aux comptes Utilisateur 2 et Utilisateur 3 afin de leur attribuer le rôle d’administrateur système.
  
1. Dans l’onglet **Centre admin** , cliquez sur **les utilisateurs > utilisateurs actifs**.
    
2. Dans la liste d’utilisateurs actifs, cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.
    
3. Dans le volet **des licences de produit** , activation de la licence du produit pour **Dynamics 365 Plan 1 Enterprise Edition** **sur**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .
    
4. Suivez les étapes 2 et 3 pour les comptes Utilisateur 2 et Utilisateur 3.
    
5. Fermez l’onglet **Centre admin** .
    
Lors de cette phase, vous allez configurer les comptes Utilisateur 2 et Utilisateur 3 en tant qu’administrateurs système de Dynamics 365.
  
1. Dans l’onglet **Centre d’administration d’Office** dans votre navigateur, dans la navigation de gauche, cliquez sur **Centre d’administration**, puis cliquez sur **Dynamics 365**.
    
    Vous devrez peut-être attendre la fin de l’approvisionnement de Dynamics 365 avant de le voir apparaître dans le menu.
    
2. Sous l’onglet Dynamics 365, cliquez sur **tous**, puis cliquez sur **le programme d’installation terminé.**
    
    Attendez la fin de l’installation.
    
    Lorsque l’installation est terminée, il affiche un tableau de bord d’activité de vente basés sur des données qui fait partie de l’abonnement de la piste. Prenez quelques instants pour afficher la **Bienvenue dans votre version d’évaluation** de vidéo. Fermez la fenêtre de la vidéo lorsque vous avez terminé.
    
3. Dans la barre d’outils en haut, cliquez sur la flèche en regard de **ventes**, cliquez sur **paramètres**, puis cliquez sur **sécurité**.
    
4. Dans la page **sécurité** , cliquez sur **utilisateurs**.
    
5. Dans la liste des utilisateurs, cliquez sur **utilisateur 2**.
    
6. Dans la barre d’outils, cliquez sur **Gérer les rôles**.
    
7. **Gérer les rôles**, cliquez sur **Administrateur système**, puis cliquez sur **OK**.
    
8. Dans la barre d’outils en haut, cliquez sur **sécurité**.
    
9. Répétez les étapes 5 à 8 pour le compte Utilisateur 3.
    
10. Fermer la **utilisateur : l’util_3** onglet.
    
> [!NOTE]
> Le rôle d’administrateur système Dynamics 365 a été automatiquement attribué à votre compte d’administrateur général Office 365. 
  
Votre environnement de développement/test comporte maintenant :
  
- Un intranet simulé exécuté dans les services d’infrastructure Azure.
    
- Des abonnements à la version d’évaluation d’Office 365 E5 Enterprise, d’EMS et de Dynamics 365 qui partagent la même organisation et le même client Azure AD avec votre liste des comptes d’utilisateur.
    
- Tous vos comptes d’utilisateur activés pour utiliser Office 365 Entreprise E5 et EMS.
    
- Vos comptes d’administrateur général d’entreprise, Utilisateur 2 et Utilisateur 3 peuvent utiliser Dynamics 365, et sont également administrateurs système de Dynamics 365.
    
La figure 3 présente la configuration finale.
  
**Figure 3 : L’intranet simulé dans Azure avec Office 365, EMS et Dynamics 365**

![Phase 3 de l’environnement de développement/test cloud One Microsoft avec Azure, Office 365, EMS et Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a>Étapes suivantes

Vous pouvez maintenant tester différentes configurations avec votre environnement de développement/test Microsoft Cloud. Voici quelques suggestions pour vous guider :
  
- [Configurer des stratégies de management (MAM) d’une application mobile dans EMS pour les applications d’Office 365](https://technet.microsoft.com/library/mt764059.aspx)
    
- [Montrer Exchange Online dans Office 365 une intégration avec les contacts de Dynamics 365](https://technet.microsoft.com/library/mt798313.aspx)
    
- [Créer un réseau simulé coexistence dans les services d’infrastructure Azure pour l’hébergement des charges de travail basé sur serveur](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ressources relatives à l'architecture informatique du cloud Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Solutions hybrides](hybrid-solutions.md)
  
[Solutions de sécurité](security-solutions.md)





