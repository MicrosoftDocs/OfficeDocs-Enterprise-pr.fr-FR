---
title: Planification du réseau et de la migration pour Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Contient des liens vers des informations sur la planification de réseau et de test et la migration vers Office 365.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223056"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="9a6f8-103">Planification du réseau et de la migration pour Office 365</span><span class="sxs-lookup"><span data-stu-id="9a6f8-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="9a6f8-104">Cet article contient des liens vers des informations sur la planification et de test de réseau et la migration vers Office 365.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="9a6f8-105">Avant de déployer Office 365 pour la première fois ou de migrer vers Office 365, vous pouvez utiliser les informations figurant dans ces rubriques pour estimer la bande passante dont vous avez besoin, puis pour tester et vérifier que vous disposez de suffisamment de bande passante pour déployer Office 365 ou migrer vers Office 365.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="9a6f8-106">Cet article fait partie de la [planification de réseau et de réglage des performances pour Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="9a6f8-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![Voir Cloud Microsoft Networking d’affiche architectes d’entreprise](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="9a6f8-108">Pour savoir comment optimiser votre réseau pour Office 365 et d’autres plateformes en nuage de Microsoft et services, voir le poster [Microsoft Cloud mise en réseau pour les architectes de l’entreprise](https://aka.ms/cloudarchnetworking) .</span><span class="sxs-lookup"><span data-stu-id="9a6f8-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="9a6f8-109">Estimation des besoins en bande passante réseau</span><span class="sxs-lookup"><span data-stu-id="9a6f8-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="9a6f8-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="9a6f8-110"></span></span>

<span data-ttu-id="9a6f8-p101">L’utilisation d’Office 365 peut augmenter l’utilisation des circuits internet de votre organisation. Il est important de déterminer si la quantité de bande passante disponible est suffisant pour traiter l’augmentation estimée après le déploiement d’Office 365 est entièrement tout en laissant au moins de 20 % la capacité à gérer le plus de jours.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p101">Using Office 365 may increase the utilization of your organization's internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="9a6f8-113">Pour estimer la bande passante, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a6f8-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="9a6f8-p102">Évaluer le nombre de clients qui utiliseront chaque sortie Internet. Permettent de gérer autant que possible la connexion de notre réseau multi-to.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p102">Assess the number of clients that will use each Internet egress. Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="9a6f8-p103">Déterminer les fonctionnalités et les services Office 365 sera disponibles pour les clients à utiliser. Vous aurez probablement des groupes de personnes avec différents services ou les profils d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p103">Determine which Office 365 services and features will be available for clients to use. You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="9a6f8-p104">Mesurer l’utilisation du réseau pour un groupe pilote de clients. Assurez-vous que les clients pilotes sont représentant les profils de personnes dans l’organisation, ainsi que les différents emplacements géographiques différents. Vous pouvez vérification vos résultats par rapport à notre anciens calculateurs pour [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)et [Skype pour les entreprises](https://go.microsoft.com/fwlink/p/?LinkId=321551) ou l' [étude de cas](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) , que nous effectuées sur votre propre réseau.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p104">Measure the network use for a pilot group of clients. Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations. You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="9a6f8-121">Utilisez les mesures à partir du groupe pilote pour tirer les conclusions besoins de l’organisation toute entière et testez de nouveau pour valider les estimations avant d’apporter des modifications à votre réseau.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="9a6f8-122">Tester votre réseau existant</span><span class="sxs-lookup"><span data-stu-id="9a6f8-122">Test your existing network</span></span>
<span data-ttu-id="9a6f8-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="9a6f8-123"></span></span>

 <span data-ttu-id="9a6f8-p105">**Outils réseau.** Tester et valider votre bande passante Internet pour déterminer les contraintes de latence, de chargement et téléchargement. Ces outils vous aideront à déterminer les fonctionnalités de votre réseau pour la migration ainsi qu’une fois que vous avez déployé entièrement.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p105">**Network tools.** Test and validate your Internet bandwidth to determine download, upload, and latency constraints. These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="9a6f8-p106">[L’Analyseur de Message Microsoft](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer est un outil efficace pour résoudre les problèmes réseau. L’Analyseur de message capture, affiche et analyse le trafic de messagerie basée sur le protocole et les messages système. L’Analyseur de message vous permet également d’importer, regrouper et analyser les données à partir des fichiers journaux et de suivi.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p106">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues. Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages. Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="9a6f8-130">[Analyseur de connectivité à distance Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=517243): teste la connectivité dans votre environnement Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="9a6f8-131">Utilisez l' [Assistant de récupération pour Office 365 et de prise en charge de Microsoft](https://diagnostics.office.com/#/Download?env=SOC) pour résoudre les problèmes d’Outlook et Office 365.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="9a6f8-132">Best practices for network planning and improving migration performance for Office 365</span><span class="sxs-lookup"><span data-stu-id="9a6f8-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="9a6f8-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="9a6f8-133"></span></span>

<span data-ttu-id="9a6f8-134">Un peu plus attentivement ces meilleures pratiques pour plus d’informations sur l’amélioration de votre expérience avec Office 365.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="9a6f8-p107">Vous souhaitez commencer à aider vos utilisateurs immédiatement ? Pour obtenir des conseils sur l’utilisation d’Office 365, notamment SharePoint Online, Exchange Online et Lync Online, lorsque votre réseau n’est pas juste coopération, voir [meilleures pratiques pour l’utilisation d’Office 365 sur un réseau lent](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) . Cet article fournit des liens des charges de contenu sur TechNet et Support.office.com pour optimiser votre expérience avec Office 365 et inclut des informations sur les méthodes pour personnaliser vos pages web et comment définir les paramètres d’Internet Explorer pour la meilleure expérience Office 365.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p107">Want to get started helping your users right away? See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating. This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="9a6f8-p108">Lisez les [Principes de connectivité réseau Office 365](https://aka.ms/o365networkingprinciples) pour comprendre les principes de connectivité pour gérer le trafic d’Office 365 en toute sécurité et d’obtenir les meilleures performances possibles. Cet article vous aideront à comprendre les plus récents conseils pour éliminer en toute sécurité Office 365 la connectivité réseau.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p108">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="9a6f8-p109">Améliorer les performances de migration de messagerie en gérant avec soin la planification des mises à jour de Windows. Vous pouvez mettre à jour vos ordinateurs clients par lots et assurez-vous que tous les ordinateurs clients sont mis à jour avant la migration vers Office 365 afin de réguler l’utilisation de la bande passante réseau. Pour plus d’informations, voir [mettre à jour et configurer les bureaux pour Office 365 pour les dernières mises à jour manuellement](https://support.microsoft.com/gp/office-2013-365-update).</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p109">Improve mail migration performance by carefully managing the schedule for Windows Updates. You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth. For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="9a6f8-p110">Le trafic réseau de Office 365 effectue mieux lorsqu’il a traité comme un service Internet approuvé et autorisé à contourner le filtrage traditionnel et analyse par certaines organisations sur le trafic réseau vers les services Internet non approuvés. Cela inclut généralement la suppression sortant traitement telles que l’authentification utilisateur du proxy et l’inspection des paquets, tout en garantissant local sortant vers Internet avec la traduction d’adresses réseau (NAT) approprié et suffisamment gérer l’augmentation de la capacité de bande passante demandes de réseau. Pour plus d’instructions sur la configuration de votre réseau pour gérer Office 365 en tant que service Internet approuvé sur votre réseau, reportez-vous aux [points de terminaison de gestion Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p110">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services. This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests. Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="9a6f8-p111">Vérifiez les [points de terminaison de gestion Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Le trafic supplémentaire sur le point d’Office 365 entraîne une augmentation des connexions sortantes proxy ainsi que d’une augmentation du trafic sécurisé sur TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p111">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="9a6f8-p112">Si votre proxy sortant nécessitent l’authentification des utilisateurs, vous pouvez rencontrer une perte de fonctionnalité ou de connectivité lente. Ignorer la nécessité d’authentification pour les domaines d’Office 365 peut réduire cette charge.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p112">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="9a6f8-p113">Si vous disposez d’un grand nombre de calendriers et de boîtes aux lettres partagés, vous pourrez voir une augmentation du nombre de connexions à partir d’Outlook vers Exchange. Par exemple, le client Outlook peut ouvrir jusqu’à deux connexions supplémentaires pour chaque calendrier partagé en cours d’utilisation. Dans ce cas, assurez-vous que le proxy sortant peut gérer les connexions, ou contournez le proxy pour les connexions à Office 365 pour Outlook.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p113">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two additional connections for each shared calendar in use. In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="9a6f8-p114">Déterminer le nombre maximal de périphériques pris en charge pour une adresse IP publique et comment équilibrer la charge entre plusieurs adresses IP. Pour plus d’informations, voir [prise en charge NAT avec Office 365](nat-support-with-office-365.md).</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p114">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="9a6f8-p115">Si vous êtes inspecter les connexions sortantes sur les ordinateurs sur votre réseau, en ignorant ce filtrage aux domaines Office 365 améliorer connectivité et performances. En outre, en ignorant inspection sortante souvent élimine le besoin d’une seule sortie Internet et permet local sortant Internet pour les demandes du réseau Office 365 destiné.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p115">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="9a6f8-p116">Certains clients de trouver les paramètres de réseau interne peuvent affecter les performances. Paramètres de taille de l’unité de transmission maximale, réseau la négociation automatique ou la détection automatique et sous-optimal itinéraires vers Internet sont des emplacements communs à consulter.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-p116">Some customers find internal network settings may affect performance. Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="9a6f8-159">Référence de planification réseau pour Office 365</span><span class="sxs-lookup"><span data-stu-id="9a6f8-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="9a6f8-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="9a6f8-160"></span></span>

<span data-ttu-id="9a6f8-161">Les rubriques suivantes contiennent des informations de référence détaillées sur Office 365 réseau.</span><span class="sxs-lookup"><span data-stu-id="9a6f8-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="9a6f8-162">Gestion des points de terminaison Office 365</span><span class="sxs-lookup"><span data-stu-id="9a6f8-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="9a6f8-163">Connectivité client</span><span class="sxs-lookup"><span data-stu-id="9a6f8-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="9a6f8-164">Réseaux de distribution de contenu</span><span class="sxs-lookup"><span data-stu-id="9a6f8-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="9a6f8-165">Enregistrements de nom DNS externes pour Office 365</span><span class="sxs-lookup"><span data-stu-id="9a6f8-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="9a6f8-166">Prise en charge du protocole IPv6 dans les services Office 365</span><span class="sxs-lookup"><span data-stu-id="9a6f8-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="9a6f8-167">Principes de connectivité réseau Office 365</span><span class="sxs-lookup"><span data-stu-id="9a6f8-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="9a6f8-168">Académie virtuelle Microsoft : Gestion des performances Office 365</span><span class="sxs-lookup"><span data-stu-id="9a6f8-168">Microsoft Virtual Academy: Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [<span data-ttu-id="9a6f8-169">Mise en réseau vidéo Office 365 Forum aux Questions (FAQ)</span><span class="sxs-lookup"><span data-stu-id="9a6f8-169">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="9a6f8-170">Planifier les périphériques réseau qui se connectent aux services Office 365</span><span class="sxs-lookup"><span data-stu-id="9a6f8-170">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="9a6f8-171">Conseillers de déploiement pour les services Office 365</span><span class="sxs-lookup"><span data-stu-id="9a6f8-171">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

