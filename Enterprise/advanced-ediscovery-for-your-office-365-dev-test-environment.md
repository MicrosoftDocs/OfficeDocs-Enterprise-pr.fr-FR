---
title: "Advanced eDiscovery pour votre environnement de développement/test Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG-
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: "Résumé : Configurer et illustrer l’avancée de Office 365 d’eDiscovery avec des exemples de données dans votre environnement de développement/test d’Office 365."
ms.openlocfilehash: a118ec2753d04afb60d13890b7d5da8c07701721
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Advanced eDiscovery pour votre environnement de développement/test Office 365

 **Résumé :** Configurer et illustrer l’avancée de Office 365 d’eDiscovery avec des exemples de données dans votre environnement de développement/test d’Office 365.
  
EDiscovery avancées d’Office 365 vous permet de trouver rapidement et d’analyser les informations pertinentes sur les données stockées dans Office 365, y compris les e-mails et les documents. Cela peut enregistrer des montants considérables de temps et de dépenses, notamment dans le cas de litiges. Pour plus d’informations, reportez-vous à la section [avancée de Office 365 une e-Discovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Avec les instructions fournies dans cet article, vous créez un petit jeu de données pour un litige fictif à propos d’un contrat et l’analysez avec Advanced eDiscovery.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Phase 1 : Création d’un environnement de développement/test Office 365

Si vous souhaitez juste tester eDiscovery avancée dans une solution légère avec la configuration minimale requise, suivez les instructions dans la Phase 2 et 3 de Phase de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester eDiscovery avancée dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Test d’e-Discovery avancée ne requiert pas l’environnement simulé enterprise, qui comprend un intranet simulé est connecté à Internet et la synchronisation d’annuaire pour une forêt Active Directory de Windows Server. Il est fourni ici en tant qu’option de sorte que vous pouvez effectuer des tests et l’expérimentation dans un environnement qui représente une organisation typique. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Phase 2 : Création des données d’exemple pour Advanced eDiscovery

Cette procédure vous permet de créer des messages électroniques que vous analyserez plus tard dans un incident Advanced eDiscovery.
  
1. Ouvrez Internet Explorer et connectez-vous à [https://outlook.com](https://outlook.com) pour le compte de Outlook que vous avez créé à la Phase 2 de[l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
    
  - Si vous utilisez l’environnement de développement/test léger, ouvrez une session privée d’Internet Explorer et connectez-vous sur votre ordinateur local.
    
  - Si vous utilisez l’environnement de développement/test entreprise simulée, utiliser le portail Azure ([https://portal.azure.com](https://portal.azure.com)) de se connecter à la machine virtuelle de CLIENT1, puis connectez-vous à partir de CLIENT1.
    
2. Dans l’onglet **Courrier de Outlook** , cliquez sur **Nouveau**.
    
3. Dans la zone **à**, tapez l’adresse de messagerie du compte de votre abonnement d’évaluation User6 ( **user6 @.** <organization name> **. onmicrosoft.com**).
    
4. Pour l’objet, tapez **l’e-mail de Test 1**.
    
5. Dans le corps, tapez **Tailspin contrat brouillon**, puis cliquez sur **Envoyer**.
    
6. Dans l’onglet **Courrier de Outlook** , cliquez sur **Nouveau**.
    
7. Dans la zone **à**, tapez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation.
    
8. Pour l’objet, tapez **Test message électronique 2**.
    
9. Dans le corps, tapez **réunion déjeuner de Tailspin**et puis cliquez sur **Envoyer**.
    
10. Dans l’onglet **Courrier de Outlook** , cliquez sur **Nouveau**.
    
11. Dans la zone **à**, tapez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation.
    
12. Pour l’objet, tapez **Test message électronique 3**.
    
13. Dans le corps, tapez **désaccord du contrat Tailspin**, puis cliquez sur **Envoyer**.
    
14. Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **se déconnecter**.
    
15. Ouvrir un nouvel onglet et vous connecter au portail Office 365 ([https://portal.office.com](https://portal.office.com)) avec le nom de compte et le mot de passe du compte User6 de votre abonnement d’évaluation.
    
16. Dans l’onglet du **portail Office 365** , cliquez sur **courrier**.
    
17. Sous l’onglet **courrier - User6 - Outlook** , vérifiez que User6 a reçu toutes les trois courriers électroniques à partir du compte de messagerie Outlook.
    
18. Revenez à l' **onglet de portail Office 365** pour User6.
    
19. Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **vous déconnecter.**
    
Dans cette procédure, vous créez deux documents Word que vous analyserez plus tard dans un incident Advanced eDiscovery.
  
1. Dans la page **Office** , cliquez sur **se connecter,** la connexion avec les informations d’identification de votre compte d’administrateur global.
    
2. Dans un nouvel onglet, accéder à l’URL de votre site de Production : **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. Dans l’onglet de la **collection de sites de Production** , de **Documents**, cliquez sur **Nouveau > Document Word**.
    
4. Sur la page **En ligne de Word** , tapez **brouillon de contrat Tailspin**et attendre jusqu'à ce qu’il affiche **enregistrée** dans le titre puis fermer l’onglet de page de **Word en ligne** .
    
5. Dans l’onglet de la **collection de sites de Production** , de **Documents**, cliquez sur **Nouveau > Document Word**.
    
6. Sous l’onglet **Word en ligne** , tapez **notes de litige de paiement de contrat Tailspin**et attendre jusqu'à ce qu’il affiche **enregistrée** dans le titre puis fermez l’onglet **Word en ligne** .
    
7. Sous l’onglet de la **collection de sites de Production** , vous devriez voir le **Document** et **Document1** dans la liste des documents.
    
8. Fermer l’onglet de la **collection de sites de Production** .
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Phase 3 : Utilisation eDiscovery avancées pour un litige

Malheureusement, un litige contractuel entre votre organisation et de la société Tailspin Toys a atteint le point d’action en justice. Dans cette procédure, vous créez et configurez un cas d’e-Discovery avancées pour rechercher et analyser les e-mails et les documents qui contiennent le texte « Contrat de Tailspin ».
  
La procédure d’utilisation d’Advanced eDiscovery est la suivante :
  
- Créer une recherche dans la sécurité &amp; centre de conformité, analyser ses résultats et préparer ensuite les résultats d’eDiscovery avancée.
    
- Créez et configurez un incident dans Advanced eDiscovery et analysez les résultats de recherche.
    
Dans cette procédure, vous créez une recherche dans la sécurité &amp; centre de « Contrat de Tailspin », regardez les résultats, de conformité et eDiscovery avancée puis préparer les résultats.
  
1. À partir de l’onglet du **portail Office 365** , cliquez sur **Admin**.
    
2. Dans la l’onglet centre Admin de navigation gauche, cliquez sur **les centres Admin > conformité**.
    
3. Sur le **sécurité &amp; la conformité** , cliquez sur **autorisations**.
    
4. Dans la liste des **autorisations** , double-cliquez sur **Gestion de l’organisation**.
    
5. Dans la fenêtre de **Groupe de rôles** , sous **les membres**, cliquez sur le signe plus.
    
6. Dans la fenêtre **Sélectionner les membres** , double-cliquez sur le nom de votre compte administrateur, puis cliquez sur **OK**.
    
7. Dans la fenêtre de **Groupe de rôles** , cliquez sur **Enregistrer**.
    
8. Dans la liste des **autorisations** , double-cliquez sur **gestionnaire eDiscovery**.
    
9. Dans la fenêtre de **Groupe de rôles** , sous **e-Discovery administrateur**, cliquez sur l’icône de signe plu.
    
10. Dans la fenêtre **Sélectionner les membres** , double-cliquez sur le nom de votre compte administrateur, puis cliquez sur **OK**.
    
11. Dans la fenêtre de **Groupe de rôles** , cliquez sur **Enregistrer**.
    
12. Dans la navigation de gauche, cliquez sur **recherche &amp; enquête > recherche de contenu de**.
    
13. Cliquez sur l’icône plus pour ajouter une recherche.
    
14. Dans la fenêtre **nouvelle recherche** , tapez **recherche de contrat Tailspin** dans la zone **nom**.
    
15. Dans **où voulez-vous rechercher ?**et cliquez sur **Rechercher partout,** sélectionnez **Exchange**, **SharePoint**et **Les dossiers publics**, puis cliquez sur **Suivant.**
    
16. Dans **que voulez-vous rechercher les ?**, type **contrat de Tailspin**et puis cliquez sur **Rechercher**.
    
17. Dans la liste des recherches, cliquez sur le nom de **recherche du contrat Tailspin** .
    
18. Dans le volet de **recherche de contrat Tailspin** , cliquez sur **Aperçu des résultats de recherche** dans les **résultats**. Vous devez voir une fenêtre répertoriant les deux documents sur le site SharePoint de Production ( **Document** et **Document1**) et les e-mails de **e-mail de Test 1** et **e-mail de Test 3** à User6. Fermez la fenêtre.
    
19. Dans le volet de **recherche de contenu** , sous **résultats d’Analyze avec l’e-Discovery avancée**, cliquez sur **Aperçu des résultats d’analyse**.
    
20. Dans la fenêtre **des résultats pour la recherche de contrat Tailspin préparer la recherche** , cliquez sur **préparer** et attendre qu’elle se termine.
    
Dans cette procédure, vous créez un incident Advanced eDiscovery et analysez les résultats de recherche de contrat Tailspin.
  
1. Dans la navigation de gauche, cliquez sur l' **e-Discovery** sous **recherche &amp; enquête**.
    
2. Dans le volet de **l’e-Discovery** , cliquez sur **Avancé eDiscovery**.
    
3. Dans l’onglet **Paramètres avancés d’e-Discovery** , cliquez sur l’icône de signe plu pour ajouter un nouveau dossier.
    
4. Dans le volet **Ajouter cas** , tapez **litige contractuel de Tailspin** dans **nom**et puis cliquez sur **OK**. Attendez que le cas doit être créé.
    
5. Double-cliquez sur le cas de **litige contractuel de Tailspin** dans la liste.
    
6. Dans la liste de **conteneur** , cliquez sur le conteneur de **recherche de contrat Tailspin** , puis cliquez sur **processus**. Attendez la fin du traitement.
    
7. Lors de la **processus : terminé** s’affiche au bas de la fenêtre, cliquez sur **processus de synthèse** dans la navigation de gauche pour voir un résumé.
    
8. Dans la navigation supérieure, cliquez sur **analyser**.
    
9. Dans la page **paramètres** , sous **thèmes**, tapez **3** dans **le nombre maximal de thèmes**.
    
10. Cliquez sur **analyser** et attendez que l’analyse à effectuer. Vous devriez voir une série de graphiques en secteurs avec l’analyse de la population cible, les documents, les e-mails et les pièces jointes. Pour plus d’informations, consultez [affichage d’analyser les résultats](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
Vous pouvez désormais utiliser cet environnement pour créer du contenu, des recherches et des incidents, et réaliser d’autres essais avec Advanced eDiscovery dans Office 365.
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Application du nuage sécurité pour votre environnement de développement/test d’Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)

[EDiscovery avancées d’Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


