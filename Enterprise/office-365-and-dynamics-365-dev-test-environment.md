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
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Résumé : Utilisez ce Guide de laboratoire de Test pour ajouter Dynamics 365 à votre environnement de développement/test Office 365.'
ms.openlocfilehash: 00d5cc0fd347aff7e201056f6af9ca271008d285
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Environnement de développement/test Office 365 et Dynamics 365

 **Résumé :** Utilisez ce Guide de laboratoire de Test pour ajouter Dynamics 365 à votre environnement de développement/test Office 365.
  
Suivez les instructions fournies dans cet article pour ajouter un abonnement à la version d’évaluation de Dynamics 365 à la même organisation que votre environnement de développement/test Office 365, créant ainsi un environnement de développement/test Office 365 et Dynamics 365.

![Environnement de développement/test Office 365 et Dynamics 365](images/o365-dynamics365-dev-test.png)
  
  
Vous pouvez utiliser un abonnement à la version d’évaluation de Dynamics 365 afin de présenter les fonctionnalités de Dynamics 365. Les solutions suivantes sont comprises dans la version d’évaluation Enterprise Edition de Dynamics 365 Plan 1 :
  
- [Microsoft Dynamics 365 pour les ventes](https://www.microsoft.com/dynamics365/sales). Augmenter vos ventes avec automation et aide à la décision numérique aidant à vos commerciaux se concentrer et travailler plus efficacement.
    
- [Microsoft Dynamics 365 pour le Service clientèle](https://www.microsoft.com/dynamics365/customer-service). Gagnez fidélité en donnant à vos agents les informations complètes et numérique aide à la décision que dont ils ont besoin pour fournir le service transparent.
    
- [Microsoft Dynamics 365 pour le Service clientèle](https://www.microsoft.com/dynamics365/field-service). Contrôleur de l’appel de service en optimisant vos planifications, équipant votre personnel et à l’aide des outils prédictives pour augmenter la marge.
    
- [Microsoft Dynamics 365 pour l’automatisation de Service Project](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Se termine correctement vos projets et créer des relations rentables avec les employés productifs et outils intelligents.
    
Vous pouvez explorer l’un des éléments ci-dessus pour votre abonnement à la version d’évaluation de Dynamics 365.
  
![Guides de laboratoire de test dans Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée

Si vous souhaitez uniquement tester Office 365 et Dynamics 365 dans une solution légère avec la configuration minimale requise, suivez les instructions en phases 2 et 3 de [l’environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester une entreprise simulée Dynamics 365 et Office 365, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).

![Environnement de développement/test Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> La configuration décrite dans cet article ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester Office 365 et Dynamics 365 dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>Phase 2 : Ajouter un abonnement à la version d’évaluation de Dynamics 365

Dans cette phase, vous vous inscrivez pour l’abonnement d’évaluation Dynamics 365 et l’ajoutez à la même organisation que votre abonnement d’évaluation Office 365.
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>Inscription à un abonnement à la version d’évaluation de Dynamics 365

1. Via un navigateur soit sur votre ordinateur de bureau (lightweight) ou à partir de CLIENT1 (entreprise en simulation), connectez-vous au portail Office 365 à [https://portal.office.com](https://portal.office.com) avec les informations d’identification de votre compte d’administrateur global.
    
2. Cliquez sur la vignette **Administration**.
    
3. Dans l’onglet **Centre d’administration Office** , dans la navigation de gauche, cliquez sur **facturation > achat de services**.
    
4. Dans la page **services d’achat** , recherchez l’élément **Dynamics 365 Plan 1 Enterprise Edition** . Placez le pointeur de la souris au-dessus de celle-ci, cliquez sur **Démarrer la version d’évaluation gratuite**.
    
5. Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.
    
6. Dans la page **Réception de la commande**, cliquez sur **Continuer**.

![Environnement de développement/test Office 365 et Dynamics 365](images/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> L’abonnement d’évaluation Dynamics 365 Plan 1 Enterprise Edition est valide pendant 30 jours. Vous pouvez facilement étendre l’abonnement d’évaluation pour une période supplémentaire de 30 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un nombre réduit de licences. 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>Phase 3 : Attribuer des administrateurs système et des licences Dynamics 365

Lors de cette phrase, vous allez affecter des licences Dynamics 365 aux comptes de l’administrateur général, ainsi qu’aux comptes Utilisateur 2 et Utilisateur 3 afin de leur attribuer le rôle d’administrateur système.
  
Suivez ces étapes pour affecter des licences Dynamics 365.
  
1. Dans l’onglet **Centre d’administration Office** , cliquez sur **utilisateurs > utilisateurs actifs**.
    
2. Dans la liste d’utilisateurs actifs, cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.
    
3. Dans le volet de **licences** , activer la licence de produit pour **Dynamics 365 Plan 1 Enterprise Edition** **activé**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .
    
4. Suivez les étapes 2 et 3 pour les comptes Utilisateur 2 et Utilisateur 3.
    
5. Fermez l’onglet **Centre d’administration Office** .
    
Lors de cette phase, vous allez configurer les comptes Utilisateur 2 et Utilisateur 3 en tant qu’administrateurs système de Dynamics 365.
  
1. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur **Admin**.
    
2. Sous l’onglet **Centre d’administration d’Office** , dans la navigation de gauche, cliquez sur **Centre d’administration**, puis cliquez sur **Dynamics 365**.
    
    Vous devrez peut-être attendre la fin de l’approvisionnement de Dynamics 365 avant de le voir apparaître dans le menu.
    
3. Sous l’onglet Dynamics 365, cliquez sur **tous ces éléments**, puis cliquez sur **le programme d’installation complète.**
    
    Attendez la fin de l’installation.
    
    Lorsque le programme d’installation est terminée, il affiche un tableau de bord ventes activité basés sur des données qui fait partie de l’abonnement de piste. Prendre un certain temps pour afficher la **Bienvenue dans la version d’évaluation de votre** vidéo. Fermez la fenêtre vidéo lorsque vous avez terminé.
    
4. Dans la barre d’outils dans la partie supérieure, cliquez sur la flèche vers le bas en regard de **ventes**, cliquez sur **paramètres**, puis cliquez sur **sécurité**.
    
5. Dans la page **sécurité** , cliquez sur **utilisateurs**.
    
6. Dans la liste des utilisateurs, cliquez sur **utilisateur 2**.
    
7. Dans la barre d’outils, cliquez sur **Gérer les rôles**.
    
8. **Gérer les rôles**, cliquez sur **Administrateur système**, puis cliquez sur **OK**.
    
9. Dans la barre d’outils dans la partie supérieure, cliquez sur **sécurité**.
    
10. Répétez les étapes 5 à 8 pour le compte Utilisateur 3.
    
11. Fermer la **utilisateur : User3** onglet.
    
> [!NOTE]
> Le rôle d’administrateur système Dynamics 365 a été automatiquement attribué à votre compte d’administrateur général Office 365. 
  
Votre environnement de développement/test Office 365 et Dynamics 365 a maintenant :
  
- Des abonnements à la version d’évaluation d’Office 365 E5 Enterprise et de Dynamics 365 qui partagent la même organisation et le même client Azure AD avec votre liste des comptes d’utilisateur.
    
- Vos comptes d’administrateur général d’entreprise, Utilisateur 2 et Utilisateur 3 peuvent utiliser à la fois Office 365 Entreprise E5 et Dynamics 365, et sont également administrateurs système de Dynamics 365.
    
## <a name="next-step"></a>Étape suivante

Configurer et illustrer puis Office 365 et Dynamics 365 fonctionnement conjoint des boîtes aux lettres dans Exchange Online avec [l’intégration Exchange Online pour votre environnement de développement/test Dynamics 365 et Office 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)

[Gestion des abonnements pour Dynamics 365 (en ligne)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Administration de Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


