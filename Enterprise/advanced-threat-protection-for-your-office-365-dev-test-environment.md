---
title: Protection avancée contre les menaces pour votre environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 'Résumé : Configurez et faites une démonstration de la protection avancée contre les menaces Office 365 dans votre environnement de développement/test Office 365.'
ms.openlocfilehash: 07411600db11c8eea825c0ef5b82ea1206d20e11
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914959"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Protection avancée contre les menaces pour votre environnement de développement/test Office 365

 **Résumé :** Configurez et faites une démonstration de la protection avancée contre les menaces Office 365 dans votre environnement de développement/test Office 365.
  
Office 365 Advanced Threat Protection (DAV) est une fonctionnalité d’Exchange Online Protection (EOP) qui permet de conserver des programmes malveillants en dehors de votre courrier électronique. Avec DAV, vous créez des stratégies dans le centre d’administration Exchange (EAC) ou de la sécurité &amp; centre de conformité qui permettent de ne garantir que les liens ou les pièces jointes dans les messages électroniques qui sont identifiés comme malveillants pas accèdent à vos utilisateurs. Pour plus d’informations, voir [protection contre les menaces avancées pour les pièces jointes fiables et les liens sécurisés](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).
  
Les instructions fournies dans cet article indiquent comment configurer et tester la protection avancée contre les menaces dans votre abonnement d’évaluation Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée

