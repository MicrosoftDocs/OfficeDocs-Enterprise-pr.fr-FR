---
title: Intégration d'Exchange Online pour votre environnement de développement/test Office 365 et Dynamics 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "Résumé : Utilisez ce Guide de laboratoire de test pour activer l'intégration de Dynamics 365 pour Exchange Online dans votre abonnement à la version d'évaluation d'Office 365."
ms.openlocfilehash: be79f58f448799bba9c4a9ee51350f198d721e0d
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574018"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a>Intégration d’Exchange Online pour votre environnement de développement/test Office 365 et Dynamics 365

 **Résumé :** Utilisez ce Guide de laboratoire de test pour activer l'intégration de Dynamics 365 pour Exchange Online dans votre abonnement à la version d'évaluation d'Office 365.
  
Un aspect utile de Microsoft Dynamics 365 est le stockage de toutes les communications client en un seul endroit, afin que toute personne disposant des autorisations appropriées puisse voir l'ensemble des enregistrements client pertinents. Par exemple, afficher tous les e-mails associés à un contact, un compte, une opportunité ou une demande de devis en particulier.
  
Pour stocker les e-mails et autres enregistrements de messagerie dans Dynamics 365, vous devez synchroniser votre système de messagerie avec Dynamics 365. La synchronisation côté serveur est la méthode de prédilection pour la synchronisation de la messagerie.
  
Utilisez ce Guide de laboratoire de test pour configurer et montrer la façon dont Exchange Online et le client Outlook Online peuvent exploiter les informations stockées dans Dynamics 365. 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a>Phase 1 : créer l’environnement de développement/test Office 365 et Dynamics 365

Suivez les instructions figurant dans la rubrique [Environnement de développement/test Office 365 et Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md) pour créer une version en mode léger ou pour entreprise simulée d'un environnement de développement/test Office 365 et Dynamics 365.
  
> [!NOTE]
> La configuration décrite dans cet article ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory (AD). Il est proposé comme option dans cet article afin que vous puissiez tester Office 365 et Dynamics 365 dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a>Phase 2 : configurer et montrer l'intégration Dynamics 365 dans Exchange Online

Suivez ces étapes pour configurer la boîte aux lettres de l'administrateur général pour l'intégration de Dynamics 365 et Exchange Online :
  
