---
title: Prise en charge de la traduction d'adresses réseau (NAT) avec Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Résumé : fournit des informations sur la façon de rapprocher le nombre correct de clients que vous pouvez utiliser par adresse IP au sein de votre organisation à l’aide de la traduction d’adresses réseau (NAT).'
ms.openlocfilehash: 6140cf664a08701e9491c241d5754d51196e3922
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844565"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="814de-103">Prise en charge de la traduction d'adresses réseau (NAT) avec Office 365</span><span class="sxs-lookup"><span data-stu-id="814de-103">NAT support with Office 365</span></span>

<span data-ttu-id="814de-104">*Cet article est valable pour Office 365 Entreprise et Microsoft 365 Entreprise*.</span><span class="sxs-lookup"><span data-stu-id="814de-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="814de-105">Auparavant, vous avez indiqué que le nombre maximal de clients Exchange à utiliser par adresse IP pour se connecter à Office 365 était environ 2 000 clients par port réseau.</span><span class="sxs-lookup"><span data-stu-id="814de-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="814de-106">Pourquoi utiliser le protocole NAT ?</span><span class="sxs-lookup"><span data-stu-id="814de-106">Why use NAT?</span></span>

<span data-ttu-id="814de-107">À l’aide de l’interface NAT, des milliers de personnes sur un réseau d’entreprise peuvent « partager » quelques adresses IP routables publiquement.</span><span class="sxs-lookup"><span data-stu-id="814de-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="814de-108">La plupart des réseaux d’entreprise utilisent l’espace d’adressage IP privé (RFC1918).</span><span class="sxs-lookup"><span data-stu-id="814de-108">Most corporate networks use private (RFC1918) IP address space.</span></span> <span data-ttu-id="814de-109">L’espace d’adressage privé est alloué par l’IANA (Internet Assigned Numbers Authority) et destiné uniquement aux réseaux qui ne sont pas routés directement vers et depuis l’Internet global.</span><span class="sxs-lookup"><span data-stu-id="814de-109">Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="814de-110">Pour fournir un accès Internet aux appareils sur un espace d’adressage IP privé, les organisations utilisent des technologies de passerelle telles que les pare-feu et les proxys qui fournissent des services de traduction d’adresses réseau (NAT) ou de traduction d’adresse de port (PAT).</span><span class="sxs-lookup"><span data-stu-id="814de-110">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services.</span></span> <span data-ttu-id="814de-111">Ces passerelles rendent le trafic à partir d’appareils internes vers Internet (y compris Office 365) semblent provenir d’une ou de plusieurs adresses IP routables publiquement.</span><span class="sxs-lookup"><span data-stu-id="814de-111">These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses.</span></span> <span data-ttu-id="814de-112">Chaque connexion sortante à partir d’un périphérique interne se traduit par un port TCP source différent sur l’adresse IP publique.</span><span class="sxs-lookup"><span data-stu-id="814de-112">Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="814de-113">Pourquoi avez-vous besoin d’un grand nombre de connexions ouvertes dans Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="814de-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="814de-114">Outlook peut ouvrir au moins huit connexions (dans les situations où il y a des compléments, des calendriers partagés, des boîtes aux lettres, etc.).</span><span class="sxs-lookup"><span data-stu-id="814de-114">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.).</span></span> <span data-ttu-id="814de-115">Étant donné qu’il y a un maximum de 64 000 ports disponibles sur un périphérique NAT basé sur Windows, il peut y avoir un maximum de 8 000 utilisateurs derrière une adresse IP pour que les ports soient épuisés.</span><span class="sxs-lookup"><span data-stu-id="814de-115">Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted.</span></span> <span data-ttu-id="814de-116">Notez que si les clients utilisent des appareils non-Windows pour la traduction d’adresses réseau (NAT), le total des ports disponibles dépend du périphérique ou du logiciel NAT utilisé.</span><span class="sxs-lookup"><span data-stu-id="814de-116">Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used.</span></span> <span data-ttu-id="814de-117">Dans ce scénario, le nombre maximal de ports peut être inférieur à 64 000.</span><span class="sxs-lookup"><span data-stu-id="814de-117">In this scenario, the maximum number of ports could be less than 64,000.</span></span> <span data-ttu-id="814de-118">La disponibilité des ports est également influencée par d’autres facteurs tels que le fait que Windows limite les ports 4 000 pour sa propre utilisation, ce qui réduit le nombre total de ports disponibles à 60, 000. il peut y avoir d’autres applications, telles qu’Internet Explorer, qui peuvent se connecter en même temps. , ce qui nécessite des ports supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="814de-118">Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="814de-119">Calcul du nombre maximal d’appareils pris en charge derrière une même adresse IP publique avec Office 365</span><span class="sxs-lookup"><span data-stu-id="814de-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="814de-120">Pour déterminer le nombre maximal d’appareils derrière une seule adresse IP publique, vous devez surveiller le trafic réseau afin de déterminer la consommation de ports maximale par client.</span><span class="sxs-lookup"><span data-stu-id="814de-120">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="814de-121">De plus, un facteur de pic doit être utilisé pour l’utilisation des ports (4 minimum).</span><span class="sxs-lookup"><span data-stu-id="814de-121">Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="814de-122">**Utilisez la formule suivante pour calculer le nombre de périphériques pris en charge par adresse IP :**</span><span class="sxs-lookup"><span data-stu-id="814de-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="814de-123">Nombre maximal d’appareils pris en charge derrière une même adresse IP publique = (64 000-Restricted ports)/(pic de consommation de ports + facteur de pic)</span><span class="sxs-lookup"><span data-stu-id="814de-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="814de-124">**Par exemple, si les éléments suivants étaient vrais :**</span><span class="sxs-lookup"><span data-stu-id="814de-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="814de-125">**Ports restreints :** 4 000 pour le système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="814de-125">**Restricted ports:** 4,000 for the operating system</span></span>

