---
title: Guide de laboratoire de test  Configurer un laboratoire de test Exchange, Lync et SharePoint intégré
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
f1.keywords:
- NOCSH
description: 'Résumé : Découvrez comment créer un laboratoire de test intégré contenant un serveur qui exécute Exchange Server 2013, un serveur qui exécute Lync Server 2013 et un serveur qui exécute SharePoint Server 2013.'
ms.openlocfilehash: 6041f47520f7a02efe08d05835ca0f15dfd6633a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841101"
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="6ea52-103">Guide de laboratoire de test : Configurer un laboratoire de test Exchange, Lync et SharePoint intégré</span><span class="sxs-lookup"><span data-stu-id="6ea52-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="6ea52-104">\*\*Résumé : \*\*Découvrez comment créer un laboratoire de test intégré contenant un serveur qui exécute Exchange Server 2013, un serveur qui exécute Lync Server 2013 et un serveur qui exécute SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="6ea52-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
 
<span data-ttu-id="6ea52-105">**Regarder la vidéo de présentation du guide de laboratoire de test Exchange, Lync et SharePoint intégré**</span><span class="sxs-lookup"><span data-stu-id="6ea52-105">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=8d1f00cc-b8b1-4394-9367-0cc9765e380a&AutoPlayVideo=false]
 
<span data-ttu-id="6ea52-106">Le laboratoire de test résultant de cette configuration, qui inclut l'authentification de serveur à serveur entre les trois types de serveurs, permet de créer et de faire la démonstration de scénarios et solutions multiproduits utilisant un serveur qui exécute Exchange Server 2013, un serveur qui exécute Lync Server 2013 et un serveur qui exécute SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="6ea52-106">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="6ea52-107">Ce document contient des instructions pour :</span><span class="sxs-lookup"><span data-stu-id="6ea52-107">This document contains instructions for:</span></span>
  
1. <span data-ttu-id="6ea52-108">Configuration du laboratoire de test de configuration de base Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="6ea52-108">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="6ea52-109">Installation et configuration d’un nouveau serveur nommé SQL1</span><span class="sxs-lookup"><span data-stu-id="6ea52-109">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="6ea52-110">Installation de SQL Server 2012 sur le serveur SQL1</span><span class="sxs-lookup"><span data-stu-id="6ea52-110">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="6ea52-111">Installation et configuration d’un nouvel ordinateur client nommé CLIENT2</span><span class="sxs-lookup"><span data-stu-id="6ea52-111">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="6ea52-112">Installation et configuration d'Exchange Server 2013 sur EX1</span><span class="sxs-lookup"><span data-stu-id="6ea52-112">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="6ea52-113">Installation et configuration d’un nouveau serveur nommé LYNC1</span><span class="sxs-lookup"><span data-stu-id="6ea52-113">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="6ea52-114">Installation de Lync Server 2013 Standard Edition sur LYNC1</span><span class="sxs-lookup"><span data-stu-id="6ea52-114">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="6ea52-115">Installation de SharePoint Server 2013 sur SP1</span><span class="sxs-lookup"><span data-stu-id="6ea52-115">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="6ea52-116">Configuration de l’intégration entre EX1, LYNC1 et SP1</span><span class="sxs-lookup"><span data-stu-id="6ea52-116">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="6ea52-117">Pour plus d'informations sur la configuration de ce laboratoire de test dans Hyper-V, voir l'article sur l'[hébergement du laboratoire de test Exchange, Lync et SharePoint intégré avec Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span><span class="sxs-lookup"><span data-stu-id="6ea52-117">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="6ea52-118">Télécharger le guide de laboratoire de test</span><span class="sxs-lookup"><span data-stu-id="6ea52-118">Download the test lab guide</span></span>

<span data-ttu-id="6ea52-119">[Guide de laboratoire de test : configurer un laboratoire de test Exchange, Lync et SharePoint intégré](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="6ea52-119">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6ea52-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ea52-120">See Also</span></span>

[<span data-ttu-id="6ea52-121">Guides de laboratoire de test</span><span class="sxs-lookup"><span data-stu-id="6ea52-121">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




