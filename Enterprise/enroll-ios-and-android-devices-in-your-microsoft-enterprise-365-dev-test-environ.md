---
title: Inscription d’appareils iOS et Android dans votre environnement de développement/test Microsoft 365 Entreprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Résumé : Utilisez ce Guide de laboratoire de Test pour inscrire des périphériques dans votre environnement de développement/test Microsoft 365 et les gérer à distance.'
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188102"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Inscription d’appareils iOS et Android dans votre environnement de développement/test Microsoft 365 Entreprise

 **Résumé :** Utilisez ce Guide de laboratoire de Test pour inscrire des périphériques dans votre environnement de développement/test Microsoft 365 et les gérer à distance.
  
La Suite de mobilité Enterprise (EMS) Microsoft protège vos employés productifs à l’aide de leurs applications favorites et leurs périphériques lors de la protection des données de votre organisation. Pour plus d’informations, voir [mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Si vous devez appliquer la sécurité au niveau du périphérique, les appareils doit s’inscrire dans Microsoft Intune. Inscription de périphérique non seulement vous aide à gérer les périphériques appartenant à l’organisation, mais également de personnel (BYOD) et des périphériques partagés, en fonction de votre organisation le juridique stratégies.
  
En suivant les instructions fournies dans cet article, vous serez en mesure de s’inscrire et tester les fonctionnalités de gestion de base des périphériques mobiles pour les périphériques iOS ou Android dans votre environnement de développement/test Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Microsoft 365

Suivez les instructions dans [l’environnement de développement/test The Microsoft 365 pour entreprises](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2 : Inscrire vos périphériques iOS ou Android

Tout d’abord, suivez les instructions fournies dans [installer et se connecter à l’application de portail d’entreprise](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) pour personnaliser l’application de portail d’entreprise Microsoft Intune pour votre client de développement/test.

Ensuite, suivez les instructions de [configurer l’accès aux ressources de votre société](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) à inscrire un périphérique iOS.

Ensuite, suivez les instructions dans [l’inscription de votre appareil Android dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) pour inscrire un appareil Android.

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a>Phase 2 : Gérer vos périphériques iOS ou Android à distance

Microsoft Intune fournit des fonctionnalités de verrouillage à distance et de réinitialisation du code secret. Si une personne perd son appareil, vous pouvez le verrouiller à distance. Si quelqu’un oublie son code secret, vous pouvez le supprimer à distance.
  
Pour verrouiller un appareil iOS à distance, procédez comme suit :
  
1.  Ouvrir un nouvel onglet et accédez à http://manage.microsoft.com (le cas échéant). 

2.  À partir de la console d’administration Microsoft Intune de votre navigateur, cliquez sur **groupes** dans le volet de navigation gauche.

3. Dans le volet **Groupes**, ouvrez **Tous les périphériques > Tous les appareils mobiles > Tous les appareils gérés par gestion directe**.
    
4. Dans le volet **Tous les appareils gérés par gestion directe**, cliquez sur l’onglet **Appareils**.
    
5. Dans la liste des périphériques, cliquez sur votre appareil iOS.  
    
6. À partir de votre appareil iOS, assurez-vous qu’il se trouve sur l’écran principal.  
    
7. À partir de votre ordinateur d’administration, dans la barre des tâches, cliquez sur **Tâches à distance > Verrouiller à distance**. Regardez votre appareil iOS lorsqu’il bascule vers l’écran de verrouillage.
    
Pour supprimer le code secret, procédez comme suit :
  
1. À partir de votre ordinateur d’administration, dans le volet **Tous les appareils gérés par gestion directe**, cliquez sur l’onglet **Appareils**.
    
2. Dans la liste, cliquez sur votre appareil iOS. Dans la barre des tâches, cliquez sur **Tâches à distance > Réinitialisation du code d’accès**. Patientez une minute.
    
3. À partir de votre appareil iOS, déverrouillez-le et constatez qu’il n’y a plus de code secret. Pour modifier à nouveau le code secret, accédez à **Paramètres**, puis **Code secret**.
    
Pour verrouiller un appareil Android à distance, procédez comme suit :
  
1. À partir de la console d’administration Microsoft Intune de votre navigateur, cliquez sur **groupes** dans le volet de navigation gauche.
    
2. Dans le volet **Groupes**, ouvrez **Tous les périphériques > Tous les appareils mobiles > Tous les appareils gérés par gestion directe**.
    
3. Dans le volet **Tous les appareils gérés par gestion directe**, cliquez sur l’onglet **Appareils**.
    
4. Dans la liste des périphériques, cliquez sur votre appareil Android.  
    
5. À partir de votre appareil Android, assurez-vous qu’il se trouve sur l’écran principal.  
    
6. À partir de votre ordinateur d’administration, dans la barre des tâches, cliquez sur **Tâches à distance > Verrouiller à distance**. Lorsque vous y êtes invité, cliquez sur **Oui**.
    
7. Regardez votre appareil Android lorsqu’il bascule vers l’écran de verrouillage.
    
Lorsque vous réinitialisez le mot de passe pour les appareils Android, le portail d’administration Intune génère et configure un mot de passe fort.
  
Pour réinitialiser le code secret à distance, procédez comme suit :
  
1. À partir de votre ordinateur d’administration, sous l’onglet de la console d’administration Microsoft Intune de votre navigateur, dans le volet **Tous les appareils gérés par gestion directe**, cliquez sur votre appareil Android.
    
2. Dans la barre des tâches, cliquez sur **Tâches à distance > Réinitialisation du code d’accès**.
    
3. À l’invite **Tâche à distance : réinitialisation du code d’accès**, cliquez sur **Oui**. Patientez une minute.
    
4. Dans le volet **Tous les appareils gérés par gestion directe**, cliquez sur l’onglet **Afficher les propriétés**.
    
5. Sous **Réinitialisation du code d’accès**, notez le nouveau code secret.
    
6. Dans votre appareil Android, entrez le nouveau code secret à partir de l’écran de verrouillage.  
    
7. Pour modifier à nouveau le code secret, accédez à **Paramètres**, appuyez sur **Appareil** et **Écran de verrouillage**, ressaisissez le nouveau mot de passe, appuyez sur **Écran de verrouillage**, puis choisissez le code secret.
    

> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles du jeu de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="see-also"></a>Voir aussi

[Environnement de développement/test Microsoft 365 Entreprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Stratégies GAM pour votre environnement de développement/test Microsoft 365 Entreprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


