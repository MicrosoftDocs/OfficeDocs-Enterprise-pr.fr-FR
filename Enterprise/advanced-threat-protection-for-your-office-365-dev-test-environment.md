---
title: "Protection avancée contre les menaces pour votre environnement de développement/test Office 365"
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "Résumé : Configurer et illustrer l’Office 365 Advanced Threat Protection dans votre environnement de développement/test d’Office 365."
ms.openlocfilehash: 2715e2722ab2826d4a4e05db0f9bd4cd9035fb98
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Protection avancée contre les menaces pour votre environnement de développement/test Office 365

 **Résumé :** Configurer et illustrer l’Office 365 Advanced Threat Protection dans votre environnement de développement/test d’Office 365.
  
Office 365 Advanced Threat Protection (ATP) est une fonctionnalité d’Exchange Online Protection (EOP) qui vous aide à garder les logiciels malveillants de votre message électronique. Avec DAV, vous créez des stratégies dans le centre d’administration Exchange (FAC) ou de la sécurité &amp; centre de conformité qui permettent de garantir à vos utilisateurs accèdent uniquement des liens ou des pièces jointes dans les e-mails qui sont identifiés comme non malveillantes. Pour plus d’informations, consultez [protection contre les menaces avancées des liens sécurisés et les pièces jointes sûres](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).
  
Les instructions fournies dans cet article indiquent comment configurer et tester la protection avancée contre les menaces dans votre abonnement d’évaluation Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée

Si vous souhaitez juste tester ATP dans une solution légère avec la configuration minimale requise, suivez les instructions dans les étapes 2 et 3 de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester l’ATP dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Le test de la protection avancée contre les menaces ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester la protection avancée contre les menaces et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>Phase 2 : Montrer le comportement de livraison de courrier électronique par défaut d’Office 365

Dans cette phase, vous démontrez qu’avant de configurer les stratégies de protection avancée contre les menaces, l’e-mail potentiellement malveillant est remis aux boîtes aux lettres Office 365 sans filtrage ni atténuation.
  
