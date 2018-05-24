---
title: Protéger les fichiers SharePoint Online avec Azure Information Protection
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 'Résumé : Découvrez comment appliquer la protection Azure Information Protection pour protéger les fichiers d’un site d’équipe SharePoint Online hautement confidentiel.'
ms.openlocfilehash: a5df4d7289ec31686ad74f78a4797e1aa3eaa447
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="796b0-103">Protéger les fichiers SharePoint Online avec Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="796b0-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="796b0-104">**Résumé :** Découvrez comment appliquer la protection Azure Information Protection pour protéger les fichiers d’un site d’équipe SharePoint Online hautement confidentiel.</span><span class="sxs-lookup"><span data-stu-id="796b0-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="796b0-p101">Suivez les étapes décrites dans cet article pour configurer Azure Information Protection pour assurer le chiffrement et configurer les autorisations des fichiers d’un site d’équipe SharePoint Online hautement confidentiel. La protection du chiffrement et des autorisations accompagne un fichier même lorsqu’il est téléchargé à partir du site. Pour en savoir plus sur les sites d’équipe SharePoint Online hautement confidentiels, consultez la rubrique [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="796b0-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="796b0-p102">Lorsque le chiffrement Azure Information Protection est appliqué aux fichiers stockés dans Office 365, le service ne peut pas traiter le contenu de ces fichiers. La co-création, eDiscovery, la recherche, Delve et d’autres fonctionnalités de collaboration ne fonctionnent pas. Les stratégies de protection contre la perte de données peuvent uniquement fonctionner avec les métadonnées (y compris les étiquettes Office 365), mais pas le contenu de ces fichiers (par exemple, des numéros de cartes de crédit au sein des fichiers).</span><span class="sxs-lookup"><span data-stu-id="796b0-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="796b0-111">Tout d’abord, suivez les instructions contenues dans [Activer Azure RMS avec le centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) pour votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="796b0-111">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="796b0-112">Ensuite, configurez Azure Information Protection avec une nouvelle sous-étiquette et une nouvelle stratégie étendue pour la protection et les autorisations de votre site d’équipe SharePoint Online hautement confidentiel.</span><span class="sxs-lookup"><span data-stu-id="796b0-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="796b0-p103">Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="796b0-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="796b0-115">Dans un nouvel onglet de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="796b0-115">In a separate tab of your browser, go to the Azure portal (https://portal.azure.com).</span></span>
    
3. <span data-ttu-id="796b0-116">Si vous configurez Azure Information Protection pour la première fois, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="796b0-116">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="796b0-117">Dans le volet Liste, cliquez sur **Plus de services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="796b0-117">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="796b0-118">Sur le panneau **Azure Information Protection**, cliquez sur **Stratégies étendues > + Ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="796b0-118">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="796b0-119">Saisissez le nom de la nouvelle stratégie dans **Nom de la stratégie** et une description dans **Description**.</span><span class="sxs-lookup"><span data-stu-id="796b0-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="796b0-120">Cliquez sur **Sélectionnez les utilisateurs ou groupes devant recevoir cette stratégie > Utilisateur/Groupes**, puis sélectionnez le groupe d’accès des membres de votre site d’équipe SharePoint Online hautement sensible. </span><span class="sxs-lookup"><span data-stu-id="796b0-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="796b0-121">Cliquez sur **Sélectionner > OK**.</span><span class="sxs-lookup"><span data-stu-id="796b0-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="796b0-122">Pour l’étiquette **Hautement confidentiel**, cliquez sur les points de suspension (...), puis sur **Ajouter une sous-étiquette**.</span><span class="sxs-lookup"><span data-stu-id="796b0-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="796b0-123">Entrez le nom de la sous-étiquette dans **Nom** et sa description dans **Description**.</span><span class="sxs-lookup"><span data-stu-id="796b0-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="796b0-124">Cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.</span><span class="sxs-lookup"><span data-stu-id="796b0-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="796b0-125">Dans la section **Protection**, cliquez sur **Azure (clé cloud)**.</span><span class="sxs-lookup"><span data-stu-id="796b0-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="796b0-126">Dans le panneau **Protection**, sous **Paramètres de protection**, cliquez sur **+ Ajouter des autorisations**.</span><span class="sxs-lookup"><span data-stu-id="796b0-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="796b0-127">Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.</span><span class="sxs-lookup"><span data-stu-id="796b0-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="796b0-128">Dans le volet **Utilisateurs et groupes AAD**, sélectionnez le groupe d’accès Membres de votre site d’équipe SharePoint Online hautement sensible, puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="796b0-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="796b0-129">Sous **Choisir des autorisations à partir de valeurs prédéfinies**, désactivez les cases à cocher **Imprimer **, **Copier et extraire le contenu** et **Transférer**.</span><span class="sxs-lookup"><span data-stu-id="796b0-129">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="796b0-130">Cliquez deux fois sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="796b0-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="796b0-131">Dans le panneau **Sous-étiquette**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="796b0-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="796b0-132">Fermez le panneau de la nouvelle stratégie étendue.</span><span class="sxs-lookup"><span data-stu-id="796b0-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="796b0-133">Dans le panneau **Azure Information Protection – Stratégies étendues**, cliquez sur **Publier**.</span><span class="sxs-lookup"><span data-stu-id="796b0-133">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
<span data-ttu-id="796b0-134">Voici la configuration finale de votre site d’équipe SharePoint Online hautement confidentiel.</span><span class="sxs-lookup"><span data-stu-id="796b0-134">This is your resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![Étiquette Azure Information Protection pour un site d’équipe SharePoint Online isolé.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="796b0-136">Vous pouvez maintenant commencer à créer des documents et à les protéger avec Azure Information Protection et votre nouvelle étiquette.</span><span class="sxs-lookup"><span data-stu-id="796b0-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="796b0-p104">Vous devez [installer le client Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur votre périphérique ou votre ordinateur Windows. Vous pouvez créer un script et automatiser l’installation, ou les utilisateurs peuvent installer le client manuellement. Consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="796b0-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="796b0-140">Côté client d’Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="796b0-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="796b0-141">Installation du client Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="796b0-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="796b0-142">Page de téléchargement de l’installation manuelle</span><span class="sxs-lookup"><span data-stu-id="796b0-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="796b0-p105">Une fois l’installation effectuée, vos utilisateurs exécutent une application Office (par exemple, Microsoft Word) pour se connecter avec leur compte Office 365. Une nouvelle barre **Information Protection** permet aux utilisateurs de sélectionner la nouvelle étiquette. Assurez-vous que vos utilisateurs connaissent le site d’équipe SharePoint Online et savent quelle étiquette utiliser, afin de protéger leurs fichiers hautement confidentiels.</span><span class="sxs-lookup"><span data-stu-id="796b0-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="796b0-146">Si vous possédez plusieurs sites d’équipe SharePoint Online hautement sensibles, vous devez créer plusieurs stratégies étendues Azure Information Protection avec des sous-étiquettes et les paramètres ci-dessus. Les autorisations de chaque sous-étiquette doivent être définies pour le groupe d’accès des membres d’un site d’équipe SharePoint Online spécifique.</span><span class="sxs-lookup"><span data-stu-id="796b0-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="796b0-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="796b0-147">See Also</span></span>

[<span data-ttu-id="796b0-148">Sécuriser les fichiers et sites SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="796b0-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="796b0-149">Sécuriser les sites SharePoint Online dans un environnement de développement/test</span><span class="sxs-lookup"><span data-stu-id="796b0-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="796b0-150">Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles</span><span class="sxs-lookup"><span data-stu-id="796b0-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="796b0-151">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="796b0-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




