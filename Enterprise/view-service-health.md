---
title: Comment vérifier l’intégrité du service Office 365
ms.author: kfollis
author: kfollis
manager: scotv
ms.date: 6/15/2018
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
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Afficher l’état des services Office 365 avant d’appeler la prise en charge pour voir s’il existe une interruption de service active
ms.openlocfilehash: d01fe8e269ace922ab92cca779d6f8fea8b6802e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540387"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="611cf-103">Comment vérifier l’intégrité du service Office 365</span><span class="sxs-lookup"><span data-stu-id="611cf-103">How to check Office 365 service health</span></span>

<span data-ttu-id="611cf-p101">Vous pouvez afficher l’intégrité d’Office 365, Yammer, Microsoft Dynamics CRM et services de cloud computing Microsoft Intune sur Office 365 ** d’intégrité du Service ** page dans le centre d’administration. Si vous rencontrez des problèmes avec un service en nuage, vous pouvez vérifier l’intégrité du service pour déterminer s’il s’agit d’un problème connu avec une résolution en cours avant d’appeler le support ou consacrez à la résolution des problèmes de temps.</span><span class="sxs-lookup"><span data-stu-id="611cf-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 ** Service health ** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="611cf-106">Comment vérifier l’intégrité du service</span><span class="sxs-lookup"><span data-stu-id="611cf-106">How to check service health</span></span>

1. <span data-ttu-id="611cf-107">Accédez à [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) et la connexion avec un compte d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="611cf-107">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="611cf-p102">Personnes qui sont affectées à l’administrateur global ou le rôle d’administrateur de service peuvent afficher l’intégrité du service. Pour permettre à Exchange, SharePoint et Skype pour les administrateurs d’entreprise afficher l’intégrité du service, ils doivent également être affectés le rôle d’administrateur de Service.</span><span class="sxs-lookup"><span data-stu-id="611cf-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span> 
  
