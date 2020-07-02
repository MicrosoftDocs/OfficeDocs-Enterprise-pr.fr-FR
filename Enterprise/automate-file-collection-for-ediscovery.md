---
title: Automatiser la collecte de fichiers pour eDiscovery
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Résumé : Apprenez à automatiser la collecte de fichiers à partir des ordinateurs des utilisateurs pour eDiscovery.'
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997975"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="4d631-103">Automatiser la collecte de fichiers pour eDiscovery</span><span class="sxs-lookup"><span data-stu-id="4d631-103">Automate file collection for eDiscovery</span></span>

<span data-ttu-id="4d631-104">All companies face the potential of lawsuits or other types of legal action.</span><span class="sxs-lookup"><span data-stu-id="4d631-104">All companies face the potential of lawsuits or other types of legal action.</span></span> <span data-ttu-id="4d631-105">While legal departments work to reduce that exposure, litigation is a fact of business life.</span><span class="sxs-lookup"><span data-stu-id="4d631-105">While legal departments work to reduce that exposure, litigation is a fact of business life.</span></span> <span data-ttu-id="4d631-106">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span><span class="sxs-lookup"><span data-stu-id="4d631-106">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="4d631-107">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span><span class="sxs-lookup"><span data-stu-id="4d631-107">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span></span> <span data-ttu-id="4d631-108">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span><span class="sxs-lookup"><span data-stu-id="4d631-108">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span></span> <span data-ttu-id="4d631-109">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span><span class="sxs-lookup"><span data-stu-id="4d631-109">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="4d631-110">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span><span class="sxs-lookup"><span data-stu-id="4d631-110">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span></span> <span data-ttu-id="4d631-111">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="4d631-111">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span></span> <span data-ttu-id="4d631-112">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span><span class="sxs-lookup"><span data-stu-id="4d631-112">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="4d631-113">Descriptif de cette solution</span><span class="sxs-lookup"><span data-stu-id="4d631-113">What this solution does</span></span>

