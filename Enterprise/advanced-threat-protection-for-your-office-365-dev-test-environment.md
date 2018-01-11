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
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "Résumé : Configurer et illustrer l’Office 365 Advanced Threat Protection dans votre environnement de développement/test d’Office 365."
ms.openlocfilehash: 3af5255d038f5cea40242162e149a873f347203f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="5f3f7-103">Protection avancée contre les menaces pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5f3f7-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="5f3f7-104">**Résumé :** Configurer et illustrer l’Office 365 Advanced Threat Protection dans votre environnement de développement/test d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="5f3f7-p101">Office 365 Advanced Threat Protection (ATP) est une fonctionnalité d’Exchange Online Protection (EOP) qui vous aide à garder les logiciels malveillants de votre message électronique. Avec DAV, vous créez des stratégies dans le centre d’administration Exchange (FAC) ou de la sécurité &amp; centre de conformité qui permettent de garantir à vos utilisateurs accèdent uniquement des liens ou des pièces jointes dans les e-mails qui sont identifiés comme non malveillantes. Pour plus d’informations, consultez [protection contre les menaces avancées des liens sécurisés et les pièces jointes sûres](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="5f3f7-108">Les instructions fournies dans cet article indiquent comment configurer et tester la protection avancée contre les menaces dans votre abonnement d’évaluation Office 365.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="5f3f7-109">Phase 1 : Créer votre environnement de développement/test Office 365 en mode léger ou pour entreprise simulée</span><span class="sxs-lookup"><span data-stu-id="5f3f7-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="5f3f7-110">Si vous souhaitez juste tester ATP dans une solution légère avec la configuration minimale requise, suivez les instructions dans les étapes 2 et 3 de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="5f3f7-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="5f3f7-111">Si vous souhaitez tester l’ATP dans une entreprise simulée, suivez les instructions de [synchronisation d’annuaire pour votre environnement de développement/test d’Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="5f3f7-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="5f3f7-p102">Le test de la protection avancée contre les menaces ne requiert pas l’environnement de développement/test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Windows Server Active Directory. Il est proposé comme option dans cet article afin que vous puissiez tester la protection avancée contre les menaces et faire des essais dans un environnement qui représente une organisation classique.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="5f3f7-114">Phase 2 : Montrer le comportement de livraison de courrier électronique par défaut d’Office 365</span><span class="sxs-lookup"><span data-stu-id="5f3f7-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="5f3f7-115">Dans cette phase, vous démontrez qu’avant de configurer les stratégies de protection avancée contre les menaces, l’e-mail potentiellement malveillant est remis aux boîtes aux lettres Office 365 sans filtrage ni atténuation.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="5f3f7-116">Ouvrez Internet Explorer et vous connecter sur le compte de Outlook que vous avez créé à la Phase 2 de [l’environnement de développement/test d’Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="5f3f7-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="5f3f7-117">Si vous utilisez l’environnement de développement/test Office 365 léger, ouvrez une session privée d’Internet Explorer et connectez-vous sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="5f3f7-118">Si vous utilisez l’environnement de développement/test Office 365 entreprise simulée, utiliser le [portail Azure](https://portal.azure.com) de se connecter à la machine virtuelle de CLIENT1, puis connectez-vous à partir de CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="5f3f7-119">Ouvrez le Bloc-notes et saisissez du texte.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="5f3f7-120">Enregistrez le fichier dans le dossier Documents sous la forme **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="5f3f7-121">Sous l’onglet messagerie Outlook de Microsoft Internet Explorer, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="5f3f7-122">Dans la zone **à**, tapez l’adresse de messagerie du nom global administrateur Office 365 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="5f3f7-123">Pour l’objet, tapez **vos nouvelles clés**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="5f3f7-124">Dans le corps, tapez **Voici le fichier**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="5f3f7-125">Cliquez sur **joindre**, double-cliquez sur **getKeys.js** dans le dossier Documents, cliquez sur **attacher en tant que copie**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="5f3f7-126">Cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-126">Click **New**.</span></span>
    
10. <span data-ttu-id="5f3f7-127">Dans la zone **à**, tapez l’adresse de messagerie du nom global administrateur Office 365 de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="5f3f7-128">Pour l’objet, tapez **Nouveau voyage de site web**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="5f3f7-129">Dans le corps, tapez **que quelqu'un m’a transmis ce site**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="5f3f7-130">Dans le corps, sélectionnez le texte de **ce site** , puis cliquez sur l’icône de lien hypertexte dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="5f3f7-131">Dans l' **URL**, tapez **http://www.spamlink.contoso.com/**et cliquez sur **OK**puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="5f3f7-132">Ouvrez une instance distincte d’Internet Explorer en mode de navigation privé, accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et vous connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="5f3f7-133">À partir de la page principale du portail, cliquez sur la mosaïque d’applications, puis cliquez sur **courrier**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="5f3f7-134">Dans la boîte de réception, cliquez sur le message dont l’objet **vos nouvelles clés**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="5f3f7-p103">Dans le dossier courrier indésirable, cliquez sur le message dont l’objet est **Nouveau voyage de site web**. Dans le message, cliquez sur le lien de **ce site** . Vous devriez voir un « Oops ! Page d’Internet Explorer n’a pas pu trouver spamlink.contoso.com. ». Voici le résultat correct, car il n’existe aucune page web à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="5f3f7-p104">Notez que deux de ces e-mails potentiellement malveillants ont été remis avec succès. L’e-mail de **vos nouvelles clés** peut contenir des logiciels malveillants non détectés et l’utilisateur a été autorisé à cliquer sur le lien nuisible dans le message de **Nouveau site web de voyage** .</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="5f3f7-143">Phase 3 : Configuration de stratégies de liens fiables et de pièce jointe fiable pour la protection avancée contre les menaces</span><span class="sxs-lookup"><span data-stu-id="5f3f7-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="5f3f7-144">Dans cette phase, vous créez et configurez une stratégie de pièce jointe fiable pour empêcher les e-mails contenant des pièces jointes potentiellement malveillantes d’être remises et une stratégie de liens fiables pour empêcher les utilisateurs de se diriger vers des URL potentiellement dangereuses.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="5f3f7-145">Sous l’onglet **Accueil de Microsoft Office** , de Microsoft Internet Explorer, cliquez sur la mosaïque de **l’Admin** .</span><span class="sxs-lookup"><span data-stu-id="5f3f7-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="5f3f7-146">Dans la navigation de gauche, cliquez sur **Centre d’administration**, puis sur **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="5f3f7-147">Dans la navigation de gauche de l’onglet de centre d’administration Exchange, cliquez sur **les menaces avancées**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="5f3f7-148">Cliquez sur l’onglet **pièces jointes sûres** , puis cliquez sur le signe plus.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="5f3f7-149">Dans la fenêtre de la **nouvelle stratégie de pièces jointes sûres** , dans la zone **nom**, tapez **Stratégie de pièce jointe sans échec - bloc**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="5f3f7-150">**Réponse inconnue contre les logiciels malveillants de pièces jointes sûres**, cliquez sur **Bloquer**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="5f3f7-151">Pour **Rediriger la pièce jointe sur la détection**, cliquez sur **Activer la redirection** et tapez l’adresse e-mail de votre compte d’administrateur global Office 365.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="5f3f7-p105">Pour **appliqué à**, cliquez sur la flèche vers le bas, puis cliquez sur **le domaine du destinataire est**. Dans la fenêtre, cliquez sur le nom de votre organisation (par exemple, contoso.onmicrosoft.com), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="5f3f7-p106">Cliquez sur **Enregistrer**. Après la mise à jour, vous devez afficher le nouveau et activé la **Stratégie de pièce jointe sans échec - bloc**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="5f3f7-156">Cliquez sur l’onglet **liens sans échec** , puis cliquez sur le signe plus.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="5f3f7-157">Dans la fenêtre de la **nouvelle stratégie de liens sécurisés** , dans la zone **nom**, tapez **Stratégie de lien sécurisé**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="5f3f7-158">**Sélectionnez l’action pour les URL potentiellement malveillants inconnus dans les messages**, cliquez **sur**et sélectionnez **ne pas autoriser les utilisateurs à l’URL d’origine**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="5f3f7-p107">Pour **appliqué à**, cliquez sur la flèche vers le bas, puis cliquez sur **le domaine du destinataire est**. Dans la fenêtre, cliquez sur le nom de votre organisation (par exemple, contoso.onmicrosoft.com), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="5f3f7-p108">Cliquez sur **Enregistrer**. Vous devriez voir le nouveau et activé la **Stratégie de liaison sécurisée**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="5f3f7-163">Phase 4 : Service Protection avancée contre les menaces en action</span><span class="sxs-lookup"><span data-stu-id="5f3f7-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="5f3f7-164">Dans cette phase, vous montrez comment le Service Protection avancée contre les menaces en action traite les e-mails potentiellement malveillants.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="5f3f7-165">À partir de l’instance de Internet Explorer que vous avez utilisé pour envoyer l’e-mail à la Phase 2, de la navigation de gauche, cliquez sur **éléments envoyés.**</span><span class="sxs-lookup"><span data-stu-id="5f3f7-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="5f3f7-166">Cliquez sur le message intitulé **vos nouvelles clés**, cliquez sur la flèche vers le bas, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="5f3f7-167">Pour le nouveau message, dans la zone **à**, tapez l’adresse e-mail du nom global administrateur Office 365 de votre abonnement d’évaluation, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="5f3f7-168">Cliquez sur le message intitulé du **Nouveau site web de voyage**, cliquez sur la flèche vers le bas, cliquez sur **répondre à tous**, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="5f3f7-p109">À partir de l’instance de Internet Explorer qui vous permet de configurer les stratégies d’ATP dans la Phase 3, cliquez sur l’onglet de centre d’administration Exchange, cliquez sur la mosaïque d’applications, puis cliquez sur **courrier**. Vous devriez voir deux nouveaux messages dans la boîte de réception :</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="5f3f7-171">Un intitulé **Fw : vos nouvelles clés**</span><span class="sxs-lookup"><span data-stu-id="5f3f7-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="5f3f7-172">Un intitulé **Fw : nouveau site web de déplacement**</span><span class="sxs-lookup"><span data-stu-id="5f3f7-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="5f3f7-p110">Ouvrez le message électronique intitulé **Fw : nouveau voyage web site** et cliquez sur le lien de **ce site** . Vous devriez voir une page « ce site Web a été classé comme malveillants. ». Cela montre que DAV vous empêche d’accéder au site web potentiellement malveillant.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="5f3f7-177">Dans l’onglet Exchange admin center de Microsoft Internet Explorer, la navigation de gauche, cliquez sur **le flux de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="5f3f7-178">Cliquez sur l’onglet **suivi du message** , puis cliquez sur **Rechercher**.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="5f3f7-p111">Dans la fenêtre de **Résultats de suivi de messages** , double-cliquez sur le message dont l’objet **vos nouvelles clés**. Ce message a été remis à la boîte de réception. Fermez cette fenêtre.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="5f3f7-p112">Double-cliquez sur le message dont l’objet est **Nouveau voyage de site web**. Ce message a été remis à la boîte de réception. Fermez cette fenêtre.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="5f3f7-p113">Double-cliquez sur le message avec l’objet **Fw : vos nouvelles clés**. Notez comment ce message a été traité par l’ATP et ensuite remis à la boîte de réception. Fermez cette fenêtre.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="5f3f7-p114">L’objectif de la stratégie de sécurité de pièces jointes a été de commencer l’analyse des pièces jointes pour le code malveillant. La pièce jointe getKeys.js a été autorisée car il n’a pas été déterminée comme étant malveillants. Cette étape indique que DAV n’a effectué une analyse de la pièce jointe.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="5f3f7-p115">Double-cliquez sur le message avec l’objet **Fw : nouveau site web de voyage**. Notez que ce message a été remis à la boîte de réception.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="5f3f7-193">Vous pouvez désormais utiliser cet environnement pour créer des stratégies et expérimenter le Service Protection avancée contre les menaces.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="5f3f7-194">Cliquez [ici](http://aka.ms/catlgstack) pour une carte visuelle de tous les articles dans la pile d’un Guide de laboratoire de Test Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="5f3f7-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5f3f7-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f3f7-195">See Also</span></span>

[<span data-ttu-id="5f3f7-196">Guides de laboratoire de test d'adoption cloud</span><span class="sxs-lookup"><span data-stu-id="5f3f7-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="5f3f7-197">Environnement de développement/test de configuration de base</span><span class="sxs-lookup"><span data-stu-id="5f3f7-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="5f3f7-198">Environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5f3f7-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="5f3f7-199">DirSync pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="5f3f7-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="5f3f7-200">Application du nuage sécurité pour votre environnement de développement/test d’Office 365</span><span class="sxs-lookup"><span data-stu-id="5f3f7-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="5f3f7-201">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="5f3f7-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="5f3f7-202">Protection contre les menaces avancées des liens sécurisés et les pièces jointes sûres</span><span class="sxs-lookup"><span data-stu-id="5f3f7-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


