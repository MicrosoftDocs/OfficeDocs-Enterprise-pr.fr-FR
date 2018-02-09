---
title: "Stratégies MAM pour votre environnement de développement/test Microsoft 365 Enterprise"
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
description: "Résumé : Utilisez ce Guide de laboratoire de Test pour ajouter des stratégies de EMS mobile application management (MAM) à votre environnement de développement/test Microsoft 365."
ms.openlocfilehash: 9eb636fe14b2fbd1fe45fb7dac528a0d4e31be36
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Stratégies MAM pour votre environnement de développement/test Microsoft 365 Enterprise

 **Résumé :** Utilisez ce Guide de laboratoire de Test pour ajouter des stratégies de EMS mobile application management (MAM) à votre environnement de développement/test Microsoft 365.
  
La mobilité d’entreprise Microsoft + sécurité (EMS) permet à votre personnel gagne en productivité tout en protégeant les données de votre organisation à l’aide de leurs applications favorites et leurs périphériques. Pour plus d’informations, reportez-vous à la section [mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Avec les instructions de cet article, vous ajoutez des stratégies de management (MAM) d’application mobile à votre environnement de développement/test Microsoft 365.
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Microsoft 365

Suivez les instructions dans [l’environnement de développement/test de l’entreprise de 365 de Microsoft](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>Phase 2 : Créer et déployer des stratégies de gestion des applications mobiles pour les appareils iOS et Android

Dans cette phase, vous créez et déployez deux stratégies de gestion des applications mobiles différentes : une pour les appareils iOS et une pour les appareils Android.
  
1. Accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et vous connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
2. Dans un nouvel onglet de votre navigateur, ouvrez le portail Azure ([https://azure.portal.com](https://azure.portal.com)) et connectez-vous en utilisant votre compte d’administrateur global de Office 365.
    
3. Sous l’onglet portail Azure dans Internet Explorer, dans le volet de navigation, cliquez sur **plus de services** (ou sur la flèche vers la droite), tapez **Intune**, puis cliquez sur **Intune**.
    
4. Dans le volet de navigation gauche, cliquez sur **Groupes**.
    
5. Sur la blade **d’utilisateurs et des groupes de groupes** , cliquez sur **Ajouter**.
    
6. Sur la lame de **groupe** , tapez **Gestion des utilisateurs de périphériques d’e/s** dans la zone **nom**, sélectionnez **assigné** dans le **type d’abonnement**, sélectionnez **Oui** pour **les fonctionnalités activer Office ?**, puis cliquez sur **créer**. 
    
7. Fermez la lame du **groupe** .
    
8. Sur la blade **d’utilisateurs et des groupes de groupes** , cliquez sur **Ajouter**.
    
9. Sur la lame de **groupe** , tapez **utilisateurs de périphériques gérés Android** dans la zone **nom**, sélectionnez **assigné** dans le **type d’abonnement**, sélectionnez **Oui** pour **les fonctionnalités activer Office ?**, puis cliquez sur **créer**.
    
10. Fermez la blade **d’utilisateurs et des groupes de groupes** .
    
11. Sur la lame **Intune** , dans la liste des **tâches rapides** , cliquez sur **créer une stratégie de conformité**.
    
12. Sur la lame de **Profils de stratégie de conformité** , cliquez sur **Créer une stratégie**.
    
13. Sur la lame de **Créer une stratégie** , dans la zone **nom**, tapez **iOS**. Dans la **plate-forme**, sélectionnez **iOS**, cliquez sur **OK** sur la lame de la **stratégie de conformité d’e/s** , puis cliquez sur **créer**.
    
14. Sur la lame de **Profils de stratégie de conformité** , cliquez sur **Créer une stratégie**.
    
15. Sur la lame de **Créer une stratégie** , dans la zone **nom**, tapez **Android**. Dans la **plate-forme**, sélectionnez **Android**, cliquez sur **OK** sur la lame de la **stratégie de conformité Android** et puis cliquez sur **créer**.
    
16. La lame de **Profils de stratégie de conformité** , cliquez sur le nom de stratégie **Android** .
    
17. Dans la navigation gauche de la lame **Android - propriétés** , cliquez sur **affectations**, puis cliquez sur **Sélectionner des groupes**.
    
18. Sur la lame **Sélectionnez groupes** , cliquez sur le groupe **d’utilisateurs de périphériques gérés Android** , puis cliquez sur **Sélectionner**.
    
19. Cliquez sur **Enregistrer**et fermez la lame **Android - affectations** .
    
20. La lame de **Profils de stratégie de conformité** , cliquez sur le nom de la stratégie **e/s** .
    
21. Dans la navigation gauche de la lame **d’iOS - propriétés** , cliquez sur **affectations**, puis cliquez sur **Sélectionner des groupes**.
    
22. Sur la lame **Sélectionnez groupes** , cliquez sur le groupe **d’utilisateurs d’appareils iOS gérés** , puis cliquez sur **Sélectionner**.
    
23. Cliquez sur **Enregistrer**et fermez la lame **iOS - affectations** .
    
24. Fermez la lame de **Profils de stratégie de conformité** .
    
25. Sur la lame **Intune** , cliquez sur **Gérer les applications** de la navigation de gauche.
    
26. Sur la blade **d’Applications Mobile** , cliquez sur **applications**.
    
27. Dans la liste des applications, cliquez sur **PowerPoint**, 
    
28. Sur la lame de **Présentation de PowerPoint** , cliquez sur **les affectations > sélectionnez Groupes > périphériques d’e/s gérés > sélectionnez**. Dans **Type**, sélectionnez **disponible**, puis cliquez sur **Enregistrer**.
    
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
    
30. Fermez la lame **Mobile Apps - applications** .
    
31. Sur la blade **d’Applications Mobile** , cliquez sur **Stratégies de Protection d’application**.
    
32. Sur la lame de **Stratégies de Protection d’application** , cliquez sur **Ajouter une stratégie**.
    
33. Sur la blade **d’Ajouter une stratégie** , tapez **e/s**, puis cliquez sur **Sélectionner les applications requises**.
    
34. Sur la blade **d’applications** , cliquez sur **PowerPoint**, **De Microsoft Dynamics CRM sur iPhone**, **Excel**, **De Microsoft Dynamics CRM sur iPhone**, **Word**, **OneNote**, **Outlook**, puis cliquez sur **Sélectionner**.
    
35. Sur la blade **d’Ajouter une stratégie** , cliquez sur **créer**.
    
36. Sur la lame de **Stratégies de Protection d’application** , cliquez sur **Ajouter une stratégie**.
    
37. Sur la blade **d’Ajouter une stratégie** , tapez **Android**, sélectionnez **Android** dans la **plate-forme**, puis cliquez sur **Sélectionnez les applications requises**.
    
38. Sur la blade **d’applications** , cliquez sur **Dynamics CRM pour tablette**, **PowerPoint**, **Excel**, **Word**, **Outlook**et **Dynamics CRM pour les téléphones**et puis cliquez sur **Sélectionner**.
    
39. Sur la blade **d’Ajouter une stratégie** , cliquez sur **créer**.
    
Vous avez deux stratégies de gestion des applications mobiles : une pour les appareils iOS et l’autre pour les appareils Android. Vous souhaitez tester les paramètres pour les applications sélectionnées.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles du jeu de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="see-also"></a>Voir aussi

[L’environnement de développement/test Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Inscrire les périphériques iOS ou Android dans votre environnement de développement/test Microsoft Enterprise 365](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