2. <span data-ttu-id="611cf-p103">Pour ouvrir l’intégrité du service, dans le centre d’administration, accédez à **la santé** \> **intégrité du Service**, ou cliquez sur le fonctionnement du Service de la carte du tableau de bord d’accueil. La carte de tableau de bord indique s’il existe un problème de service active et les liens vers la page de l’intégrité du service détaillées.</span><span class="sxs-lookup"><span data-stu-id="611cf-p103">To open service health, in the admin center, go to **Health** \> **Service health**, or click the Service health card on the Home dashboard. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Carte de tableau de bord pour l’intégrité du service](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="611cf-113">L’état d’intégrité de chaque service cloud s’affiche sous forme de tableau avec une icône pour indiquer les états possibles.</span><span class="sxs-lookup"><span data-stu-id="611cf-113">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="611cf-114">Vous pouvez également utiliser l' [application d’administration d’Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) sur votre appareil mobile pour afficher l’intégrité du Service, qui est idéal pour garder le contact avec les notifications push.</span><span class="sxs-lookup"><span data-stu-id="611cf-114">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="611cf-115">Afficher les détails de l’intégrité du service validées</span><span class="sxs-lookup"><span data-stu-id="611cf-115">View details of posted service health</span></span>

<span data-ttu-id="611cf-p104">Dans l’affichage par défaut, tous les services et leur état d’intégrité actuel sont affichés. Pour filtrer l’affichage aux services actuellement rencontre un incident, sélectionnez **Incidents** dans la barre ombrée située à gauche. **Conseils** de sélection affiche uniquement les services qui possèdent un avis publié. À partir de l’affichage de **tous les services** , en cliquant sur l’état du service affiché ouvrira une vue récapitulative de l’avis ou un incident.</span><span class="sxs-lookup"><span data-stu-id="611cf-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![Affichage des problèmes en cours de fonctionnement du service](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="611cf-121">L’avis ou le résumé de l’incident fournit les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="611cf-121">The advisory or incident summary provides the following information:</span></span> 
  
![Capture d’écran étiquetage les champs dans un avis de service](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="611cf-123">Un problème identificateur et résumé instruction du problème.</span><span class="sxs-lookup"><span data-stu-id="611cf-123">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="611cf-p105">L’état actuel. Voir les définitions d’état dans cet article pour obtenir une explication de chaque état potentiel.</span><span class="sxs-lookup"><span data-stu-id="611cf-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="611cf-126">Une description de la manière dont ce problème peut affecter les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="611cf-126">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="611cf-p106">L’heure à laquelle le problème a été démarré et la dernière fois que le message de l’intégrité du service a été mis à jour. Pendant toute la durée d’un problème nous envoyer des messages fréquents pour vous informer de la progression que nous faisons dans l’application d’une solution.</span><span class="sxs-lookup"><span data-stu-id="611cf-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="611cf-129">Sélectionnez le lien **Afficher les détails** pour afficher plus d’informations sur le problème, y compris l’historique de tous les messages publiés pendant que nous travailler sur une solution.</span><span class="sxs-lookup"><span data-stu-id="611cf-129">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="611cf-130">Détails d’intégrité du service de traduction</span><span class="sxs-lookup"><span data-stu-id="611cf-130">Translate service health details</span></span>

<span data-ttu-id="611cf-p107">Étant donné que des explications service d’intégrité sont validées en temps réel, ils ne sont pas traduits automatiquement à votre langue et les détails d’un événement de service sont en anglais uniquement. Pour traduire l’explication, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="611cf-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="611cf-133">Accédez au [traducteur](https://www.bing.com/translator/).</span><span class="sxs-lookup"><span data-stu-id="611cf-133">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="611cf-p108">Dans la page **intégrité du Service** , sélectionnez un avis ou un incident. Sous **Afficher les détails**, copiez le texte sur le problème.</span><span class="sxs-lookup"><span data-stu-id="611cf-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="611cf-136">Dans Translator, collez le texte, puis choisissez **traduire**.</span><span class="sxs-lookup"><span data-stu-id="611cf-136">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="611cf-137">Définitions</span><span class="sxs-lookup"><span data-stu-id="611cf-137">Definitions</span></span>

<span data-ttu-id="611cf-p109">La plupart des services de synchronisation s’affiche comme intègre sans informations complémentaires. Lorsqu’un service rencontre un problème, le problème est identifié comme un avis ou un incident et indique l’état actuel.</span><span class="sxs-lookup"><span data-stu-id="611cf-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="611cf-p110">Planifié la gestion des événements ne sont pas affichés dans le fonctionnement du service. Vous pouvez suivre les événements de maintenance prévues par les mises à jour avec le **Centre de messages**. Filtre pour les messages sont considérés comme Plan changement permettant de savoir quand la modification sur le point d’arriver, comment préparer et son effet. Pour plus d’informations, consultez la rubrique [Centre de messages dans Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) .</span><span class="sxs-lookup"><span data-stu-id="611cf-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="611cf-144">Incidents et conseils</span><span class="sxs-lookup"><span data-stu-id="611cf-144">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Icône d’information pour avis](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="611cf-p111">Si un service a un avis indiqué, nous avons pris connaissance d’un problème qui affecte certains utilisateurs, mais le service est toujours disponible. Dans un avis, il est souvent une solution de contournement à ce problème, le problème peut être intermittent ou impact étendue et l’utilisateur est limité.</span><span class="sxs-lookup"><span data-stu-id="611cf-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Icône de point d’exclamation d’incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="611cf-p112">Si un service a un incident actif indiqué, il s’agit d’un problème critique et le service ou une fonction principale du service n’est pas disponible. Par exemple, utilisateurs Impossible d’envoyer et recevoir du courrier électronique ou Impossible de connexion. Incidents ont un impact notable aux utilisateurs. Lorsqu’il existe un incident en cours, nous fournissons des mises à jour concernant l’enquête, des efforts d’atténuation et de confirmation de la solution dans le tableau de bord de l’intégrité de Service.</span><span class="sxs-lookup"><span data-stu-id="611cf-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="611cf-153">Définitions d’état</span><span class="sxs-lookup"><span data-stu-id="611cf-153">Status definitions</span></span>

<span data-ttu-id="611cf-154">| |</span><span class="sxs-lookup"><span data-stu-id="611cf-154"></span></span>
|<span data-ttu-id="611cf-155">**État**</span><span class="sxs-lookup"><span data-stu-id="611cf-155">**Status**</span></span>|<span data-ttu-id="611cf-156">**Définition**</span><span class="sxs-lookup"><span data-stu-id="611cf-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="611cf-157">Étude</span><span class="sxs-lookup"><span data-stu-id="611cf-157">Investigating</span></span>  <br/> |<span data-ttu-id="611cf-158">Nous vous un problème potentiel et rassemblez plus d’informations sur ce qui se passe l’étendue de l’impact.</span><span class="sxs-lookup"><span data-stu-id="611cf-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span>  <br/> |
|<span data-ttu-id="611cf-159">Dégradation du service</span><span class="sxs-lookup"><span data-stu-id="611cf-159">Service degradation</span></span>  <br/> |<span data-ttu-id="611cf-p113">Nous avons vérifié qu’il existe un problème qui peut-être affecter l’utilisation d’un service ou la fonctionnalité. Vous pouvez voir ce statut si un service ne fonctionne plus lentement que d’habitude, il existe des interruptions intermittentes, ou si une fonctionnalité ne fonctionne pas, par exemple.</span><span class="sxs-lookup"><span data-stu-id="611cf-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span>  <br/> |
|<span data-ttu-id="611cf-162">Interruption de service</span><span class="sxs-lookup"><span data-stu-id="611cf-162">Service interruption</span></span>  <br/> |<span data-ttu-id="611cf-p114">Vous verrez ce statut si nous déterminons qu’un problème affecte la possibilité pour les utilisateurs d’accéder au service. Dans ce cas, le problème est important et peut être reproduit de façon cohérente.</span><span class="sxs-lookup"><span data-stu-id="611cf-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span>  <br/> |
|<span data-ttu-id="611cf-165">Restauration d’un service</span><span class="sxs-lookup"><span data-stu-id="611cf-165">Restoring service</span></span>  <br/> |<span data-ttu-id="611cf-166">La cause du problème a été identifiée, nous savons quelle action corrective effectuer et en mettant le service à un état sain.</span><span class="sxs-lookup"><span data-stu-id="611cf-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span>  <br/> |
|<span data-ttu-id="611cf-167">Récupération d’étendue</span><span class="sxs-lookup"><span data-stu-id="611cf-167">Extended recovery</span></span>  <br/> |<span data-ttu-id="611cf-p115">Cet état indique que les actions correctives sont en cours pour restaurer le service pour la plupart des utilisateurs mais prendront un certain temps pour atteindre tous les systèmes concernés. Vous pouvez également voir ce statut si nous avons apporté de correction pour réduire l’impact pendant que nous attendons pour appliquer un correctif permanent temporaire.</span><span class="sxs-lookup"><span data-stu-id="611cf-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span>  <br/> |
|<span data-ttu-id="611cf-170">Enquête suspendue</span><span class="sxs-lookup"><span data-stu-id="611cf-170">Investigation suspended</span></span>  <br/> |<span data-ttu-id="611cf-p116">Si notre analyse détaillée d’un problème potentiel se traduit par une demande pour plus d’informations à partir de clients pour nous permettre d’approfondir, vous voyez ce statut. Si vous devez agir, nous allons vous permettent de savoir quelles données ou des journaux, nous avons besoin.</span><span class="sxs-lookup"><span data-stu-id="611cf-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span>  <br/> |
|<span data-ttu-id="611cf-173">Service restauré</span><span class="sxs-lookup"><span data-stu-id="611cf-173">Service restored</span></span>  <br/> |<span data-ttu-id="611cf-p117">Nous avons confirmé que les actions correctives a résolu le problème sous-jacent et le service a été restaurée à un état sain. Pour déterminer la cause du problème, afficher les détails du problème.</span><span class="sxs-lookup"><span data-stu-id="611cf-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span>  <br/> |
   
## <a name="history"></a><span data-ttu-id="611cf-176">Historique</span><span class="sxs-lookup"><span data-stu-id="611cf-176">History</span></span>

<span data-ttu-id="611cf-p118">Intégrité du service vous permet de consulter l’état d’intégrité actuel et afficher l’historique des incidents et conseils de service au cours des 30 derniers jours. Pour afficher la derniers d’intégrité de tous les services, sélectionnez **Afficher l’historique** sur la page **intégrité du Service** .</span><span class="sxs-lookup"><span data-stu-id="611cf-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Afficher le lien vers l’historique d’intégrité](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="611cf-180">Une liste de tous les messages de l’intégrité du service validées dans la période sélectionnée est affichée, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="611cf-180">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![Afficher l’historique d’intégrité de service](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="611cf-p119">Vous pouvez afficher l’historique des résultats pour les 7 derniers jours ou cours des 30 derniers jours. Sélectionnez une ligne pour afficher plus d’informations sur ce problème.</span><span class="sxs-lookup"><span data-stu-id="611cf-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="611cf-184">Pour plus d’informations sur notre engagement à temps de fonctionnement, voir [operations Transparent d’Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span><span class="sxs-lookup"><span data-stu-id="611cf-184">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="611cf-185">Laisser des commentaires</span><span class="sxs-lookup"><span data-stu-id="611cf-185">Leave feedback</span></span>

<span data-ttu-id="611cf-p120">Notre objectif est de vous assurer que les informations vous concernant un problème en cours soient utile, précise et en temps voulu. Pour nous indiquer comment nous faisons, sélectionnez un nombre d’étoiles. Une fois que vous donnez une note de 1 à 5 étoiles, vous pouvez donner des commentaires sur tous les détails. Nous allons utiliser vos commentaires afin d’affiner notre système de l’intégrité du service.</span><span class="sxs-lookup"><span data-stu-id="611cf-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Formulaire de commentaires pour les problèmes d’intégrité du service](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="611cf-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="611cf-191">See also</span></span>

[<span data-ttu-id="611cf-192">Rapports sur les activités dans le centre d’administration d’Office 365</span><span class="sxs-lookup"><span data-stu-id="611cf-192">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