Si vous souhaitez uniquement tester DAV dans une solution légère avec la configuration minimale requise, suivez les instructions en phases 2 et 3 de [l’environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester DAV dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Le test de la protection avancée contre les menaces ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester la protection avancée contre les menaces et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>Phase 2 : Illustrer le comportement de remise du courrier électronique par défaut d’Office 365

Dans cette phase, vous démontrez qu’avant de configurer les stratégies de protection avancée contre les menaces, l’e-mail potentiellement malveillant est remis aux boîtes aux lettres Office 365 sans filtrage ni atténuation.
  
1. Ouvrez Internet Explorer et connectez-vous au compte Outlook que vous avez créé dans la Phase 2 de [l’environnement de développement/test Office 365](office-365-dev-test-environment.md).
    
  - Si vous utilisez l’environnement de développement/test Office 365 léger, ouvrez une session privée d’Internet Explorer et connectez-vous sur votre ordinateur local.
    
  - Si vous utilisez l’environnement de développement/test Office 365 entreprise simulé, utilisez le [portail Azure](https://portal.azure.com) pour se connecter à l’ordinateur virtuel CLIENT1 et puis se connecter à partir de CLIENT1.
    
2. Ouvrez le Bloc-notes et saisissez du texte.
    
3. Enregistrez le fichier dans le dossier Documents sous le nom **getKeys.js**.
    
4. Dans l’onglet Courrier Outlook d’Internet Explorer, cliquez sur **Nouveau**.
    
5. Dans **À**, tapez l’adresse e-mail du nom de l’administrateur général Office 365 de votre abonnement d’évaluation.
    
6. Dans l’objet, tapez **Vos nouvelles clés**.
    
7. Dans le corps, tapez **Voici le fichier**.
    
8. Cliquez sur **Joindre**, double-cliquez sur **getKeys.js** dans le dossier Documents, cliquez sur **Joindre une copie**, puis cliquez sur **Envoyer**.
    
9. Cliquez sur **Nouveau**.
    
10. Dans **À**, tapez l’adresse e-mail du nom de l’administrateur général Office 365 de votre abonnement d’évaluation.
    
11. Dans l’objet, tapez **Nouveau site web de voyage**.
    
12. Dans le corps, tapez **Quelqu'un m’a transmis ce site**.
    
13. Dans le corps, sélectionnez le texte **ce site** et cliquez sur l’icône de lien hypertexte dans la barre d’outils.
    
14. Dans l' **URL**, tapez **http://www.spamlink.contoso.com/**, cliquez sur **OK**, puis cliquez sur **Envoyer**.
    
15. Ouvrez une instance distincte de Internet Explorer en mode de navigation privée, accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et se connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
16. Dans la page principale du portail, cliquez sur la vignette d’applications, puis cliquez sur **Courrier**.
    
17. Dans la boîte de réception, cliquez sur le message ayant pour objet **Vos nouvelles clés**.
    
18. Dans le dossier courrier indésirable, cliquez sur le message avec l’objet du **Nouveau site web en déplacement**. Dans le message, cliquez sur le lien de **ce site** . Vous devez voir une « Oops ! Page d’Internet Explorer n’a pas pu trouver spamlink.contoso.com. ». Il s’agit du résultat correct, car il n’existe aucune page web à cet emplacement.
    
Vous remarquez que ces deux e-mails potentiellement malveillants ont été remis correctement. L’e-mail **Vos nouvelles clés** pouvait contenir un programme malveillant non détecté et l’utilisateur a été autorisé à cliquer sur le lien potentiellement malveillant dans l’e-mail **Nouveau site web de voyage**.
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>Phase 3 : Configuration de stratégies de liens fiables et de pièce jointe fiable pour la protection avancée contre les menaces

Dans cette phase, vous créez et configurez une stratégie de pièce jointe fiable pour empêcher les e-mails contenant des pièces jointes potentiellement malveillantes d’être remises et une stratégie de liens fiables pour empêcher les utilisateurs de se diriger vers des URL potentiellement dangereuses.
  
1. Sous l’onglet **Accueil Microsoft Office** d’Internet Explorer, cliquez sur la vignette de **l’administrateur** .
    
2. Dans le volet de navigation gauche, cliquez sur **Centres d’administration**, puis sur **Exchange**.
    
3. Dans le volet de navigation gauche de l’onglet Centre d’administration Exchange, cliquez sur **Menaces avancées**.
    
4. Cliquez sur l’onglet **Pièces jointes approuvées**, puis sur le signe plus.
    
5. Dans la fenêtre de la **nouvelle stratégie de pièces jointes fiables** , dans **nom**, tapez **Stratégie de pièce jointe sécurisé - bloc**.
    
6. **Réponse de programmes malveillants inconnu fiables de pièces jointes**, cliquez sur **Bloquer**.
    
7. Pour **Rediriger la pièce jointe en cas de détection**, cliquez sur **Activer la redirection** et tapez l’adresse e-mail de votre compte d’administrateur général Office 365.
    
8. Pour **s’applique à**, cliquez sur la flèche vers le bas, puis cliquez sur **le domaine du destinataire est**. Dans la fenêtre, cliquez sur le nom de votre organisation (par exemple, contoso.onmicrosoft.com), puis cliquez sur **OK**.
    
9. Cliquez sur **Enregistrer**. Après la mise à jour, vous devez afficher le nouveau et activé la **Stratégie de pièce jointe sans échec - bloc**.
    
10. Cliquez sur l’onglet **Liens approuvés**, puis sur le signe plus.
    
11. Dans la fenêtre **Nouvelle stratégie de liens approuvés**, dans **Nom**, tapez **Stratégie de liens approuvés**.
    
12. Pour **Sélectionnez l’action à appliquer pour les URL potentiellement malveillantes contenues dans les messages**, cliquez sur **Activée**, puis sélectionnez **Ne pas autoriser les utilisateurs à cliquer vers l’URL d’origine**.
    
13. Pour **s’applique à**, cliquez sur la flèche vers le bas, puis cliquez sur **le domaine du destinataire est**. Dans la fenêtre, cliquez sur le nom de votre organisation (par exemple, contoso.onmicrosoft.com), puis cliquez sur **OK**.
    
14. Cliquez sur **Enregistrer**. La **nouvelle stratégie de liens** activée s’affiche.
    
## <a name="phase-4-show-atp-in-action"></a>Phase 4 : Service Protection avancée contre les menaces en action

Dans cette phase, vous montrez comment le Service Protection avancée contre les menaces en action traite les e-mails potentiellement malveillants.
  
1. À partir de l’instance d’Internet Explorer que vous avez utilisé pour envoyer le courrier électronique à la Phase 2, dans le volet de navigation gauche, cliquez sur **éléments envoyés.**
    
2. Cliquez sur le courrier électronique intitulé **vos nouvelles clés**, cliquez sur la flèche vers le bas, puis cliquez sur **Transférer**.
    
3. Pour le nouveau message, dans **À**, tapez l’adresse e-mail du nom de l’administrateur général Office 365 de votre abonnement d’évaluation, puis cliquez sur **Envoyer**.
    
4. Cliquez sur le courrier électronique intitulé **New se déplacent le site web**, cliquez sur la flèche vers le bas, cliquez sur **répondre à tous**, puis cliquez sur **Envoyer**.
    
5. À partir de l’instance d’Internet Explorer que vous avez utilisée pour configurer les stratégies du Service Protection avancée contre les menaces à la phase 3, cliquez sur l’onglet Centre d’administration Exchange, cliquez sur la vignette d’applications, puis cliquez sur **Courrier**. Deux nouveaux e-mails apparaissent dans la boîte de réception :
    
  - Un e-mail intitulé **Fw : Vos nouvelles clés**
    
  - Un e-mail intitulé **Fw : Nouveau site web de voyage**
    
6. Ouvrez le message électronique intitulé **TR : nouveau site web de déplacements** et cliquez sur le lien de **ce site** . Vous devez voir une page « ce site Web a été classé comme malveillants. ». Cela montre que DAV vous empêche d’accéder au site web malveillant.
    
7. Dans l’onglet Centre d’administration Exchange d’Internet Explorer, dans le volet de navigation gauche, cliquez sur **Flux de messagerie**.
    
8. Cliquez sur l’onglet **Suivi des messages**, puis sur **Rechercher**.
    
9. Dans la fenêtre de **Résultats de suivi des messages** , double-cliquez sur le message avec l’objet **vos nouvelles clés**. Ce message a bien été remis à la boîte de réception. Fermez cette fenêtre.
    
10. Double-cliquez sur le message avec l’objet du **Nouveau site web en déplacement**. Ce message a bien été remis à la boîte de réception. Fermez cette fenêtre.
    
11. Double-cliquez sur le message avec l’objet **TR : vos nouvelles clés**. Notez comment ce message a été traité par DAV et puis remis à la boîte de réception. Fermez cette fenêtre.
    
    > [!NOTE]
    > L’objectif de la stratégie de pièces jointes sûres était de commencer l’analyse des pièces jointes pour le code malveillant. La pièce jointe getKeys.js a été autorisée, car il n’a pas été déterminée malveillants. Cette étape indique que DAV effectuer une analyse de la pièce jointe. 
  
12. Double-cliquez sur le message avec l’objet **TR : nouveau site web de déplacements**. Notez que ce message a bien été remis à la boîte de réception.
    
Vous pouvez désormais utiliser cet environnement pour créer des stratégies et expérimenter le Service Protection avancée contre les menaces.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Sécurité des applications cloud pour votre environnement de développement/test Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md) 

[Protection avancée contre les menaces pour les pièces jointes et liens fiables](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


