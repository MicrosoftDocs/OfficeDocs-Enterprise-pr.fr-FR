---
title: Stratégies MAM pour votre environnement de développement/test Microsoft 365 pour entreprises
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: 'Résumé : Utilisez ce Guide de laboratoire de Test pour ajouter des stratégies de gestion (MAM) EMS application mobile à votre environnement de développement/test Microsoft 365.'
ms.openlocfilehash: 1d4ede9b5757d4adce8909586790bcad51f7433f
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Stratégies MAM pour votre environnement de développement/test Microsoft 365 pour entreprises

 **Résumé :** Utilisez ce Guide de laboratoire de Test pour ajouter des stratégies de gestion (MAM) EMS application mobile à votre environnement de développement/test Microsoft 365.
  
La mobilité d’entreprise Microsoft + la sécurité (EMS) permet de conserver vos employés productifs à l’aide de leurs applications favorites et leurs périphériques lors de la protection des données de votre organisation. Pour plus d’informations, voir [mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Avec les instructions de cet article, vous ajoutez des stratégies de gestion (MAM) des applications mobiles pour votre environnement de développement/test Microsoft 365.
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>Phase 1 : Création de votre environnement de développement/test Microsoft 365

Suivez les instructions dans [l’environnement de développement/test The Microsoft 365 pour entreprises](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>Phase 2 : Créer et déployer des stratégies de gestion des applications mobiles pour les appareils iOS et Android

Dans cette phase, vous créez et déployez deux stratégies de gestion des applications mobiles différentes : une pour les appareils iOS et une pour les appareils Android.
  
1. Accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et se connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
2. Dans un nouvel onglet de votre navigateur, ouvrez le portail Azure ([https://azure.portal.com](https://azure.portal.com)) et connectez-vous à l’aide de votre compte d’administrateur général Office 365.
    
3. Sous l’onglet portail Azure dans Internet Explorer, dans le volet de navigation, cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.
    
4. Dans le volet de navigation gauche, cliquez sur **Groupes**.
    
5. Sur le serveur lame **groupes de groupes** , cliquez sur **+ Nouveau groupe**.
    
6. Dans la **groupe** lame, sélectionnez **Office 365** pour **type de groupe ?**, tapez **gérées les utilisateurs d’appareils iOS** dans **nom**, sélectionnez **assigné** dans le **type d’appartenance**et puis cliquez sur **créer**. 
    
7. Fermez la lame de **groupe** .
    
8. Sur le serveur lame **groupes de groupes** , cliquez sur **Ajouter**.
    
9. Dans la **groupe** lame, sélectionnez **Office 365** pour **type de groupe ?**, tapez **utilisateur d’un appareil Android gérés** dans **nom**, sélectionnez **assigné** dans le **type d’appartenance**, puis cliquez sur **créer**.
    
10. Fermez la lame de **groupes de groupes** .
    
11. Dans la lame **Intune** , dans la liste des **tâches rapides** , cliquez sur **créer une stratégie de conformité**.
    
12. Sur le serveur lame **Profils de stratégie de conformité** , cliquez sur **Créer une stratégie**.
    
13. Sur le serveur lame **Créer une stratégie** , dans **nom**, tapez **iOS**. Dans la **plateforme**, sélectionnez **iOS**, cliquez sur **OK** dans la **stratégie de conformité iOS** lame, puis cliquez sur **créer**.
    
14. Sur le serveur lame **Profils de stratégie de conformité** , cliquez sur **Créer une stratégie**.
    
15. Sur le serveur lame **Créer une stratégie** , dans **nom**, tapez **Android**. Dans la **plateforme**, sélectionnez **Android**, cliquez sur **OK** dans la **stratégie de conformité Android** lame, puis cliquez sur **créer**.
    
16. Sur le serveur lame **Profils de stratégie de conformité** , cliquez sur le nom de stratégie **Android** .
    
17. Dans la navigation de gauche de la lame **Android - propriétés** , cliquez sur **les affectations**, puis cliquez sur **Sélectionner des groupes**.
    
18. Sur le serveur lame **Sélectionnez groupes** , cliquez sur le groupe **d’utilisateurs d’appareils Android géré** , puis cliquez sur **Sélectionner**.
    
19. Cliquez sur **Enregistrer**, puis fermez la lame **Android - affectations** .
    
20. Sur le serveur lame **Profils de stratégie de conformité** , cliquez sur le nom de stratégie **iOS** .
    
21. Dans la navigation de gauche de la lame **iOS - propriétés** , cliquez sur **les affectations**, puis cliquez sur **Sélectionner des groupes**.
    
22. Sur le serveur lame **Sélectionnez groupes** , cliquez sur le groupe **d’utilisateurs d’appareils iOS géré** , puis cliquez sur **Sélectionner**.
    
23. Cliquez sur **Enregistrer**, puis fermez la lame **iOS - affectations** .
    
24. Fermez la lame de **Profils de stratégie de conformité** .
    
25. Sur le serveur lame **Intune** , cliquez sur **Gérer les applications** dans le volet de navigation gauche.
    
26. Sur le serveur lame **Applications Mobile** , cliquez sur **applications**.
    
27. Dans la liste des applications, cliquez sur **PowerPoint**, 
    
28. Sur le serveur lame **Présentation PowerPoint** , cliquez sur **affectations > sélectionnez Groupes > périphériques iOS gérés > sélectionnez**. Dans **Type**, sélectionnez **disponible**, puis cliquez sur **Enregistrer**.
    
29. Répétez l’étape 28 pour les applications suivantes :
    
  - Outlook pour Android
    
  - Word pour iOS
    
  - Excel pour iOS
    
  - Outlook pour iOS
    
  - Microsoft Dynamics CRM sur iPad pour iOS
    
  - Microsoft Dynamics CRM sur iPhone pour iOS
    
  - Dynamics CRM pour les téléphones Android
    
  - Dynamics CRM pour les tablettes Android
    
  - Excel pour Android
    
  - Word pour Android
    
  - OneNote pour iOS
    
30. Fermez la lame **Applications Mobile - applications** .
    
31. Sur le serveur lame **Applications Mobile** , cliquez sur **Stratégies de Protection des applications**.
    
32. Sur le serveur lame de **Stratégies de Protection des applications** , cliquez sur **Ajouter une stratégie**.
    
33. Sur le serveur lame **Ajouter une stratégie** , tapez **iOS**, puis cliquez sur **Sélectionner les applications nécessaires**.
    
34. Sur le serveur lame **applications** , cliquez sur **PowerPoint**, **Microsoft Dynamics CRM sur iPhone**, **Excel**, **Microsoft Dynamics CRM sur iPhone**, **Word**, **OneNote**, **Outlook**, puis cliquez sur **Sélectionner**.
    
35. Sur le serveur lame **Ajouter une stratégie** , cliquez sur **créer**.
    
36. Sur le serveur lame de **Stratégies de Protection des applications** , cliquez sur **Ajouter une stratégie**.
    
37. Sur le serveur lame **Ajouter une stratégie** , tapez **Android**, sélectionnez **Android** de **plateforme**, puis cliquez sur **Sélectionner les applications requises**.
    
38. Sur le serveur lame **applications** , cliquez sur **Dynamics CRM pour tablettes**, **PowerPoint**, **Excel**, **Word**, **Outlook**et **Dynamics CRM pour les téléphones**, puis cliquez sur **Sélectionner**.
    
39. Sur le serveur lame **Ajouter une stratégie** , cliquez sur **créer**.
    
Vous avez deux stratégies de gestion des applications mobiles : une pour les appareils iOS et l’autre pour les appareils Android. Vous souhaitez tester les paramètres pour les applications sélectionnées.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles du jeu de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="see-also"></a>Voir aussi

[Environnement de développement/test Microsoft 365 Entreprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Inscription d’appareils iOS et Android dans votre environnement de développement/test Microsoft Enterprise 365](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


