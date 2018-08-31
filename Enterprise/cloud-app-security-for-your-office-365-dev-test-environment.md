---
title: Sécurité des applications cloud pour votre environnement de développement/test Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
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
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 'Résumé : Configurez et faites une démonstration de la sécurité des applications cloud Office 365 dans votre environnement de développement/test Office 365.'
ms.openlocfilehash: 089b9771d0600f8c74bc7b4c30ff2a4931c93ae6
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915759"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="38524-103">Sécurité des applications cloud pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="38524-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="38524-104">**Résumé :** Configurez et faites une démonstration de la sécurité des applications cloud Office 365 dans votre environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="38524-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="38524-p101">Office 365 Cloud application sécurité, anciennement appelé Office 365 gestion avancée de sécurité, vous permet de créer des stratégies pour surveiller et vous informent des activités suspectes dans votre abonnement Office 365, afin que vous pouvez examiner et prendre possibles mesures correctives. Pour plus d’informations, voir [Vue d’ensemble du nuage application sécurité dans Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="38524-p101">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action. For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="38524-107">Les instructions fournies dans cet article indiquent comment activer et tester la sécurité des applications cloud dans votre abonnement d’évaluation Office 365.</span><span class="sxs-lookup"><span data-stu-id="38524-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="38524-108">Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="38524-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="38524-109">Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée</span><span class="sxs-lookup"><span data-stu-id="38524-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="38524-110">Si vous souhaitez uniquement tester la sécurité d’application de Cloud de manière léger avec la configuration minimale requise, suivez les instructions en phases 2 et 3 de [l’environnement de développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="38524-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="38524-111">Si vous souhaitez tester la sécurité d’application Cloud dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="38524-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="38524-p102">Le test de la sécurité des applications cloud ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester la sécurité des applications cloud et faire des essais dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="38524-p102">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="38524-114">Phase 2 : Avant d’activer la sécurité des applications cloud et de créer une stratégie</span><span class="sxs-lookup"><span data-stu-id="38524-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="38524-115">Dans cette procédure, vous montrez qu’avant l’activation de la sécurité des applications dans le nuage, modification du rôle d’un utilisateur ne fournit aucune notification par courrier électronique à l’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="38524-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="38524-116">Tester le comportement par défaut des notifications d’Office 365</span><span class="sxs-lookup"><span data-stu-id="38524-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="38524-117">Accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et se connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="38524-117">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="38524-118">Si vous utilisez l’environnement de développement/test Office 365 léger, connectez-vous sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="38524-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="38524-119">Si vous utilisez l’environnement de développement/test Office 365 entreprise simulé, utilisez le [portail Azure](https://portal.azure.com) pour se connecter à l’ordinateur virtuel CLIENT1 et puis se connecter à partir de CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="38524-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="38524-120">Sur la page principale du portail, cliquez sur **Administrateur**.</span><span class="sxs-lookup"><span data-stu-id="38524-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="38524-121">Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="38524-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="38524-122">	Cliquez sur le compte **Utilisateur 4**.</span><span class="sxs-lookup"><span data-stu-id="38524-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="38524-123">Sur la page **utilisateur 4**, cliquez sur **Modifier** pour la ligne **Rôles**.</span><span class="sxs-lookup"><span data-stu-id="38524-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="38524-p103">Sur la page **Modifier les rôles d’utilisateur**, cliquez sur **Administrateur général**, entrez **utilisateur4@contoso.com** comme **autre adresse de messagerie**, puis cliquez sur **Enregistrer**. Cliquez sur **Fermer** à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="38524-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="38524-126">	Sélectionnez l’icône de lanceur d’applications dans l’angle supérieur gauche et choisissez **Messagerie**.</span><span class="sxs-lookup"><span data-stu-id="38524-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="38524-p104">Attendez 30 minutes. Ne Notez qu’aucun message électronique dans la boîte de réception pour vous avertir de la modification au rôle d’utilisateur 4 en tant qu’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="38524-p104">Wait 30 minutes. Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="38524-129">Phase 3 : Activer la sécurité des applications cloud et créer une stratégie</span><span class="sxs-lookup"><span data-stu-id="38524-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="38524-p105">Cette procédure indique comment activer la sécurité des applications cloud et créer une stratégie permettant d’envoyer des notifications par e-mail à votre compte d’administrateur général en cas de modification des rôles des comptes d’utilisateur. Cette procédure requiert les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="38524-p105">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles. This procedure requires:</span></span>
  
- <span data-ttu-id="38524-132">Le nom du compte d’administrateur général et le mot de passe associés à votre abonnement d’évaluation d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="38524-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="38524-133">Le nom et le mot de passe du compte Utilisateur 5 de votre abonnement d’évaluation d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="38524-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="38524-134">Activer et configurer la sécurité des applications cloud</span><span class="sxs-lookup"><span data-stu-id="38524-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="38524-135">Accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et se connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="38524-135">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="38524-p106">Cliquez sur la vignette de **l’administrateur** . Dans l’onglet **Centre d’administration d’Office** , cliquez sur **centres d’administration > sécurité et conformité**.</span><span class="sxs-lookup"><span data-stu-id="38524-p106">Click the **Admin** tile. On the **Office Admin center** tab, click **Admin centers > Security & Compliance**.</span></span>
    
3. <span data-ttu-id="38524-138">Dans le volet de navigation de gauche, cliquez sur **Alertes > Gérer les alertes avancées**.</span><span class="sxs-lookup"><span data-stu-id="38524-138">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="38524-139">Sur la page **Gérer les alertes avancées**, cliquez sur **Activer Sécurité des applications cloud Office 365**, puis sur **Atteindre Sécurité des applications cloud Office 365**.</span><span class="sxs-lookup"><span data-stu-id="38524-139">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="38524-140">Sur le nouvel onglet **Tableau de bord**, cliquez sur **Contrôle > Stratégies**.</span><span class="sxs-lookup"><span data-stu-id="38524-140">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="38524-141">Sur la page **Stratégies**, cliquez sur **Créer une stratégie**, puis sur **Stratégie d’activité**.</span><span class="sxs-lookup"><span data-stu-id="38524-141">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="38524-142">Dans **Nom de la stratégie**, saisissez **Activité administrative**.</span><span class="sxs-lookup"><span data-stu-id="38524-142">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="38524-143">Dans **Gravité de la stratégie**, cliquez sur **Élevée**.</span><span class="sxs-lookup"><span data-stu-id="38524-143">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="38524-144">Dans **Catégorie**, cliquez sur **Comptes privilégiés**.</span><span class="sxs-lookup"><span data-stu-id="38524-144">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="38524-145">Dans **Créer des filtres pour la stratégie**, dans **Activités correspondant à tous les critères suivants**, cliquez sur **Activité administrative**.</span><span class="sxs-lookup"><span data-stu-id="38524-145">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="38524-p107">Dans **Alertes**, cliquez sur **Envoyer une alerte par e-mail**. Dans **À**, entrez l’adresse de messagerie de votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="38524-p107">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="38524-148">Au bas de la page, cliquez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="38524-148">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="38524-149">Phase 4 : Afficher la sécurité des applications cloud en action</span><span class="sxs-lookup"><span data-stu-id="38524-149">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="38524-150">Cette procédure permet de montrer comment la sécurité des applications cloud crée des alertes et envoie des notifications par e-mail au compte d’administrateur général quand l’utilisateur 4 fait de l’utilisateur 5 un administrateur de gestion des utilisateurs et de mots de passe.</span><span class="sxs-lookup"><span data-stu-id="38524-150">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="38524-151">Faire une démonstration de la notification par e-mail après modification des rôles de compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="38524-151">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="38524-152">Dans l’angle supérieur droit, cliquez sur l’icône de l’utilisateur, puis cliquez sur **Déconnexion**.</span><span class="sxs-lookup"><span data-stu-id="38524-152">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="38524-153">Accédez à [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="38524-153">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
3. <span data-ttu-id="38524-154">Sur la page de connexion Office 365, cliquez sur **Utiliser un autre compte**.</span><span class="sxs-lookup"><span data-stu-id="38524-154">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="38524-155">Entrez le nom du compte Utilisateur 4 et le mot de passe associé, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="38524-155">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="38524-156">Si nécessaire, modifiez le mot de passe du compte utilisateur 4, puis cliquez sur **Mettre à jour le mot de passe et se connecter**.</span><span class="sxs-lookup"><span data-stu-id="38524-156">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="38524-157">Sur la page du portail Office 365, cliquez sur **Administrateur**.</span><span class="sxs-lookup"><span data-stu-id="38524-157">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="38524-158">Si nécessaire, cliquez sur **Annuler** lorsque vous êtes invité à mettre à jour les informations de contact de votre administrateur.</span><span class="sxs-lookup"><span data-stu-id="38524-158">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="38524-159">Sur la page principale du portail, cliquez sur **Administrateur**.</span><span class="sxs-lookup"><span data-stu-id="38524-159">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="38524-160">Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="38524-160">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="38524-161">Cliquez sur le compte **Utilisateur 5**.</span><span class="sxs-lookup"><span data-stu-id="38524-161">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="38524-162">Sur la page **utilisateur 5**, cliquez sur **Modifier** pour la ligne **Rôles**.</span><span class="sxs-lookup"><span data-stu-id="38524-162">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="38524-p108">Sur la page **Modifier les rôles d’utilisateur**, cliquez sur **Administrateur personnalisé**, cliquez sur **Administrateur de mots de passe** et sur **Administrateur de gestion des utilisateurs**, entrez **utilisateur5@contoso.com** comme **autre adresse de messagerie**, puis cliquez sur **Enregistrer**. Cliquez sur **Fermer** à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="38524-p108">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="38524-165">Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **Déconnexion**. </span><span class="sxs-lookup"><span data-stu-id="38524-165">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="38524-166">Accédez à [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="38524-166">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
15. <span data-ttu-id="38524-167">Sur la **page de connexion Office 365**, cliquez sur le nom de votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="38524-167">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="38524-168">Entrez le mot de passe, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="38524-168">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="38524-169">Sur la page principale du portail, cliquez sur **Administrateur**.</span><span class="sxs-lookup"><span data-stu-id="38524-169">From the main portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="38524-170">Cliquez sur le **sécurité &amp; conformité** mosaïque.</span><span class="sxs-lookup"><span data-stu-id="38524-170">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="38524-171">Dans le volet de navigation de gauche, cliquez sur **Alertes > Gérer les alertes avancées**.</span><span class="sxs-lookup"><span data-stu-id="38524-171">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="38524-172">Sur la page **Gérer les alertes avancées**, cliquez sur **Atteindre Sécurité des applications cloud Office 365**.</span><span class="sxs-lookup"><span data-stu-id="38524-172">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="38524-173">Sur le nouvel onglet **Tableau de bord**, remarquez les deux nouvelles alertes pour **Activité administrative**.</span><span class="sxs-lookup"><span data-stu-id="38524-173">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="38524-p109">Dans l’onglet d’accueil **Microsoft Office**, cliquez sur **Admin**. Patientez 30 minutes. </span><span class="sxs-lookup"><span data-stu-id="38524-p109">From the **Microsoft Office Home** tab, click **Mail**. Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="38524-p110">Vous devriez voir deux nouveaux messages électroniques dont le titre mentionne le **service de notification Microsoft Azure AD** dans la boîte de réception. L’un d’eux indique que le compte Utilisateur 5 a été ajouté au rôle **Administrateur de mots de passe** et l’autre que ce même compte a été ajouté au rôle **Administrateur d'utilisateurs** (équivalent du rôle d’administrateur de gestion des utilisateurs dans le centre d’administration Office 365).</span><span class="sxs-lookup"><span data-stu-id="38524-p110">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**. One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="38524-p111">Vous pouvez maintenant utiliser cet environnement pour créer de nouvelles stratégies et autres expérimenter la sécurité d’application Office 365 dans le nuage. Pour des liens vers des articles de configuration supplémentaires, voir [préparer à Office 365 nuage sécurité des applications](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) .</span><span class="sxs-lookup"><span data-stu-id="38524-p111">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security. See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="38524-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38524-180">See Also</span></span>

[<span data-ttu-id="38524-181">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="38524-181">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="38524-182">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="38524-182">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="38524-183">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="38524-183">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="38524-184">Vue d’ensemble de la sécurité d’application Cloud dans Office 365</span><span class="sxs-lookup"><span data-stu-id="38524-184">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


