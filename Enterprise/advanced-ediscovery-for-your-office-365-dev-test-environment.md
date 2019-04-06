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
ms.openlocfilehash: b9c12a132eb83f0317503a736313b547dfe475e7
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038018"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Advanced eDiscovery pour votre environnement de développement/test Office 365

 **Résumé :** Configurez et faites une démonstration d’Office 365 Advanced eDiscovery avec des données d’échantillon dans votre environnement de développement/test Office 365.
  
Office 365 Advanced eDiscovery vous permet de trouver et d'analyser rapidement les informations pertinentes dans les données stockées dans Office 365, y compris le courrier électronique et les documents. Cela permet de réaliser des économies importantes en matière de temps et d’argent, notamment en cas de litige. Pour plus d'informations, voir [Découverte électronique avancée Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Avec les instructions fournies dans cet article, vous créez un petit jeu de données pour un litige fictif à propos d’un contrat et l’analysez avec Advanced eDiscovery.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de One Microsoft Cloud.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Phase 1 : Création d’un environnement de développement/test Office 365

Si vous souhaitez simplement tester Advanced eDiscovery de manière légère avec la configuration minimale requise, suivez les instructions de la phase 2 et de la phase 3 de l' [environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester la découverte électronique avancée dans une entreprise simulée, suivez les instructions de [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Le test de eDiscovery avancé ne nécessite pas l'environnement d'entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d'annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici comme option afin que vous puissiez effectuer des tests et des expérimentations dans un environnement qui représente une organisation typique. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Phase 2 : Création des données d’exemple pour Advanced eDiscovery

Cette procédure vous permet de créer des messages électroniques que vous analyserez plus tard dans un incident Advanced eDiscovery.
  
1. Ouvrez Internet Explorer et connectez [https://outlook.com](https://outlook.com) -vous au compte Outlook que vous avez créé au cours de la phase 2 de l'environnement de[développement/test Office 365](office-365-dev-test-environment.md).
    
  - Si vous utilisez l’environnement de développement/test léger, ouvrez une session privée d’Internet Explorer et connectez-vous sur votre ordinateur local.
    
  - Si vous utilisez l'environnement de développement/test d'entreprise simulé, utilisez le portail Azure ([https://portal.azure.com](https://portal.azure.com)) pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de client1.
    
2. Dans l’onglet **Courrier Outlook**, cliquez sur **Nouveau**.
    
3. Dans **à**, tapez l'adresse de messagerie du compte User6 de votre abonnement à la version d'évaluation ( **User6 @.**<organization name> **. onmicrosoft.com**).
    
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
    
14. Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis sur **Déconnexion**.
    
15. Ouvrez un nouvel onglet et connectez-vous au portail Office 365 ([https://www.office.com](https://www.office.com)) avec le nom de compte et le mot de passe du compte User6 de votre abonnement à la version d'évaluation.
    
16. Dans l’onglet **Portail Office 365**, cliquez sur **Courrier**.
    
17. Sous l'onglet **mail-User6-Outlook** , vérifiez que User6 a reçu les trois messages électroniques du compte de messagerie Outlook.
    
18. Revenez à l’**onglet Portail Office 365** pour User6.
    
19. Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis sur **Déconnexion**.
    
Dans cette procédure, vous créez deux documents Word que vous analyserez plus tard dans un incident Advanced eDiscovery.
  
1. Dans la page **Office**, cliquez sur **Se connecter,** puis connectez-vous avec les informations d’identification de votre compte d’administrateur global.
    
2. dans un nouvel onglet, accédez à l'URL de votre site SharePoint de Production: **https://** <fictional organization name> **. sharepoint.com/sites/production**
    
3. Dans l’onglet **Collection de sites de production**, sous **Documents**, cliquez sur **Nouveau > Document Word**.
    
4. Sur la page **Word Online**, saisissez **Brouillon de contrat Tailspin**, patientez jusqu’à ce que le titre affiche **Enregistré**, puis fermez l’onglet de la page **Word Online**.
    
5. Dans l’onglet **Collection de sites de production**, sous **Documents**, cliquez sur **Nouveau > Document Word**.
    
6. 	Dans l’onglet **Word Online**, saisissez **Notes sur le litige lié au contrat Tailspin**, patientez jusqu’à ce que le titre affiche **Enregistré**, puis fermez l’onglet **Word Online**.
    
7. Dans l’onglet **Collection de sites de production**, Vous devriez voir **Document** et **Document1** dans la liste de documents.
    
8. Fermez l’onglet **Collection de sites de production**.
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Phase 3: utiliser Advanced eDiscovery pour un litige légal

Malheureusement, un litige contractuel entre votre organisation et Tailspin Toys a atteint le point d’action en justice. Dans cette procédure, vous créez et configurez un cas avancé de découverte électronique pour rechercher et analyser le courrier électronique et les documents qui contiennent le texte «Tailspin Contract».
  
La procédure d’utilisation d’Advanced eDiscovery est la suivante :
  
- Créez une recherche dans le centre &amp; de sécurité conformité, analysez ses résultats, puis préparez les résultats pour Advanced eDiscovery.
    
- Créez et configurez un incident dans Advanced eDiscovery et analysez les résultats de recherche.
    
Dans cette procédure, vous créez une recherche dans le centre &amp; de sécurité conformité pour «Tailspin Contract», examinez les résultats, puis préparez les résultats pour Advanced eDiscovery.
  
1. Dans l’onglet **Portail Office 365**, cliquez sur **Admin**.
    
2. Dans le volet de navigation gauche de l’onglet Centre d’administration, cliquez sur **Centres d’administration > Conformité**.
    
3. Sous l' **onglet &amp; conformité de sécurité** , cliquez sur **autorisations**.
    
4. Dans la liste **Autorisations**, double-cliquez sur **Gestion de l’organisation**.
    
5. Dans la fenêtre **Groupe de rôles**, sous **Membres**, cliquez sur le signe plus.
    
6. Dans la fenêtre **Sélectionner les membres**, double-cliquez sur le nom de votre compte d’administrateur, puis cliquez sur **OK**.
    
7. Dans la fenêtre **Groupe de rôles**, cliquez sur **Enregistrer**.
    
8. Dans la liste **Autorisations**, double-cliquez sur **Gestionnaire eDiscovery**.
    
9. Dans la fenêtre **Groupe de rôles**, sous **Administrateur eDiscovery**, cliquez sur l’icône plus.
    
10. Dans la fenêtre **Sélectionner les membres**, double-cliquez sur le nom de votre compte d’administrateur, puis cliquez sur **OK**.
    
11. Dans la fenêtre **Groupe de rôles**, cliquez sur **Enregistrer**.
    
12. Dans le volet de navigation de gauche, cliquez sur Search **Search &amp; > content Search**.
    
13. Cliquez sur l’icône plus pour ajouter une recherche.
    
14. Dans la fenêtre **Nouvelle recherche**, saisissez **Recherche de contrat Tailspin** dans **Nom**.
    
15. Dans **Dans quels emplacements voulez-vous effectuer la recherche ?**, cliquez sur **Rechercher partout**, sélectionnez **Exchange**, **SharePoint** et **Dossiers publics**, puis cliquez sur **Suivant**.
    
16. Dans **Que voulez-vous chercher ?**, saisissez **Contrat Tailspin**, puis cliquez sur **Recherche**.
    
17. Dans la liste des recherches, cliquez sur le nom **Recherche de contrat Tailspin**.
    
18. Dans le volet **Recherche de contrat Tailspin**, cliquez sur **Aperçu des résultats de recherche** sous **Résultats**. Vous devriez voir une fenêtre répertoriant les deux documents sur le site SharePoint de production ( **document** et **Document1**) et les e-mails de **test 1** et de **courrier électronique de test 3** vers User6. Fermez la fenêtre.
    
19. Dans le volet **Recherche de contenu**, sous **Analyser les résultats avec Advanced eDiscovery**, cliquez sur **Aperçu des résultats pour l’analyse**.
    
20. Dans la fenêtre **Préparer les résultats de recherche pour la recherche de contrat Tailspin**, cliquez sur **Préparer** et attendez qu’elle se termine.
    
Dans cette procédure, vous créez un incident Advanced eDiscovery et analysez les résultats de recherche de contrat Tailspin.
  
1. Dans le volet de navigation de gauche, cliquez sur **eDiscovery** sous **enquête de recherche &amp; **.
    
2. Dans le volet **eDiscovery**, cliquez sur **Atteindre Advanced eDiscovery**.
    
3. Dans l’onglet **Advanced eDiscovery**, cliquez sur l’icône plus pour ajouter un nouvel incident.
    
4. 	Dans le volet **Ajouter un incident**, saisissez **Litige de contrat Tailspin** dans **Nom**, puis cliquez sur **OK**. Attendez que l’incident soit créé.
    
5. Double-cliquez sur l’incident **Litige de contrat Tailspin** dans la liste. 
    
6. Dans la liste **conteneur** , cliquez sur le conteneur de **recherche de contrat Tailspin** , puis sur **traiter**. Attendez la fin du traitement.
    
7. Lorsque le message **Processus : terminé** apparaît en bas de la fenêtre, cliquez sur **Résumé du processus** dans le volet de navigation de gauche pour afficher un résumé.
    
8. Dans la partie supérieure de la navigation, cliquez sur **Analyser**.
    
9. Dans la page **Installation**, sous **Thèmes**, saisissez **3** dans **Nombre maximal de thèmes**.
    
10. Cliquez sur **Analyser** et attendez que l’analyse se termine. Vous devriez voir une série de graphiques en secteurs avec l’analyse de la population cible, des documents, des messages électroniques et des pièces jointes. Pour plus d'informations, consultez la rubrique [affichage des résultats](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)de l'analyse.
    
Vous pouvez désormais utiliser cet environnement pour créer du contenu, des recherches et des incidents, et réaliser d’autres essais avec Advanced eDiscovery dans Office 365.
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Sécurité des applications cloud pour votre environnement de développement/test Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)

[Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


