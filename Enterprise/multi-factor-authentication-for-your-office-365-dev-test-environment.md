---
title: Authentification multifacteur pour votre environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 'Résumé : Configurer l’authentification multifacteur à l’aide de messages texte envoyés à un Smartphone dans un environnement de développement/test Office 365.'
ms.openlocfilehash: 13dc02cc23d12f6eb6e2898d34271685badd9f5a
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573978"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Authentification multifacteur pour votre environnement de développement/test Office 365

 **Résumé :** Configurer l’authentification multifacteur à l’aide de messages texte envoyés à un Smartphone dans un environnement de développement/test Office 365.
  
Pour un niveau de sécurité supplémentaire pour la connexion à votre abonnement Office 365, vous pouvez activer l'authentification multifacteur Azure, qui nécessite plus qu'un nom d'utilisateur et un mot de passe pour authentifier un compte. Avec l’authentification multifacteur pour Office 365, les utilisateurs sont tenus de confirmer la bonne réception d’un appel téléphonique, de taper un code de vérification envoyé dans un message texte ou de spécifier un mot de passe d’application sur leur smartphone après avoir entré correctement leur mot de passe. Ils peuvent se connecter uniquement lorsque ce deuxième facteur d’authentification a été respecté. 
  
Cet article décrit comment activer et tester l’authentification basée sur message texte pour un compte Office 365 spécifique.
  
Il existe deux phases de configuration de l’authentification multifacteur pour Office 365 dans un environnement de développement/test :
  
1. Créez l’environnement de développement/test Office 365.
    
2. Activez et testez l’authentification multifacteur pour le compte d’utilisateur 2.
    
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée

Si vous souhaitez simplement tester l'authentification multifacteur de manière légère avec la configuration minimale requise, suivez les instructions des phases 2 et 3 de l' [environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester l'authentification multifacteur dans une entreprise simulée, suivez les instructions de [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Le test de l’authentification multifacteur ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester l’authentification multifacteur et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2

Activez l’authentification multifacteur pour le compte d’utilisateur 2 en procédant comme suit :
  
1. Ouvrez une instance distincte de votre navigateur, accédez au portail Office 365 ([https://www.office.com](https://www.office.com)), puis connectez-vous à votre abonnement d'évaluation Office 365 avec votre compte d'administrateur général.
    
2. Sur la page principale du portail, cliquez sur **Administrateur**.
    
3. Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
4. Dans le volet utilisateurs actifs, cliquez sur **plus d' > d'authentification multifacteur**.
    
5. Dans la liste, sélectionnez le compte **utilisateur 2** .
    
6. Dans la section **Utilisateur 2**, sous **Étapes rapides**, cliquez sur **Activer**.
    
7. Dans la boîte de dialogue **À propos de l’activation de l’authentification multifacteur**, cliquez sur **Activer Multi-Factor Authentication**.
    
8. Dans la boîte de dialogue **mises à jour réussies** , cliquez sur **Fermer**.
    
9. Dans l’onglet **Microsoft Office Famille**, cliquez sur l’icône du compte utilisateur en haut à droite, puis cliquez sur **Déconnexion**.
    
10. Fermez l’instance de navigateur.
    
Terminez la configuration pour que le compte d’utilisateur 2 utilise un message texte pour la validation et testez-le en procédant comme suit :
  
1. Ouvrez une nouvelle instance de votre navigateur.
    
2. Accédez au portail Office 365 ([https://www.office.com](https://www.office.com)) et connectez-vous avec le compte utilisateur 2 (utilisateur2 @\<Organization name>. onmicrosoft. com) et le mot de passe.
    
3. Après vous être connecté, vous êtes invité à configurer le compte pour la validation de sécurité supplémentaire. Cliquez sur **Configurer maintenant**.
    
4. Sur la page **Vérification de sécurité supplémentaire** : 
    
  - Sélectionnez le pays ou la région.
    
  - Tapez le numéro de téléphone du smartphone qui recevra les SMS.
    
  - dans **méthode**, cliquez sur **m'envoyer un code par message texte**.
    
5. Cliquez sur **Suivant**.
    
6. Entrez le code de vérification du SMS reçu sur votre smartphone, puis cliquez sur **Vérifier**.
    
7. Sur la page **Étape 3 : Conservez la page des applications existantes**, enregistrez le mot de passe de l’application affiché pour le compte d’utilisateur 2 dans un endroit sûr, puis cliquez sur **Terminé**.
    
8. Si c’est la première fois que vous vous connectez avec le compte d’utilisateur 2, vous êtes invité à modifier le mot de passe. Tapez le mot de passe d’origine et un nouveau mot de passe à deux reprises, puis cliquez sur **Mettre à jour le mot de passe et se connecter**. Enregistrez le nouveau mot de passe dans un endroit sûr.
    
    Vous devriez voir le portail Office 365 pour utilisateur 2 sur l'onglet **Accueil Microsoft Office** de votre navigateur.
    
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)

[Planifier l'authentification multifacteur pour les déploiements d'Office 365](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

