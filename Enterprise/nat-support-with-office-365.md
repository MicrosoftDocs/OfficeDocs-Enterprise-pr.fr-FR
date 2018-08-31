---
title: Prise en charge de la traduction d’adresses réseau (NAT) dans Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Résumé : Fournit des informations détaillées sur la manière d’estimer correctement le nombre de clients que vous pouvez utiliser par adresse IP au sein de votre organisation à l’aide de la traduction d’adresses réseau (NAT).'
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540308"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="7acd1-103">Prise en charge de la traduction d’adresses réseau (NAT) dans Office 365</span><span class="sxs-lookup"><span data-stu-id="7acd1-103">NAT support with Office 365</span></span>

 <span data-ttu-id="7acd1-104">**Résumé :** Fournit des informations détaillées sur la manière d’estimer correctement le nombre de clients que vous pouvez utiliser par adresse IP au sein de votre organisation à l’aide de la traduction d’adresses réseau (NAT).</span><span class="sxs-lookup"><span data-stu-id="7acd1-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="7acd1-105">Auparavant, conseils suggéré que le nombre maximal de clients Exchange que vous devez utiliser par adresse IP pour se connecter à Office 365 a environ 2 000 clients par port réseau.</span><span class="sxs-lookup"><span data-stu-id="7acd1-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="7acd1-106">Pourquoi utiliser la traduction d’adresses réseau (NAT) ?</span><span class="sxs-lookup"><span data-stu-id="7acd1-106">Why use NAT?</span></span>

<span data-ttu-id="7acd1-107">À l’aide de NAT, des milliers de personnes sur un réseau d’entreprise peuvent « partager » les quelques adresses IP publiquement routables.</span><span class="sxs-lookup"><span data-stu-id="7acd1-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="7acd1-p101">La plupart des réseaux d’entreprise utilisent un espace d’adressage IP privé (RFC1918). Un espace d’adressage IP est alloué par l’organisme IANA (Internet Assigned Numbers Authority). Il est destiné uniquement aux réseaux qui n’effectuent pas de routage entrant ou sortant directement avec Internet.</span><span class="sxs-lookup"><span data-stu-id="7acd1-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="7acd1-p102">Pour fournir l’accès à Internet pour les appareils dans un espace d’adressage IP privé, les organisations utilisent des technologies de passerelle telles que des pare-feu et des proxys qui fournissent la traduction d’adresses réseau (NAT) ou les services (PAT) traduction d’adresse port. Ces passerelles rendre le trafic interne appareils Internet (y compris Office 365) semblent provenir d’une ou plusieurs adresses IP publiquement routables. Chaque connexion sortante à partir d’un périphérique interne se traduit par un port TCP de sources différents sur l’adresse IP publique.</span><span class="sxs-lookup"><span data-stu-id="7acd1-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="7acd1-113">Pourquoi avez-vous besoin ouvrir autant de connexions à Office 365 en même temps ?</span><span class="sxs-lookup"><span data-stu-id="7acd1-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="7acd1-p103">Outlook peut ouvrir huit connexions ou plus (dans les cas où des compléments, des calendriers partagés, des boîtes aux lettres, etc. sont présents). Le nombre maximal de ports disponibles étant de 64 000 sur un appareil NAT Windows, plus de 8 000 utilisateurs peuvent se trouver derrière une adresse IP avant que les ports soient saturés. Prenez note que, si des clients utilisent des appareils non compatibles avec le système d’exploitation Windows pour la NAT, le nombre total de ports disponibles dépend de l’appareil NAT ou du logiciel utilisés. Dans ce scénario, le nombre maximal de ports peut être inférieur à 64 000. La disponibilité des ports est également influencée par d’autres facteurs, tels que le fait que Windows réserve 4 000 ports pour son propre usage, ce qui réduit le nombre total de ports disponibles à 60 000. D’autres applications telles qu’Internet Explorer peuvent également se connecter au même moment, ce qui nécessite des ports supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="7acd1-p103">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="7acd1-119">Calcul du nombre maximal de périphériques pris en charge derrière une adresse IP publique avec Office 365</span><span class="sxs-lookup"><span data-stu-id="7acd1-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="7acd1-p104">Pour déterminer le nombre maximal de périphériques derrière une adresse IP publique, vous devez analyser le trafic réseau pour déterminer la consommation de ports pointe par client. En outre, un facteur de pointe doit être utilisé pour l’utilisation du port (au moins 4).</span><span class="sxs-lookup"><span data-stu-id="7acd1-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="7acd1-122">**Utilisez la formule suivante pour calculer le nombre de périphériques pris en charge par adresse IP :**</span><span class="sxs-lookup"><span data-stu-id="7acd1-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="7acd1-123">Maximum pris en charge les périphériques derrière une adresse IP publique = (64 000 - ports réservés) / (pic de consommation de ports + facteur de pointe)</span><span class="sxs-lookup"><span data-stu-id="7acd1-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="7acd1-124">**Par exemple, si les éléments suivants ont la valeur trus :**</span><span class="sxs-lookup"><span data-stu-id="7acd1-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="7acd1-125">**Ports réservés :** 4 000 pour le système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="7acd1-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="7acd1-126">**Pic de consommation de ports :** 6 par appareil</span><span class="sxs-lookup"><span data-stu-id="7acd1-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="7acd1-127">**Facteur de pointe :** 4</span><span class="sxs-lookup"><span data-stu-id="7acd1-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="7acd1-128">Ensuite, la valeur maximale périphériques pris en charge derrière une adresse IP publique = (64 000-4 000) / (6 + 4) = 6 000</span><span class="sxs-lookup"><span data-stu-id="7acd1-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="7acd1-p105">Avec la version d’Office 365 pack, inclus dans les mises à jour de septembre 2011 pour Microsoft Office Outlook 2007 ou de novembre 2011 pour Microsoft Outlook 2010 ou d’une mise à jour ultérieur, le nombre de connexions à partir d’Outlook (à la fois Office Outlook 2007 avec le Service d’hébergement Pack 2 et Outlook 2010) pour Exchange peut être aussi peu que 2. Vous devez prendre en compte les différents systèmes d’exploitation, comportements de l’utilisateur, et ainsi de suite pour déterminer le nombre maximum et minimum des ports qui nécessite votre réseau à l’utilisation maximale.</span><span class="sxs-lookup"><span data-stu-id="7acd1-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="7acd1-131">Si vous souhaitez prendre en charge plusieurs périphériques derrière une adresse IP publique, suivez la procédure présentée pour évaluer le nombre maximal de périphériques pouvant être pris en charge :</span><span class="sxs-lookup"><span data-stu-id="7acd1-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="7acd1-p106">Surveiller le trafic réseau pour déterminer la consommation de ports pointe par client. Vous devez recueillir ces données :</span><span class="sxs-lookup"><span data-stu-id="7acd1-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="7acd1-134">À partir de plusieurs emplacements</span><span class="sxs-lookup"><span data-stu-id="7acd1-134">From multiple locations</span></span>
    
