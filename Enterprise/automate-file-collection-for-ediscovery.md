---
title: Automatiser la collecte de fichiers pour eDiscovery
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Résumé : Apprenez à automatiser la collecte de fichiers à partir des ordinateurs des utilisateurs pour eDiscovery.'
ms.openlocfilehash: 0133da6eecb229ad999043c9dfcb15d98a732829
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030488"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="6d5e9-103">Automatiser la collecte de fichiers pour eDiscovery</span><span class="sxs-lookup"><span data-stu-id="6d5e9-103">Automate file collection for eDiscovery</span></span>

 <span data-ttu-id="6d5e9-104">**Résumé :** Apprenez à automatiser la collecte de fichiers à partir des ordinateurs des utilisateurs pour eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-104">**Summary:** Learn how to automate file collection from user computers for eDiscovery.</span></span>
  
<span data-ttu-id="6d5e9-p101">Toutes les sociétés peuvent être confrontées à des poursuites judiciaires ou à d'autres types d'action en justice. Bien que les départements juridiques tentent de réduire l'exposition, la résolution de litiges fait partie de la vie des entreprises. Lorsqu'une entreprise est confrontée à une action légale, il est de son devoir, via le processus de découverte légale, de fournir tout document pertinent requis par le tribunal et la partie adverse.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p101">All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="6d5e9-p102">La découverte électronique est le processus par lequel les entreprises inventorient, recherchent, conservent, filtrent et rendent disponibles les documents pertinents existant sous forme électronique. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, et Exchange Online peuvent contenir de grandes quantités de documents. Selon la version, ces produits peuvent prendre en charge eDiscovery et la conservation inaltérable (Lync via Exchange Server), ce qui facilite le travail d'indexation, d'identification, de conservation et de filtrage du contenu le plus pertinent pour une affaire donnée.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p102">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="6d5e9-p103">Une grande quantité de documents est également stockée sur les ordinateurs locaux des utilisateurs (dépositaires), et non dans un emplacement centralisé. Il est ainsi pratiquement impossible d'effectuer des recherches dans SharePoint 2013. Or, si la recherche y est impossible, vous ne pouvez pas inclure l'instance dans eDiscovery. Cette solution vous montre comment utiliser les scripts d'ouverture de session, System Center Orchestrator 2012 R2 et Windows PowerShell pour que Exchange Server automatise l'identification et la collecte des documents à partir des ordinateurs des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p103">Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="6d5e9-114">Descriptif de cette solution</span><span class="sxs-lookup"><span data-stu-id="6d5e9-114">What this solution does</span></span>

