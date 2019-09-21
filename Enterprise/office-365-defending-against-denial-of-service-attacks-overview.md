---
title: Défense contre les attaques par déni de service dans Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Vue d’ensemble des attaques par déni de service (DoS).
ms.openlocfilehash: 55fffccfc59f13d32cdd19930320c1df1cf58461
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067388"
---
# <a name="defend-against-denial-of-service-attacks-in-office-365"></a><span data-ttu-id="32cfb-103">Défense contre les attaques par déni de service dans Office 365</span><span class="sxs-lookup"><span data-stu-id="32cfb-103">Defend Against Denial-of-Service Attacks in Office 365</span></span>

## <a name="introduction"></a><span data-ttu-id="32cfb-104">Introduction</span><span class="sxs-lookup"><span data-stu-id="32cfb-104">Introduction</span></span>

<span data-ttu-id="32cfb-105">Microsoft offre une infrastructure de confiance pour plus de 200 services Cloud hébergés dans une infrastructure de Cloud internationale de plus de 100 centres de donnees.</span><span class="sxs-lookup"><span data-stu-id="32cfb-105">Microsoft delivers a trustworthy infrastructure for more than 200 cloud services hosted in a global cloud infrastructure of more than 100 datacenters.</span></span> <span data-ttu-id="32cfb-106">Ces approches sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="32cfb-106">These include:</span></span>

- <span data-ttu-id="32cfb-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="32cfb-107">Microsoft Azure</span></span>
- <span data-ttu-id="32cfb-108">Microsoft Bing</span><span class="sxs-lookup"><span data-stu-id="32cfb-108">Microsoft Bing</span></span>
- <span data-ttu-id="32cfb-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="32cfb-109">Microsoft Dynamics 365</span></span>
- <span data-ttu-id="32cfb-110">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="32cfb-110">Microsoft Office 365</span></span>
- <span data-ttu-id="32cfb-111">Microsoft OneDrive</span><span class="sxs-lookup"><span data-stu-id="32cfb-111">Microsoft OneDrive</span></span>
- <span data-ttu-id="32cfb-112">Skype</span><span class="sxs-lookup"><span data-stu-id="32cfb-112">Skype</span></span>
- <span data-ttu-id="32cfb-113">Xbox LIVE</span><span class="sxs-lookup"><span data-stu-id="32cfb-113">Xbox Live</span></span>

<span data-ttu-id="32cfb-114">En tant qu’organisation mondiale avec une présence Internet importante et de nombreuses propriétés Internet importantes qui fournissent des services en nuage, Microsoft est une cible commune et commune aux pirates et autres personnes malveillantes.</span><span class="sxs-lookup"><span data-stu-id="32cfb-114">As a global organization with a significant Internet presence and many prominent Internet properties that provide cloud services, Microsoft is a large, common target for hackers and other malicious individuals.</span></span> <span data-ttu-id="32cfb-115">La couche de communication réseau entre les clients et le Cloud Microsoft est l’une des principales cibles d’attaques malveillantes.</span><span class="sxs-lookup"><span data-stu-id="32cfb-115">The network communication layer between clients and the Microsoft Cloud is one of the biggest targets of malicious attacks.</span></span> <span data-ttu-id="32cfb-116">En fait, Microsoft s’exécute de façon continue et permanente sous une forme de cyber basée sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="32cfb-116">In fact, Microsoft is continuously and persistently under some form of network-based cyberattack.</span></span> <span data-ttu-id="32cfb-117">En fonction de ces principes, Microsoft utilise des principes de sécurité de défense en profondeur pour protéger ses services et réseaux Cloud.</span><span class="sxs-lookup"><span data-stu-id="32cfb-117">In line with this, Microsoft uses defense-in-depth security principles to protect its cloud services and networks.</span></span> <span data-ttu-id="32cfb-118">Sans systèmes d’atténuation fiables et persistants qui se défendent contre ces attaques, les services Cloud de Microsoft seraient hors ligne et indisponibles pour les clients.</span><span class="sxs-lookup"><span data-stu-id="32cfb-118">Without reliable and persistent mitigation systems that defend against these attacks, Microsoft's cloud services would be offline and unavailable to customers.</span></span>

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a><span data-ttu-id="32cfb-119">Définition et symptômes des attaques par déni de service</span><span class="sxs-lookup"><span data-stu-id="32cfb-119">Definition and Symptoms of Denial-of-Service Attacks</span></span>

