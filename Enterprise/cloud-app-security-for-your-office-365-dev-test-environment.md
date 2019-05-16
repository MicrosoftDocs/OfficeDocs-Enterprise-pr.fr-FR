---
title: Sécurité des applications cloud pour votre environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 'Résumé : Configurez et faites une démonstration de la sécurité des applications cloud Office 365 dans votre environnement de développement/test Office 365.'
ms.openlocfilehash: af2a2657ede46818b9d705ca38f99d779f98fb11
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068100"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Sécurité des applications cloud pour votre environnement de développement/test Office 365

 **Résumé :** Configurez et faites une démonstration de la sécurité des applications cloud Office 365 dans votre environnement de développement/test Office 365.
  
Office 365 Cloud App Security, précédemment appelé Office 365 Advanced Security Management, vous permet de créer des stratégies qui surveillent et vous informent des activités suspectes dans votre abonnement Office 365, afin que vous puissiez examiner et prendre les mesures correctives possibles. transactionnelle. Pour plus d’informations, reportez-vous à la rubrique [vue d’ensemble de la sécurité des applications Cloud dans Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
  
Les instructions fournies dans cet article indiquent comment activer et tester la sécurité des applications cloud dans votre abonnement d’évaluation Office 365.
  
> [!TIP]
> Cliquez sur[ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles dans le Guide de Laboratoire Test Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée

Si vous souhaitez simplement tester la sécurité des applications Cloud avec la configuration minimale requise, suivez les instructions des phases 2 et 3 de l' [environnement de développement/test Office 365](office-365-dev-test-environment.md).
  
Si vous souhaitez tester la sécurité des applications Cloud dans une entreprise simulée, suivez les instructions de [DirSync pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Le test de la sécurité des applications Cloud ne nécessite pas l’environnement de développement/test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Il est proposé comme option dans cet article afin que vous puissiez tester la sécurité des applications cloud et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>Phase 2 : Avant d’activer la sécurité des applications cloud et de créer une stratégie

Dans cette procédure, vous démontrez qu’avant d’activer la sécurité des applications Cloud, la modification du rôle d’un utilisateur n’offre aucune notification par courrier électronique à l’administrateur général.
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Tester le comportement par défaut des notifications d’Office 365

1. Accédez au centre d’administration de Microsoft 365[https://admin.microsoft.com](https://admin.microsoft.com)() et connectez-vous à votre abonnement d’évaluation Office 365 avec votre compte d’administrateur général.
    
  - Si vous utilisez l’environnement de développement/test Office 365 léger, connectez-vous sur votre ordinateur local.
    
  - Si vous utilisez l’environnement de développement/test Office 365 entreprise simulé, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle CLIENT1, puis connectez-vous à partir de client1.
    
2. Sur la page principale du portail, cliquez sur **Administrateur**.
    
3. Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
4. 	Cliquez sur le compte **Utilisateur 4**.
    
5. Sur la page **utilisateur 4**, cliquez sur **Modifier** pour la ligne **Rôles**.
    
6. Sur la page **Modifier les rôles d’utilisateur**, cliquez sur **Administrateur général**, entrez **utilisateur4@contoso.com** comme **autre adresse de messagerie**, puis cliquez sur **Enregistrer**. Cliquez sur **Fermer** à deux reprises.
    
7. 	Sélectionnez l’icône de lanceur d’applications dans l’angle supérieur gauche et choisissez **Messagerie**.
    
8. Attendez 30 minutes. Notez qu’aucun message électronique dans la boîte de réception ne vous avertit de la modification apportée au rôle de l’utilisateur 4 en tant qu’administrateur général.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>Phase 3 : Activer la sécurité des applications cloud et créer une stratégie

Cette procédure indique comment activer la sécurité des applications cloud et créer une stratégie permettant d’envoyer des notifications par e-mail à votre compte d’administrateur général en cas de modification des rôles des comptes d’utilisateur. Cette procédure requiert les éléments suivants :
  
- Le nom du compte d’administrateur général et le mot de passe associés à votre abonnement d’évaluation d’Office 365.
    
- Le nom et le mot de passe du compte Utilisateur 5 de votre abonnement d’évaluation d’Office 365.
    
### <a name="enable-and-configure-cloud-app-security"></a>Activer et configurer la sécurité des applications cloud

1. Accédez au centre d’administration de Microsoft 365[https://admin.microsoft.com](https://admin.microsoft.com)() et connectez-vous à votre abonnement d’évaluation Office 365 avec votre compte d’administrateur général.
    
2. Cliquez sur la vignette **Administration**. Dans l’onglet **Centre d’administration Office** , cliquez sur centres d’administration **_GT_ sécurité & conformité**.
    
3. Dans le volet de navigation de gauche, cliquez sur **Alertes > Gérer les alertes avancées**.
    
4. Sur la page **Gérer les alertes avancées**, cliquez sur **Activer Sécurité des applications cloud Office 365**, puis sur **Atteindre Sécurité des applications cloud Office 365**.
    
5. Sur le nouvel onglet **Tableau de bord**, cliquez sur **Contrôle > Stratégies**.
    
6. Sur la page **Stratégies**, cliquez sur **Créer une stratégie**, puis sur **Stratégie d’activité**.
    
7. Dans **Nom de la stratégie**, saisissez **Activité administrative**.
    
8. Dans **Gravité de la stratégie**, cliquez sur **Élevée**.
    
9. Dans **Catégorie**, cliquez sur **Comptes privilégiés**.
    
10. Dans **Créer des filtres pour la stratégie**, dans **Activités correspondant à tous les critères suivants**, cliquez sur **Activité administrative**.
    
11. Dans **Alertes**, cliquez sur **Envoyer une alerte par e-mail**. Dans **À**, entrez l’adresse de messagerie de votre compte d’administrateur général.
    
12. Au bas de la page, cliquez sur **Créer**.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>Phase 4 : Afficher la sécurité des applications cloud en action

Cette procédure permet de montrer comment la sécurité des applications cloud crée des alertes et envoie des notifications par e-mail au compte d’administrateur général quand l’utilisateur 4 fait de l’utilisateur 5 un administrateur de gestion des utilisateurs et de mots de passe.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>Faire une démonstration de la notification par e-mail après modification des rôles de compte d’utilisateur

1. Dans l’angle supérieur droit, cliquez sur l’icône de l’utilisateur, puis cliquez sur **Déconnexion**.
    
2. Accédez à [https://www.office.com](https://www.office.com).
    
3. Sur la page de connexion Office 365, cliquez sur **Utiliser un autre compte**.
    
4. Entrez le nom du compte Utilisateur 4 et le mot de passe associé, puis cliquez sur **Se connecter**.
    
5. Si nécessaire, modifiez le mot de passe du compte utilisateur 4, puis cliquez sur **Mettre à jour le mot de passe et se connecter**.
    
6. Sur la page du portail Office 365, cliquez sur **Administrateur**.
    
7. Si nécessaire, cliquez sur **Annuler** lorsque vous êtes invité à mettre à jour les informations de contact de votre administrateur.
    
8. Sur la page principale du portail, cliquez sur **Administrateur**.
    
9. Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
10. Cliquez sur le compte **Utilisateur 5**.
    
11. Sur la page **utilisateur 5**, cliquez sur **Modifier** pour la ligne **Rôles**.
    
12. Sur la page **Modifier les rôles d’utilisateur**, cliquez sur **Administrateur personnalisé**, cliquez sur **Administrateur de mots de passe** et sur **Administrateur de gestion des utilisateurs**, entrez **utilisateur5@contoso.com** comme **autre adresse de messagerie**, puis cliquez sur **Enregistrer**. Cliquez sur **Fermer** à deux reprises.
    
13. Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**.  
    
14. Accédez à [https://www.office.com](https://www.office.com).
    
15. Sur la **page de connexion Office 365**, cliquez sur le nom de votre compte d’administrateur général.
    
16. Entrez le mot de passe, puis cliquez sur **Se connecter**.
    
17. À partir de la page du portail Office 365, cliquez sur **administrateur**.
    
18. Cliquez sur la vignette **conformité de sécurité &amp; ** .
    
19. Dans le volet de navigation de gauche, cliquez sur **Alertes > Gérer les alertes avancées**.
    
20. Sur la page **Gérer les alertes avancées**, cliquez sur **Atteindre Sécurité des applications cloud Office 365**.
    
21. Sur le nouvel onglet **Tableau de bord**, remarquez les deux nouvelles alertes pour **Activité administrative**.
    
22. Dans l’onglet d’accueil **Microsoft Office**, cliquez sur **Admin**. Patientez 30 minutes.  
    
    Vous devriez voir deux nouveaux messages électroniques dont le titre mentionne le **service de notification Microsoft Azure AD** dans la boîte de réception. L’un d’eux indique que le compte Utilisateur 5 a été ajouté au rôle **Administrateur de mots de passe** et l’autre que ce même compte a été ajouté au rôle **Administrateur d'utilisateurs** (équivalent du rôle d’administrateur de gestion des utilisateurs dans le centre d’administration Office 365).
    
Vous pouvez désormais utiliser cet environnement pour créer des stratégies et expérimenter plus en profondeur la sécurité des applications cloud Office 365. Voir [Get Ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) pour obtenir des liens vers d’autres Articles de configuration.
  
## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test d’adoption cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Environnement de développement/test Office 365](office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)

[Vue d’ensemble de la sécurité des applications Cloud dans Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