<span data-ttu-id="6d5e9-p104">Cette solution utilise un groupe de sécurité global, une stratégie de groupe et un script Windows PowerShell pour localiser, inventorier et recueillir du contenu et les fichiers du magasin personnel (PST) Outlook à partir d'ordinateurs locaux des utilisateurs vers un partage de fichiers caché. À partir de là, les fichiers PST peuvent être importés dans Exchange Server 2013 ou Exchange Online. Tous les fichiers sont ensuite déplacés à l'aide d'un runbook System Center Orchestrator 2012 R2 vers un autre partage de fichier dans Microsoft Azure pour un stockage à long terme et d'une indexation par SharePoint 2013. Vous utilisez ensuite les centres eDiscovery dans votre déploiement SharePoint 2013 sur site ou dans SharePoint Online comme vous le feriez régulièrement pour effectuer une eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p104">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="6d5e9-p105">Cette solution utilise robocopy pour copier des fichiers à partir d'ordinateurs de dépositaires vers un partage de fichiers centralisé. Étant donné que robocopy ne copie pas les fichiers qui sont ouverts ou verrouillés, tous les fichiers, y compris les fichiers PST, ouverts par le dépositaire ne seront pas collectés. Vous devrez les collecter manuellement. Cette solution vous fournit une liste qui identifie de manière explicite les fichiers impossibles à copier et le chemin d'accès complet à chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p105">This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="6d5e9-123">Le diagramme suivant vous guide à travers les étapes et les éléments de la solution.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-123">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![Vue d’ensemble de la solution de regroupement automatique de fichiers](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="6d5e9-125">\*\*\*\*Légende\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6d5e9-125">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![légende magenta 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="6d5e9-127">Créez un objet de stratégie de groupe (GPO) et associez-le au script d’ouverture de session de collecte.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-127">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![légende magenta 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="6d5e9-129">Configurez le filtre de sécurité de l’objet de stratégie de groupe pour appliquer l’objet de stratégie de groupe uniquement au groupe des dépositaires.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-129">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![légende magenta 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="6d5e9-131">Un dépositaire ouvre une session et l’objet de stratégie de groupe s’exécute, appelant le script d’ouverture de session de collecte</span><span class="sxs-lookup"><span data-stu-id="6d5e9-131">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![légende magenta 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="6d5e9-133">Le script d’ouverture de session de collecte répertorie tous les lecteurs connectés localement à l’ordinateur des dépositaires, en cherchant les fichiers que vous souhaitez et en enregistrant leur emplacement.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-133">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![légende magenta 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="6d5e9-135">Le script d’ouverture de session de collecte copie les fichiers inventoriés sur un partage de fichiers caché sur le serveur intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-135">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![légende magenta 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="6d5e9-137">(Option A) Exécutez manuellement le script d'importation PST pour importer les fichiers PST collectés dans Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-137">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![légende magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="6d5e9-139">(Option B) À l'aide de l'outil et du processus d'importation de Office 365, importez les fichiers PST collectés dans Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-139">(Option B) Using the Office 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![légende magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="6d5e9-141">Déplacez tous les fichiers collectés vers un partage de fichiers Azure pour un stockage à long terme avec le runbook MoveToColdStorageSystem Center Orchestrator 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-141">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![légende magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="6d5e9-143">Indexez les fichiers dans le partage des fichiers de stockage froid avec SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-143">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![légende magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="6d5e9-145">Effectuez eDiscovery sur le contenu dans l'espace de stockage froid et le Exchange Server 2013 sur site.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-145">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![légende magenta 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="6d5e9-147">Effectuez eDiscovery sur le contenu dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-147">Perform eDiscovery on content in Office 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="6d5e9-148">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="6d5e9-148">Prerequisites</span></span>

<span data-ttu-id="6d5e9-p106">La configuration de cette solution nécessite plusieurs éléments, dont la plupart sont probablement en place et configurés si vous envisagez eDiscovery. Pour les éléments que vous n'avez pas ou ceux qui requièrent une configuration spécifique, nous allons vous fournir les liens, d'après lesquels vous devez élaborer votre configuration de base. La configuration de base doit être en place avant de configurer la solution elle-même.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p106">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="6d5e9-152">Configuration de base</span><span class="sxs-lookup"><span data-stu-id="6d5e9-152">Base configuration</span></span>

|<span data-ttu-id="6d5e9-153">**Élément**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-153">**Element**</span></span>|<span data-ttu-id="6d5e9-154">**Lien**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-154">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6d5e9-155">Domaine Services de domaine Active Directory (AD DS)</span><span class="sxs-lookup"><span data-stu-id="6d5e9-155">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="6d5e9-156">Connectivité Internet à partir de votre réseau local</span><span class="sxs-lookup"><span data-stu-id="6d5e9-156">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="6d5e9-157">SQL Server 2012 pour prendre en charge SharePoint 2013 et System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6d5e9-157">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="6d5e9-158">Déploiement de System Center 2012 - Orchestrator</span><span class="sxs-lookup"><span data-stu-id="6d5e9-158">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="6d5e9-159">Sur site ou SharePoint 2013 basé sur Azure pour eDiscovery (requis pour l'option A)</span><span class="sxs-lookup"><span data-stu-id="6d5e9-159">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="6d5e9-160">Serveur de partage de fichiers sur site pour le placement en zone de transit</span><span class="sxs-lookup"><span data-stu-id="6d5e9-160">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="6d5e9-161">Exchange Server 2013 sur site pour l'importation du PST de l'option A</span><span class="sxs-lookup"><span data-stu-id="6d5e9-161">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="6d5e9-162">La mise à jour cumulative 5 (15.913.22) est disponible sur le site [Mise à jour cumulative 5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-162">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="6d5e9-163">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6d5e9-163">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="6d5e9-164">Déploiement de System Center 2012 - Orchestrator</span><span class="sxs-lookup"><span data-stu-id="6d5e9-164">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="6d5e9-165">Office 365 (Plan E3) avec Exchange Online et SharePoint Online (requis pour l'option B)</span><span class="sxs-lookup"><span data-stu-id="6d5e9-165">Office 365 (E3 Plan) with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="6d5e9-166">Pour souscrire à un abonnement E3 Office 365, voir la page relative à l'[abonnement Office 365 E3](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-166">To sign up for an Office 365 E3 subscription, see [Office 365 E3 subscription](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span></span>  <br/> |
|<span data-ttu-id="6d5e9-167">Abonnement Azure avec un ordinateur virtuel</span><span class="sxs-lookup"><span data-stu-id="6d5e9-167">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="6d5e9-168">Pour vous inscrire à Azure, voir la page d'[abonnement à Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span><span class="sxs-lookup"><span data-stu-id="6d5e9-168">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="6d5e9-169">Une connexion VPN entre votre réseau local et votre abonnement Azure</span><span class="sxs-lookup"><span data-stu-id="6d5e9-169">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="6d5e9-170">Pour configurer un tunnel VPN entre votre abonnement Azure et votre réseau local, voir [Connecter un réseau local à Microsoft Azure Virtual Network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-170">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="6d5e9-171">SharePoint 2013eDiscovery configuré pour effectuer une recherche dans SharePoint et Exchange Server 2013, et éventuellement Lync Server 2013</span><span class="sxs-lookup"><span data-stu-id="6d5e9-171">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="6d5e9-172">Pour configurer la eDiscovery de cette façon, voir [Configurer eDiscovery dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) et[Guide de laboratoire de test : configurez eDiscovery pour un laboratoire de test de partages de fichiers Exchange, Lync, SharePoint et Windows ](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-172">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="6d5e9-173">eDiscovery dans Office 365 pour SharePoint Online et Exchange Online</span><span class="sxs-lookup"><span data-stu-id="6d5e9-173">eDiscovery in Office 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="6d5e9-174">Pour configurer la eDiscovery dans Office 365, voir [Configurer un centre eDiscovery dans SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628)</span><span class="sxs-lookup"><span data-stu-id="6d5e9-174">To configure eDiscovery in Office 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="6d5e9-175">Configurer l’environnement</span><span class="sxs-lookup"><span data-stu-id="6d5e9-175">Configure the environment</span></span>

<span data-ttu-id="6d5e9-176">Maintenant que la configuration de base est en place, vous pouvez passer à la configuration de la solution elle-même.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-176">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="6d5e9-177">Partage de fichiers intermédiaires</span><span class="sxs-lookup"><span data-stu-id="6d5e9-177">Staging file share</span></span>

1. <span data-ttu-id="6d5e9-178">Dans le domaine local, créez un groupe de sécurité global nommé Custodians.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-178">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="6d5e9-p107">Créez un partage de fichiers cachés pour les fichiers qui sont collectés à partir d'ordinateurs de dépositaires. Il doit s'agir d'un serveur local. Par exemple, sur un serveur appelé Staging, créez un partage de fichiers appelé Cases$. Le **$** est requis pour en faire un partage caché.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p107">Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="6d5e9-183">Définissez les autorisations de partage suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-183">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="6d5e9-184">Dépositaires : Modifier, Lire</span><span class="sxs-lookup"><span data-stu-id="6d5e9-184">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="6d5e9-185">Administrateurs : Contrôle total</span><span class="sxs-lookup"><span data-stu-id="6d5e9-185">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="6d5e9-186">Sous-système approuvé Exchange : Modifier, Lire</span><span class="sxs-lookup"><span data-stu-id="6d5e9-186">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="6d5e9-p108">Ouvrez l'onglet **Sécurité**, ajoutez le groupe des dépositaires, puis cliquez sur **Avancé**. Définissez les autorisations suivantes pour le groupe des dépositaires :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p108">Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="6d5e9-189">**Type : Refuser**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-189">**Type: Deny**</span></span>
    
  - <span data-ttu-id="6d5e9-190">**S'applique à : Ce dossier, les sous-dossiers et les fichiers**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-190">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="6d5e9-191">Cliquez sur **Autorisations avancées** et sélectionnez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-191">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="6d5e9-192">**Lecture des attributs**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-192">**Read attributes**</span></span>
    
  - <span data-ttu-id="6d5e9-193">**Lecture des attributs étendus**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-193">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="6d5e9-194">**Autorisations de lecture**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-194">**Read permissions**</span></span>
    
6. <span data-ttu-id="6d5e9-195">Testez l’accès au partage de fichiers Cases$ en effectuant les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-195">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="6d5e9-196">Ajoutez un utilisateur au groupe des dépositaires.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-196">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="6d5e9-197">Placez un fichier dans le dossier Cases$.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-197">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="6d5e9-p109">En tant qu'utilisateur, accédez au serveur intermédiaire, par exemple accédez au partage \\\\Staging pour voir quels partages sont disponibles. Vous ne devriez pas voir le partage **Cases$** répertorié.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p109">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="6d5e9-p110">Saisissez manuellement le chemin d’accès complet au partage Cases$ dans Explorer. Cela devrait ouvrir le partage Cases$.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p110">Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="6d5e9-p111">Essayez d’ouvrir le fichier que vous avez placé dans le partage. Vous ne devriez pas y parvenir</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p111">Try to open the file you previously placed in the share. This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="6d5e9-204">Script d’ouverture de session</span><span class="sxs-lookup"><span data-stu-id="6d5e9-204">Logon script</span></span>

1. <span data-ttu-id="6d5e9-205">Copiez et collez ce script Windows PowerShell dans le bloc-notes :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-205">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
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

2. <span data-ttu-id="6d5e9-206">Enregistrez le script ci-dessus sous CollectionScript.ps1 dans un emplacement facile à trouver, par exemple C:\\AFCScripts.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-206">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="6d5e9-p112">Utilisez la fonctionnalité Accédez à dans le bloc-notes. Apportez les modifications suivantes, selon vos besoins :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p112">Use the Go To feature in Notepad. Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="6d5e9-209">**Ligne #**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-209">**Line #**</span></span>|<span data-ttu-id="6d5e9-210">**Ce que vous devez modifier**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-210">**What you need to change**</span></span>|<span data-ttu-id="6d5e9-211">**Obligatoire/facultatif**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-211">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="6d5e9-212">71</span><span class="sxs-lookup"><span data-stu-id="6d5e9-212">71</span></span>  <br/> |<span data-ttu-id="6d5e9-p113">Variable **$FileTypes**. Inclure toutes les extensions de type de fichier que vous souhaitez que le script inventorie et collecte dans la variable du tableau</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p113">**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. </span></span><br/> |<span data-ttu-id="6d5e9-215">Facultatif</span><span class="sxs-lookup"><span data-stu-id="6d5e9-215">Optional</span></span>  <br/> |
|<span data-ttu-id="6d5e9-216">76 et 77</span><span class="sxs-lookup"><span data-stu-id="6d5e9-216">76 and 77</span></span>  <br/> |<span data-ttu-id="6d5e9-p114">Modifier la conception de la variable **$CaseNo** en fonction de vos besoins. Le script capture la date et heure actuelles et y ajoute le nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p114">Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. </span></span><br/> |<span data-ttu-id="6d5e9-219">Facultatif</span><span class="sxs-lookup"><span data-stu-id="6d5e9-219">Optional</span></span>  <br/> |
|<span data-ttu-id="6d5e9-220">80</span><span class="sxs-lookup"><span data-stu-id="6d5e9-220">80</span></span>  <br/> |<span data-ttu-id="6d5e9-221">La variable **$CaseRootLocation** doit être configurée pour votre partage des fichiers de collecte de serveurs intermédiaires. Par exemple **\\\\Staging\\Cases$**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-221">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="6d5e9-222">Requis</span><span class="sxs-lookup"><span data-stu-id="6d5e9-222">Required</span></span>  <br/> |
   
4. <span data-ttu-id="6d5e9-223">Placez le fichier CollectionScript.ps1 dans le partage des fichiers d’accès réseau sur un contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-223">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="6d5e9-224">Configuration de l’objet de stratégie de groupe pour le script d’ouverture de session et le groupe de dépositaires</span><span class="sxs-lookup"><span data-stu-id="6d5e9-224">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="6d5e9-225">Configurez un script d'ouverture de session pour le groupe de dépositaires en suivant les instructions de la section concernant la manière d'affecter des scripts d'ouverture de session utilisateur dans la rubrique relative à l'[utilisation des scripts de démarrage, d'arrêt, d'ouverture et de fermeture de session dans la stratégie de groupe](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-225">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="6d5e9-226">Supprimez les utilisateurs authentifiés de **Filtrage de sécurité** et ajoutez le groupe des dépositaires.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-226">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="6d5e9-227">Importation du PST de l'option A, script pour Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="6d5e9-227">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="6d5e9-228">Copiez et collez le script Windows PowerShell suivant dans le bloc-notes :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-228">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
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

2. <span data-ttu-id="6d5e9-p115">Enregistrez le script en tant que PSTImportScript.ps1 dans un emplacement facile à trouver. Par exemple et pour une grande facilité d'utilisation, créez un dossier sur votre serveur intermédiaire appelé \\\\Staging\\AFCScripts et enregistrez le script ici.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p115">Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="6d5e9-231">Utilisez la fonctionnalité Accédez à dans le bloc-notes et apportez les modifications suivantes, selon vos besoins :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-231">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="6d5e9-232">**Ligne #**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-232">**Line #**</span></span>|<span data-ttu-id="6d5e9-233">**Ce que vous devez modifier**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-233">**What you need to change**</span></span>|<span data-ttu-id="6d5e9-234">**Obligatoire/facultatif**</span><span class="sxs-lookup"><span data-stu-id="6d5e9-234">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="6d5e9-235">an</span><span class="sxs-lookup"><span data-stu-id="6d5e9-235">12</span></span>  <br/> |<span data-ttu-id="6d5e9-p116">**$FolderIdentifier** marque les dossiers de boîte aux lettres vers lesquels les fichiers PST sont importés. Modifier si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p116">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. </span></span><br/> |<span data-ttu-id="6d5e9-238">Facultatif</span><span class="sxs-lookup"><span data-stu-id="6d5e9-238">Optional</span></span>  <br/> |
|<span data-ttu-id="6d5e9-239">cm</span><span class="sxs-lookup"><span data-stu-id="6d5e9-239">17</span></span>  <br/> |<span data-ttu-id="6d5e9-240">**$ConnectionUri** doit être configuré pour votre propre serveur.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-240">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="6d5e9-p117">> [!IMPORTANT]> Vérifiez que votre **$ConnectionUri** pointe vers un emplacement http://, et non pas https://. Cela ne fonctionnera pas avec https://</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p117">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.</span></span>          |<span data-ttu-id="6d5e9-243">Requis</span><span class="sxs-lookup"><span data-stu-id="6d5e9-243">Required</span></span>  <br/> |
   
4. <span data-ttu-id="6d5e9-244">Vérifiez que le compte Sous-système approuvé Exchange dispose des autorisations de lecture, écriture et exécution sur le partage \\\\Staging\\Cases$.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-244">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="6d5e9-245">Le script d’importation PST nécessite les deux paramètres d’entrée suivants :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-245">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="6d5e9-246">**$SourcePath** L'emplacement des fichiers PST à importer, par exemple \\\\Staging\\Cases$.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-246">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="6d5e9-247">**$MailboxAlias** L'alias de la boîte aux lettres cible qui recevra les éléments de messagerie importés.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-247">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="6d5e9-248">Par exemple, si vous voulez importer tous les fichiers PST depuis le chemin \\\\Staging\Cases$ vers une boîte aux lettres avec l'alias eDiscoveryMailbox, vous devrez exécuter le script comme suit`\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-248">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="6d5e9-249">Importation des fichiers PST de l'option B, pour Exchange Online</span><span class="sxs-lookup"><span data-stu-id="6d5e9-249">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="6d5e9-p118">Créez la structure de la boîte aux lettres pour y placer les fichiers PST importés. Pour plus d'informations sur la création d'une boîte aux lettres utilisateur dans Exchange Online, voir[Création de boîtes aux lettres utilisateur dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p118">Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="6d5e9-252">Stockage froid</span><span class="sxs-lookup"><span data-stu-id="6d5e9-252">Cold storage</span></span>

1. <span data-ttu-id="6d5e9-253">Créez un partage de fichiers sur la Ordinateur virtuel Azure où tous les fichiers collectés seront placés, par exemple \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-253">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="6d5e9-p119">Accordez au moins les autorisations de lecture du partage et de tous les sous-dossiers et fichiers au compte d'accès au contenu par défaut. Pour plus d'informations sur la configuration de la recherche SharePoint 2013, voir [Créer et configurer une application de service de recherche dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940)</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p119">Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="6d5e9-256">Si vous envisagez l'importation de fichiers PST à partir de \\\\AZFile1\\ContentColdStorage, accordez les autorisations de lecture, écriture et exécution du sous-système approuvé Exchange au partage.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-256">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="6d5e9-257">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="6d5e9-257">Orchestrator</span></span>

1. <span data-ttu-id="6d5e9-258">Téléchargez le [runbook MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) à partir du Centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-258">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="6d5e9-p120">Ouvrez le **Runbook Designer**, dans le panneau **Connexions**, cliquez sur le dossier dans lequel vous souhaitez importer le runbook. Cliquez sur le menu **Actions**, puis cliquez sur **Importer**. La boîte de dialogue **Importer** s'affiche.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p120">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="6d5e9-262">Dans la boîte **Emplacement du fichier**, saisissez le chemin d'accès et le nom du runbook que vous souhaitez importer ou cliquez sur les points de suspension ( **...**) pour rechercher le fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-262">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="6d5e9-p121">Sélectionnez **Importer le runbook** et **Importer les données chiffrées d'Orchestrator**. Effacez **Compteurs**, **Planifications**, **Variables**, **Groupes d'ordinateurs**, **Importer les configurations globales**, et **Remplacer les configurations globales existantes**.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p121">Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="6d5e9-265">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-265">Click **Finish**.</span></span>
    
6. <span data-ttu-id="6d5e9-266">Modifiez le runbook **MoveFilesToColdStorage** comme suit :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-266">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="6d5e9-p122">Activité **Déplacer le fichier**: définissez le chemin d'accès du **fichier source** sur le partage des fichiers de collecte, par exemple \\\\Staging\\cases$. Définissez le **dossier de destination** sur l'emplacement de partage des fichiers de stockage froid dans Azure, par exemple \\\\AZFile1\\ContentColdStorage. Sélectionnez **Créer un fichier avec un nom unique**.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p122">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="6d5e9-270">Activité **Supprimer le dossier**: définissez le **chemin d'accès** sur le partage des fichiers de collecte, par exemple \\\\Staging\\cases$\\*, et sélectionnez **Supprimer tous les fichiers et sous-dossiers**.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-270">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="6d5e9-271">Déployer le runbook **MoveToColdStorage** en utilisant les procédures décrites dans l'article sur le[déploiement de runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-271">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="6d5e9-272">Recherche du stockage froid pour une instance SharePoint sur site</span><span class="sxs-lookup"><span data-stu-id="6d5e9-272">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="6d5e9-p123">Créez une nouvelle source de contenu dans votre batterie de serveurs SharePoint 2013 pour le partage du stockage froid dans Azure, par exemple \\\\AZFile1\\ContentColdStorage. Pour plus d'informations sur la gestion des sources de contenu, voir [Ajouter, modifier ou supprimer une source de contenu dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p123">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="6d5e9-p124">Démarrez une analyse complète. Pour plus d'informations, voir [Démarrer, suspendre, reprendre ou arrêter une analyse dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p124">Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="6d5e9-277">Utilisation de la solution</span><span class="sxs-lookup"><span data-stu-id="6d5e9-277">Using the solution</span></span>

<span data-ttu-id="6d5e9-p125">Il existe cinq étapes principales concernant l'utilisation de cette solution, en supposant que vous ne souhaitez pas ingérer les fichiers PST dans Exchange Server 2013 et Exchange Online. Cette section vous fournit les procédures pour tous les cas. Votre interaction principale avec la solution aura lieu en effectuant les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p125">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="6d5e9-281">Gestion de l’appartenance des utilisateurs dans le groupe des dépositaires.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-281">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="6d5e9-p126">Erreurs</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p126">Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="6d5e9-285">Gestion du processus d’importation PST.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-285">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="6d5e9-286">Déplacement des fichiers de collecte vers l’emplacement de stockage froid.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-286">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="6d5e9-p127">Toutes les autres étapes ne sont pas propres à cette solution. Ce sont des tâches administratives standard que vous effectuez dans SharePoint 2013, Office 365 et Azure. Il existe des aspects pour lesquels cette solution ne propose aucune recommandation et pour lesquels vous devrez utiliser votre meilleur jugement selon les besoins de votre société, tels que :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p127">All the other steps are not specific to this solution. They are standard administrative tasks that you perform in SharePoint 2013, and Office 365 and Azure. There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="6d5e9-290">Suivi de vos cas eDiscovery et de la répartition des dépositaires en fonction des cas.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-290">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="6d5e9-291">Contrôle de la répartition des ensembles de collecte de fichiers en fonction des cas eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-291">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="6d5e9-292">Coordination du calendrier d’importation et des étapes de déplacement vers l’emplacement de stockage froid.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-292">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="6d5e9-293">Gestion de l'espace de fichier utilisé dans Azure.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-293">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="6d5e9-294">Gestion des boîtes aux lettres vers lesquelles les fichiers PST sont importés.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-294">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="6d5e9-295">Sauvegarde et restauration de toutes les données locales.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-295">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="6d5e9-296">Gestion de dépositaire</span><span class="sxs-lookup"><span data-stu-id="6d5e9-296">Custodian management</span></span>

- <span data-ttu-id="6d5e9-p128">Pour démarrer le processus de collecte automatique des fichiers pour un utilisateur individuel, ajoutez-les au groupe des dépositaires. La prochaine fois que l'utilisateur se connecte, le script d'ouverture de session affecté au groupe des dépositaires via la stratégie de groupe s'exécutera.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p128">To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="6d5e9-299">Surveillance des fichiers collectés et examen des fichiers journaux</span><span class="sxs-lookup"><span data-stu-id="6d5e9-299">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="6d5e9-p129">Observez le partage des fichiers de collecte, par exemple \\\\Staging\\cases$\\* pour le dossier de collecte à partir de l'utilisateur. Le nom du dossier sera formaté comme suit :  *aaaaMMjjHHmm_NomUtilisateur*  .</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p129">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="6d5e9-p130">Lorsque la collecte est terminée, ouvrez le dossier de collecte et accédez au dossier _Log. Les éléments suivants s'affichent dans le dossier _Log :</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p130">When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="6d5e9-p131">Un seul fichier XML pour chaque lecteur local sur l'ordinateur des utilisateurs, par exemple **A.xml**, **C.xml**. Ces fichiers contiennent les lecteurs d'inventaire d'après lesquels ils sont nommés et ils sont utilisés pour l'opération robocopy.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p131">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="6d5e9-p132">Le script de collecte crée uniquement une entrée dans le fichier d'inventaire pour les types de fichiers que vous avez définis dans le script lui-même. Il ne crée pas une entrée d'inventaire pour chaque fichier sur l'ordinateur des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p132">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="6d5e9-p133">Un seul fichier journal nommé FileCopyErrors.log est exécuté pour chaque collecte. Ce fichier contient une liste des fichiers que robocopy n'a pas pu copier sur le partage de collecte de fichiers, par exemple, \\\\Staging\\cases$\\*. Vous devrez l'examiner et décider des mesures à adopter pour ces fichiers manquants. En règle générale, vous devez les rassembler manuellement si vous souhaitez les conserver ou vous pouvez décider qu'ils ne sont pas nécessaires et qu'ils peuvent donc être omis de la collecte.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p133">One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="6d5e9-312">Importation des fichiers PST de l'option A pour Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="6d5e9-312">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="6d5e9-p134">Ouvrez une session sur le serveur qui héberge le partage des fichiers de collecte, par exemple **Staging** et ouvrez Windows PowerShell. Pour plus d'informations sur le démarrage de Windows PowerShell, voir l'article relatif au[démarrage de Windows PowerShell sous Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p134">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="6d5e9-p135">Définissez la stratégie d'exécution sur Illimitée. Saisissez  `Set-ExecutionPolicy Unrestricted -Scope Process` dans Windows PowerShell et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p135">Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="6d5e9-p136">Exécutez le fichier PSTImportScript.ps1 et indiquez les paramètres **$SourcePath** et **$MailboxAlias**. Pour plus d'informations sur l'exécution des scripts Windows PowerShell, voir[Prise en charge des scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p136">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="6d5e9-319">Recherchez les erreurs dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-319">Review the output for errors.</span></span>
    
5. <span data-ttu-id="6d5e9-p137">Avant d'essayer d'importer un fichier PST portant le même nom dans la même boîte aux lettres, vous devez supprimer la demande d'importation de boîte aux lettres. Pour ce faire, exécutez la commande suivante :  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. Vous serez invité à supprimer chaque demande individuelle de la file d'attente. Répondez selon vos besoins.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p137">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="6d5e9-324">Importation des fichiers PST de l'option B, pour Exchange Online</span><span class="sxs-lookup"><span data-stu-id="6d5e9-324">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="6d5e9-325">Pour placer les fichiers PST collectés dans Exchange Online, suivez les procédures décrites dans la section concernant l'importation de fichiers vers Office 365 via le chargement réseau dans la rubrique relative au [service d'importation Office 365](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-325">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Office 365 through the network upload section of [Office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="6d5e9-326">Déplacement vers l’emplacement de stockage froid</span><span class="sxs-lookup"><span data-stu-id="6d5e9-326">Move to cold storage</span></span>

1. <span data-ttu-id="6d5e9-327">Exécutez le runbook **MoveToColdStorage** à l'aide des procédures décrites dans la rubrique relative à l'[exécution de runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-327">Run the **MoveToColdStorage** runbook using the procedures in[Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="6d5e9-p138">Observez le partage de fichiers Azure que vous utilisez pour le stockage à long terme, par exemple \\\\AZFile1\\ContentColdStorage et le partage des fichiers de collecte sur site, par exemple \\\\Staging\\cases$. Vous devriez voir les fichiers et dossiers apparaître dans le partage des fichiers de stockage froid et disparaître du partage des fichiers de collecte.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p138">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="6d5e9-330">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="6d5e9-330">eDiscovery</span></span>

1. <span data-ttu-id="6d5e9-p139">Autorisez l'analyse complète du partage des fichiers de stockage froid à s'exécuter en tant que planification ou lancez une analyse. Pour plus d'informations sur le démarrage d'analyses complètes ou incrémentielles, voir [Démarrer, suspendre, reprendre ou arrêter une analyse dans SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-p139">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="6d5e9-333">Créez un cas eDiscovery dans SharePoint 2013 si vous avez utilisé l'option A pour l'importation d'un fichier PST ou créez un cas eDiscovery dans SharePoint Online si vous avez utilisé l'option B.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-333">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