<span data-ttu-id="4d631-114">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span><span class="sxs-lookup"><span data-stu-id="4d631-114">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span></span> <span data-ttu-id="4d631-115">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="4d631-115">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span></span> <span data-ttu-id="4d631-116">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="4d631-116">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span></span> <span data-ttu-id="4d631-117">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="4d631-117">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="4d631-118">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span><span class="sxs-lookup"><span data-stu-id="4d631-118">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span></span> <span data-ttu-id="4d631-119">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span><span class="sxs-lookup"><span data-stu-id="4d631-119">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span></span> <span data-ttu-id="4d631-120">You will have to collect them manually.</span><span class="sxs-lookup"><span data-stu-id="4d631-120">You will have to collect them manually.</span></span> <span data-ttu-id="4d631-121">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span><span class="sxs-lookup"><span data-stu-id="4d631-121">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="4d631-122">Le diagramme suivant vous guide à travers les étapes et les éléments de la solution.</span><span class="sxs-lookup"><span data-stu-id="4d631-122">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![Vue d’ensemble de la solution de regroupement automatique de fichiers](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="4d631-124">\*\*\*\*Légende\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="4d631-124">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![légende magenta 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="4d631-126">Créez un objet de stratégie de groupe (GPO) et associez-le au script d’ouverture de session de collecte.</span><span class="sxs-lookup"><span data-stu-id="4d631-126">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![légende magenta 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="4d631-128">Configurez le filtre de sécurité de l’objet de stratégie de groupe pour appliquer l’objet de stratégie de groupe uniquement au groupe des dépositaires.</span><span class="sxs-lookup"><span data-stu-id="4d631-128">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![légende magenta 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="4d631-130">Un dépositaire ouvre une session et l’objet de stratégie de groupe s’exécute, appelant le script d’ouverture de session de collecte</span><span class="sxs-lookup"><span data-stu-id="4d631-130">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![légende magenta 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="4d631-132">Le script d’ouverture de session de collecte répertorie tous les lecteurs connectés localement à l’ordinateur des dépositaires, en cherchant les fichiers que vous souhaitez et en enregistrant leur emplacement.</span><span class="sxs-lookup"><span data-stu-id="4d631-132">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![légende magenta 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="4d631-134">Le script d’ouverture de session de collecte copie les fichiers inventoriés sur un partage de fichiers caché sur le serveur intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="4d631-134">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![légende magenta 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="4d631-136">(Option A) Exécutez manuellement le script d'importation PST pour importer les fichiers PST collectés dans Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="4d631-136">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![légende magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="4d631-138">(Option B) À l’aide de l’outil et du processus d’importation de Microsoft 365, importez les fichiers PST collectés dans Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="4d631-138">(Option B) Using the Microsoft 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![légende magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="4d631-140">Déplacez tous les fichiers collectés vers un partage de fichiers Azure pour un stockage à long terme avec le runbook MoveToColdStorageSystem Center Orchestrator 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="4d631-140">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![légende magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="4d631-142">Indexez les fichiers dans le partage des fichiers de stockage froid avec SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="4d631-142">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![légende magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="4d631-144">Effectuez eDiscovery sur le contenu dans l'espace de stockage froid et le Exchange Server 2013 sur site.</span><span class="sxs-lookup"><span data-stu-id="4d631-144">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![légende magenta 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="4d631-146">Effectuer eDiscovery sur le contenu de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="4d631-146">Perform eDiscovery on content in Microsoft 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="4d631-147">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4d631-147">Prerequisites</span></span>

<span data-ttu-id="4d631-148">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="4d631-148">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span></span> <span data-ttu-id="4d631-149">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span><span class="sxs-lookup"><span data-stu-id="4d631-149">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span></span> <span data-ttu-id="4d631-150">You must have the base configuration in place before you configure the solution itself.</span><span class="sxs-lookup"><span data-stu-id="4d631-150">You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="4d631-151">Configuration de base</span><span class="sxs-lookup"><span data-stu-id="4d631-151">Base configuration</span></span>

|<span data-ttu-id="4d631-152">**Élément**</span><span class="sxs-lookup"><span data-stu-id="4d631-152">**Element**</span></span>|<span data-ttu-id="4d631-153">**Lien**</span><span class="sxs-lookup"><span data-stu-id="4d631-153">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4d631-154">Domaine Services de domaine Active Directory (AD DS)</span><span class="sxs-lookup"><span data-stu-id="4d631-154">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="4d631-155">Connectivité Internet à partir de votre réseau local</span><span class="sxs-lookup"><span data-stu-id="4d631-155">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="4d631-156">SQL Server 2012 pour prendre en charge SharePoint 2013 et System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="4d631-156">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="4d631-157">Déploiement de System Center 2012 - Orchestrator</span><span class="sxs-lookup"><span data-stu-id="4d631-157">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="4d631-158">Sur site ou SharePoint 2013 basé sur Azure pour eDiscovery (requis pour l'option A)</span><span class="sxs-lookup"><span data-stu-id="4d631-158">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="4d631-159">Serveur de partage de fichiers sur site pour le placement en zone de transit</span><span class="sxs-lookup"><span data-stu-id="4d631-159">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="4d631-160">Exchange Server 2013 sur site pour l'importation du PST de l'option A</span><span class="sxs-lookup"><span data-stu-id="4d631-160">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="4d631-161">La mise à jour cumulative 5 (15.913.22) est disponible sur le site [Mise à jour cumulative 5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span><span class="sxs-lookup"><span data-stu-id="4d631-161">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="4d631-162">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="4d631-162">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="4d631-163">Déploiement de System Center 2012 - Orchestrator</span><span class="sxs-lookup"><span data-stu-id="4d631-163">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="4d631-164">Microsoft 365 E3 avec Exchange Online et SharePoint Online (requis pour l’option B)</span><span class="sxs-lookup"><span data-stu-id="4d631-164">Microsoft 365 E3 with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="4d631-165">Pour vous inscrire à un abonnement Microsoft 365 E3, consultez la rubrique [microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span><span class="sxs-lookup"><span data-stu-id="4d631-165">To sign up for a Microsoft 365 E3 subscription, see [Microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span></span>  <br/> |
|<span data-ttu-id="4d631-166">Abonnement Azure avec un ordinateur virtuel</span><span class="sxs-lookup"><span data-stu-id="4d631-166">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="4d631-167">Pour vous inscrire à Azure, voir la page d'[abonnement à Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span><span class="sxs-lookup"><span data-stu-id="4d631-167">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="4d631-168">Une connexion VPN entre votre réseau local et votre abonnement Azure</span><span class="sxs-lookup"><span data-stu-id="4d631-168">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="4d631-169">Pour configurer un tunnel VPN entre votre abonnement Azure et votre réseau local, voir [Connecter un réseau local à Microsoft Azure Virtual Network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span><span class="sxs-lookup"><span data-stu-id="4d631-169">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="4d631-170">SharePoint 2013eDiscovery configuré pour effectuer une recherche dans SharePoint et Exchange Server 2013, et éventuellement Lync Server 2013</span><span class="sxs-lookup"><span data-stu-id="4d631-170">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="4d631-171">Pour configurer la eDiscovery de cette façon, voir [Configurer eDiscovery dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) et[Guide de laboratoire de test : configurez eDiscovery pour un laboratoire de test de partages de fichiers Exchange, Lync, SharePoint et Windows ](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span><span class="sxs-lookup"><span data-stu-id="4d631-171">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="4d631-172">eDiscovery dans Microsoft 365 pour SharePoint Online et Exchange Online</span><span class="sxs-lookup"><span data-stu-id="4d631-172">eDiscovery in Microsoft 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="4d631-173">Pour configurer la fonctionnalité eDiscovery dans Microsoft 365, voir [configurer un centre eDiscovery dans SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span><span class="sxs-lookup"><span data-stu-id="4d631-173">To configure eDiscovery in Microsoft 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="4d631-174">Configurer l’environnement</span><span class="sxs-lookup"><span data-stu-id="4d631-174">Configure the environment</span></span>

<span data-ttu-id="4d631-175">Maintenant que la configuration de base est en place, vous pouvez passer à la configuration de la solution elle-même.</span><span class="sxs-lookup"><span data-stu-id="4d631-175">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="4d631-176">Partage de fichiers intermédiaires</span><span class="sxs-lookup"><span data-stu-id="4d631-176">Staging file share</span></span>

1. <span data-ttu-id="4d631-177">Dans le domaine local, créez un groupe de sécurité global nommé Custodians.</span><span class="sxs-lookup"><span data-stu-id="4d631-177">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="4d631-178">Create a hidden file share for the files that are collected from Custodians computers.</span><span class="sxs-lookup"><span data-stu-id="4d631-178">Create a hidden file share for the files that are collected from Custodians computers.</span></span> <span data-ttu-id="4d631-179">This should be on an on-premises server.</span><span class="sxs-lookup"><span data-stu-id="4d631-179">This should be on an on-premises server.</span></span> <span data-ttu-id="4d631-180">For example, on a server called Staging, create a file share called Cases$.</span><span class="sxs-lookup"><span data-stu-id="4d631-180">For example, on a server called Staging, create a file share called Cases$.</span></span> <span data-ttu-id="4d631-181">The **$** is required to make this a hidden share.</span><span class="sxs-lookup"><span data-stu-id="4d631-181">The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="4d631-182">Définissez les autorisations de partage suivantes :</span><span class="sxs-lookup"><span data-stu-id="4d631-182">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="4d631-183">Dépositaires : Modifier, Lire</span><span class="sxs-lookup"><span data-stu-id="4d631-183">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="4d631-184">Administrateurs : Contrôle total</span><span class="sxs-lookup"><span data-stu-id="4d631-184">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="4d631-185">Sous-système approuvé Exchange : Modifier, Lire</span><span class="sxs-lookup"><span data-stu-id="4d631-185">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="4d631-186">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="4d631-186">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span></span> <span data-ttu-id="4d631-187">Set the following permissions for the Custodians group:</span><span class="sxs-lookup"><span data-stu-id="4d631-187">Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="4d631-188">**Type : Refuser**</span><span class="sxs-lookup"><span data-stu-id="4d631-188">**Type: Deny**</span></span>
    
  - <span data-ttu-id="4d631-189">**S'applique à : Ce dossier, les sous-dossiers et les fichiers**</span><span class="sxs-lookup"><span data-stu-id="4d631-189">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="4d631-190">Cliquez sur **Autorisations avancées** et sélectionnez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4d631-190">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="4d631-191">**Lecture des attributs**</span><span class="sxs-lookup"><span data-stu-id="4d631-191">**Read attributes**</span></span>
    
  - <span data-ttu-id="4d631-192">**Lecture des attributs étendus**</span><span class="sxs-lookup"><span data-stu-id="4d631-192">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="4d631-193">**Autorisations de lecture**</span><span class="sxs-lookup"><span data-stu-id="4d631-193">**Read permissions**</span></span>
    
6. <span data-ttu-id="4d631-194">Testez l’accès au partage de fichiers Cases$ en effectuant les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4d631-194">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="4d631-195">Ajoutez un utilisateur au groupe des dépositaires.</span><span class="sxs-lookup"><span data-stu-id="4d631-195">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="4d631-196">Placez un fichier dans le dossier Cases$.</span><span class="sxs-lookup"><span data-stu-id="4d631-196">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="4d631-197">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span><span class="sxs-lookup"><span data-stu-id="4d631-197">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span></span> <span data-ttu-id="4d631-198">You shouldn't see the **Cases$** share listed.</span><span class="sxs-lookup"><span data-stu-id="4d631-198">You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="4d631-199">Manually type the full path to the Cases$ share into Explorer.</span><span class="sxs-lookup"><span data-stu-id="4d631-199">Manually type the full path to the Cases$ share into Explorer.</span></span> <span data-ttu-id="4d631-200">This should open the Cases$ share.</span><span class="sxs-lookup"><span data-stu-id="4d631-200">This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="4d631-201">Try to open the file you previously placed in the share.</span><span class="sxs-lookup"><span data-stu-id="4d631-201">Try to open the file you previously placed in the share.</span></span> <span data-ttu-id="4d631-202">This should fail.</span><span class="sxs-lookup"><span data-stu-id="4d631-202">This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="4d631-203">Script d’ouverture de session</span><span class="sxs-lookup"><span data-stu-id="4d631-203">Logon script</span></span>

1. <span data-ttu-id="4d631-204">Copiez et collez ce script Windows PowerShell dans le bloc-notes :</span><span class="sxs-lookup"><span data-stu-id="4d631-204">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. <span data-ttu-id="4d631-205">Enregistrez le script ci-dessus sous CollectionScript.ps1 dans un emplacement facile à trouver, par exemple C:\\AFCScripts.</span><span class="sxs-lookup"><span data-stu-id="4d631-205">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="4d631-206">Use the Go To feature in Notepad.</span><span class="sxs-lookup"><span data-stu-id="4d631-206">Use the Go To feature in Notepad.</span></span> <span data-ttu-id="4d631-207">Make the following changes, as needed:</span><span class="sxs-lookup"><span data-stu-id="4d631-207">Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="4d631-208">**Ligne #**</span><span class="sxs-lookup"><span data-stu-id="4d631-208">**Line #**</span></span>|<span data-ttu-id="4d631-209">**Ce que vous devez modifier**</span><span class="sxs-lookup"><span data-stu-id="4d631-209">**What you need to change**</span></span>|<span data-ttu-id="4d631-210">**Obligatoire/facultatif**</span><span class="sxs-lookup"><span data-stu-id="4d631-210">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4d631-211">71</span><span class="sxs-lookup"><span data-stu-id="4d631-211">71</span></span>  <br/> |<span data-ttu-id="4d631-212">**$FileTypes** variable.</span><span class="sxs-lookup"><span data-stu-id="4d631-212">**$FileTypes** variable.</span></span> <span data-ttu-id="4d631-213">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span><span class="sxs-lookup"><span data-stu-id="4d631-213">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span></span> <br/> |<span data-ttu-id="4d631-214">Facultatif</span><span class="sxs-lookup"><span data-stu-id="4d631-214">Optional</span></span>  <br/> |
|<span data-ttu-id="4d631-215">76 et 77</span><span class="sxs-lookup"><span data-stu-id="4d631-215">76 and 77</span></span>  <br/> |<span data-ttu-id="4d631-216">Change the way the **$CaseNo** variable is built to suit your needs.</span><span class="sxs-lookup"><span data-stu-id="4d631-216">Change the way the **$CaseNo** variable is built to suit your needs.</span></span> <span data-ttu-id="4d631-217">The script captures the current date and time and appends the user name to it.</span><span class="sxs-lookup"><span data-stu-id="4d631-217">The script captures the current date and time and appends the user name to it.</span></span> <br/> |<span data-ttu-id="4d631-218">Facultatif</span><span class="sxs-lookup"><span data-stu-id="4d631-218">Optional</span></span>  <br/> |
|<span data-ttu-id="4d631-219">80</span><span class="sxs-lookup"><span data-stu-id="4d631-219">80</span></span>  <br/> |<span data-ttu-id="4d631-220">La variable **$CaseRootLocation** doit être configurée pour votre partage des fichiers de collecte de serveurs intermédiaires. Par exemple **\\\\Staging\\Cases$**</span><span class="sxs-lookup"><span data-stu-id="4d631-220">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="4d631-221">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="4d631-221">Required</span></span>  <br/> |
   
4. <span data-ttu-id="4d631-222">Placez le fichier CollectionScript.ps1 dans le partage des fichiers d’accès réseau sur un contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="4d631-222">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="4d631-223">Configuration de l’objet de stratégie de groupe pour le script d’ouverture de session et le groupe de dépositaires</span><span class="sxs-lookup"><span data-stu-id="4d631-223">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="4d631-224">Configurez un script d'ouverture de session pour le groupe de dépositaires en suivant les instructions de la section concernant la manière d'affecter des scripts d'ouverture de session utilisateur dans la rubrique relative à l'[utilisation des scripts de démarrage, d'arrêt, d'ouverture et de fermeture de session dans la stratégie de groupe](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span><span class="sxs-lookup"><span data-stu-id="4d631-224">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="4d631-225">Supprimez les utilisateurs authentifiés de **Filtrage de sécurité** et ajoutez le groupe des dépositaires.</span><span class="sxs-lookup"><span data-stu-id="4d631-225">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="4d631-226">Importation du PST de l'option A, script pour Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="4d631-226">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="4d631-227">Copiez et collez le script Windows PowerShell suivant dans le bloc-notes :</span><span class="sxs-lookup"><span data-stu-id="4d631-227">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. <span data-ttu-id="4d631-228">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span><span class="sxs-lookup"><span data-stu-id="4d631-228">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span></span> <span data-ttu-id="4d631-229">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span><span class="sxs-lookup"><span data-stu-id="4d631-229">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="4d631-230">Utilisez la fonctionnalité Accédez à dans le bloc-notes et apportez les modifications suivantes, selon vos besoins :</span><span class="sxs-lookup"><span data-stu-id="4d631-230">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="4d631-231">**Ligne #**</span><span class="sxs-lookup"><span data-stu-id="4d631-231">**Line #**</span></span>|<span data-ttu-id="4d631-232">**Ce que vous devez modifier**</span><span class="sxs-lookup"><span data-stu-id="4d631-232">**What you need to change**</span></span>|<span data-ttu-id="4d631-233">**Obligatoire/facultatif**</span><span class="sxs-lookup"><span data-stu-id="4d631-233">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4d631-234">12 </span><span class="sxs-lookup"><span data-stu-id="4d631-234">12</span></span>  <br/> |<span data-ttu-id="4d631-235">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span><span class="sxs-lookup"><span data-stu-id="4d631-235">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span></span> <span data-ttu-id="4d631-236">Change this if necessary.</span><span class="sxs-lookup"><span data-stu-id="4d631-236">Change this if necessary.</span></span> <br/> |<span data-ttu-id="4d631-237">Facultatif</span><span class="sxs-lookup"><span data-stu-id="4d631-237">Optional</span></span>  <br/> |
|<span data-ttu-id="4d631-238">17 </span><span class="sxs-lookup"><span data-stu-id="4d631-238">17</span></span>  <br/> |<span data-ttu-id="4d631-239">**$ConnectionUri** doit être configuré pour votre propre serveur.</span><span class="sxs-lookup"><span data-stu-id="4d631-239">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="4d631-240">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span><span class="sxs-lookup"><span data-stu-id="4d631-240">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span></span> <span data-ttu-id="4d631-241">It won't work with https:.</span><span class="sxs-lookup"><span data-stu-id="4d631-241">It won't work with https:.</span></span>          |<span data-ttu-id="4d631-242">Requis</span><span class="sxs-lookup"><span data-stu-id="4d631-242">Required</span></span>  <br/> |
   
4. <span data-ttu-id="4d631-243">Vérifiez que le compte Sous-système approuvé Exchange dispose des autorisations de lecture, écriture et exécution sur le partage \\\\Staging\\Cases$.</span><span class="sxs-lookup"><span data-stu-id="4d631-243">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="4d631-244">Le script d’importation PST nécessite les deux paramètres d’entrée suivants :</span><span class="sxs-lookup"><span data-stu-id="4d631-244">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="4d631-245">**$SourcePath** L'emplacement des fichiers PST à importer, par exemple \\\\Staging\\Cases$.</span><span class="sxs-lookup"><span data-stu-id="4d631-245">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="4d631-246">**$MailboxAlias** L'alias de la boîte aux lettres cible qui recevra les éléments de messagerie importés.</span><span class="sxs-lookup"><span data-stu-id="4d631-246">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="4d631-247">Par exemple, si vous voulez importer tous les fichiers PST depuis le chemin \\\\Staging\Cases$ vers une boîte aux lettres avec l'alias eDiscoveryMailbox, vous devrez exécuter le script comme suit`\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span><span class="sxs-lookup"><span data-stu-id="4d631-247">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="4d631-248">Importation des fichiers PST de l'option B, pour Exchange Online</span><span class="sxs-lookup"><span data-stu-id="4d631-248">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="4d631-249">Create the mailbox structure to place the imported PST files into.</span><span class="sxs-lookup"><span data-stu-id="4d631-249">Create the mailbox structure to place the imported PST files into.</span></span> <span data-ttu-id="4d631-250">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span><span class="sxs-lookup"><span data-stu-id="4d631-250">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="4d631-251">Stockage froid</span><span class="sxs-lookup"><span data-stu-id="4d631-251">Cold storage</span></span>

1. <span data-ttu-id="4d631-252">Créez un partage de fichiers sur la Ordinateur virtuel Azure où tous les fichiers collectés seront placés, par exemple \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="4d631-252">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="4d631-253">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span><span class="sxs-lookup"><span data-stu-id="4d631-253">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span></span> <span data-ttu-id="4d631-254">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span><span class="sxs-lookup"><span data-stu-id="4d631-254">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="4d631-255">Si vous envisagez l'importation de fichiers PST à partir de \\\\AZFile1\\ContentColdStorage, accordez les autorisations de lecture, écriture et exécution du sous-système approuvé Exchange au partage.</span><span class="sxs-lookup"><span data-stu-id="4d631-255">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="4d631-256">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="4d631-256">Orchestrator</span></span>

1. <span data-ttu-id="4d631-257">Téléchargez le [runbook MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) à partir du Centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4d631-257">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="4d631-258">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span><span class="sxs-lookup"><span data-stu-id="4d631-258">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span></span> <span data-ttu-id="4d631-259">Click the **Actions** menu, and the click **Import**.</span><span class="sxs-lookup"><span data-stu-id="4d631-259">Click the **Actions** menu, and the click **Import**.</span></span> <span data-ttu-id="4d631-260">The **Import** dialog box appears.</span><span class="sxs-lookup"><span data-stu-id="4d631-260">The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="4d631-261">Dans la boîte **Emplacement du fichier**, saisissez le chemin d'accès et le nom du runbook que vous souhaitez importer ou cliquez sur les points de suspension ( **...**) pour rechercher le fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="4d631-261">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="4d631-262">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span><span class="sxs-lookup"><span data-stu-id="4d631-262">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span></span> <span data-ttu-id="4d631-263">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span><span class="sxs-lookup"><span data-stu-id="4d631-263">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="4d631-264">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="4d631-264">Click **Finish**.</span></span>
    
6. <span data-ttu-id="4d631-265">Modifiez le runbook **MoveFilesToColdStorage** comme suit :</span><span class="sxs-lookup"><span data-stu-id="4d631-265">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="4d631-266">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span><span class="sxs-lookup"><span data-stu-id="4d631-266">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="4d631-267">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="4d631-267">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="4d631-268">Select **Create a file with a unique name**.</span><span class="sxs-lookup"><span data-stu-id="4d631-268">Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="4d631-269">Activité **Supprimer le dossier**: définissez le **chemin d'accès** sur le partage des fichiers de collecte, par exemple \\\\Staging\\cases$\\*, et sélectionnez **Supprimer tous les fichiers et sous-dossiers**.</span><span class="sxs-lookup"><span data-stu-id="4d631-269">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="4d631-270">Déployer le runbook **MoveToColdStorage** en utilisant les procédures décrites dans l'article sur le[déploiement de runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span><span class="sxs-lookup"><span data-stu-id="4d631-270">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="4d631-271">Recherche du stockage froid pour une instance SharePoint sur site</span><span class="sxs-lookup"><span data-stu-id="4d631-271">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="4d631-272">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="4d631-272">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="4d631-273">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="4d631-273">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="4d631-274">Start a full crawl.</span><span class="sxs-lookup"><span data-stu-id="4d631-274">Start a full crawl.</span></span> <span data-ttu-id="4d631-275">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="4d631-275">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="4d631-276">Utilisation de la solution</span><span class="sxs-lookup"><span data-stu-id="4d631-276">Using the solution</span></span>

<span data-ttu-id="4d631-277">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="4d631-277">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span></span> <span data-ttu-id="4d631-278">This section provides you with the procedures for all of them.</span><span class="sxs-lookup"><span data-stu-id="4d631-278">This section provides you with the procedures for all of them.</span></span> <span data-ttu-id="4d631-279">Your primary interaction with the solution will be in doing the following:</span><span class="sxs-lookup"><span data-stu-id="4d631-279">Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="4d631-280">Gestion de l’appartenance des utilisateurs dans le groupe des dépositaires.</span><span class="sxs-lookup"><span data-stu-id="4d631-280">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="4d631-281">Review the log files generated by the logon script.</span><span class="sxs-lookup"><span data-stu-id="4d631-281">Review the log files generated by the logon script.</span></span> <span data-ttu-id="4d631-282">The FileCopyErrors.log lists all the files that were not successfully copied.</span><span class="sxs-lookup"><span data-stu-id="4d631-282">The FileCopyErrors.log lists all the files that were not successfully copied.</span></span> <span data-ttu-id="4d631-283">You need to decide what you want to do with them</span><span class="sxs-lookup"><span data-stu-id="4d631-283">You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="4d631-284">Gestion du processus d’importation PST.</span><span class="sxs-lookup"><span data-stu-id="4d631-284">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="4d631-285">Déplacement des fichiers de collecte vers l’emplacement de stockage froid.</span><span class="sxs-lookup"><span data-stu-id="4d631-285">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="4d631-286">Toutes les autres étapes ne sont pas propres à cette solution.</span><span class="sxs-lookup"><span data-stu-id="4d631-286">All the other steps are not specific to this solution.</span></span> <span data-ttu-id="4d631-287">Il s’agit de tâches d’administration standard que vous effectuez dans SharePoint 2013, Microsoft 365 et Azure.</span><span class="sxs-lookup"><span data-stu-id="4d631-287">They are standard administrative tasks that you perform in SharePoint 2013, Microsoft 365, and Azure.</span></span> <span data-ttu-id="4d631-288">Il existe des aspects pour lesquels cette solution ne propose aucune recommandation et pour lesquels vous devrez utiliser votre meilleur jugement selon les besoins de votre société, tels que :</span><span class="sxs-lookup"><span data-stu-id="4d631-288">There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="4d631-289">Suivi de vos cas eDiscovery et de la répartition des dépositaires en fonction des cas.</span><span class="sxs-lookup"><span data-stu-id="4d631-289">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="4d631-290">Contrôle de la répartition des ensembles de collecte de fichiers en fonction des cas eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="4d631-290">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="4d631-291">Coordination du calendrier d’importation et des étapes de déplacement vers l’emplacement de stockage froid.</span><span class="sxs-lookup"><span data-stu-id="4d631-291">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="4d631-292">Gestion de l'espace de fichier utilisé dans Azure.</span><span class="sxs-lookup"><span data-stu-id="4d631-292">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="4d631-293">Gestion des boîtes aux lettres vers lesquelles les fichiers PST sont importés.</span><span class="sxs-lookup"><span data-stu-id="4d631-293">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="4d631-294">Sauvegarde et restauration de toutes les données locales.</span><span class="sxs-lookup"><span data-stu-id="4d631-294">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="4d631-295">Gestion de dépositaire</span><span class="sxs-lookup"><span data-stu-id="4d631-295">Custodian management</span></span>

- <span data-ttu-id="4d631-296">To start the automated file collection process for an individual user, add them to the Custodians group.</span><span class="sxs-lookup"><span data-stu-id="4d631-296">To start the automated file collection process for an individual user, add them to the Custodians group.</span></span> <span data-ttu-id="4d631-297">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span><span class="sxs-lookup"><span data-stu-id="4d631-297">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="4d631-298">Surveillance des fichiers collectés et examen des fichiers journaux</span><span class="sxs-lookup"><span data-stu-id="4d631-298">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="4d631-299">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span><span class="sxs-lookup"><span data-stu-id="4d631-299">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span></span> <span data-ttu-id="4d631-300">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span><span class="sxs-lookup"><span data-stu-id="4d631-300">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="4d631-301">When the collection is completed, open the collection folder, and browse to the _Log folder.</span><span class="sxs-lookup"><span data-stu-id="4d631-301">When the collection is completed, open the collection folder, and browse to the _Log folder.</span></span> <span data-ttu-id="4d631-302">In the _Log folder, you will see the following:</span><span class="sxs-lookup"><span data-stu-id="4d631-302">In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="4d631-303">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span><span class="sxs-lookup"><span data-stu-id="4d631-303">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span></span> <span data-ttu-id="4d631-304">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span><span class="sxs-lookup"><span data-stu-id="4d631-304">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="4d631-305">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span><span class="sxs-lookup"><span data-stu-id="4d631-305">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span></span> <span data-ttu-id="4d631-306">It will not create an inventory entry for every file on the user's computer.</span><span class="sxs-lookup"><span data-stu-id="4d631-306">It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="4d631-307">One log file named FileCopyErrors.log for each collection run.</span><span class="sxs-lookup"><span data-stu-id="4d631-307">One log file named FileCopyErrors.log for each collection run.</span></span> <span data-ttu-id="4d631-308">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span><span class="sxs-lookup"><span data-stu-id="4d631-308">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span></span> <span data-ttu-id="4d631-309">You will need to review this and decide what actions to take for these missed files.</span><span class="sxs-lookup"><span data-stu-id="4d631-309">You will need to review this and decide what actions to take for these missed files.</span></span> <span data-ttu-id="4d631-310">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span><span class="sxs-lookup"><span data-stu-id="4d631-310">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="4d631-311">Importation des fichiers PST de l'option A pour Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="4d631-311">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="4d631-312">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d631-312">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span></span> <span data-ttu-id="4d631-313">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span><span class="sxs-lookup"><span data-stu-id="4d631-313">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="4d631-314">Set the Execution policy to Unrestricted .</span><span class="sxs-lookup"><span data-stu-id="4d631-314">Set the Execution policy to Unrestricted .</span></span> <span data-ttu-id="4d631-315">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span><span class="sxs-lookup"><span data-stu-id="4d631-315">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="4d631-316">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span><span class="sxs-lookup"><span data-stu-id="4d631-316">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span></span> <span data-ttu-id="4d631-317">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span><span class="sxs-lookup"><span data-stu-id="4d631-317">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="4d631-318">Recherchez les erreurs dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="4d631-318">Review the output for errors.</span></span>
    
5. <span data-ttu-id="4d631-319">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span><span class="sxs-lookup"><span data-stu-id="4d631-319">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span></span> <span data-ttu-id="4d631-320">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span><span class="sxs-lookup"><span data-stu-id="4d631-320">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span></span> <span data-ttu-id="4d631-321">You will be prompted to remove each individual request from the queue.</span><span class="sxs-lookup"><span data-stu-id="4d631-321">You will be prompted to remove each individual request from the queue.</span></span> <span data-ttu-id="4d631-322">Respond as needed.</span><span class="sxs-lookup"><span data-stu-id="4d631-322">Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="4d631-323">Importation des fichiers PST de l'option B, pour Exchange Online</span><span class="sxs-lookup"><span data-stu-id="4d631-323">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="4d631-324">Pour placer les fichiers PST collectés dans Exchange Online, suivez les procédures décrites dans la section importer des fichiers dans Microsoft 365 via le [chargement réseau](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span><span class="sxs-lookup"><span data-stu-id="4d631-324">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Microsoft 365 through [network upload](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="4d631-325">Déplacement vers l’emplacement de stockage froid</span><span class="sxs-lookup"><span data-stu-id="4d631-325">Move to cold storage</span></span>

1. <span data-ttu-id="4d631-326">Exécutez l’runbook **runbook movetocoldstorage** à l’aide des procédures décrites dans [Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span><span class="sxs-lookup"><span data-stu-id="4d631-326">Run the **MoveToColdStorage** runbook using the procedures in [Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="4d631-327">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span><span class="sxs-lookup"><span data-stu-id="4d631-327">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="4d631-328">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span><span class="sxs-lookup"><span data-stu-id="4d631-328">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="4d631-329">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="4d631-329">eDiscovery</span></span>

1. <span data-ttu-id="4d631-330">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span><span class="sxs-lookup"><span data-stu-id="4d631-330">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span></span> <span data-ttu-id="4d631-331">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="4d631-331">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="4d631-332">Créez un cas eDiscovery dans SharePoint 2013 si vous avez utilisé l'option A pour l'importation d'un fichier PST ou créez un cas eDiscovery dans SharePoint Online si vous avez utilisé l'option B.</span><span class="sxs-lookup"><span data-stu-id="4d631-332">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

