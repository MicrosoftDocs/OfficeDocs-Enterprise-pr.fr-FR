---
title: "Authentification multifacteur pour votre environnement de développement/test Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: TLG, Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "Résumé : Configurer plusieurs facteurs d’authentification à l’aide de messages textuels envoyés sur un téléphone intelligent dans un environnement de développement/test d’Office 365."
ms.openlocfilehash: 5f0767aedd69cd568c88617eac739ba7abb00b9b
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Authentification multifacteur pour votre environnement de développement/test Office 365

 **Résumé :** Configurer plusieurs facteurs d’authentification à l’aide de messages textuels envoyés sur un téléphone intelligent dans un environnement de développement/test d’Office 365.
  
Pour bénéficier d’un niveau supplémentaire de sécurité lors de la connexion à votre abonnement Office 365, vous pouvez activer l’authentification multifacteur Azure, qui exige davantage qu’un simple nom d’utilisateur et mot de passe pour vérifier un compte. Avec l’authentification multifacteur pour Office 365, les utilisateurs sont tenus de confirmer la bonne réception d’un appel téléphonique, de taper un code de vérification envoyé dans un message texte ou de spécifier un mot de passe d’application sur leur smartphone après avoir entré correctement leur mot de passe. Ils peuvent se connecter uniquement lorsque ce deuxième facteur d’authentification a été respecté.  
  
Cet article décrit comment activer et tester l’authentification basée sur message texte pour un compte Office 365 spécifique.
  
Il existe deux phases de configuration de l’authentification multifacteur pour Office 365 dans un environnement de développement/test :
  
1. Créez l’environnement de développement/test Office 365.
    
2. Activez et testez l’authentification multifacteur pour le compte d’utilisateur 2.
    
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée

Si vous souhaitez juste tester plusieurs facteurs d’authentification d’une façon légère avec la configuration minimale requise, suivez les instructions dans les étapes 2 et 3 de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester une authentification multifactorielle dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Le test de l’authentification multifacteur ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester l’authentification multifacteur et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2

Activez l’authentification multifacteur pour le compte d’utilisateur 2 en procédant comme suit :
  
1. Ouvrir une autre instance de votre navigateur et accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) puis connectez-vous à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
2. À partir de la page principale du portail, cliquez sur **Admin**.
    
3. Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
4. Dans le volet utilisateurs actifs, cliquez sur **plus > installation Azure multi-facteurs auth**.
    
5. Dans la liste, cliquez sur le compte de **l’utilisateur 2** .
    
6. Dans la section **2 de l’utilisateur** , sous **étapes rapides**, cliquez sur **Activer**.
    
7. Dans la boîte de dialogue **sur l’activation de plusieurs facteur auth** , cliquez sur **Activer l’authentification de plusieurs facteur**.
    
8. Dans la boîte de dialogue **mise à jour réussie** , cliquez sur **Fermer**.
    
9. Sous l’onglet **Accueil de Microsoft Office** , cliquez sur l’icône de compte utilisateur dans le coin supérieur droit, puis cliquez sur **se déconnecter**.
    
10. Fermez l’instance de navigateur.
    
Terminez la configuration pour que le compte d’utilisateur 2 utilise un message texte pour la validation et testez-le en procédant comme suit :
  
1. Ouvrez une nouvelle instance de votre navigateur.
    
2. Accédez au portail d’Office 365 ([https://portal.office.com](https://portal.office.com)) et connectez-vous avec le compte d’utilisateur 2 (Utilisateur2 @\<nom de l’organisation >. onmicrosoft.com) et le mot de passe.
    
3. Après l’ouverture de session, vous êtes invité à configurer le compte pour la validation de la sécurité supplémentaires. Cliquez sur **Installer maintenant**.
    
4. Dans la page **vérification de la sécurité supplémentaires** :
    
  - Sélectionnez le pays ou la région.
    
  - Tapez le numéro de téléphone du smartphone qui recevra les SMS.
    
  - Sélectionnez **M’envoyer un code par message texte**.
    
5. Cliquez sur **Contact**.
    
6. Saisissez le code de vérification dans le message reçu sur votre téléphone intelligent, puis cliquez sur **Vérifier**.
    
7. Sur le **étape 3 : conserver vos applications existantes** la page Enregistrer le mot de passe d’application affichée pour le compte de l’utilisateur 2 dans un emplacement sécurisé et puis cliquez sur **terminé**.
    
8. Sur la page de connexion, tapez le mot de passe pour le compte de l’utilisateur 2, puis cliquez sur **se connecter**.
    
9. Saisissez le code de vérification dans le message reçu sur votre téléphone intelligent, puis cliquez sur **se connecter**.
    
10. Si c’est la première fois vous connecté avec le compte de l’utilisateur 2, vous êtes invité à modifier le mot de passe. Tapez le mot de passe d’origine et un nouveau mot de passe deux fois, puis cliquez sur **mettre à jour le mot de passe et connectez-vous**. Enregistrer le nouveau mot de passe dans un endroit sûr.
    
    Vous devriez voir le portail Office 365 pour l’utilisateur 2.
    
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)

[Plan d’authentification à plusieurs facteurs pour les déploiements d’Office 365](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