1. Ouvrez Internet Explorer et vous connecter sur le compte de Outlook que vous avez créé à la Phase 2 de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
    
  - Si vous utilisez l’environnement de développement/test Office 365 léger, ouvrez une session privée d’Internet Explorer et connectez-vous sur votre ordinateur local.
    
  - Si vous utilisez l’environnement de développement/test Office 365 entreprise simulée, utiliser le [portail Azure](https://portal.azure.com) de se connecter à la machine virtuelle de CLIENT1, puis connectez-vous à partir de CLIENT1.
    
2. Ouvrez le Bloc-notes et saisissez du texte.
    
3. Enregistrez le fichier dans le dossier Documents sous la forme **getKeys.js**.
    
4. Sous l’onglet messagerie Outlook de Microsoft Internet Explorer, cliquez sur **Nouveau**.
    
5. Dans la zone **à**, tapez l’adresse de messagerie du nom global administrateur Office 365 de votre abonnement d’évaluation.
    
6. Pour l’objet, tapez **vos nouvelles clés**.
    
7. Dans le corps, tapez **Voici le fichier**.
    
8. Cliquez sur **joindre**, double-cliquez sur **getKeys.js** dans le dossier Documents, cliquez sur **attacher en tant que copie**, puis cliquez sur **Envoyer**.
    
9. Cliquez sur **Nouveau**.
    
10. Dans la zone **à**, tapez l’adresse de messagerie du nom global administrateur Office 365 de votre abonnement d’évaluation.
    
11. Pour l’objet, tapez **Nouveau voyage de site web**.
    
12. Dans le corps, tapez **que quelqu'un m’a transmis ce site**.
    
13. Dans le corps, sélectionnez le texte de **ce site** , puis cliquez sur l’icône de lien hypertexte dans la barre d’outils.
    
14. Dans l' **URL**, tapez **http://www.spamlink.contoso.com/**et cliquez sur **OK**puis cliquez sur **Envoyer**.
    
15. Ouvrez une instance distincte d’Internet Explorer en mode de navigation privé, accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et vous connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
16. À partir de la page principale du portail, cliquez sur la mosaïque d’applications, puis cliquez sur **courrier**.
    
17. Dans la boîte de réception, cliquez sur le message dont l’objet **vos nouvelles clés**.
    
18. Dans le dossier courrier indésirable, cliquez sur le message dont l’objet est **Nouveau voyage de site web**. Dans le message, cliquez sur le lien de **ce site** . Vous devriez voir un « Oops ! Page d’Internet Explorer n’a pas pu trouver spamlink.contoso.com. ». Voici le résultat correct, car il n’existe aucune page web à cet emplacement.
    
Notez que deux de ces e-mails potentiellement malveillants ont été remis avec succès. L’e-mail de **vos nouvelles clés** peut contenir des logiciels malveillants non détectés et l’utilisateur a été autorisé à cliquer sur le lien nuisible dans le message de **Nouveau site web de voyage** .
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>Phase 3 : Configuration de stratégies de liens fiables et de pièce jointe fiable pour la protection avancée contre les menaces

Dans cette phase, vous créez et configurez une stratégie de pièce jointe fiable pour empêcher les e-mails contenant des pièces jointes potentiellement malveillantes d’être remises et une stratégie de liens fiables pour empêcher les utilisateurs de se diriger vers des URL potentiellement dangereuses.
  
1. Sous l’onglet **Accueil de Microsoft Office** , de Microsoft Internet Explorer, cliquez sur la mosaïque de **l’Admin** .
    
2. Dans la navigation de gauche, cliquez sur **Centre d’administration**, puis sur **Exchange**.
    
3. Dans la navigation de gauche de l’onglet de centre d’administration Exchange, cliquez sur **les menaces avancées**.
    
4. Cliquez sur l’onglet **pièces jointes sûres** , puis cliquez sur le signe plus.
    
5. Dans la fenêtre de la **nouvelle stratégie de pièces jointes sûres** , dans la zone **nom**, tapez **Stratégie de pièce jointe sans échec - bloc**.
    
6. **Réponse inconnue contre les logiciels malveillants de pièces jointes sûres**, cliquez sur **Bloquer**.
    
7. Pour **Rediriger la pièce jointe sur la détection**, cliquez sur **Activer la redirection** et tapez l’adresse e-mail de votre compte d’administrateur global Office 365.
    
8. Pour **appliqué à**, cliquez sur la flèche vers le bas, puis cliquez sur **le domaine du destinataire est**. Dans la fenêtre, cliquez sur le nom de votre organisation (par exemple, contoso.onmicrosoft.com), puis cliquez sur **OK**.
    
9. Cliquez sur **Enregistrer**. Après la mise à jour, vous devez afficher le nouveau et activé la **Stratégie de pièce jointe sans échec - bloc**.
    
10. Cliquez sur l’onglet **liens sans échec** , puis cliquez sur le signe plus.
    
11. Dans la fenêtre de la **nouvelle stratégie de liens sécurisés** , dans la zone **nom**, tapez **Stratégie de lien sécurisé**.
    
12. **Sélectionnez l’action pour les URL potentiellement malveillants inconnus dans les messages**, cliquez **sur**et sélectionnez **ne pas autoriser les utilisateurs à l’URL d’origine**.
    
13. Pour **appliqué à**, cliquez sur la flèche vers le bas, puis cliquez sur **le domaine du destinataire est**. Dans la fenêtre, cliquez sur le nom de votre organisation (par exemple, contoso.onmicrosoft.com), puis cliquez sur **OK**.
    
14. Cliquez sur **Enregistrer**. Vous devriez voir le nouveau et activé la **Stratégie de liaison sécurisée**.
    
## <a name="phase-4-show-atp-in-action"></a>Phase 4 : Service Protection avancée contre les menaces en action

Dans cette phase, vous montrez comment le Service Protection avancée contre les menaces en action traite les e-mails potentiellement malveillants.
  
1. À partir de l’instance de Internet Explorer que vous avez utilisé pour envoyer l’e-mail à la Phase 2, de la navigation de gauche, cliquez sur **éléments envoyés.**
    
2. Cliquez sur le message intitulé **vos nouvelles clés**, cliquez sur la flèche vers le bas, puis cliquez sur **suivant**.
    
3. Pour le nouveau message, dans la zone **à**, tapez l’adresse e-mail du nom global administrateur Office 365 de votre abonnement d’évaluation, puis cliquez sur **Envoyer**.
    
4. Cliquez sur le message intitulé du **Nouveau site web de voyage**, cliquez sur la flèche vers le bas, cliquez sur **répondre à tous**, puis cliquez sur **Envoyer**.
    
5. À partir de l’instance de Internet Explorer qui vous permet de configurer les stratégies d’ATP dans la Phase 3, cliquez sur l’onglet de centre d’administration Exchange, cliquez sur la mosaïque d’applications, puis cliquez sur **courrier**. Vous devriez voir deux nouveaux messages dans la boîte de réception :
    
  - Un intitulé **Fw : vos nouvelles clés**
    
  - Un intitulé **Fw : nouveau site web de déplacement**
    
6. Ouvrez le message électronique intitulé **Fw : nouveau voyage web site** et cliquez sur le lien de **ce site** . Vous devriez voir une page « ce site Web a été classé comme malveillants. ». Cela montre que DAV vous empêche d’accéder au site web potentiellement malveillant.
    
7. Dans l’onglet Exchange admin center de Microsoft Internet Explorer, la navigation de gauche, cliquez sur **le flux de messagerie**.
    
8. Cliquez sur l’onglet **suivi du message** , puis cliquez sur **Rechercher**.
    
9. Dans la fenêtre de **Résultats de suivi de messages** , double-cliquez sur le message dont l’objet **vos nouvelles clés**. Ce message a été remis à la boîte de réception. Fermez cette fenêtre.
    
10. Double-cliquez sur le message dont l’objet est **Nouveau voyage de site web**. Ce message a été remis à la boîte de réception. Fermez cette fenêtre.
    
11. Double-cliquez sur le message avec l’objet **Fw : vos nouvelles clés**. Notez comment ce message a été traité par l’ATP et ensuite remis à la boîte de réception. Fermez cette fenêtre.
    
    > [!NOTE]
    > L’objectif de la stratégie de sécurité de pièces jointes a été de commencer l’analyse des pièces jointes pour le code malveillant. La pièce jointe getKeys.js a été autorisée car il n’a pas été déterminée comme étant malveillants. Cette étape indique que DAV n’a effectué une analyse de la pièce jointe. 
  
12. Double-cliquez sur le message avec l’objet **Fw : nouveau site web de voyage**. Notez que ce message a été remis à la boîte de réception.
    
Vous pouvez désormais utiliser cet environnement pour créer des stratégies et expérimenter le Service Protection avancée contre les menaces.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Application du nuage sécurité pour votre environnement de développement/test d’Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md) 

[Protection contre les menaces avancées des liens sécurisés et les pièces jointes sûres](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


