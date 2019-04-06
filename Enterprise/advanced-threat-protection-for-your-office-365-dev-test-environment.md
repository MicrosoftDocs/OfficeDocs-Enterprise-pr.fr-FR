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
ms.openlocfilehash: 4ef057480f0ebfb2e64529f39d0db65031b75010
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037938"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Protection avancée contre les menaces pour votre environnement de développement/test Office 365

 **Résumé :** Configurez et faites une démonstration de la protection avancée contre les menaces Office 365 dans votre environnement de développement/test Office 365.
  
La protection avancée contre les menaces Office 365 est une fonctionnalité d’Exchange Online Protection (EOP) qui vous permet de lutter contre les programmes malveillants dans votre environnement de messagerie. Avec la protection avancée contre les menaces, vous créez des stratégies dans le centre d'administration &amp; Exchange ou dans le centre de sécurité conformité afin de garantir que vos utilisateurs peuvent accéder uniquement aux liens ou aux pièces jointes dans les e-mails identifiés comme non malveillants. Pour plus d'informations, consultez la rubrique [Protection avancée contre les menaces pour les pièces jointes et liens fiables](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).
  
Les instructions fournies dans cet article indiquent comment configurer et tester la protection avancée contre les menaces dans votre abonnement d’évaluation Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée

Si vous souhaitez simplement tester la protection avancée contre les menaces de manière légère avec la configuration minimale requise, suivez les instructions des phases 2 et 3 de l' [environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester la protection avancée contre les menaces dans une entreprise simulée, suivez les instructions de [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Le test de l'ATP ne nécessite pas l'environnement de développement/test d'entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d'annuaires pour une forêt des services de domaine Active Directory (AD DS). Il est proposé comme option dans cet article afin que vous puissiez tester la protection avancée contre les menaces et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>Phase 2: montrer le comportement de remise par défaut des messages d'Office 365

Dans cette phase, vous démontrez qu’avant de configurer les stratégies de protection avancée contre les menaces, l’e-mail potentiellement malveillant est remis aux boîtes aux lettres Office 365 sans filtrage ni atténuation.
  
1. Ouvrez Internet Explorer et connectez-vous au compte Outlook que vous avez créé au cours de la phase 2 de l' [environnement de développement/test Office 365](office-365-dev-test-environment.md).
    
  - Si vous utilisez l’environnement de développement/test Office 365 léger, ouvrez une session privée d’Internet Explorer et connectez-vous sur votre ordinateur local.
    
  - Si vous utilisez l'environnement de développement/test Office 365 entreprise simulé, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de client1.
    
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
    
14. Dans **URL**, tapez **http://www.spamlink.contoso.com/**, cliquez sur **OK**, puis cliquez sur **Envoyer**.
    
