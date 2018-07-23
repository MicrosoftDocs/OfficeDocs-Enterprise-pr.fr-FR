---
title: Inscription d’appareils iOS et Android dans votre environnement de développement/test Microsoft 365 Entreprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Résumé : Utilisez ce Guide de laboratoire de Test pour inscrire des périphériques dans votre environnement de développement/test Microsoft 365 et les gérer à distance.'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720410"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Inscription d’appareils iOS et Android dans votre environnement de développement/test Microsoft 365 Entreprise

 **Résumé :** Utilisez ce Guide de laboratoire de Test pour inscrire des périphériques dans votre environnement de développement/test Microsoft 365 et les gérer à distance.
  
La Suite de mobilité Enterprise (EMS) Microsoft protège vos employés productifs à l’aide de leurs applications favorites et leurs périphériques lors de la protection des données de votre organisation. Pour plus d’informations, voir [mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Si vous devez appliquer la sécurité au niveau du périphérique, les appareils doit s’inscrire dans Microsoft Intune. Inscription de périphérique non seulement vous aide à gérer les périphériques appartenant à l’organisation, mais également de personnel (BYOD) et des périphériques partagés, en fonction de votre organisation le juridique stratégies.
  
En suivant les instructions fournies dans cet article, vous serez en mesure de s’inscrire et tester les fonctionnalités de gestion de base des périphériques mobiles pour les périphériques iOS ou Android dans votre environnement de développement/test Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Microsoft 365

Suivez les instructions dans [l’environnement de développement/test The Microsoft 365 pour entreprises](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2 : Inscrire vos périphériques iOS ou Android

Tout d’abord, suivez les instructions fournies dans [installer et se connecter à l’application de portail d’entreprise](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) pour personnaliser l’application de portail d’entreprise Microsoft Intune pour votre environnement de test.

Ensuite, suivez les instructions de [configurer l’accès aux ressources de votre société](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) à inscrire un périphérique iOS.

Ensuite, suivez les instructions dans [l’inscription de votre appareil Android dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) pour inscrire un appareil Android.

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Phase 3 : Gérer vos périphériques iOS ou Android à distance

Intune Microsoft fournit à distance verrouillage et code secret réinitialisation de fonctionnalités. Si une personne perd leur appareil, vous pouvez verrouiller le périphérique à distance. Si une personne oublie son code confidentiel, vous pouvez le réinitialiser à distance.
  
Pour verrouiller une iOS ou un appareil Android à distance :

1. Connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) avec les informations d’identification de votre compte d’administrateur global.
2. Cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.
3. Cliquez sur **périphériques > tous les périphériques**.
4. Dans la liste des périphériques, cliquez sur un appareil Android ou sur iOS, puis cliquez sur l’action **Verrouiller à distance** .

    
Pour réinitialiser le code secret à distance, procédez comme suit :

1. Si nécessaire, connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) avec les informations d’identification de votre compte d’administrateur global.
2. Cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.
3. Cliquez sur **périphériques > tous les périphériques**.
4. Dans la liste des périphériques gérer, cliquez sur un appareil Android ou sur iOS et choisissez **... Plus**. Puis sélectionnez l’action **Supprimer le code secret** périphérique à distance.

Pour une expérimentation supplémentaire, voir [actions de périphérique disponible](https://docs.microsoft.com/intune/device-management#available-device-actions).

    

> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles du jeu de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="see-also"></a>Voir aussi

[Environnement de développement/test Microsoft 365 Entreprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Stratégies GAM pour votre environnement de développement/test Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