<span data-ttu-id="32cfb-120">Pour attaquer les services réseau, il est possible de créer de nombreuses requêtes auprès d’hôtes de service afin de submerger le réseau et les serveurs afin de refuser les services aux utilisateurs légitimes.</span><span class="sxs-lookup"><span data-stu-id="32cfb-120">One way to attack network services is to create many requests against service hosts to overwhelm the network and servers to deny service to legitimate users.</span></span> <span data-ttu-id="32cfb-121">Il s’agit d’une attaque par déni de service (DoS).</span><span class="sxs-lookup"><span data-stu-id="32cfb-121">This is referred to as a denial-of-service (DoS) attack.</span></span> <span data-ttu-id="32cfb-122">Lorsque l’attaque est effectuée par plusieurs acteurs, points de terminaison et/ou vecteurs, elle est considérée comme une attaque de déni de service distribuée.</span><span class="sxs-lookup"><span data-stu-id="32cfb-122">When the attack is performed by multiple actors, endpoints, and/or vectors, it is referred to as a distributed denial-of-service (DDoS) attack.</span></span> <span data-ttu-id="32cfb-123">Bien que les moyens, les motivations et les cibles varient, les attaques DoS et DDoS consistent généralement à empêcher un site ou un service Internet de fonctionner correctement ou du tout, de façon temporaire ou indéfinie.</span><span class="sxs-lookup"><span data-stu-id="32cfb-123">Although the means, motives, and targets vary, DoS and DDoS attacks generally consist of efforts to prevent an Internet site or service from functioning correctly or at all, either temporarily or indefinitely.</span></span>

<span data-ttu-id="32cfb-124">L’équipe américaine de préparation de l' [urgence informatique](https://www.us-cert.gov/) (US-CERT) définit les symptômes des attaques par déni :</span><span class="sxs-lookup"><span data-stu-id="32cfb-124">The [United States Computer Emergency Readiness Team](https://www.us-cert.gov/) (US-CERT) defines symptoms of DoS attacks to include:</span></span>

- <span data-ttu-id="32cfb-125">Ralentissement des performances réseau (lors de l’ouverture de fichiers ou accès aux sites Internet)</span><span class="sxs-lookup"><span data-stu-id="32cfb-125">Unusually slow network performance (when opening files or accessing Internet sites)</span></span>
- <span data-ttu-id="32cfb-126">Indisponibilité d’un site Web</span><span class="sxs-lookup"><span data-stu-id="32cfb-126">Unavailability of a Web site</span></span>
- <span data-ttu-id="32cfb-127">Impossibilité d’accéder à un site Web</span><span class="sxs-lookup"><span data-stu-id="32cfb-127">Inability to access a Web site</span></span>
- <span data-ttu-id="32cfb-128">Augmentation spectaculaire du courrier indésirable reçu</span><span class="sxs-lookup"><span data-stu-id="32cfb-128">Dramatic increase in received spam</span></span>
- <span data-ttu-id="32cfb-129">Déconnexion d’une connexion Internet câblée ou sans fil</span><span class="sxs-lookup"><span data-stu-id="32cfb-129">Disconnection of a wireless or wired Internet connection</span></span>
- <span data-ttu-id="32cfb-130">Perte d’accès à long terme pour le Web ou tout service Internet</span><span class="sxs-lookup"><span data-stu-id="32cfb-130">Long-term loss of access to the Web or any Internet services</span></span>

## <a name="related-topics"></a><span data-ttu-id="32cfb-131">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="32cfb-131">Related Topics</span></span>

- [<span data-ttu-id="32cfb-132">Principes fondamentaux de défense contre les attaques par déni de service</span><span class="sxs-lookup"><span data-stu-id="32cfb-132">Core Principles of Defense Against Denial-of-Service Attacks</span></span>](office-365-core-principles-of-defense-against-dos-attacks.md)
- [<span data-ttu-id="32cfb-133">Stratégie de défense contre les attaques par déni de service de Microsoft</span><span class="sxs-lookup"><span data-stu-id="32cfb-133">Microsoft's Denial-of-Service Defense Strategy</span></span>](office-365-microsoft-dos-defense-strategy.md)
- [<span data-ttu-id="32cfb-134">Protection des services de Cloud Computing Microsoft contre les attaques par déni de service</span><span class="sxs-lookup"><span data-stu-id="32cfb-134">Defending Microsoft Cloud Services Against Denial-of-Service Attacks</span></span>](office-365-defending-cloud-services-against-dos-attacks.md)