1. À l'aide d'une session privée de votre navigateur [http://admin.microsoft.com](http://admin.microsoft.com) , accédez à et connectez-vous à l'aide de votre compte d'administrateur global Office 365.
    
2. Sur la page **Accueil Microsoft Office**, cliquez sur la mosaïque **Messagerie**.
    
3. Dans l'onglet nouveau **courrier** de votre navigateur, cliquez sur **nouveau** , puis observez comment le coin inférieur du volet sous la zone de saisie d'un message possède une icône pour mes modèles.
    
     ![Nouveau message électronique vide sans l’intégration à Dynamics 365.](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. Cliquez sur **Abandonner** et laissez l'onglet **Messagerie** ouvert.
    
5. Cliquez sur l'onglet **Accueil Microsoft Office** de votre navigateur, puis cliquez sur la mosaïque **Administration**.
    
6. Dans le volet de navigation gauche de l'onglet **Centre d'administration Office**, cliquez sur **Centres d'administration > Dynamics 365**.
    
7. Dans le nouvel onglet **Dynamics 365** de votre navigateur, dans la liste des instances de Dynamics 365, cliquez sur **Ouvrir**.
    
8. Dans le nouvel onglet **Administration** de votre navigateur, dans la barre de navigation, cliquez sur la flèche vers le bas en regard de **Paramètres**, puis cliquez sur **Configuration de la messagerie** sous **Système**.
    
9.  Sur la page **Configuration de la messagerie**, cliquez sur **Paramètres de configuration de la messagerie**.
    
10. Dans l'onglet **Messagerie** de la boîte de dialogue **Paramètres du système**, remplacez **Rendez-vous, contacts et tâches** par **Synchronisation côté serveur**, puis cliquez sur **OK**.
    
11. Sur la page **Configuration de la messagerie**, cliquez sur **Boîtes aux lettres**.
    
12. Sélectionnez le nom de l'administrateur général Office 365 dans la colonne de gauche, cliquez sur **Appliquer les paramètres de courrier électronique par défaut** dans la barre d'outils, puis cliquez sur **OK**.
    
13. Cliquez sur **Approuver l'adresse de messagerie** dans la barre d'outils, puis cliquez sur **OK**.
    
14. Sélectionnez le nom de l’administrateur général Office 365 dans la colonne de gauche, cliquez sur **Tester&amp; Activer les boîtes aux lettres** dans la barre d’outils, puis cliquez sur **OK**.
    
15. Cliquez sur l'onglet **Messagerie** ouvert et vérifiez que l'administrateur général a reçu un message de test.
    
16. Revenez à l'onglet **Boîtes aux lettres - Boîtes aux lettres actives** de votre navigateur, puis actualisez la page. Les colonnes **Statut des courriers électroniques entrants** et **Statut des courriers électroniques sortants** doivent être définies sur **Succès** pour le nom de compte d'administrateur général. Notez qu'il faut compter jusqu'à 15 minutes pour exécuter les deux tests.
    
Suivez ces étapes pour installer l'application Dynamics 365 pour Outlook et montrer les fonctionnalités de Dynamics 365 au sein de la boîte aux lettres de l'administrateur général :
  
1. Dans l'onglet **Boîtes aux lettres - Boîtes aux lettres actives** de votre navigateur, cliquez sur la flèche vers le bas en regard de **Paramètres**, puis cliquez sur **Application Dynamics 365 pour Outlook** sous **Système**.
    
2. Sur la page **Prise en main de l'application Microsoft Dynamics 365 pour Outlook**, cliquez sur le nom de l'administrateur général, puis cliquez sur **Ajouter l'application à Outlook**. La colonne **Statut** indique **En attente**.
    
3. Actualisez la page jusqu'à ce que le statut devienne **Ajouté à Outlook**. Notez qu'il faut compter jusqu'à 15 minutes pour exécuter cette configuration.
    
4. Cliquez sur l'onglet **Messagerie** de votre navigateur et fermez-le.
    
5. Cliquez sur l'onglet **Accueil Microsoft Office** de votre navigateur, puis cliquez sur la mosaïque **Messagerie**.
    
6. Dans le nouvel **Messagerie** de votre navigateur, cliquez sur **Nouveau**. Notez que le coin inférieur du volet sous la zone de saisie d'un message contient désormais une icône pour Dynamics 365.
    
     ![Nouveau message électronique vide avec l’intégration à Dynamics 365, affichant la nouvelle icône.](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. Cliquez sur l'icône Dynamics 365. Vous devriez voir un volet **Dynamics 365**, à partir duquel vous pouvez suivre ces modèles de messagerie ou d'accès, de la documentation commerciale ou des articles.
    
8. Dans le champ **À** de l'e-mail, tapez **alex.y.wu@outlook.com**, puis cliquez sur **Réessayer**dans le volet **Dynamics 365**. Vous devriez voir une section **Destinataires** dans le volet **Dynamics 365** avec des informations sur Alex Wu, un contact de l'application de vente qui a été fournie avec les exemples de données pour votre abonnement à la version d'évaluation.
    
     ![Volet d’informations Dynamics 365 pour un contact commercial stocké dans Dynamics 365.](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. Cliquez sur **Abandonner**.

> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles du jeu de guides de laboratoire de test de Microsoft Cloud.
    
## <a name="see-also"></a>Voir aussi

[Environnement de développement/test Office 365 et Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
  
[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)

[Gestion des abonnements pour Dynamics 365 (en ligne)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Administration de Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


