---
title: Planifier les périphériques réseau qui se connectent aux services Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Résumé : Décrit les éléments à prendre en compte pour la capacité réseau, les accélérateurs WAN et les périphériques d’équilibrage de charge qui sont utilisés pour se connecter à Office 365.'
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933121"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="c59b4-103">Planifier les périphériques réseau qui se connectent aux services Office 365</span><span class="sxs-lookup"><span data-stu-id="c59b4-103">Plan for network devices that connect to Office 365 services</span></span>

 <span data-ttu-id="c59b4-104">**Résumé** : Décrit les éléments à prendre en compte pour la capacité réseau, les accélérateurs WAN et les périphériques d’équilibrage de charge qui sont utilisés pour se connecter à Office 365.</span><span class="sxs-lookup"><span data-stu-id="c59b4-104">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>
  
<span data-ttu-id="c59b4-p101">Matériel réseau peut-être comporter des limites du nombre de sessions simultanées qui sont prises en charge. Pour les organisations ayant plus de 2 000 utilisateurs, nous vous recommandons de surveiller les leurs périphériques réseau pour vous assurer qu’ils sont capables de traiter le trafic du service Office 365 supplémentaire. SNMP Simple Network Management Protocol () logiciels de surveillance peuvent vous aider à effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="c59b4-p101">Some network hardware may have limitations on the number of concurrent sessions that are supported. For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic. Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="c59b4-108">Cet article fait partie de la [planification de réseau et de réglage des performances pour Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="c59b4-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="c59b4-p102">Les paramètres de proxy Internet sortant également affectent la connectivité aux services Office 365 pour les applications clientes sur site. Vous devez également configurer vos périphériques de proxy réseau pour autoriser les connexions pour les applications et les URL de services de cloud Microsoft. Chaque organisation est différente. Pour avoir une idée de la façon dont Microsoft gère ce processus et la quantité de bande passante que nous provisionner, [Lisez l’étude de cas](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span><span class="sxs-lookup"><span data-stu-id="c59b4-p102">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications. You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications. Every organization is different. To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="c59b4-113">Le Skype suivante pour les articles d’aide Business ont plus d’informations sur Skype pour les paramètres d’entreprise :</span><span class="sxs-lookup"><span data-stu-id="c59b4-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="c59b4-114">Dépannage Skype pour les erreurs de connexion Business Online pour les administrateurs</span><span class="sxs-lookup"><span data-stu-id="c59b4-114">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="c59b4-115">Vous ne pouvez pas vous connecter à Skype pour les entreprises, ou certaines fonctionnalités ne fonctionnent pas, car un pare-feu local bloque la connexion</span><span class="sxs-lookup"><span data-stu-id="c59b4-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="c59b4-116">Alors que la plupart de ces paramètres sont Skype pour spécifiques à l’entreprise, les instructions générales sur la configuration du réseau sont utile pour tous les services Office 365.</span><span class="sxs-lookup"><span data-stu-id="c59b4-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="c59b4-117">Détermination de la capacité réseau</span><span class="sxs-lookup"><span data-stu-id="c59b4-117">Determining Network Capacity</span></span>

<span data-ttu-id="c59b4-p103">Chaque périphérique réseau existant sur une connexion présente une limite de capacité, notamment les cartes réseau de serveur et de client, les routeurs, les commutateurs et les concentrateurs qui les relient. Une capacité réseau adéquate signifie qu'aucun de ces périphériques réseau n'est saturé. Il est essentiel de contrôler l'activité réseau pour s'assurer que les charges réelles sur chaque périphérique réseau sont inférieures à leur capacité maximale. La capacité réseau a une incidence sur les performances des périphériques proxy.</span><span class="sxs-lookup"><span data-stu-id="c59b4-p103">Every network device that exists on a connection has its capacity limit. These devices include the client and server network adapters, routers, switches, and hubs that interconnect them. Adequate network capacity means that none of them are saturated. Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity. Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="c59b4-p104">Dans la plupart des cas, la bande passante Internet définit la limite pour la quantité de trafic. Faibles performances pendant les heures de pointe du trafic est probablement dû à une utilisation excessive de la liaison Internet. Cette situation s’applique également à un scénario de succursale, où les ordinateurs de serveur proxy branch office sont connectés au périphérique proxy aux sièges sociaux de la branche via une liaison lente de réseau étendu (WAN).</span><span class="sxs-lookup"><span data-stu-id="c59b4-p104">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic. Weak performance during peak traffic hours is probably caused by excessive use of the Internet link. This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="c59b4-p105">Pour tester la capacité du réseau, surveiller l’activité du réseau sur l’interface réseau de proxy. S’il est plus de 75 % de la bande passante maximale d’une interface réseau, envisagez d’augmenter la bande passante de l’infrastructure réseau qui est insuffisant. Ou bien, envisagez d’utiliser des fonctionnalités avancées, telles que la compression HTTP.</span><span class="sxs-lookup"><span data-stu-id="c59b4-p105">To test network capacity, monitor the network activity on the proxy network interface. If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate. Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="c59b4-129">Accélérateurs de réseau étendu</span><span class="sxs-lookup"><span data-stu-id="c59b4-129">WAN Accelerators</span></span>

<span data-ttu-id="c59b4-p106">Si votre organisation utilise des équipements de proxy de l’accélération de réseau (étendu WAN) étendu, vous pouvez rencontrer des problèmes lorsque vous accédez aux services Office 365. Vous devrez peut-être optimiser votre réseau ou les périphériques pour vous assurer que vos utilisateurs une expérience cohérente lorsque vous accédez à Office 365. Par exemple, les services Office 365 chiffrer certains contenus Office 365 et l’en-tête TCP. Votre appareil ne peut pas être en mesure de gérer ce type de trafic.</span><span class="sxs-lookup"><span data-stu-id="c59b4-p106">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services. You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365. For example, Office 365 services encrypt some Office 365 content and the TCP header. Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="c59b4-134">Lire notre déclaration de prise en charge sur [contrôleur d’optimisation WAN à l’aide de ou périphériques/Inspection du trafic avec Office 365](https://support.microsoft.com/kb/2690045).</span><span class="sxs-lookup"><span data-stu-id="c59b4-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="c59b4-135">Périphériques d'équilibrage de charge matérielle et logicielle</span><span class="sxs-lookup"><span data-stu-id="c59b4-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="c59b4-p107">Pour répartir les demandes adressées à vos serveurs ADFS (Active Directory Federation Services) ou serveurs Exchange hybrides, votre organisation doit utiliser une solution d'équilibrage de la charge matérielle (HLP) ou d'équilibrage de la charge réseau (NLB). Les périphériques d'équilibrage de la charge contrôlent le trafic réseau vers les serveurs locaux. Ces serveurs sont essentiels pour garantir la disponibilité de l'authentification unique et du déploiement Exchange hybride.</span><span class="sxs-lookup"><span data-stu-id="c59b4-p107">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers. Load-balancing devices control the network traffic to the on-premises servers. These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="c59b4-p108">Nous proposons une solution d’équilibrage de charge réseau basé sur logiciel intégrée à Windows Server. Office 365 prend en charge cette solution pour équilibrer la charge.</span><span class="sxs-lookup"><span data-stu-id="c59b4-p108">We provide a software-based NLB solution built into Windows Server. Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="c59b4-141">Pare-feu et des proxys</span><span class="sxs-lookup"><span data-stu-id="c59b4-141">Firewalls and proxies</span></span>

<span data-ttu-id="c59b4-142">Pour plus d’informations sur la configuration des pare-feu et des proxys pour se connecter à Office 365, lisez les [points de terminaison de gestion Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), la [connectivité réseau vers Office 365](network-connectivity.md)et [points de terminaison Office 365 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) pour en savoir plus sur les périphériques et sélection de circuits.</span><span class="sxs-lookup"><span data-stu-id="c59b4-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c59b4-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c59b4-143">See also</span></span>

[<span data-ttu-id="c59b4-144">Conseillers de déploiement pour les services Office 365</span><span class="sxs-lookup"><span data-stu-id="c59b4-144">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
