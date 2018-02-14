---
title: "Sécurité des applications cloud pour votre environnement de développement/test Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "Résumé : Configurer et illustrer l’Office 365 nuage App sécurité dans votre environnement de développement/test d’Office 365."
ms.openlocfilehash: ac5f5c25ecb4d97ac1c8fe3b48096ee02da2ec3e
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Sécurité des applications cloud pour votre environnement de développement/test Office 365

 **Résumé :** Configurer et illustrer l’Office 365 nuage App sécurité dans votre environnement de développement/test d’Office 365.
  
Sécurité du nuage de Office 365 App, précédemment appelée Office 365 sécurité Gestion avancée, permet vous permet de créer des stratégies de surveillent et de vous informent des activités suspectes dans votre abonnement à Office 365, afin que vous pouvez examiner et prendre possible action de conversion. Pour plus d’informations, consultez [Vue d’ensemble de nuage App sécurité dans Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
  
Les instructions fournies dans cet article indiquent comment activer et tester la sécurité des applications cloud dans votre abonnement d’évaluation Office 365.
  
> [!TIP]
> Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée

Si vous souhaitez juste tester App du nuage sécurité dans une solution légère avec la configuration minimale requise, suivez les instructions dans les étapes 2 et 3 de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester le nuage App sécurité dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Le test de la sécurité des applications cloud ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester la sécurité des applications cloud et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>Phase 2 : Avant d’activer la sécurité des applications cloud et de créer une stratégie

Dans cette procédure, vous montrez qu’avant d’activer la sécurité des applications de Cloud, la modification de rôle d’un utilisateur ne fournit aucune notification par e-mail à l’administrateur global.
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Tester le comportement par défaut des notifications d’Office 365

1. Accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et vous connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
  - Si vous utilisez l’environnement de développement/test Office 365 léger, connectez-vous sur votre ordinateur local.
    
  - Si vous utilisez l’environnement de développement/test Office 365 entreprise simulée, utiliser le [portail Azure](https://portal.azure.com) de se connecter à la machine virtuelle de CLIENT1, puis connectez-vous à partir de CLIENT1.
    
2. À partir de la page principale du portail, cliquez sur **Admin**.
    
3. Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
4. Cliquez sur le compte de **l’utilisateur 4** .
    
5. Sur la page **4 de l’utilisateur** , cliquez sur **Modifier** pour la ligne de **rôles** .
    
6. Dans la page **Modifier les rôles des utilisateurs** , cliquez sur **administrateur Global**, tapez **user4@contoso.com** dans l' **adresse de messagerie Alternative**et puis cliquez sur **Enregistrer**. Cliquez deux fois sur **Fermer** .
    
7. Sélectionnez l’icône du Lanceur app dans l’angle supérieur gauche et choisissez **courrier**.
    
8. Attendez 30 minutes. Notez qu’il n’existe aucun message électronique dans la boîte de réception qui vous avertit de la modification du rôle d’utilisateur 4 en tant qu’un administrateur global.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>Phase 3 : Activer la sécurité des applications cloud et créer une stratégie

Cette procédure indique comment activer la sécurité des applications cloud et créer une stratégie permettant d’envoyer des notifications par e-mail à votre compte d’administrateur général en cas de modification des rôles des comptes d’utilisateur. Cette procédure requiert les éléments suivants :
  
- Le nom du compte d’administrateur général et le mot de passe associés à votre abonnement d’évaluation d’Office 365.
    
- Le nom et le mot de passe du compte Utilisateur 5 de votre abonnement d’évaluation d’Office 365.
    
### <a name="enable-and-configure-cloud-app-security"></a>Activer et configurer la sécurité des applications cloud

1. Accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et vous connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
2. Cliquez sur le **sécurité &amp; la conformité** en mosaïque.
    
3. Dans le volet de navigation de gauche, cliquez sur **alertes > Gestion avancée des alertes**.
    
4. Sur la page **Gestion avancée des alertes** , cliquez sur **Activer la sécurité pour application Cloud Microsoft Office 365**, puis cliquez sur **Atteindre la sécurité pour application Cloud Microsoft Office 365**.
    
5. Dans le nouvel onglet de **tableau de bord** , cliquez sur **contrôle > stratégies**.
    
6. Sur la page de **stratégie** , cliquez sur **créer une stratégie**, puis cliquez sur **stratégie de l’activité**.
    
7. Dans la zone **nom de la stratégie**, tapez **activité Administrative**.
    
8. **Gravité de la stratégie**, cliquez sur **élevé**.
    
9. Dans la **catégorie**, cliquez sur **comptes privilégiés**.
    
10. **Créer des filtres pour la stratégie**, des **activités correspondant à tous les éléments suivants**, cliquez sur **activité Administrative**.
    
11. Dans les **alertes**, cliquez sur **Envoyer une alerte par e-mail**. Dans la zone **à**, tapez l’adresse e-mail de votre compte d’administrateur global.
    
12. En bas de la page, cliquez sur **créer**.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>Phase 4 : Afficher la sécurité des applications cloud en action

Cette procédure permet de montrer comment la sécurité des applications cloud crée des alertes et envoie des notifications par e-mail au compte d’administrateur général quand l’utilisateur 4 fait de l’utilisateur 5 un administrateur de gestion des utilisateurs et de mots de passe.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>Faire une démonstration de la notification par e-mail après modification des rôles de compte d’utilisateur

1. Dans l’angle supérieur droit, cliquez sur l’icône de l’utilisateur, puis cliquez sur **se déconnecter**.
    
2. Accédez à [https://portal.office.com](https://portal.office.com).
    
3. Sur la page de connexion Office 365, cliquez sur **utiliser un autre compte**.
    
4. Tapez le nom du compte 4 de l’utilisateur et son mot de passe, puis cliquez sur **se connecter**.
    
5. Si nécessaire, modifier le mot de passe du compte utilisateur 4, puis cliquez sur **mettre à jour le mot de passe et de vous connecter**.
    
6. Dans la page du portail Office 365, cliquez sur **administration**.
    
7. Si nécessaire, cliquez sur **Annuler** lorsque vous êtes invité à mettre à jour de vos informations de contact d’administration.
    
8. À partir de la page principale du portail, cliquez sur **Admin**.
    
9. Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
10. Cliquez sur le compte **d’utilisateur 5** .
    
11. Dans la page **5 de l’utilisateur** , cliquez sur **Modifier** pour la ligne de **rôles** .
    
12. Dans la page **Modifier les rôles de l’utilisateur** , cliquez sur **administrateur de personnalisé**et cliquez sur **administrateur de mot de passe** et **l’administrateur de gestion d’utilisateur**, tapez **user5@contoso.com** dans l' **adresse de messagerie Alternative**, puis cliquez sur **Enregistrer**. Cliquez deux fois sur **Fermer** .
    
13. Cliquez sur l’icône de l’utilisateur dans l’angle supérieur droit, puis cliquez sur **se déconnecter**. 
    
14. Accédez à [https://portal.office.com](https://portal.office.com).
    
15. Dans la page **Office 365 se connecter** , cliquez sur le nom de votre compte d’administrateur global.
    
16. Tapez le mot de passe, puis cliquez sur **se connecter**.
    
17. À partir de la page principale du portail, cliquez sur **Admin**.
    
18. Cliquez sur le **sécurité &amp; la conformité** en mosaïque.
    
19. Dans le volet de navigation de gauche, cliquez sur **alertes > Gestion avancée des alertes**.
    
20. Sur la page **Gestion avancée des alertes** , cliquez sur **sécurité pour application Cloud Microsoft Office 365**.
    
21. Sur le nouvel onglet de **tableau de bord** , notez les nouvelles deux alertes pour **une activité d’administration**.
    
22. À partir de l’onglet **Accueil de Microsoft Office** , cliquez sur **courrier**. Attendez 30 minutes. 
    
    Vous devriez voir deux nouveaux messages dans la boîte de réception avec le titre, **Le Service de Notification d’annonces Microsoft Azure**. Un message indique que le compte d’utilisateur 5 a été ajouté au rôle **Administrateur de mot de passe** et un autre message indique que le compte d’utilisateur 5 a été ajouté au rôle **Administrateur d’utilisateurs** (égal au rôle administrateur d’utilisateurs gestion dans la Centre d’administration Office 365).
    
Vous pouvez maintenant utiliser cet environnement pour créer de nouvelles stratégies et expérimenter davantage de sécurité pour application Cloud Microsoft Office 365. Pour des liens vers des articles de configuration supplémentaires, voir [Préparez-vous à sécurité pour application Cloud Microsoft Office 365](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) .
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d'adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)

[Vue d’ensemble des applications du nuage sécurité dans Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


