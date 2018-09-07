---
title: Environnement de développement/test Office 365 et Dynamics 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Résumé : Utilisez ce guide de laboratoire de test pour ajouter Dynamics 365 à votre environnement de développement/test Office 365.'
ms.openlocfilehash: 195e5ab4fd96d1f238c96d47cc7406a45e0e02b1
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915209"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Environnement de développement/test Office 365 et Dynamics 365

 **Résumé :** Utilisez ce guide de laboratoire de test pour ajouter Dynamics 365 à votre environnement de développement/test Office 365.
  
Suivez les instructions fournies dans cet article pour ajouter un abonnement à la version d’évaluation de Dynamics 365 à la même organisation que votre environnement de développement/test Office 365, créant ainsi un environnement de développement/test Office 365 et Dynamics 365.

![Environnement de développement/test Office 365 et Dynamics 365](media/o365-dynamics365-dev-test.png)
  
  
Vous pouvez utiliser un abonnement à la version d’évaluation de Dynamics 365 afin de présenter les fonctionnalités de Dynamics 365. Les solutions suivantes sont comprises dans la version d’évaluation Enterprise Edition de Dynamics 365 Plan 1 :
  
- [Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Augmentez vos ventes grâce à l’automatisation et aux outils numériques qui permettent à vos collaborateurs de rester concentrés et de travailler plus efficacement.
    
- [Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Fidélisez vos agents en leur fournissant l’ensemble des informations et des outils numériques dont ils ont besoin pour proposer un service impeccable.
    
- [Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Contrôlez les visites de réparation en optimisant vos plannings, en équipant votre personnel d’appareils adaptés et en utilisant des outils de prévision en vue d’augmenter vos bénéfices.
    
- [Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/fr-FR/dynamics365/project-service-automation). Menez vos projets à bien et initiez des relations fructueuses grâce à des collaborateurs productifs et des outils intelligents.
    
Vous pouvez explorer l’un des éléments ci-dessus pour votre abonnement à la version d’évaluation de Dynamics 365.
  
![Guides de laboratoire de test dans Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée

Si vous souhaitez simplement tester Office 365 et Dynamics 365 avec une configuration minimale, suivez les instructions des étapes 2 et 3 de la rubrique [Environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester Office 365 et Dynamics 365 dans une entreprise simulée, suivez les instructions de la rubrique [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).

![Environnement de développement/test Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> La configuration décrite dans cet article ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester Office 365 et Dynamics 365 dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>Phase 2 : Ajouter un abonnement à la version d’évaluation de Dynamics 365

Dans cette phase, vous vous inscrivez pour l’abonnement d’évaluation Dynamics 365 et l’ajoutez à la même organisation que votre abonnement d’évaluation Office 365.
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>Inscription à un abonnement à la version d’évaluation de Dynamics 365

1. En utilisant un navigateur sur votre ordinateur de bureau (simplifié) ou sur CLIENT1 (entreprise de simulation), connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) à l’aide des informations d’identification de votre compte Administrateur général.
    
2. Cliquez sur la vignette **Administration**.
    
3. Sous l’onglet **Centre d’administration Office**, dans le volet de navigation de gauche, cliquez sur **Facturation > Acheter des services**.
    
4. Dans la page **Acheter des services**, recherchez l’élément **Dynamics 365 Plan 1 Enterprise Edition**. Placez le curseur de la souris dessus et cliquez sur **Démarrer l’essai gratuit**.
    
5. Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.
    
6. Dans la page **Réception de la commande**, cliquez sur **Continuer**.

![Environnement de développement/test Office 365 et Dynamics 365](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> L’abonnement d’évaluation Dynamics 365 Plan 1 Enterprise Edition est valide pendant 30 jours. Vous pouvez facilement étendre l’abonnement d’évaluation pour une période supplémentaire de 30 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un nombre réduit de licences. 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>Phase 3 : Attribuer des administrateurs système et des licences Dynamics 365

Lors de cette phrase, vous allez affecter des licences Dynamics 365 aux comptes de l’administrateur général, ainsi qu’aux comptes Utilisateur 2 et Utilisateur 3 afin de leur attribuer le rôle d’administrateur système.
  
Suivez ces étapes pour affecter des licences Dynamics 365.
  
1. Sous l’onglet **Centre d’administration Office**, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
2. Dans la liste des utilisateurs actifs, sélectionnez votre compte Administrateur général, puis cliquez sur **Modifier** pour **Licences de produits**.
    
3. 	Dans le volet **Licences de produit**, activez la licence de produit pour **Dynamics 365 Plan 1 Enterprise Edition** en sélectionnant **Activer**, cliquez sur **Enregistrer**, puis cliquez deux fois sur **Fermer**.
    
4. Suivez les étapes 2 et 3 pour les comptes Utilisateur 2 et Utilisateur 3.
    
5. Fermez l’onglet **Centre d’administration Office**.
    
Lors de cette phase, vous allez configurer les comptes Utilisateur 2 et Utilisateur 3 en tant qu’administrateurs système de Dynamics 365.
  
1. Dans l’onglet **Accueil Microsoft Office**, cliquez sur **Administrateur**.
    
2. Sur l’onglet **Centre d’administration Office**, cliquez sur **Centres d’administration** dans le volet de navigation de gauche, puis sur **Dynamics 365**.
    
    Vous devrez peut-être attendre la fin de l’approvisionnement de Dynamics 365 avant de le voir apparaître dans le menu.
    
3. Sur l’onglet Dynamics 365, cliquez sur **Toutes ces options**, puis sur **Terminer l’installation**.
    
    Attendez la fin de l’installation.
    
    Une fois l’installation terminée, un tableau de bord Activité de ventes reposant sur des exemples de données inclus dans l’abonnement d’essai est affiché. Visionnez la **vidéo de présentation de l’essai**. Fermez la fenêtre de la vidéo lorsque vous avez terminé.
    
4. Dans la barre d’outils située en haut de l’écran, cliquez sur la flèche vers le bas en regard de **Ventes**, sur **Paramètres** puis sur **Sécurité**.
    
5. Dans la page **Sécurité**, cliquez sur **Utilisateurs**.
    
6. Dans la liste des utilisateurs, cliquez sur **Utilisateur 2**.
    
7. Dans la barre d’outils, cliquez sur **Gérer les rôles**.
    
8. Dans **Gérer les rôles**, cliquez sur **Administrateur système**, puis sur **OK**.
    
9. Dans la barre d’outils en haut de l’écran, cliquez sur **Sécurité**.
    
10. Répétez les étapes 5 à 8 pour le compte Utilisateur 3.
    
11. Fermez l’onglet **Utilisateur :User3**.
    
> [!NOTE]
> Le rôle d’administrateur système Dynamics 365 a été automatiquement attribué à votre compte d’administrateur général Office 365. 
  
Votre environnement de développement/test Office 365 et Dynamics 365 a maintenant :
  
- Des abonnements à la version d’évaluation d’Office 365 E5 Enterprise et de Dynamics 365 qui partagent la même organisation et le même client Azure AD avec votre liste des comptes d’utilisateur.
    
- Vos comptes d’administrateur général d’entreprise, Utilisateur 2 et Utilisateur 3 peuvent utiliser à la fois Office 365 Entreprise E5 et Dynamics 365, et sont également administrateurs système de Dynamics 365.
    
## <a name="next-step"></a>Étape suivante

Configurez Office 365 et Dynamics 365, et expliquez comment ils fonctionnent ensemble dans les boîtes aux lettres Exchange Online avec la rubrique relative à l’[intégration à Exchange Online de votre environnement de développement/test Office 365 et Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)

[Gestion des abonnements pour Dynamics 365 (en ligne)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Administration de Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


