---
title: FAQ général relatif au déplacement de données
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 9/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: Vous trouverez ici les réponses aux questions d’ordre générales sur le déplacement des données principales vers un nouveau localisés de centre de données.
ms.openlocfilehash: 40f83ee94aaa7c919f08d91d888ff131da02df67
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540492"
---
# <a name="data-move-general-faq"></a><span data-ttu-id="49850-103">FAQ général relatif au déplacement de données</span><span class="sxs-lookup"><span data-stu-id="49850-103">Data move general FAQ</span></span>

<span data-ttu-id="49850-104">Vous trouverez ici les réponses aux questions d’ordre générales sur le déplacement des données principales vers un nouveau localisés de centre de données.</span><span class="sxs-lookup"><span data-stu-id="49850-104">Here are answers to general questions about moving core data to a new datacenter geo.</span></span>
  
 <span data-ttu-id="49850-105">**Q. Comment vous assurez-vous que mes données client sont sécurisées lors du déplacement et qu'il n'y aura pas de temps d'arrêt ?**</span><span class="sxs-lookup"><span data-stu-id="49850-105">**Q. How do you make sure my customer data is safe during the move and that I won't experience downtime?**</span></span>
  
<span data-ttu-id="49850-p101">Déplacements de données a sont une opération de service principal avec un impact minimal sur les utilisateurs finaux. Fonctionnalités qui peuvent être affectées sont répertoriées dans [pendant et après le déplacement de vos données](during-and-after-your-data-move.md). Nous respecter la disponibilité [Microsoft Online Services Service au niveau du contrat de](https://go.microsoft.com/fwlink/p/?LinkId=523897) sorte que rien que les clients ont besoin pour préparer ou pour surveiller pendant le déplacement.</span><span class="sxs-lookup"><span data-stu-id="49850-p101">A. Data moves are a back-end service operation with minimal impact to end-users. Features that can be impacted are listed in [During and after your data move](during-and-after-your-data-move.md). We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move.</span></span> 
  
<span data-ttu-id="49850-p102">Tous les services Office 365 sont exécutés avec les mêmes versions dans les centres de données. Vous pouvez ainsi être certain de la cohérence des fonctionnalités. Votre service est entièrement pris en charge tout au long du processus.</span><span class="sxs-lookup"><span data-stu-id="49850-p102">All Office 365 services run the same versions in the datacenters, so you can be assured of consistent functionality. Your service is fully supported throughout the process.</span></span>
  
 <span data-ttu-id="49850-112">**Q : quel est l’impact des différents services situés dans différentes zones géographiques ?**</span><span class="sxs-lookup"><span data-stu-id="49850-112">**Q. What is the impact of having different services located in different geos?**</span></span>
  
<span data-ttu-id="49850-p103">R. pour certains clients existants et au milieu du processus de déplacement, les services Office 365 peuvent se trouver dans différentes zones géographiques. Nos services s’exécutent indépendamment les uns des autres, et il n’existe aucun impact sur l’utilisateur si c’est le cas.</span><span class="sxs-lookup"><span data-stu-id="49850-p103">A. For some existing customers and customers in the middle of the move process, some of the Office 365 services may be located in different geos. Our services run independently of each other and there is no user impact if this is the case.</span></span>
  
 <span data-ttu-id="49850-116">**Q. nouveaux clients Office 365 est automatiquement mis en service dans la nouvelle géographiques de centre de données ?**</span><span class="sxs-lookup"><span data-stu-id="49850-116">**Q. Will new Office 365 customers be automatically provisioned in the new datacenter geos?**</span></span>
  
<span data-ttu-id="49850-p104">R. Oui. Une fois qu’un nouveau localisés de centre de données est disponible, nouvel Office 365 pour entreprises qui sélectionner un pays éligible pour la nouvelle localisés en tant que leur pays pendant l’inscription auront leurs données principales hébergées dans le nouveau localisés de centre de données.</span><span class="sxs-lookup"><span data-stu-id="49850-p104">A. Yes. Once a new datacenter geo is available, new Office 365 for business customers who select a country eligible for the new geo as their country during sign-up will have their core data hosted in the new datacenter geo.</span></span>
  
 <span data-ttu-id="49850-120">**Q. Où se trouvent mes données ?**</span><span class="sxs-lookup"><span data-stu-id="49850-120">**Q. Where is my data is located?**</span></span>
  
<span data-ttu-id="49850-p105">Nous publier à l’emplacement du centre de données géographiques, centres de données et l’emplacement des données du client sur le [Centre de données interactif Office 365 mappe ](https://o365datacentermap.azurewebsites.net). 1er août, vous serez en mesure de vérifier l’emplacement de vos données client au repos par le biais de la section emplacement des données dans votre profil d’organisation dans le centre d’administration d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="49850-p105">We publish the location of datacenter geos, datacenters, and location of customer data on the [ Office 365 interactive datacenter maps ](https://o365datacentermap.azurewebsites.net). As of August 1, you will be able to verify the location of your customer data at rest via the Data Location section under your Organization Profile in the Office 365 Admin Center.</span></span>
  
 <span data-ttu-id="49850-123">**Q. les clients Office 365 existants sont déplacées vers le nouveau géographiques de centre de données ?**</span><span class="sxs-lookup"><span data-stu-id="49850-123">**Q. Will existing Office 365 customers be moved to the new datacenter geos?**</span></span>
  
<span data-ttu-id="49850-p106">Clients a éligibles Office 365 peuvent demander à leurs données principales déplacées vers le nouveau géographiques. Les clients devront soumettre une demande avant le délai de leur localisés afin de participer.</span><span class="sxs-lookup"><span data-stu-id="49850-p106">A. Eligible Office 365 customers can request to have their core data moved to the new geos. Customers will need to submit a request before the deadline for their geo in order to participate.</span></span> 
  
 <span data-ttu-id="49850-127">**Q. Quels clients peuvent demander un déplacement ?**</span><span class="sxs-lookup"><span data-stu-id="49850-127">**Q. What customers are eligible to request a move?**</span></span>
  
<span data-ttu-id="49850-p107">Clients commerciaux a existant Office 365 qui a sélectionné un pays éligible pour la nouvelle localisés de centre de données sera en mesure de demander un déplacement.</span><span class="sxs-lookup"><span data-stu-id="49850-p107">A. Existing Office 365 commercial customers who selected a country eligible for the new datacenter geo will be able to request a move.</span></span> 
  
 <span data-ttu-id="49850-130">**Q. Quand pourrai-je demander un déplacement ?**</span><span class="sxs-lookup"><span data-stu-id="49850-130">**Q. When will I be able to request a move?**</span></span>
  
<span data-ttu-id="49850-p108">R. La période de demande sera annoncée sur la page [Procédure de demande d'un déplacement de données](request-your-data-move.md).</span><span class="sxs-lookup"><span data-stu-id="49850-p108">A. The request period will be announced on the [How to request your data move](request-your-data-move.md) page.</span></span> 
  
 <span data-ttu-id="49850-133">**Q. Comment effectuer ma demande de déplacement ?**</span><span class="sxs-lookup"><span data-stu-id="49850-133">**Q. How can I request to be moved?**</span></span>
  
<span data-ttu-id="49850-p109">R. Les clients éligibles verront une page correspondante dans leur [portail d'administration Office 365](https://portal.office.com/). Reportez-vous à la section [Procédure de demande d'un déplacement de données](request-your-data-move.md) pour obtenir des informations sur la demande de déplacement.</span><span class="sxs-lookup"><span data-stu-id="49850-p109">A. Eligible customers will see a page in their [Office 365 Admin Portal](https://portal.office.com/). Please see [How to request your data move](request-your-data-move.md) for instructions on how to request a move.</span></span> 
  
 <span data-ttu-id="49850-137">**Q. Puis-je modifier ma sélection après avoir demandé un déplacement ?**</span><span class="sxs-lookup"><span data-stu-id="49850-137">**Q. Can I change my selection after requesting a move?**</span></span>
  
<span data-ttu-id="49850-p110">R. Nous ne pouvons pas vous enlever du processus une fois que vous avez envoyé votre demande.</span><span class="sxs-lookup"><span data-stu-id="49850-p110">A. It is not possible for us to remove you from the process after you submit your request.</span></span>
  
 <span data-ttu-id="49850-140">**Q. Que se passe-t-il si je ne fais pas la demande de déplacement avant la date d'échéance ?**</span><span class="sxs-lookup"><span data-stu-id="49850-140">**Q. What happens if I do not request a move before the deadline?**</span></span>
  
<span data-ttu-id="49850-p111">R. nous ne peuvent pas accepter les demandes de déplacement après la date d’échéance de chaque zone géographique.</span><span class="sxs-lookup"><span data-stu-id="49850-p111">A. We are unable to accept requests to be moved after the deadline in each geo.</span></span>
  
 <span data-ttu-id="49850-143">**Q. Que se passe-t-il si je veux déplacer mes données afin de bénéficier de meilleures performances réseau ?**</span><span class="sxs-lookup"><span data-stu-id="49850-143">**Q. What if I want to move my data in order to get better network performance?**</span></span>
  
<span data-ttu-id="49850-p112">En cours a presque atteint un centre de données Office 365 n’est pas une garantie pour de meilleures performances réseau. Il existe de nombreux facteurs et composants dont l’impact sur les performances du réseau entre l’utilisateur final et le service Office 365. Pour plus d’informations à ce sujet et réglage des performances, voir [planification de réseau et de réglage des performances pour Office 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="49850-p112">Being close to an Office 365 datacenter is not a guarantee for a better networking performance. There are many factors and components that impact the network performance between the end user and the Office 365 service. For more information about this and performance tuning see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>
  
 <span data-ttu-id="49850-147">**Q. Les données de tous les services sont-elles déplacées le même jour ?**</span><span class="sxs-lookup"><span data-stu-id="49850-147">**Q. Do all the services move their data on the same day?**</span></span>
  
<span data-ttu-id="49850-p113">R. Les données des services ne sont pas déplacées en même temps. Chaque service sera déplacé indépendamment et leurs données le seront probablement à différents moments.</span><span class="sxs-lookup"><span data-stu-id="49850-p113">A. The services do not move their data at the same time. Each service will move independently and will likely move their data at different times.</span></span>
  
 <span data-ttu-id="49850-151">**Q. Puis-je choisir la date du déplacement de mes données ?**</span><span class="sxs-lookup"><span data-stu-id="49850-151">**Q. Can I choose when I want my data to be moved?**</span></span>
  
<span data-ttu-id="49850-p114">R. Les clients ne peuvent pas sélectionner une date spécifique, ni retarder leur déplacement. En outre, nous ne pouvons pas communiquer une date spécifique ou une période pour les déplacements.</span><span class="sxs-lookup"><span data-stu-id="49850-p114">A. Customers are not able to select a specific date, they cannot delay their move, and we cannot share a specific date or timeframe for the moves.</span></span>
  
 <span data-ttu-id="49850-154">**Q. Pouvez-vous m'indiquer quand mes données seront déplacées ?**</span><span class="sxs-lookup"><span data-stu-id="49850-154">**Q. Can you share when my data will be be moved?**</span></span>
  
<span data-ttu-id="49850-p115">R. Les déplacements de données sont des opérations principales qui ont une incidence minime sur les utilisateurs finals. La complexité, la précision et l'échelle en fonction desquelles nous devons effectuer les déplacements de données dans un environnement automatisé et commandé de façon globale ne nous permettent pas d'indiquer la date de fin du déplacement pour votre client ou tout autre client unique. Les clients recevront une confirmation dans le centre de messages pour chaque service concerné une fois que le déplacement des données sera terminé.</span><span class="sxs-lookup"><span data-stu-id="49850-p115">A. Data moves are a back-end operation with minimal impact to end-users. The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant. Customers will receive one confirmation in Message Center per participating service when its data move has completed.</span></span> 
  
 <span data-ttu-id="49850-159">**Q. Que se passe-t-il si les utilisateurs accèdent à des services lors du déplacement des données ?**</span><span class="sxs-lookup"><span data-stu-id="49850-159">**Q. What happens if users access services while the data is being moved?**</span></span>
  
<span data-ttu-id="49850-p116">R. Reportez-vous à la section [Pendant et après le déplacement de vos données](during-and-after-your-data-move.md) pour consulter la liste complète des fonctionnalités qui peuvent être limitées à certains moments du déplacement des données pour chaque service.</span><span class="sxs-lookup"><span data-stu-id="49850-p116">A. See [During and after your data move](during-and-after-your-data-move.md) for a complete list of features that may be limited during portions of the data move for each service.</span></span> 
  
 <span data-ttu-id="49850-162">**Q. Comment savoir que le déplacement est terminé ?**</span><span class="sxs-lookup"><span data-stu-id="49850-162">**Q. How do I know the move is complete?**</span></span>
  
<span data-ttu-id="49850-p117">R. Surveillez le centre de messages Office 365 dans l'attente de la confirmation de la fin du déplacement des données de chaque service. Une fois que les données de chaque service sont déplacées, nous vous en informons par message. Vous obtiendrez donc trois messages indiquant : un pour Exchange Online, un pour SharePoint Online et un pour Skype Entreprise Online.</span><span class="sxs-lookup"><span data-stu-id="49850-p117">A. Watch the Office 365 message center for confirmation that the move of each service's data is complete. When each service's data is moved, we'll post a completion notice so you'll get three completion notices: one each for Exchange Online, SharePoint Online, and Skype for Business Online.</span></span>
  
<span data-ttu-id="49850-166">Si vous rencontrez des problèmes après le déplacement, contactez le [support Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) pour obtenir de l'aide.</span><span class="sxs-lookup"><span data-stu-id="49850-166">If you see any issues after the move, contact [Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) to get assistance.</span></span> 
  
 <span data-ttu-id="49850-167">**Q : quelles données pour Office 365 sont stockées dans la nouvelle géographiques de centre de données ?**</span><span class="sxs-lookup"><span data-stu-id="49850-167">**Q. What data for Office 365 is stored in the new datacenter geos?**</span></span>
  
<span data-ttu-id="49850-p118">R. Si une dispositions client son client dans un de la nouvelle géographiques du centre de données, Microsoft stocke les données de client suivants au repos dans la zone géographique :</span><span class="sxs-lookup"><span data-stu-id="49850-p118">A. If a customer provisions its tenant in one of the new datacenter geos, Microsoft stores the following customer data at rest within the geo:</span></span>
  
- <span data-ttu-id="49850-170">Contenu de boîte aux lettres Exchange Online (corps de courrier électronique, entrées de calendrier et contenu de pièces jointes)</span><span class="sxs-lookup"><span data-stu-id="49850-170">Exchange Online mailbox content (e-mail body, calendar entries, and the content of email attachments)</span></span>
    
- <span data-ttu-id="49850-171">Contenu de site SharePoint Online et fichiers stockés dans ce site, y compris le contenu Project Online et Access Online</span><span class="sxs-lookup"><span data-stu-id="49850-171">SharePoint Online site content and the files stored within that site, including Project Online and Access Online content.</span></span>
    
<span data-ttu-id="49850-172">En outre, ces données ne sont pas répliquées en dehors de la zone géographique.</span><span class="sxs-lookup"><span data-stu-id="49850-172">In addition, this data is not replicated outside of the geo.</span></span>
  
 <span data-ttu-id="49850-173">**Q : je suis un client Office 365 de la nouvelle géographiques de centre de données, mais lorsque j’inscrit, j’ai sélectionné un autre pays. Comment puis-je être déplacé vers le nouveau localisés de centre de données ?**</span><span class="sxs-lookup"><span data-stu-id="49850-173">**Q. I am an Office 365 customer in one of the new datacenter geos, but when I signed up, I selected a different country. How can I be moved to the new datacenter geo?**</span></span>
  
<span data-ttu-id="49850-p119">R. Malheureusement, il n'est pas possible de modifier le pays associé à votre client. Au lieu de cela, vous devez créer un client Office 365 avec un nouvel abonnement et déplacer manuellement les utilisateurs et les données vers le nouveau client.</span><span class="sxs-lookup"><span data-stu-id="49850-p119">A. Unfortunately, it is not possible to change the country associated with your tenant. Instead, you need to create a new Office 365 tenant with a new subscription and manually move your users and data to the new tenant.</span></span>
  
 <span data-ttu-id="49850-177">**Q. Ma facture sera-t-elle modifiée ?**</span><span class="sxs-lookup"><span data-stu-id="49850-177">**Q. Will there be any changes on my bill?**</span></span>
  
<span data-ttu-id="49850-p120">R. Dans la plupart des cas, les clients ne verront pas de modification sur leur facture.</span><span class="sxs-lookup"><span data-stu-id="49850-p120">A. In most cases there are no changes that customers in will see on their billing statement.</span></span>
  
<span data-ttu-id="49850-p121">Microsoft facturera à tous les clients australiens d'Office 365 un montant supplémentaire correspondant à la taxe australienne sur les produits et services pour les services Office 365 et leur enverra des factures fiscales. Cette modification a lieu car la taxe australienne sur les produits et services est due sur la fourniture taxable de produits et de services fournis et proposés en Australie.</span><span class="sxs-lookup"><span data-stu-id="49850-p121">Microsoft will charge all Australian customers of Office 365 an additional amount equal to the Australian GST for Office 365 services and will issue tax invoices. This change will occur because Australian GST is payable on taxable supplies of goods and services provided and offered in Australia.</span></span>
  
 <span data-ttu-id="49850-182">**Q. Que se passe-t-il si nous sommes en train de migrer des données de messagerie électronique vers Office 365 lors du déplacement d'Exchange Online ?**</span><span class="sxs-lookup"><span data-stu-id="49850-182">**Q. What happens if we are in process of email data migration to Office 365 during the Exchange Online move?**</span></span>
  
<span data-ttu-id="49850-p122">R. Si des courriers électroniques sont en cours de migration, toutes les boîtes aux lettres individuelles actuellement en cours de migration seront annulées en attendant la finalisation du déplacement du client. La migration de ces boîtes aux lettres redémarrera automatiquement lorsque le client sera dans les centres de données cible.</span><span class="sxs-lookup"><span data-stu-id="49850-p122">A. If email migrations are in progress, any individual mailboxes that are currently being migrated will be canceled while the tenant move finalizes, and migration of those mailboxes will automatically restart once the tenant is in the target datacenters.</span></span>
  
 <span data-ttu-id="49850-185">**Q : une fois que les données sont déplacées en dehors de la précédente localisés de centre de données, est qu’il retiré de ces centres de données ?**</span><span class="sxs-lookup"><span data-stu-id="49850-185">**Q. After data is moved out of the previous datacenter geo, is it removed from those datacenters?**</span></span>
  
<span data-ttu-id="49850-p123">R. Oui, les anciennes données seront supprimées définitivement après un certain temps.</span><span class="sxs-lookup"><span data-stu-id="49850-p123">A. Yes, the old data will be purged after a period of time.</span></span>
  
 <span data-ttu-id="49850-188">**Q. Puis-je piloter certains utilisateurs ?**</span><span class="sxs-lookup"><span data-stu-id="49850-188">**Q. Can I pilot some users?**</span></span>
  
<span data-ttu-id="49850-p124">R. lorsque votre client Office 365 est déplacé vers un nouveau localisés de centre de données, tous les utilisateurs sont déplacés à la fois. Vous pouvez créer un client d’évaluation distinct pour tester la connectivité, mais le client d’évaluation ne peut être combiné en aucune manière avec votre client existant.</span><span class="sxs-lookup"><span data-stu-id="49850-p124">A. When your Office 365 tenant is moved to a new datacenter geo, all users are moved at once. You can create a separate trial tenant to test connectivity, but the trial tenant can't be combined in any way with your existing tenant.</span></span>
  
 <span data-ttu-id="49850-192">**Q. Comment serai-je averti du déplacement et qui, au sein de mon entreprise, en sera averti ?**</span><span class="sxs-lookup"><span data-stu-id="49850-192">**Q. How will I be notified about the move and who at my company will be notified?**</span></span>
  
<span data-ttu-id="49850-p125">R. Nous vous avertirons par le biais du centre de message Office 365, qui est visible par toutes les personnes dotées d'autorisations d'administrateur dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="49850-p125">A. We'll use the Office 365 message center, which is visible to anyone with any admin permissions in Office 365.</span></span>
  
 <span data-ttu-id="49850-195">**Q. Je ne souhaite pas attendre que Microsoft déplace mes données. Puis-je simplement créer un client et le déplacer moi-même ?**</span><span class="sxs-lookup"><span data-stu-id="49850-195">**Q. I don't want to wait for Microsoft to move my data. Can I just create a new tenant and move myself?**</span></span>
  
<span data-ttu-id="49850-p126">R. Oui, toutefois le processus ne sera pas aussi transparent que s'il était effectué par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="49850-p126">A. Yes, however the process will not be as seamless as if Microsoft were to perform the data move.</span></span>
  
<span data-ttu-id="49850-p127">Si vous créez un nouveau client une fois la nouvelle localisés de centre de données est disponible, le nouveau client sera hébergé dans la nouvelle localisés. Ce nouveau client est complètement distinct de votre client précédent et vous êtes responsable du déplacement de toutes les boîtes aux lettres utilisateur, le contenu de site, noms de domaine et d’autres données. Notez que vous ne peut pas déplacer le nom du client à partir d’un client vers un autre. Nous vous recommandons d’attendre le programme move fourni par Microsoft comme nous allons prendre en charge de transférer tous les paramètres, les données et les abonnements pour vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="49850-p127">If you create a new tenant after the new datacenter geo is available, the new tenant will be hosted in the new geo. This new tenant is completely separate from your previous tenant and you would be responsible for moving all user mailboxes, site content, domain names, and any other data. Note that you can't move the tenant name from one tenant to another. We recommend that you wait for the move program provided by Microsoft as we'll take care of moving all settings, data, and subscriptions for your users.</span></span>
  
 <span data-ttu-id="49850-202">**Q. Je ne suis pas prêt pour le déplacement, puis-je choisir une date spécifique ?**</span><span class="sxs-lookup"><span data-stu-id="49850-202">**Q. I'm not ready to be moved, can I pick a specific move date?**</span></span>
  
<span data-ttu-id="49850-p128">R. Vous ne pouvez pas modifier la date de déplacement des données client de chaque service. Les déplacements de données sont des opérations principales qui ont une incidence minime sur les utilisateurs finals.</span><span class="sxs-lookup"><span data-stu-id="49850-p128">A. It is not possible for you to change when each service's customer data will be moved. Data moves are a back-end operation with minimal impact to end-users.</span></span>
  
 <span data-ttu-id="49850-206">**Q : Mes données client a déjà été déplacées vers un nouveau localisés de centre de données. Puis-je déplacer retour ?**</span><span class="sxs-lookup"><span data-stu-id="49850-206">**Q. My customer data has already been moved to a new datacenter geo. Can I move back?**</span></span>
  
<span data-ttu-id="49850-p129">R. il n’est pas possible. Les clients qui ont été déplacés vers les nouveaux centres de données localisés ne peut pas être ramenés. En tant que client dans n’importe quel localisés, vous serez confronté à la même qualité de service, de performances et de contrôles de sécurité comme auparavant.</span><span class="sxs-lookup"><span data-stu-id="49850-p129">A. This is not possible. Customers who have been moved to new geo datacenters cannot be moved back. As a customer in any geo, you will experience the same quality of service, performance, and security controls as you did before.</span></span>
  
 <span data-ttu-id="49850-211">**Q. les nouveau géographiques datacenter utiliser les mêmes versions des services Office 365 en tant que les zones géographiques de centre de données actuel ?**</span><span class="sxs-lookup"><span data-stu-id="49850-211">**Q. Do the new datacenter geos use the same versions of Office 365 services as the current datacenter geos?**</span></span>
  
<span data-ttu-id="49850-p130">R. Oui.</span><span class="sxs-lookup"><span data-stu-id="49850-p130">A. Yes.</span></span>
  
 <span data-ttu-id="49850-214">**Q. Les clients Office 365 hébergés dans les nouveaux centres de données seront-ils disponibles pour les utilisateurs situés dans un autre pays ?**</span><span class="sxs-lookup"><span data-stu-id="49850-214">**Q. Will Office 365 tenants hosted in the new datacenters be available to users outside of the country?**</span></span>
  
<span data-ttu-id="49850-p131">R. Oui. Microsoft gère un vaste réseau mondial avec des connexions Internet publiques dans plus de 50 endroits dans 23 pays du monde et des accords d'homologation avec plus de 1 500 fournisseurs de services Internet. Les utilisateurs pourront accéder aux centres de données par Internet, où qu'ils soient.</span><span class="sxs-lookup"><span data-stu-id="49850-p131">A. Yes. Microsoft maintains a large global network with public Internet connections in more than 50 locations in 23 countries around the world with peering agreements with more than 1,500 Internet Service Providers (ISPs). Users will be able to access the datacenters from wherever they are on the Internet.</span></span>
  

