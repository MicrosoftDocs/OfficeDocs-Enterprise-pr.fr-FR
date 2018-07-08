---
title: Stratégies GAM pour votre environnement de développement/test Microsoft 365 Entreprise
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
ms.openlocfilehash: 0a5c81665edf06631b8cebc57c9e715c78d3d85e
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188152"
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Stratégies GAM pour votre environnement de développement/test Microsoft 365 Entreprise

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
    
7. Fermez le volet **Groupe**.
    
8. Sur le serveur lame **groupes de groupes** , cliquez sur **Ajouter**.
    
9. Dans la **groupe** lame, sélectionnez **Office 365** pour **type de groupe ?**, tapez **utilisateur d’un appareil Android gérés** dans **nom**, sélectionnez **assigné** dans le **type d’appartenance**, puis cliquez sur **créer**.
    
10. Fermez la lame de **groupes de groupes** .
    
11. Dans le volet **Intune**, dans la liste **Tâches rapides**, cliquez sur **Créer une stratégie de conformité**.
    
12. Dans le volet **Profils de stratégie de conformité**, cliquez sur **Créer une stratégie**.
    
13. Dans le volet **Créer une stratégie**, dans **Nom**, tapez **iOS**. Dans **Plateforme**, sélectionnez **iOS**, cliquez sur **OK** dans le volet **Stratégie de conformité iOS**, puis cliquez sur **Créer**.
    
14. Dans le volet **Profils de stratégie de conformité**, cliquez sur **Créer une stratégie**.
    
15. Dans le volet **Créer une stratégie**, dans **Nom**, tapez **Android**. Dans **Plateforme**, sélectionnez **Android**, cliquez sur **OK** dans le volet **Stratégie de conformité Android**, puis cliquez sur **Créer**.
    
16. Dans le volet **Profils de stratégie de conformité**, cliquez sur le nom de la stratégie **Android**.
    
17. Dans la barre de navigation de gauche du volet **Android - Propriétés**, cliquez sur **Affectations**, puis cliquez sur **Sélectionner des groupes**.
    
18. Dans le volet **Sélectionner des groupes**, sélectionnez le groupe **Utilisateurs d’appareils Android partagés**, puis cliquez sur **Sélectionner**.
    
19. Cliquez sur **Enregistrer**, puis fermez la lame **Android - affectations** .
    
20. Dans le volet **Profils de stratégie de conformité**, cliquez sur le nom de la stratégie **iOS**.
    
21. Dans la barre de navigation de gauche du volet **iOS - Propriétés**, cliquez sur **Affectations**, puis cliquez sur **Sélectionner des groupes**.
    
22. Dans le volet **Sélectionner des groupes**, sélectionnez le groupe **Utilisateurs d’appareils iOS gérés**, puis cliquez sur **Sélectionner**.
    
23. Cliquez sur **Enregistrer**, puis fermez la lame **iOS - affectations** .
    
24. Fermez le volet **Profils de stratégie de conformité**.
    
25. Dans le volet **Intune**, cliquez sur **Gérer les applications** dans le volet de navigation de gauche.
    
26. Dans le volet **Applications mobiles**, cliquez sur **Applications**.
    
27. Dans la liste des applications, cliquez sur **PowerPoint**.  
    
28. Dans le volet **Présentation PowerPoint**, cliquez sur **Affectations > Sélectionner des groupes > Appareils iOS gérés > Sélectionner**. Dans **Type**, sélectionnez **Disponible**, puis cliquez sur **Enregistrer**.
    
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
    
30. Fermez le volet **Applications mobiles - Applications**.
    
31. Dans le volet **Applications mobiles**, cliquez sur **Stratégies de protection de l’application**.
    
32. Dans le volet **Stratégies de protection de l’application**, cliquez sur **Ajouter une stratégie**.
    
33. Dans le volet **Ajouter une stratégie**, tapez **iOS**, puis cliquez sur **Sélectionner les applications requises**.
    
34. Dans le volet **Applications**, cliquez sur **PowerPoint**, **Microsoft Dynamics CRM sur iPhone**, **Excel**, **Microsoft Dynamics CRM sur iPhone**, **Word**, **OneNote** et **Outlook**, puis cliquez sur **Sélectionner**.
    
35. Dans le volet **Ajouter une stratégie**, cliquez sur **Créer**.
    
36. Dans le volet **Stratégies de protection de l’application**, cliquez sur **Ajouter une stratégie**.
    
37. Dans le volet **Ajouter une stratégie**, tapez **Android**, sélectionnez **Android** dans **Plateforme**, puis cliquez sur **Sélectionner les applications requises**.
    
38. Dans le volet **Applications**, cliquez sur **PowerPoint**, **Dynamics CRM pour tablettes**, **Excel**, **Word**, **Outlook**, et **Dynamics CRM pour téléphones**, puis cliquez sur **Sélectionner**.
    
39. Dans le volet **Ajouter une stratégie**, cliquez sur **Créer**.
    
Vous avez deux stratégies de gestion des applications mobiles : une pour les appareils iOS et l’autre pour les appareils Android. Vous souhaitez tester les paramètres pour les applications sélectionnées.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles du jeu de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="see-also"></a>Voir aussi

[Environnement de développement/test Microsoft 365 Entreprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Inscription d’appareils iOS et Android dans votre environnement de développement/test Microsoft 365 Entreprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