- <span data-ttu-id="814de-126">**Consommation de ports PIC :** 6 par appareil</span><span class="sxs-lookup"><span data-stu-id="814de-126">**Peak port consumption:** 6 per device</span></span>

- <span data-ttu-id="814de-127">**Facteur de crête :** 4</span><span class="sxs-lookup"><span data-stu-id="814de-127">**Peak factor:** 4</span></span>

<span data-ttu-id="814de-128">Ensuite, le nombre maximal d’appareils pris en charge derrière une seule adresse IP publique = (64 000-4000)/(6 + 4) = 6 000</span><span class="sxs-lookup"><span data-stu-id="814de-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="814de-129">Avec la version du pack d’hébergement Office 365, incluse dans les mises à jour de septembre 2011 pour Microsoft Office Outlook 2007 ou 2011 pour Microsoft Outlook 2010, ou une mise à jour ultérieure, le nombre de connexions à partir d’Outlook (à la fois Office Outlook 2007 avec le service Pack 2 et Outlook 2010) vers Exchange peuvent être aussi peu que 2.</span><span class="sxs-lookup"><span data-stu-id="814de-129">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2.</span></span> <span data-ttu-id="814de-130">Vous devez prendre en facteur les différents systèmes d’exploitation, comportements d’utilisateur, etc., pour déterminer le nombre minimal et maximal de ports requis par votre réseau au niveau maximal.</span><span class="sxs-lookup"><span data-stu-id="814de-130">You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="814de-131">Si vous souhaitez prendre en charge un plus grand nombre d’appareils derrière une même adresse IP publique, suivez les étapes décrites pour évaluer le nombre maximal d’appareils pouvant être pris en charge :</span><span class="sxs-lookup"><span data-stu-id="814de-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="814de-132">Surveillez le trafic réseau pour déterminer la consommation de ports maximale par client.</span><span class="sxs-lookup"><span data-stu-id="814de-132">Monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="814de-133">Vous devez collecter ces données :</span><span class="sxs-lookup"><span data-stu-id="814de-133">You should collect this data:</span></span>
  
- <span data-ttu-id="814de-134">À partir de plusieurs emplacements</span><span class="sxs-lookup"><span data-stu-id="814de-134">From multiple locations</span></span>
    
- <span data-ttu-id="814de-135">À partir de plusieurs appareils</span><span class="sxs-lookup"><span data-stu-id="814de-135">From multiple devices</span></span>
    
- <span data-ttu-id="814de-136">À plusieurs reprises</span><span class="sxs-lookup"><span data-stu-id="814de-136">At multiple times</span></span>
    
<span data-ttu-id="814de-137">Utilisez la formule précédente pour calculer le nombre maximal d’utilisateurs par adresse IP qui peuvent être pris en charge dans leur environnement.</span><span class="sxs-lookup"><span data-stu-id="814de-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="814de-138">Il existe différentes méthodes de répartition de la charge client sur des adresses IP publiques supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="814de-138">There are various methods for distributing client load across additional public IP addresses.</span></span> <span data-ttu-id="814de-139">Les stratégies disponibles dépendent des fonctionnalités de la solution de passerelle d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="814de-139">Strategies available depend on the capabilities of the corporate gateway solution.</span></span> <span data-ttu-id="814de-140">La solution la plus simple consiste à segmenter votre espace d’adressage utilisateur et à « assigner » de façon statique des adresses IP à chaque passerelle.</span><span class="sxs-lookup"><span data-stu-id="814de-140">The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway.</span></span> <span data-ttu-id="814de-141">La possibilité d’utiliser un pool d’adresses IP constitue une autre alternative offerte par de nombreux périphériques de passerelle.</span><span class="sxs-lookup"><span data-stu-id="814de-141">Another alternative that many gateway devices offer is the ability to use a pool of IP addresses.</span></span> <span data-ttu-id="814de-142">L’avantage du pool d’adresses est qu’il est plus dynamique et moins susceptible de nécessiter des ajustements au fur et à mesure que votre base d’utilisateurs se développe.</span><span class="sxs-lookup"><span data-stu-id="814de-142">The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="814de-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="814de-143">See also</span></span>

[<span data-ttu-id="814de-144">Gestion des points de terminaison Office 365</span><span class="sxs-lookup"><span data-stu-id="814de-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="814de-145">Points de terminaison Office 365 - FAQ</span><span class="sxs-lookup"><span data-stu-id="814de-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
