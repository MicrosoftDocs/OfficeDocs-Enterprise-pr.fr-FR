---
title: "Guide de laboratoire de test  Configurer un laboratoire de test Exchange, Lync et SharePoint intégré"
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
description: "Résumé : Découvrez comment créer un laboratoire de test intégré contenant un serveur qui exécute Exchange Server 2013, un serveur qui exécute Lync Server 2013 et un serveur qui exécute SharePoint Server 2013."
ms.openlocfilehash: 6fc3bc05db0d28bc4de2be77671ccf5e8fc55926
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2017
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="0d83b-103">Guide de laboratoire de test : Configurer un laboratoire de test Exchange, Lync et SharePoint intégré</span><span class="sxs-lookup"><span data-stu-id="0d83b-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="0d83b-104">**Résumé :** Apprenez à créer un atelier de test intégré qui contient un serveur qui exécute Exchange Server 2013, un serveur qui exécute Microsoft Lync Server 2013 et un serveur qui exécute SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="0d83b-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="0d83b-105">Le laboratoire de test résultant de cette configuration, qui inclut l'authentification de serveur à serveur entre les trois types de serveurs, permet de créer et de faire la démonstration de scénarios et solutions multiproduits utilisant un serveur qui exécute Exchange Server 2013, un serveur qui exécute Lync Server 2013 et un serveur qui exécute SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="0d83b-105">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="0d83b-106">Ce document contient les instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="0d83b-106">This document contains instructions for the following:</span></span>
  
1. <span data-ttu-id="0d83b-107">Configuration du laboratoire de test de configuration de base Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="0d83b-107">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="0d83b-108">Installation et configuration d'un nouveau serveur nommé SQL1</span><span class="sxs-lookup"><span data-stu-id="0d83b-108">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="0d83b-109">Installation de SQL Server 2012 sur le serveur SQL1</span><span class="sxs-lookup"><span data-stu-id="0d83b-109">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="0d83b-110">Installation et configuration d'un nouvel ordinateur client nommé CLIENT2</span><span class="sxs-lookup"><span data-stu-id="0d83b-110">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="0d83b-111">Installation et configuration d'Exchange Server 2013 sur EX1</span><span class="sxs-lookup"><span data-stu-id="0d83b-111">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="0d83b-112">Installation et configuration d'un nouveau serveur nommé LYNC1</span><span class="sxs-lookup"><span data-stu-id="0d83b-112">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="0d83b-113">Installation de Lync Server 2013 Standard Edition sur LYNC1</span><span class="sxs-lookup"><span data-stu-id="0d83b-113">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="0d83b-114">Installation de SharePoint Server 2013 sur SP1</span><span class="sxs-lookup"><span data-stu-id="0d83b-114">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="0d83b-115">Configuration de l'intégration entre EX1, LYNC1 et SP1</span><span class="sxs-lookup"><span data-stu-id="0d83b-115">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="0d83b-116">**Regarder la vidéo de présentation du guide de laboratoire de test Exchange, Lync et SharePoint intégré**</span><span class="sxs-lookup"><span data-stu-id="0d83b-116">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

![Icône Vidéo (bouton de lecture)](images/mod_icon_video_M.png)
  
<span data-ttu-id="0d83b-118">Pour plus d'informations sur la configuration de ce laboratoire de test dans Hyper-V, voir l'article sur l'[hébergement du laboratoire de test Exchange, Lync et SharePoint intégré avec Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span><span class="sxs-lookup"><span data-stu-id="0d83b-118">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="0d83b-119">Télécharger le guide de laboratoire de test</span><span class="sxs-lookup"><span data-stu-id="0d83b-119">Download the test lab guide</span></span>

<span data-ttu-id="0d83b-120">[Guide de laboratoire de test : configurer un laboratoire de test Exchange, Lync et SharePoint intégré](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="0d83b-120">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0d83b-121">See Also</span><span class="sxs-lookup"><span data-stu-id="0d83b-121">See Also</span></span>

[<span data-ttu-id="0d83b-122">Guides de laboratoire de test</span><span class="sxs-lookup"><span data-stu-id="0d83b-122">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