15. Ouvrez une instance distincte d'Internet Explorer en mode de navigation privée, accédez au centre d'administration 365 de[https://admin.microsoft.com](https://admin.microsoft.com)Microsoft (), puis connectez-vous à votre abonnement d'évaluation Office 365 avec votre compte d'administrateur général.
    
16. Dans la page principale du portail, cliquez sur la vignette d’applications, puis cliquez sur **Courrier**.
    
17. Dans la boîte de réception, cliquez sur le message ayant pour objet **Vos nouvelles clés**.
    
18. Dans le dossier Courrier indésirable, cliquez sur le message ayant pour objet **Nouveau site web de voyage**. À l’intérieur du message, cliquez sur le lien **ce site**. Vous devriez voir un «! Internet Explorer n'a pas pu trouver spamlink.contoso.com. réserve. C’est le résultat correct, car il n’existe aucune page web à cet emplacement.
    
Vous remarquez que ces deux e-mails potentiellement malveillants ont été remis correctement. L’e-mail **Vos nouvelles clés** pouvait contenir un programme malveillant non détecté et l’utilisateur a été autorisé à cliquer sur le lien potentiellement malveillant dans l’e-mail **Nouveau site web de voyage**.
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>Phase 3 : Configuration de stratégies de liens fiables et de pièce jointe fiable pour la protection avancée contre les menaces

Dans cette phase, vous créez et configurez une stratégie de pièce jointe fiable pour empêcher les e-mails contenant des pièces jointes potentiellement malveillantes d’être remises et une stratégie de liens fiables pour empêcher les utilisateurs de se diriger vers des URL potentiellement dangereuses.
  
1. Dans l'onglet **Accueil Microsoft Office** d'Internet Explorer, cliquez sur la vignette **administrateur** .
    
2. Dans le volet de navigation gauche, cliquez sur **Centres d’administration**, puis sur **Exchange**.
    
3. Dans le volet de navigation gauche de l’onglet Centre d’administration Exchange, cliquez sur **Menaces avancées**.
    
4. Cliquez sur l’onglet **Pièces jointes approuvées**, puis sur le signe plus.
    
5. Dans la fenêtre **nouvelle stratégie de pièces jointes approuvées** , dans **nom**, tapez **stratégie de pièces jointes approuvées-bloquer**.
    
6. Pour les **pièces jointEs approuvées réponse aux programmes malveillants**inconnus, cliquez sur **bloquer**.
    
7. Pour **Rediriger la pièce jointe en cas de détection**, cliquez sur **Activer la redirection** et tapez l’adresse e-mail de votre compte d’administrateur général Office 365.
    
8. Pour **Appliqué à**, cliquez sur la flèche du menu déroulant, puis sur **Le domaine du destinataire est**. Dans la fenêtre, cliquez sur le nom de votre organisation (par exemple, contoso.onmicrosoft.com), puis cliquez sur **OK**.
    
9. Cliquez sur **Enregistrer**. Après la mise à jour, vous devriez voir le **bloc stratégie de pièces jointEs approuvées**nouveau et activé.
    
10. Cliquez sur l’onglet **Liens approuvés**, puis sur le signe plus.
    
11. Dans la fenêtre **Nouvelle stratégie de liens approuvés**, dans **Nom**, tapez **Stratégie de liens approuvés**.
    
12. Pour **Sélectionnez l’action à appliquer pour les URL potentiellement malveillantes contenues dans les messages**, cliquez sur **Activée**, puis sélectionnez **Ne pas autoriser les utilisateurs à cliquer vers l’URL d’origine**.
    
13. Pour **Appliqué à**, cliquez sur la flèche du menu déroulant, puis sur **Le domaine du destinataire est**. Dans la fenêtre, cliquez sur le nom de votre organisation (par exemple, contoso.onmicrosoft.com), puis cliquez sur **OK**.
    
14. Cliquez sur **Enregistrer**. La **nouvelle stratégie de liens** activée s’affiche.
    
## <a name="phase-4-show-atp-in-action"></a>Phase 4 : Service Protection avancée contre les menaces en action

Dans cette phase, vous montrez comment le Service Protection avancée contre les menaces en action traite les e-mails potentiellement malveillants.
  
1. À partir de l'instance d'Internet Explorer que vous avez utilisée pour envoyer le courrier électronique à la phase 2, dans le volet de navigation de gauche, cliquez sur **éléments envoyés.**
    
2. Cliquez sur l'e-mail intitulé **vos nouvelles clés**, cliquez sur la flèche vers le bas, puis sur **transférer**.
    
3. Pour le nouveau message, dans **À**, tapez l’adresse e-mail du nom de l’administrateur général Office 365 de votre abonnement d’évaluation, puis cliquez sur **Envoyer**.
    
4. Cliquez sur le message électronique intitulé **nouveau site Web de voyage**, cliquez sur la flèche vers le bas, cliquez sur **répondre à tous**, puis cliquez sur **Envoyer**.
    
5. À partir de l’instance d’Internet Explorer que vous avez utilisée pour configurer les stratégies du Service Protection avancée contre les menaces à la phase 3, cliquez sur l’onglet Centre d’administration Exchange, cliquez sur la vignette d’applications, puis cliquez sur **Courrier**. Deux nouveaux e-mails apparaissent dans la boîte de réception :
    
  - Un e-mail intitulé **Fw : Vos nouvelles clés**
    
  - Un e-mail intitulé **Fw : Nouveau site web de voyage**
    
6. Ouvrez le message électronique intitulé **FW: New Travel Web site** et cliquez sur le lien **ce site** . Vous devriez voir un «ce site Web a été classé comme malveillant». réserve. Cela démontre qu'ATP vous empêche d'accéder au site Web potentiellement malveillant.
    
7. Dans l’onglet Centre d’administration Exchange d’Internet Explorer, dans le volet de navigation gauche, cliquez sur **Flux de messagerie**.
    
8. Cliquez sur l’onglet **Suivi des messages**, puis sur **Rechercher**.
    
9. Dans la fenêtre **Résultats du suivi des messages**, double-cliquez sur le message ayant pour objet **Vos nouvelles clés**. Ce message a bien été remis dans la boîte de réception. Fermez cette fenêtre.
    
10. Double-cliquez sur le message ayant pour objet **Nouveau site web de voyage**. Ce message a bien été remis dans la boîte de réception. Fermez cette fenêtre.
    
11. Double-cliquez sur le message ayant pour objet **Fw : Vos nouvelles clés**. Notez comment ce message a été traité par ATP, puis remis dans la boîte de réception. Fermez cette fenêtre.
    
    > [!NOTE]
    > L'objectif de la stratégie de pièces jointes fiables était de commencer à analyser les pièces jointes à la recherche de code malveillant. La pièce jointe getKeys. js a été autorisée car elle n'a pas été jugée malveillante. Cette étape montre que ATP a effectué une analyse de la pièce jointe. 
  
12. Double-cliquez sur le message ayant pour objet **Fw : Nouveau site web de voyage**. Notez que ce message a bien été remis dans la boîte de réception.
    
Vous pouvez désormais utiliser cet environnement pour créer des stratégies et expérimenter le Service Protection avancée contre les menaces.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de One Microsoft Cloud.
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test de configuration de base](base-configuration-dev-test-environment.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Sécurité des applications cloud pour votre environnement de développement/test Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md) 

[Protection avancée contre les menaces pour les pièces jointes et liens fiables](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


