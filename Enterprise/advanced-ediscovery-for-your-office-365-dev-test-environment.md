---
title: Advanced eDiscovery pour votre environnement de développement/test Office 365
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
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 'Résumé : Configurez et faites une démonstration d’Office 365 Advanced eDiscovery avec des données d’échantillon dans votre environnement de développement/test Office 365.'
ms.openlocfilehash: c93900e07b8b9adbe0f1120eca77019b9dcc1eda
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897507"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Advanced eDiscovery pour votre environnement de développement/test Office 365

 **Résumé :** Configurez et faites une démonstration d’Office 365 Advanced eDiscovery avec des données d’échantillon dans votre environnement de développement/test Office 365.
  
EDiscovery avancées Office 365 vous permet de trouver rapidement et analyser les informations pertinentes sur les données stockées dans Office 365, notamment le courrier électronique et des documents. Cette possibilité d’enregistrer quantités énormes de temps et de dépenses, notamment dans le cas de litige. Pour plus d’informations, voir [eDiscovery Office 365 avancés](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Avec les instructions fournies dans cet article, vous créez un petit jeu de données pour un litige fictif à propos d’un contrat et l’analysez avec Advanced eDiscovery.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Phase 1 : Création d’un environnement de développement/test Office 365

Si vous souhaitez uniquement tester eDiscovery avancée dans une solution légère avec la configuration minimale requise, suivez les instructions de la Phase 2 et 3 de Phase de [l’environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester eDiscovery avancée dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Test de découverte électronique avancée ne nécessite pas de l’environnement d’entreprise simulé, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option de sorte que vous pouvez effectuer des tests et l’expérimentation dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Phase 2 : Création des données d’exemple pour Advanced eDiscovery

Cette procédure vous permet de créer des messages électroniques que vous analyserez plus tard dans un incident Advanced eDiscovery.
  
1. Ouvrez Internet Explorer et vous connecter à [https://outlook.com](https://outlook.com) pour le compte Outlook que vous avez créé dans la Phase 2 de[l’environnement de développement/test Office 365](office-365-dev-test-environment.md).
    
  - Si vous utilisez l’environnement de développement/test léger, ouvrez une session privée d’Internet Explorer et connectez-vous sur votre ordinateur local.
    
  - Si vous utilisez l’environnement de développement/test entreprise simulé, utiliser le portail Azure ([https://portal.azure.com](https://portal.azure.com)) pour se connecter à l’ordinateur virtuel CLIENT1 et puis se connecter à partir de CLIENT1.
    
2. Dans l’onglet **Courrier Outlook**, cliquez sur **Nouveau**.
    
3. Dans la zone **à**, tapez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation ( **user6 @.** <organization name> **. onmicrosoft.com**).
    
4. Pour l’objet, saisissez **Message électronique de test 1**.
    
5. Dans le corps, saisissez **Brouillon de contrat Tailspin**, puis cliquez sur **Envoyer**.
    
6. Dans l’onglet **Courrier Outlook**, cliquez sur **Nouveau**.
    
7. Dans **À**, saisissez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation.
    
8. Pour l’objet, saisissez **Message électronique de test 2**.
    
9. Dans le corps, saisissez **Réunion Tailspin à l’heure du déjeuner**, puis cliquez sur **Envoyer**.
    
10. Dans l’onglet **Courrier Outlook**, cliquez sur **Nouveau**.
    
11. Dans **À**, saisissez l’adresse de messagerie du compte User6 de votre abonnement d’évaluation.
    
12. Pour l’objet, saisissez **Message électronique de test 3**.
    
13. Dans le corps, saisissez **Désaccord sur le contrat Tailspin**, puis cliquez sur **Envoyer**.
    
14. Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **se déconnecter**.
    
15. Ouvrez un nouvel onglet et connectez-vous au portail Office 365 ([https://portal.office.com](https://portal.office.com)) avec le nom de compte et mot de passe du compte User6 de votre abonnement d’évaluation.
    
16. Dans l’onglet **Portail Office 365**, cliquez sur **Courrier**.
    
17. Sous l’onglet **messagerie - User6 - Outlook** , vérifiez que User6 provenant de tous les messages trois électroniques au compte de messagerie Outlook.
    
18. Revenez à l’**onglet Portail Office 365** pour User6.
    
19. Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis sur **Déconnexion**.
    
Dans cette procédure, vous créez deux documents Word que vous analyserez plus tard dans un incident Advanced eDiscovery.
  
1. Dans la page **Office**, cliquez sur **Se connecter,** puis connectez-vous avec les informations d’identification de votre compte d’administrateur global.
    
2. Dans un nouvel onglet, accéder à l’URL de votre site SharePoint de Production : **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. Dans l’onglet **Collection de sites de production**, sous **Documents**, cliquez sur **Nouveau > Document Word**.
    
4. Sur la page **Word Online**, saisissez **Brouillon de contrat Tailspin**, patientez jusqu’à ce que le titre affiche **Enregistré**, puis fermez l’onglet de la page **Word Online**.
    
5. Dans l’onglet **Collection de sites de production**, sous **Documents**, cliquez sur **Nouveau > Document Word**.
    
6. 	Dans l’onglet **Word Online**, saisissez **Notes sur le litige lié au contrat Tailspin**, patientez jusqu’à ce que le titre affiche **Enregistré**, puis fermez l’onglet **Word Online**.
    
7. Dans l’onglet **Collection de sites de production**, Vous devriez voir **Document** et **Document1** dans la liste de documents.
    
8. Fermez l’onglet **Collection de sites de production**.
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Phase 3 : Utilisation avancée eDiscovery pour un litige

Malheureusement, un litige contrat entre votre organisation et les Tailspin Toys a atteint le point d’action juridique. Dans cette procédure, vous créez et configurez un cas eDiscovery avancé pour rechercher et analyser les e-mails et les documents qui contiennent le texte « Contrat Tailspin ».
  
La procédure d’utilisation d’Advanced eDiscovery est la suivante :
  
- Créer une recherche dans la sécurité &amp; centre de conformité, analyser les résultats et préparer les résultats de la découverte électronique avancée.
    
- Créez et configurez un incident dans Advanced eDiscovery et analysez les résultats de recherche.
    
Dans cette procédure, vous créez une recherche dans la sécurité &amp; du centre de « Contrat Tailspin », recherchez les résultats et préparer les résultats de la découverte électronique avancée de conformité.
  
1. Dans l’onglet **Portail Office 365**, cliquez sur **Admin**.
    
2. Dans le volet de navigation gauche de l’onglet Centre d’administration, cliquez sur **Centres d’administration > Conformité**.
    
3. Sur le **sécurité &amp; conformité** , cliquez sur **autorisations**.
    
4. Dans la liste **Autorisations**, double-cliquez sur **Gestion de l’organisation**.
    
5. Dans la fenêtre **Groupe de rôles**, sous **Membres**, cliquez sur le signe plus.
    
6. Dans la fenêtre **Sélectionner les membres**, double-cliquez sur le nom de votre compte d’administrateur, puis cliquez sur **OK**.
    
7. Dans la fenêtre **Groupe de rôles**, cliquez sur **Enregistrer**.
    
8. Dans la liste **Autorisations**, double-cliquez sur **Gestionnaire eDiscovery**.
    
9. Dans la fenêtre **Groupe de rôles**, sous **Administrateur eDiscovery**, cliquez sur l’icône plus.
    
10. Dans la fenêtre **Sélectionner les membres**, double-cliquez sur le nom de votre compte d’administrateur, puis cliquez sur **OK**.
    
11. Dans la fenêtre **Groupe de rôles**, cliquez sur **Enregistrer**.
    
12. Dans la navigation de gauche, cliquez sur **recherche &amp; recherche de contenu enquête >**.
    
13. Cliquez sur l’icône plus pour ajouter une recherche.
    
14. Dans la fenêtre **Nouvelle recherche**, saisissez **Recherche de contrat Tailspin** dans **Nom**.
    
15. Dans **Dans quels emplacements voulez-vous effectuer la recherche ?**, cliquez sur **Rechercher partout**, sélectionnez **Exchange**, **SharePoint** et **Dossiers publics**, puis cliquez sur **Suivant**.
    
16. Dans **Que voulez-vous chercher ?**, saisissez **Contrat Tailspin**, puis cliquez sur **Recherche**.
    
17. Dans la liste des recherches, cliquez sur le nom **Recherche de contrat Tailspin**.
    
18. Dans le volet de **recherche de contrat Tailspin** , cliquez sur **Aperçu des résultats de recherche** sous **résultats**. Vous devez voir une fenêtre répertoriant les deux documents sur le site SharePoint de Production ( **Document** et **Document1**) et les **Test courrier 1** et **Test message électronique 3** les messages électroniques à User6. Fermez la fenêtre.
    
19. Dans le volet **Recherche de contenu**, sous **Analyser les résultats avec Advanced eDiscovery**, cliquez sur **Aperçu des résultats pour l’analyse**.
    
20. Dans la fenêtre **Préparer les résultats de recherche pour la recherche de contrat Tailspin**, cliquez sur **Préparer** et attendez qu’elle se termine.
    
Dans cette procédure, vous créez un incident Advanced eDiscovery et analysez les résultats de recherche de contrat Tailspin.
  
1. Dans la navigation de gauche, cliquez sur **eDiscovery** sous **recherche &amp; enquête**.
    
2. Dans le volet **eDiscovery**, cliquez sur **Atteindre Advanced eDiscovery**.
    
3. Dans l’onglet **Advanced eDiscovery**, cliquez sur l’icône plus pour ajouter un nouvel incident.
    
4. 	Dans le volet **Ajouter un incident**, saisissez **Litige de contrat Tailspin** dans **Nom**, puis cliquez sur **OK**. Attendez que l’incident soit créé.
    
5. Double-cliquez sur l’incident **Litige de contrat Tailspin** dans la liste. 
    
6. Dans la liste du **conteneur** , cliquez sur le conteneur de **recherche de contrat Tailspin** , puis cliquez sur **le processus**. Attendez la fin du traitement.
    
7. Lorsque le message **Processus : terminé** apparaît en bas de la fenêtre, cliquez sur **Résumé du processus** dans le volet de navigation de gauche pour afficher un résumé.
    
8. Dans la partie supérieure de la navigation, cliquez sur **Analyser**.
    
9. Dans la page **Installation**, sous **Thèmes**, saisissez **3** dans **Nombre maximal de thèmes**.
    
10. Cliquez sur **analyser** et attendez que l’analyse à effectuer. Vous devez voir une série de graphiques en secteurs avec l’analyse de la population cible, documents, messages électroniques et les pièces jointes. Pour plus d’informations, voir [affichage analyser les résultats](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
Vous pouvez désormais utiliser cet environnement pour créer du contenu, des recherches et des incidents, et réaliser d’autres essais avec Advanced eDiscovery dans Office 365.
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Sécurité des applications cloud pour votre environnement de développement/test Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)

[Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