- <span data-ttu-id="7acd1-135">À partir de plusieurs appareils</span><span class="sxs-lookup"><span data-stu-id="7acd1-135">From multiple devices</span></span>
    
- <span data-ttu-id="7acd1-136">À plusieurs moments différents</span><span class="sxs-lookup"><span data-stu-id="7acd1-136">At multiple times</span></span>
    
<span data-ttu-id="7acd1-137">Pour calculer le nombre maximal d'utilisateurs par adresse IP qui peuvent être pris en charge dans leur environnement, utilisez la formule précédente.</span><span class="sxs-lookup"><span data-stu-id="7acd1-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="7acd1-p107">Il existe différentes méthodes de distribution de charge du client sur des adresses IP publiques supplémentaires. Stratégies disponibles varient selon les fonctionnalités de la solution de passerelle d’entreprise. La solution la plus simple consiste à votre espace d’adressage utilisateur de segment et statiquement « affecter » un nombre d’adresses IP pour chaque passerelle. Une autre solution offrent de nombreux périphériques de passerelle est la possibilité d’utiliser un pool d’adresses IP. L’avantage du pool d’adresses est qu’il est beaucoup plus dynamique et moins susceptibles d’exiger l’ajustement que votre base d’utilisateurs augmente.</span><span class="sxs-lookup"><span data-stu-id="7acd1-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7acd1-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7acd1-143">See also</span></span>

[<span data-ttu-id="7acd1-144">Gestion des points de terminaison Office 365</span><span class="sxs-lookup"><span data-stu-id="7acd1-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="7acd1-145">Points de terminaison Office 365 FAQ</span><span class="sxs-lookup"><span data-stu-id="7acd1-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

