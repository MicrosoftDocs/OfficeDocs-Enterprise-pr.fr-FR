---
title: Vérifier l'état du service Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Afficher l'état d'intégrité des services Office 365 avant d'appeler la prise en charge pour déterminer s'il existe une interruption de service Active
ms.openlocfilehash: 7a8d6c028caa72d332a51123233b2d0642311da0
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085293"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="d0159-103">Vérifier l'état du service Office 365</span><span class="sxs-lookup"><span data-stu-id="d0159-103">How to check Office 365 service health</span></span>

<span data-ttu-id="d0159-p101">Vous pouvez afficher l'état de santé d'Office 365, de Yammer, de Microsoft Dynamics CRM et des services Cloud Microsoft Intune sur la page d' **État du service** Office 365 dans le centre d'administration. Si vous rencontrez des problèmes avec un service Cloud, vous pouvez vérifier l'état du service pour déterminer s'il s'agit d'un problème connu avec une résolution en cours avant d'appeler le support technique ou de consacrer du temps à la résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="d0159-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 **Service health** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 

<span data-ttu-id="d0159-106">Si vous ne parvenez pas à vous connecter au service portail de service, vous pouvez utiliser la [page État du service](https://status.office365.com) pour vérifier les problèmes connus qui vous empêchent de vous connecter à votre client.</span><span class="sxs-lookup"><span data-stu-id="d0159-106">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="d0159-107">Vérifier l'état du service</span><span class="sxs-lookup"><span data-stu-id="d0159-107">How to check service health</span></span>

1. <span data-ttu-id="d0159-108">Accédez à [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) et connectez-vous avec un compte d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="d0159-108">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="d0159-p102">Les personnes dotées d'un rôle d'administrateur général ou d'administrateur de service peuvent afficher l'état du service. Pour afficher l'état du service, les administrateurs Exchange, SharePoint et Skype Entreprise doivent aussi disposer d'un rôle d'administrateur portant sur ce service.</span><span class="sxs-lookup"><span data-stu-id="d0159-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span>
  
2. <span data-ttu-id="d0159-p103">Pour ouvrir l'état du service, dans le centre d'administration, accédez à intégrité du**service**d' **intégrité** > ou cliquez sur la carte d' **intégrité des services** dans le tableau de **bord d'accueil**. La carte de tableau de bord indique s'il existe un problème de service actif et des liens vers la page d'état détaillé du service.</span><span class="sxs-lookup"><span data-stu-id="d0159-p103">To open service health, in the admin center, go to **Health** > **Service health**, or click the **Service health card** on the **Home dashboard**. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="d0159-114">L'état d'intégrité de chaque service cloud apparaît dans un tableau avec une icône pour indiquer les différents états possibles.</span><span class="sxs-lookup"><span data-stu-id="d0159-114">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="d0159-115">Vous pouvez également utiliser l'[application Office 365 Admin](https://go.microsoft.com/fwlink/p/?linkid=627216) sur votre appareil mobile pour afficher l'état du service, ce qui constitue un excellent moyen de vous tenir informé des notifications Push.</span><span class="sxs-lookup"><span data-stu-id="d0159-115">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="d0159-116">Afficher les détails relatifs à l'état du service publié</span><span class="sxs-lookup"><span data-stu-id="d0159-116">View details of posted service health</span></span>

<span data-ttu-id="d0159-p104">Dans l'affichage par défaut, tous les services et leur état d'intégrité actuel sont affichés. Pour filtrer votre vue sur les services rencontrant actuellement un incident, sélectionnez **incidents** dans la barre ombrée sur la gauche. La sélection des **avis** affiche uniquement les services pour lesquels un avis a déjà été publié. Dans l'affichage **tous les services** , cliquez sur l'état du service affiché pour ouvrir une vue récapitulative de l'avis ou de l'incident.</span><span class="sxs-lookup"><span data-stu-id="d0159-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="d0159-122">Le récapitulatif de l'avis ou de l'incident fournit les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d0159-122">The advisory or incident summary provides the following information:</span></span> 
  
![Capture d'écran des champs d'un avis de service](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="d0159-124">Identifiant et récapitulatif du problème.</span><span class="sxs-lookup"><span data-stu-id="d0159-124">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="d0159-p105">État actuel. Reportez-vous aux définitions d'état de cet article pour plus d'informations sur chaque état possible.</span><span class="sxs-lookup"><span data-stu-id="d0159-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="d0159-127">Description de la manière dont ce problème peut affecter les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d0159-127">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="d0159-p106">Heure à laquelle le problème s'est manifesté pour la première fois et heure à laquelle le message d'état du service a été mis à jour. Pendant toute la durée d'un problème, nous publions de fréquents messages pour vous informer de notre progression à y remédier.</span><span class="sxs-lookup"><span data-stu-id="d0159-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="d0159-130">Sélectionnez le lien **Afficher les détails** pour afficher plus d'informations sur ce problème, y compris l'historique de tous les messages publiés lors de sa résolution.</span><span class="sxs-lookup"><span data-stu-id="d0159-130">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="d0159-131">Traduire les détails d'état du service</span><span class="sxs-lookup"><span data-stu-id="d0159-131">Translate service health details</span></span>

<span data-ttu-id="d0159-p107">Les explications relatives à l'état du service étant publiées en temps réel, elles ne sont pas traduites automatiquement dans votre langue, et les détails d'un événement de service sont uniquement disponibles en anglais. Pour traduire ces explications, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d0159-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="d0159-134">Accédez à [Translator](https://www.bing.com/translator/).</span><span class="sxs-lookup"><span data-stu-id="d0159-134">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="d0159-p108">Sur la page **État du Service**, sélectionnez un avis ou un incident. Sous **Afficher les détails**, copiez le texte relatif au problème.</span><span class="sxs-lookup"><span data-stu-id="d0159-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="d0159-137">Dans Translator, collez le texte, puis sélectionnez **Traduire**.</span><span class="sxs-lookup"><span data-stu-id="d0159-137">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="d0159-138">Définitions</span><span class="sxs-lookup"><span data-stu-id="d0159-138">Definitions</span></span>

<span data-ttu-id="d0159-p109">En règle générale, les services apparaissent comme intègres, sans autres informations. Lorsqu'un service présente un problème, ce problème est identifié sous forme d'avis ou d'incident et son état actuel s'affiche.</span><span class="sxs-lookup"><span data-stu-id="d0159-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="d0159-p110">Les événements de maintenance planifiée ne s'affichent pas dans l'état du service. Le **Centre de messages** vous permet de suivre les événements de maintenance planifiée. Filtrez les messages par Planification des modifications pour connaître le moment où une modification interviendra, son effet et comment vous y préparer. Pour plus d'informations, voir [Centre de messages dans Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093).</span><span class="sxs-lookup"><span data-stu-id="d0159-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="d0159-145">Incidents et avis</span><span class="sxs-lookup"><span data-stu-id="d0159-145">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="d0159-p111">Un service accompagné d'un avis indique que nous sommes conscients du problème qui affecte certains utilisateurs, mais que ce service est toujours disponible. Un avis propose souvent une solution de contournement du problème, qui peut intermittent ou limité en termes d'impact sur les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d0159-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="d0159-p112">Si un service présente un incident actif, cela signifie qu'il s'agit d'un problème critique et que le service ou une de ses fonctions principales n'est pas disponible. Par exemple, les utilisateurs peuvent ne pas être en mesure d'envoyer et de recevoir des e-mails ni de se connecter. Les incidents ont un impact significatif sur les utilisateurs. En cas d'incident, nous publions des mises à jour relatives à son examen, aux efforts déployés pour y remédier, et sa résolution apparaît dans le tableau de bord d'état du service.</span><span class="sxs-lookup"><span data-stu-id="d0159-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="d0159-154">Définitions des états</span><span class="sxs-lookup"><span data-stu-id="d0159-154">Status definitions</span></span>

|<span data-ttu-id="d0159-155">**État**</span><span class="sxs-lookup"><span data-stu-id="d0159-155">**Status**</span></span>|<span data-ttu-id="d0159-156">**Définition**</span><span class="sxs-lookup"><span data-stu-id="d0159-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d0159-157">**Examen en cours**</span><span class="sxs-lookup"><span data-stu-id="d0159-157">**Investigating**</span></span> | <span data-ttu-id="d0159-158">Nous sommes conscients d'un problème potentiel et recueillons des informations sur ce problème et son impact.</span><span class="sxs-lookup"><span data-stu-id="d0159-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="d0159-159">**Dégradation du service**</span><span class="sxs-lookup"><span data-stu-id="d0159-159">**Service degradation**</span></span> | <span data-ttu-id="d0159-p113">Nous avons identifié un problème susceptible d'affecter l'utilisation d'un service ou d'une fonctionnalité. Cet état peut s'afficher si un service s'avère plus lent qu'habituellement, s'il présente des interruptions intermittentes ou si une fonctionnalité est défaillante, par exemple.</span><span class="sxs-lookup"><span data-stu-id="d0159-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="d0159-162">**Interruption du service**</span><span class="sxs-lookup"><span data-stu-id="d0159-162">**Service interruption**</span></span> | <span data-ttu-id="d0159-p114">Cet état s'affiche si nous identifions un problème qui affecte la capacité des utilisateurs à accéder au service. Dans ce cas, le problème est significatif et peut se répéter.</span><span class="sxs-lookup"><span data-stu-id="d0159-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="d0159-165">**Service en cours de restauration**</span><span class="sxs-lookup"><span data-stu-id="d0159-165">**Restoring service**</span></span> | <span data-ttu-id="d0159-166">La cause du problème a été identifiée, nous connaissons l'action corrective à appliquer et le service est en cours de restauration.</span><span class="sxs-lookup"><span data-stu-id="d0159-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="d0159-167">**Récupération étendue**</span><span class="sxs-lookup"><span data-stu-id="d0159-167">**Extended recovery**</span></span> | <span data-ttu-id="d0159-p115">Cet état indique qu'une action corrective est en cours afin de restaurer le service pour la plupart des utilisateurs, mais qu'il faudra un certain temps pour qu'elle s'applique à tous les systèmes concernés. Cet état peut également s'afficher si nous proposons un correctif temporaire visant à réduire l'impact du problème en attendant un correctif définitif.</span><span class="sxs-lookup"><span data-stu-id="d0159-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="d0159-170">**Examen suspendu**</span><span class="sxs-lookup"><span data-stu-id="d0159-170">**Investigation suspended**</span></span> | <span data-ttu-id="d0159-p116">Cet état s'affiche si l'examen détaillé d'un problème potentiel implique plus d'informations de la part des clients afin de nous permettre de mieux l'étudier. Dans ce cas, nous vous indiquerons les données ou journaux dont nous avons besoin.</span><span class="sxs-lookup"><span data-stu-id="d0159-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="d0159-173">**Service restauré**</span><span class="sxs-lookup"><span data-stu-id="d0159-173">**Service restored**</span></span> | <span data-ttu-id="d0159-p117">L'action corrective a permis de résoudre le problème sous-jacent et le service a été restauré. Pour en savoir plus, consultez les détails relatifs au problème.</span><span class="sxs-lookup"><span data-stu-id="d0159-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="d0159-176">**Publication du rapport post-incident**</span><span class="sxs-lookup"><span data-stu-id="d0159-176">**Post-incident report published**</span></span> | <span data-ttu-id="d0159-177">Nous avons publié un rapport de l'incident post pour un problème spécifique qui inclut les informations de la cause première et les étapes suivantes pour éviter que le problème ne se reproduise.</span><span class="sxs-lookup"><span data-stu-id="d0159-177">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
   
## <a name="history"></a><span data-ttu-id="d0159-178">Historique</span><span class="sxs-lookup"><span data-stu-id="d0159-178">History</span></span>

<span data-ttu-id="d0159-p118">L'état du service vous permet de consulter l'état actuel de l'intégrité et d'afficher l'historique des avis de service et des incidents ayant influencé votre client au cours des 30 derniers jours. Pour afficher l'intégrité passée de tous les services, sélectionnez **afficher l'historique** sur la page **État du service** .</span><span class="sxs-lookup"><span data-stu-id="d0159-p118">Service health lets you look at current health status and view the history of any service advisories and incidents that have impacted your tenant in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="d0159-182">La liste de tous les messages d'état des services publiés au cours de la période sélectionnée s'affiche comme suit :</span><span class="sxs-lookup"><span data-stu-id="d0159-182">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="d0159-p119">Vous pouvez afficher l'historique des intégrités pendant les 7 derniers jours ou les 30 derniers jours. Sélectionnez une ligne pour afficher plus de détails sur ce problème.</span><span class="sxs-lookup"><span data-stu-id="d0159-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="d0159-186">Pour plus d'informations sur notre engagement en matière de disponibilité, consultez la rubrique [opérations transparentes d'Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span><span class="sxs-lookup"><span data-stu-id="d0159-186">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="d0159-187">Laisser un commentaire</span><span class="sxs-lookup"><span data-stu-id="d0159-187">Leave feedback</span></span>

<span data-ttu-id="d0159-p120">Nous mettons tout en œuvre pour que les informations que nous vous fournissons soient opportunes, précises et utiles. Pour évaluer nos interventions, sélectionnez un nombre d'étoiles. Après nous avoir attribué une note de 1 à 5 étoiles, vous pouvez envoyer des commentaires sur des détails spécifiques. Nous utiliserons vos commentaires pour affiner notre système d'état des services.</span><span class="sxs-lookup"><span data-stu-id="d0159-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="d0159-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0159-193">See also</span></span>

[<span data-ttu-id="d0159-194">Rapports d'activité dans le Centre d'administration Office 365</span><span class="sxs-lookup"><span data-stu-id="d0159-194">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

