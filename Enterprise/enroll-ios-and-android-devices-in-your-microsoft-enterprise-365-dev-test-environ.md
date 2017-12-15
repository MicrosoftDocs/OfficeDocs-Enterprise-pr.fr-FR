---
title: "Inscrire les périphériques iOS ou Android dans votre environnement de développement/test Microsoft Enterprise 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Résumé : Utilisez ce Guide de laboratoire de Test pour inscrire des périphériques de votre environnement de développement/test Microsoft 365 et de les gérer à distance."
ms.openlocfilehash: 8ad22ed62d8e7cac8aca225af42e389dc05cb2b5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>Inscrire les périphériques iOS ou Android dans votre environnement de développement/test Microsoft Enterprise 365

 **Résumé :** Ce Guide de laboratoire de Test permet d’inscrire des périphériques de votre environnement de développement/test Microsoft 365 et de les gérer à distance.
  
La Suite de mobilité entreprise (EMS) de Microsoft permet à votre personnel gagne en productivité tout en protégeant les données de votre organisation à l’aide de leurs applications favorites et leurs périphériques. Pour plus d’informations, reportez-vous à la section [mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Si vous avez besoin d’appliquer la sécurité au niveau de l’appareil, vous devez inscrire vos appareils auprès de Microsoft Intune. L’inscription d’appareil vous permet non seulement de gérer les périphériques appartenant à l’entreprise, mais également les périphériques personnels (BYOD) et partagés, en fonction des stratégies juridiques de votre organisation.
  
En suivant les instructions fournies dans cet article, vous serez en mesure de s’inscrire et à tester les fonctions de gestion de base des périphériques mobiles pour les périphériques iOS ou Android dans votre environnement de développement/test Microsoft 365.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Microsoft 365

Suivez les instructions dans [l’environnement de développement/test de l’entreprise de 365 de Microsoft](the-microsoft-365-enterprise-dev-test-environment.md).
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a>Phase 2 : Personnalisation de l’application de portail d’entreprise Microsoft Intune

Utilisez ces étapes pour personnaliser l’application de portail d’entreprise Microsoft Intune pour votre société fictive :
  
1. Dans un nouvel onglet, ouvrez la console d’administration Microsoft Intune ([https://manage.microsoft.com](https://manage.microsoft.com)).
    
2. Cliquez sur **Admin** dans le volet de navigation, puis cliquez sur **Gestion des périphériques mobiles** dans le volet de **l’Administration** .
    
3. Dans la liste des **tâches** , sélectionnez **l’Autorité de gestion de périphérique Mobile défini**. Assurez-vous qu’elle est définie sur **Microsoft Intune**.
    
4. Dans le volet **d’Administration** , cliquez sur **Portail d’entreprise**.
    
5. Dans le volet de **Portail d’entreprise** , configurez les paramètres suivants :
    
  - Nom de la société : \<nom de votre société fictive >
    
  - Nom de contact de département informatique : **User5**
    
  - Numéro de téléphone du service informatique : **555-1234**
    
  - Adresse de messagerie du service informatique : **User5 @**\<nom de l’organisation fictive > **. onmicrosoft.com** (l’adresse de messagerie du compte User5)
    
6. Dans une **personnalisation**, sélectionnez **vert** dans la **couleur de thème**.
    
7. Cliquez sur **Enregistrer**.
    
Ensuite, vous installez l’application de portail d’entreprise Microsoft Intune et inscrivez un appareil iOS ou Android, puis testez les fonctionnalités de gestion de base à partir de la console d’administration Microsoft Intune.
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a>Phase 3 (pour les appareils iOS uniquement) : Inscription et gestion d’un appareil iOS

Pour inscrire un appareil iOS à gérer avec Intune, vous avez besoin des éléments suivants :
  
- Un appareil iOS, comme un iPad ou iPhone.
    
- Connaissance du mot de passe du périphérique iOS.
    
- Un ID de Apple (un nom de compte et le mot de passe). Si vous n’en avez pas encore, rendez-vous sur le [site Web de Apple ID](https://appleid.apple.com/#!&amp;page=signin) et cliquez sur **créer votre ID d’Apple**. Créer un ID d’Apple correspondant au compte d’administrateur global de votre abonnement à Office 365. Enregistrer votre nouveau nom de compte Apple ID et le mot de passe dans un endroit sûr.
    
Un certificat de services de notifications push Apple (APN) est nécessaire pour qu’Intune puisse gérer les appareils iOS et Mac. Une fois le certificat ajouté à Intune, les utilisateurs peuvent installer l’application de portail d’entreprise Microsoft Intune pour inscrire leurs appareils, ou l’administrateur peut configurer la gestion des appareils iOS appartenant à l’entreprise.
  
Vous avez besoin d’un fichier de demande de signature de certificat pour demander un certificat de relation de confiance à partir du portail de certificats Push Apple. Pour obtenir un fichier de requête de signature de certificat, procédez comme suit :
  
1. Dans la console d’administration Microsoft Intune, cliquez sur **Admin** dans le volet de navigation.
    
    Dans le volet **d’Administration** , ouvrez **Gestion des périphériques mobiles > iOS et Mac OS X**, puis cliquez sur **télécharger un certificat de APNs** dans les **tâches**. 
    
2. Dans le volet de **télécharger un certificat de APNs** , cliquez sur **Télécharger la demande de certificat APNs**. Enregistrez le certificat de signature d’un fichier de demande (.csr) localement avec le nom **test-dev**.
    
Pour obtenir un certificat de service de notifications Push Apple, procédez comme suit :
  
1. Ouvrir un nouvel onglet, accédez au [Portail de certificats Apple Push](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)et connectez-vous avec votre ID d’Apple.
    
2. Dans la page **Mise en route** , cliquez sur **créer un certificat**.
    
3. Dans la page **Conditions d’utilisation** , sélectionnez **J’ai lu et accepte les conditions d’utilisation**, puis cliquez sur **Accepter**.
    
4. Sur la page **créer un nouveau certificat de Push** , cliquez sur **Parcourir** et sélectionnez le fichier **test.csr-dev** enregistré dans la procédure précédente, puis cliquez sur **Télécharger**. Lorsque vous êtes invité à ouvrir un fichier json, enregistrez-le dans le même dossier que celui où se trouve le fichier test.csr-dev.
    
5. Ouvrez le [Portail de certificats Apple Push](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) dans un autre onglet et des **certificats de serveurs tiers**, cliquez sur **Télécharger**.
    
6. Lorsque vous êtes invité à ouvrir un fichier .pem, l’enregistrer sous le nom **dev-test.pem** dans le même dossier que celui où se trouve le fichier test.csr-dev. Il s’agit de votre certificat d’APNs.
    
Pour charger le certificat APNs dans Intune, procédez comme suit :
  
1. Sous l’onglet de la console d’administration de Microsoft Intune, sur la page **télécharger un certificat de APNs** , cliquez sur **Télécharger le certificat APNs**.
    
2. Cliquez sur **Parcourir** et indiquez le fichier **dev-test.pem** .
    
3. Cliquez sur **Ouvrir**, tapez le nom de votre compte Apple ID, puis cliquez sur **Télécharger**. Vous devez voir un message **prêt pour l’inscription** sur la page **iOS et les paramètres de gestion de périphérique MaxOS X Mobile** .
    
Avec le certificat APNs installé, Intune peut désormais inscrire et gérer des appareils iOS en plaçant la stratégie sur les appareils mobiles inscrits.
  
Pour télécharger l’application de portail d’entreprise Microsoft Intune et inscrire l’appareil iOS, procédez comme suit :
  
1. À partir de votre appareil iOS, connectez-vous avec votre identifiant Apple.
    
2. Ouvrez l’app **Store d’Apple** .
    
3. Tapez **intune** dans la zone Rechercher, puis cliquez sur **Portail d’entreprise Microsoft Intune**, puis **obtenir**et **installer**.
    
4. Après l’installation, cliquez sur **Ouvrir**.
    
5. Sur l’écran **Intune Entreprise Portal** , connectez-vous à votre compte d’administrateur global de Office 365.
    
6. Dans l’écran **Paramètres de société d’accès** , cliquez sur **commencer**et puis cliquez sur **Continuer** .
    
7. Sur le **ce qui vient ensuite ?** de l’écran, cliquez sur **inscrire**.
    
8. Sur le **administrateur de périphérique Activate ?** de l’écran, cliquez sur **Activer**.
    
9. Dans l’écran **Profil de gestion** , cliquez sur **installer**.
    
10. Dans **Entrez le mot de passe**, tapez votre mot de passe de périphérique iOS.
    
11. Dans l’écran **ce qui vient ensuite** , cliquez sur **inscrire**.
    
12. **Installer un profil**, cliquez sur **installer**.
    
13. Dans la page **Avertissement** , cliquez sur **installer**.
    
14. **Gestion à distance**, cliquez sur **Approuver**.
    
15. Cliquez sur **terminé** pour terminer le processus d’inscription.
    
16. Lorsque vous êtes invité à **Ouvrir cette page dans « Portail Comp » ?**, cliquez sur **Ouvrir**.
    
17. Dans l’écran **Paramètres de société d’accès** , cliquez sur **commencer**et appuyez sur **terminé**.
    
18. Dans l’écran principal de l’application de portail d’entreprise Microsoft Intune, vous devez voir :
    
  - Une bannière verte.
    
  - Le nom de votre société fictive dans le coin supérieur gauche.
    
  - Le nom du périphérique iOS répertorié dans **Mes périphériques**.
    
  - Dans la section de **support technique** , le **Nom du Contact** **User5** avec le numéro de téléphone **555-1234** et un bouton de **Contact par courrier électronique** .
    
Microsoft Intune fournit des fonctionnalités de verrouillage à distance et de réinitialisation du code secret. Si une personne perd son appareil, vous pouvez le verrouiller à distance. Si quelqu’un oublie son code secret, vous pouvez le supprimer à distance.
  
Pour verrouiller un appareil iOS à distance, procédez comme suit :
  
1. À partir de votre ordinateur d’administration, sur l’onglet de console d’administration Microsoft Intune de votre navigateur, cliquez sur **groupes** dans la navigation de gauche.
    
2. Dans le volet **groupes** , ouvrez **tous les périphériques > appareils mobiles tous les > tous les périphériques gérés directement**.
    
3. Dans le volet **Tous les périphériques gérés Direct** , cliquez sur l’onglet **périphériques** .
    
4. Dans la liste des périphériques, cliquez sur votre appareil iOS.  
    
5. À partir de votre appareil iOS, assurez-vous qu’il se trouve sur l’écran principal.  
    
6. À partir de votre ordinateur d’administration, sur la barre des tâches, cliquez sur **des tâches à distance > verrouillage à distance**. Observez votre périphérique iOS qu’il passe à l’écran de verrouillage.
    
Pour supprimer le code secret, procédez comme suit :
  
1. À partir de votre ordinateur d’administration, dans le volet **Tous les périphériques gérés Direct** , cliquez sur l’onglet **périphériques** .
    
2. Dans la liste, cliquez sur votre périphérique iOS. Dans la barre des tâches, cliquez sur **des tâches à distance > réinitialisation de mot de passe**. Attendez une minute.
    
3. À partir de votre périphérique iOS, déverrouiller et notez qu’il n’est plus un mot de passe. Pour modifier le code secret de nouveau, allez dans **paramètres**, puis sur **mot de passe**.
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a>Phase 3 (pour les appareils Android uniquement) : Inscription et gestion d’un appareil Android

Vous avez besoin des éléments suivants pour inscrire un appareil Android à gérer avec Intune :
  
- Un appareil Android.
    
- Connaissance du mot de passe du périphérique.
    
Pour télécharger l’application de portail d’entreprise Intune et inscrire l’appareil Android, procédez comme suit :
  
1. À partir de votre appareil Android, accédez à la **Banque de lecture de Google**et puis cliquez sur **Mise en route**.
    
2. Tapez **intune** dans la zone Rechercher et appuyez sur le **portail d’entreprise intune** dans les résultats de recherche.
    
3. Cliquez sur l’élément **Intune Entreprise Portal** , puis **installer**.
    
4. Sur l’écran **pour terminer l’installation compte** , cliquez sur **Continuer**, puis sur **Ignorer**.
    
5. Dans le **Portail d’entreprise Intune**, cliquez sur **Accepter**. L’installation de l’application.
    
6. Cliquez sur **Ouvrir**, puis **reconnectez-vous**.
    
7. Sur l’écran **Intune Entreprise Portal** , connectez-vous à votre compte d’administrateur global de Office 365.
    
8. Dans l’écran **Paramètres de société d’accès** , cliquer deux fois **commencer**, puis sur **Continuer** .
    
9. Sur le **ce qui vient ensuite ?** de l’écran, cliquez sur **inscrire**.
    
10. Sur le **administrateur de périphérique Activate ?** de l’écran, cliquez sur **Activer.**
    
11. Sur l’écran de la **Politique de confidentialité** , sélectionnez **J’accepte** et puis cliquez sur **Confirmer**. Attendez la fin du processus d’inscription.
    
12. Dans l’écran **Paramètres de société d’accès** , cliquez sur **Continuer**et appuyez sur **terminé**.
    
13. Dans l’écran principal de l’application de portail d’entreprise Microsoft Intune, vous devriez voir une bannière verte et le nom de votre société fictive dans le coin supérieur gauche.
    
14. Cliquez sur **Mes périphériques**. Vous devez voir votre nom appareil Android dans la liste.
    
15. Cliquez sur **Contact informatique**. Vous devez voir le numéro de téléphone de **555-1234**, un bouton **contacter par e-mail** , et contact de l’informatique de **User5**.
    
Microsoft Intune fournit des fonctionnalités de verrouillage à distance et de réinitialisation du code secret. Si une personne perd son appareil, vous pouvez le verrouiller à distance. Si quelqu’un oublie son code secret, vous pouvez le réinitialiser à distance.
  
Pour verrouiller un appareil Android à distance, procédez comme suit :
  
1. À partir de votre ordinateur d’administration, sur l’onglet de console d’administration Microsoft Intune de votre navigateur, cliquez sur **groupes** dans la navigation de gauche.
    
2. Dans le volet **groupes** , ouvrez **tous les périphériques > appareils mobiles tous les > tous les périphériques gérés directement**.
    
3. Dans le volet **Tous les périphériques gérés Direct** , cliquez sur l’onglet **périphériques** .
    
4. Dans la liste des périphériques, cliquez sur votre appareil Android.  
    
5. À partir de votre appareil Android, assurez-vous qu’il se trouve sur l’écran principal.  
    
6. À partir de votre ordinateur d’administration, sur la barre des tâches, cliquez sur **des tâches à distance > verrouillage à distance**. Lorsque vous y êtes invité, cliquez sur **Oui**.
    
7. Regardez votre appareil Android lorsqu’il bascule vers l’écran de verrouillage.
    
Lorsque vous réinitialisez le mot de passe pour des appareils Android, le portail d’administration Intune génère et configure un mot de passe fort.
  
Pour réinitialiser le code secret à distance, procédez comme suit :
  
1. À partir de votre ordinateur d’administration, sur l’onglet de console d’administration Microsoft Intune de votre navigateur, dans le volet **Tous les périphériques gérés Direct** , cliquez sur votre appareil Android.
    
2. Dans la barre des tâches, cliquez sur **des tâches à distance > réinitialisation de mot de passe**.
    
3. Sur le **tâche à distance : réinitialisation du mot de passe** invite, cliquez sur **Oui**. Attendez une minute.
    
4. Dans le volet **Tous les périphériques gérés Direct** , cliquez sur **Afficher les propriétés**.
    
5. Sous **Réinitialisation de mot de passe**, notez le code secret de nouveau.
    
6. Dans votre appareil Android, entrez le nouveau code secret à partir de l’écran de verrouillage.  
    
7. Pour modifier le code précédent, dans **paramètres**, cliquez sur le **périphérique**, cliquez sur **écran de verrouillage**, entrez le nouveau code à nouveau, cliquez sur **verrouillage de l’écran**et votre choix pour le mot de passe.
    
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.
  
## <a name="see-also"></a>See Also

[L’environnement de développement/test Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Stratégies MAM pour votre environnement de développement/test Microsoft 365 Enterprise](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)

[Mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


