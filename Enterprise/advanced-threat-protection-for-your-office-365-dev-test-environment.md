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
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="b9f32-103">Protection avancée contre les menaces pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="b9f32-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="b9f32-104">**Résumé :** Configurez et faites une démonstration de la protection avancée contre les menaces Office 365 dans votre environnement de développement/test Office 365.</span><span class="sxs-lookup"><span data-stu-id="b9f32-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="b9f32-p101">Office 365 Advanced Threat Protection (DAV) est une fonctionnalité d’Exchange Online Protection (EOP) qui permet de conserver des programmes malveillants en dehors de votre courrier électronique. Avec DAV, vous créez des stratégies dans le centre d’administration Exchange (EAC) ou de la sécurité &amp; centre de conformité qui permettent de ne garantir que les liens ou les pièces jointes dans les messages électroniques qui sont identifiés comme malveillants pas accèdent à vos utilisateurs. Pour plus d’informations, voir [protection contre les menaces avancées pour les pièces jointes fiables et les liens sécurisés](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="b9f32-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="b9f32-108">Les instructions fournies dans cet article indiquent comment configurer et tester la protection avancée contre les menaces dans votre abonnement d’évaluation Office 365.</span><span class="sxs-lookup"><span data-stu-id="b9f32-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="b9f32-109">Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée</span><span class="sxs-lookup"><span data-stu-id="b9f32-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="b9f32-110">Si vous souhaitez uniquement tester DAV dans une solution légère avec la configuration minimale requise, suivez les instructions en phases 2 et 3 de [l’environnement de développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="b9f32-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="b9f32-111">Si vous souhaitez tester DAV dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="b9f32-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="b9f32-p102">Le test de la protection avancée contre les menaces ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester la protection avancée contre les menaces et faire des essais dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="b9f32-114">Phase 2 : Illustrer le comportement de remise du courrier électronique par défaut d’Office 365</span><span class="sxs-lookup"><span data-stu-id="b9f32-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="b9f32-115">Dans cette phase, vous démontrez qu’avant de configurer les stratégies de protection avancée contre les menaces, l’e-mail potentiellement malveillant est remis aux boîtes aux lettres Office 365 sans filtrage ni atténuation.</span><span class="sxs-lookup"><span data-stu-id="b9f32-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="b9f32-116">Ouvrez Internet Explorer et connectez-vous au compte Outlook que vous avez créé dans la Phase 2 de [l’environnement de développement/test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="b9f32-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="b9f32-117">Si vous utilisez l’environnement de développement/test Office 365 léger, ouvrez une session privée d’Internet Explorer et connectez-vous sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b9f32-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="b9f32-118">Si vous utilisez l’environnement de développement/test Office 365 entreprise simulé, utilisez le [portail Azure](https://portal.azure.com) pour se connecter à l’ordinateur virtuel CLIENT1 et puis se connecter à partir de CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="b9f32-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="b9f32-119">Ouvrez le Bloc-notes et saisissez du texte.</span><span class="sxs-lookup"><span data-stu-id="b9f32-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="b9f32-120">Enregistrez le fichier dans le dossier Documents sous le nom **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="b9f32-121">Dans l’onglet Courrier Outlook d’Internet Explorer, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="b9f32-122">Dans **À**, tapez l’adresse e-mail du nom de l’administrateur général Office 365 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="b9f32-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="b9f32-123">Dans l’objet, tapez **Vos nouvelles clés**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="b9f32-124">Dans le corps, tapez **Voici le fichier**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="b9f32-125">Cliquez sur **Joindre**, double-cliquez sur **getKeys.js** dans le dossier Documents, cliquez sur **Joindre une copie**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="b9f32-126">Cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-126">Click **New**.</span></span>
    
10. <span data-ttu-id="b9f32-127">Dans **À**, tapez l’adresse e-mail du nom de l’administrateur général Office 365 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="b9f32-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="b9f32-128">Dans l’objet, tapez **Nouveau site web de voyage**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="b9f32-129">Dans le corps, tapez **Quelqu'un m’a transmis ce site**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="b9f32-130">Dans le corps, sélectionnez le texte **ce site** et cliquez sur l’icône de lien hypertexte dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="b9f32-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="b9f32-131">Dans l' **URL**, tapez **http://www.spamlink.contoso.com/**, cliquez sur **OK**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="b9f32-132">Ouvrez une instance distincte de Internet Explorer en mode de navigation privée, accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et se connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="b9f32-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="b9f32-133">Dans la page principale du portail, cliquez sur la vignette d’applications, puis cliquez sur **Courrier**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="b9f32-134">Dans la boîte de réception, cliquez sur le message ayant pour objet **Vos nouvelles clés**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="b9f32-p103">Dans le dossier courrier indésirable, cliquez sur le message avec l’objet du **Nouveau site web en déplacement**. Dans le message, cliquez sur le lien de **ce site** . Vous devez voir une « Oops ! Page d’Internet Explorer n’a pas pu trouver spamlink.contoso.com. ». Il s’agit du résultat correct, car il n’existe aucune page web à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="b9f32-p104">Vous remarquez que ces deux e-mails potentiellement malveillants ont été remis correctement. L’e-mail **Vos nouvelles clés** pouvait contenir un programme malveillant non détecté et l’utilisateur a été autorisé à cliquer sur le lien potentiellement malveillant dans l’e-mail **Nouveau site web de voyage**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="b9f32-143">Phase 3 : Configuration de stratégies de liens fiables et de pièce jointe fiable pour la protection avancée contre les menaces</span><span class="sxs-lookup"><span data-stu-id="b9f32-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="b9f32-144">Dans cette phase, vous créez et configurez une stratégie de pièce jointe fiable pour empêcher les e-mails contenant des pièces jointes potentiellement malveillantes d’être remises et une stratégie de liens fiables pour empêcher les utilisateurs de se diriger vers des URL potentiellement dangereuses.</span><span class="sxs-lookup"><span data-stu-id="b9f32-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="b9f32-145">Sous l’onglet **Accueil Microsoft Office** d’Internet Explorer, cliquez sur la vignette de **l’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="b9f32-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="b9f32-146">Dans le volet de navigation gauche, cliquez sur **Centres d’administration**, puis sur **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="b9f32-147">Dans le volet de navigation gauche de l’onglet Centre d’administration Exchange, cliquez sur **Menaces avancées**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="b9f32-148">Cliquez sur l’onglet **Pièces jointes approuvées**, puis sur le signe plus.</span><span class="sxs-lookup"><span data-stu-id="b9f32-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="b9f32-149">Dans la fenêtre de la **nouvelle stratégie de pièces jointes fiables** , dans **nom**, tapez **Stratégie de pièce jointe sécurisé - bloc**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="b9f32-150">**Réponse de programmes malveillants inconnu fiables de pièces jointes**, cliquez sur **Bloquer**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="b9f32-151">Pour **Rediriger la pièce jointe en cas de détection**, cliquez sur **Activer la redirection** et tapez l’adresse e-mail de votre compte d’administrateur général Office 365.</span><span class="sxs-lookup"><span data-stu-id="b9f32-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="b9f32-p105">Pour **s’applique à**, cliquez sur la flèche vers le bas, puis cliquez sur **le domaine du destinataire est**. Dans la fenêtre, cliquez sur le nom de votre organisation (par exemple, contoso.onmicrosoft.com), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="b9f32-p106">Cliquez sur **Enregistrer**. Après la mise à jour, vous devez afficher le nouveau et activé la **Stratégie de pièce jointe sans échec - bloc**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="b9f32-156">Cliquez sur l’onglet **Liens approuvés**, puis sur le signe plus.</span><span class="sxs-lookup"><span data-stu-id="b9f32-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="b9f32-157">Dans la fenêtre **Nouvelle stratégie de liens approuvés**, dans **Nom**, tapez **Stratégie de liens approuvés**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="b9f32-158">Pour **Sélectionnez l’action à appliquer pour les URL potentiellement malveillantes contenues dans les messages**, cliquez sur **Activée**, puis sélectionnez **Ne pas autoriser les utilisateurs à cliquer vers l’URL d’origine**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="b9f32-p107">Pour **s’applique à**, cliquez sur la flèche vers le bas, puis cliquez sur **le domaine du destinataire est**. Dans la fenêtre, cliquez sur le nom de votre organisation (par exemple, contoso.onmicrosoft.com), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="b9f32-p108">Cliquez sur **Enregistrer**. La **nouvelle stratégie de liens** activée s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="b9f32-163">Phase 4 : Service Protection avancée contre les menaces en action</span><span class="sxs-lookup"><span data-stu-id="b9f32-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="b9f32-164">Dans cette phase, vous montrez comment le Service Protection avancée contre les menaces en action traite les e-mails potentiellement malveillants.</span><span class="sxs-lookup"><span data-stu-id="b9f32-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="b9f32-165">À partir de l’instance d’Internet Explorer que vous avez utilisé pour envoyer le courrier électronique à la Phase 2, dans le volet de navigation gauche, cliquez sur **éléments envoyés.**</span><span class="sxs-lookup"><span data-stu-id="b9f32-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="b9f32-166">Cliquez sur le courrier électronique intitulé **vos nouvelles clés**, cliquez sur la flèche vers le bas, puis cliquez sur **Transférer**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="b9f32-167">Pour le nouveau message, dans **À**, tapez l’adresse e-mail du nom de l’administrateur général Office 365 de votre abonnement d’évaluation, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="b9f32-168">Cliquez sur le courrier électronique intitulé **New se déplacent le site web**, cliquez sur la flèche vers le bas, cliquez sur **répondre à tous**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="b9f32-p109">À partir de l’instance d’Internet Explorer que vous avez utilisée pour configurer les stratégies du Service Protection avancée contre les menaces à la phase 3, cliquez sur l’onglet Centre d’administration Exchange, cliquez sur la vignette d’applications, puis cliquez sur **Courrier**. Deux nouveaux e-mails apparaissent dans la boîte de réception :</span><span class="sxs-lookup"><span data-stu-id="b9f32-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="b9f32-171">Un e-mail intitulé **Fw : Vos nouvelles clés**</span><span class="sxs-lookup"><span data-stu-id="b9f32-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="b9f32-172">Un e-mail intitulé **Fw : Nouveau site web de voyage**</span><span class="sxs-lookup"><span data-stu-id="b9f32-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="b9f32-p110">Ouvrez le message électronique intitulé **TR : nouveau site web de déplacements** et cliquez sur le lien de **ce site** . Vous devez voir une page « ce site Web a été classé comme malveillants. ». Cela montre que DAV vous empêche d’accéder au site web malveillant.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="b9f32-177">Dans l’onglet Centre d’administration Exchange d’Internet Explorer, dans le volet de navigation gauche, cliquez sur **Flux de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="b9f32-178">Cliquez sur l’onglet **Suivi des messages**, puis sur **Rechercher**.</span><span class="sxs-lookup"><span data-stu-id="b9f32-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="b9f32-p111">Dans la fenêtre de **Résultats de suivi des messages** , double-cliquez sur le message avec l’objet **vos nouvelles clés**. Ce message a bien été remis à la boîte de réception. Fermez cette fenêtre.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="b9f32-p112">Double-cliquez sur le message avec l’objet du **Nouveau site web en déplacement**. Ce message a bien été remis à la boîte de réception. Fermez cette fenêtre.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="b9f32-p113">Double-cliquez sur le message avec l’objet **TR : vos nouvelles clés**. Notez comment ce message a été traité par DAV et puis remis à la boîte de réception. Fermez cette fenêtre.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="b9f32-p114">L’objectif de la stratégie de pièces jointes sûres était de commencer l’analyse des pièces jointes pour le code malveillant. La pièce jointe getKeys.js a été autorisée, car il n’a pas été déterminée malveillants. Cette étape indique que DAV effectuer une analyse de la pièce jointe.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="b9f32-p115">Double-cliquez sur le message avec l’objet **TR : nouveau site web de déplacements**. Notez que ce message a bien été remis à la boîte de réception.</span><span class="sxs-lookup"><span data-stu-id="b9f32-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="b9f32-193">Vous pouvez désormais utiliser cet environnement pour créer des stratégies et expérimenter le Service Protection avancée contre les menaces.</span><span class="sxs-lookup"><span data-stu-id="b9f32-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="b9f32-194">Cliquez [ici](http://aka.ms/catlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="b9f32-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b9f32-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9f32-195">See Also</span></span>

[<span data-ttu-id="b9f32-196">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="b9f32-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="b9f32-197">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="b9f32-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="b9f32-198">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="b9f32-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="b9f32-199">DirSync pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="b9f32-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="b9f32-200">Sécurité des applications cloud pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="b9f32-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="b9f32-201">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="b9f32-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="b9f32-202">Protection avancée contre les menaces pour les pièces jointes et liens fiables</span><span class="sxs-lookup"><span data-stu-id="b9f32-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


