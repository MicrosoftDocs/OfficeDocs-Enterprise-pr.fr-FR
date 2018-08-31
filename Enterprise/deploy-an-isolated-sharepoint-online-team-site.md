---
title: Déploiement d’un site d’équipe SharePoint Online isolé
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: 'Résumé : Découvrez comment déployer un nouveau site d’équipe SharePoint Online isolé en suivant ces instructions détaillées.'
ms.openlocfilehash: e71564248716523a53fcdda48f3a9fdc6349a2c5
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914949"
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="15840-103">Déploiement d’un site d’équipe SharePoint Online isolé</span><span class="sxs-lookup"><span data-stu-id="15840-103">Deploy an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="15840-104">**Résumé :** Découvrez comment déployer un nouveau site d’équipe SharePoint Online isolé en suivant ces instructions détaillées.</span><span class="sxs-lookup"><span data-stu-id="15840-104">**Summary:** Deploy a new isolated SharePoint Online team site with these step-by-step instructions.</span></span>
  
<span data-ttu-id="15840-p101">Cet article est un guide de déploiement détaillé pour créer et configurer un site d’équipe SharePoint Online isolé dans Microsoft Office 365. Pour cela, vous devez utiliser les trois groupes SharePoint par défaut et les niveaux d’autorisation correspondants (un groupe d’accès Azure Active Directory (AD) pour chaque niveau d’accès).</span><span class="sxs-lookup"><span data-stu-id="15840-p101">This article is a step-by-step deployment guide for creating and configuring an isolated SharePoint Online team site in Microsoft Office 365. These steps assume the use of the three default SharePoint groups and corresponding permission levels, with a single Azure Active Directory (AD)-based access group for each level of access.</span></span>
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a><span data-ttu-id="15840-107">Phase 1 : Créer et remplir les groupes d’accès de site d’équipe</span><span class="sxs-lookup"><span data-stu-id="15840-107">Phase 1: Create and populate the team site access groups</span></span>

<span data-ttu-id="15840-108">Au cours de cette phase, vous allez créer les trois groupes d’accès basés sur Azure AD pour les trois groupes SharePoint par défaut et les remplir avec les comptes d’utilisateur appropriés.</span><span class="sxs-lookup"><span data-stu-id="15840-108">In this phase, you create the three Azure AD-based access groups for the three default SharePoint groups and populate them with the appropriate user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="15840-p102">Pour réaliser les étapes suivantes, vous devez avoir créé tous les comptes d’utilisateur nécessaires et leur avoir affecté les licences appropriées. Dans le cas contraire, ajoutez-les et attribuez-leur des licences avant de passer à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="15840-p102">The following steps assume that all necessary user accounts already exist and are assigned the appropriate licenses. If not, please add them and assign licenses before proceeding to step 1.</span></span> 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a><span data-ttu-id="15840-111">Étape 1 : liste des administrateurs SharePoint Online du site</span><span class="sxs-lookup"><span data-stu-id="15840-111">Step 1: List the SharePoint Online admins for the site</span></span>

<span data-ttu-id="15840-112">Choisissez les comptes d’utilisateur des administrateurs SharePoint Online pour le site d’équipe isolé.</span><span class="sxs-lookup"><span data-stu-id="15840-112">Determine the set of user accounts corresponding to the SharePoint Online admins for the isolated team site.</span></span>
  
<span data-ttu-id="15840-113">Si vous gérez des comptes d’utilisateur et des groupes via Office 365 et que vous souhaitez utiliser Windows PowerShell, dressez une liste de leurs noms d’utilisateur principaux (UPN) (exemple d’UPN : belindan@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="15840-113">If you are managing user accounts and groups through Office 365 and want to use Windows PowerShell, make a list of their user principal names (UPNs) (example UPN: belindan@contoso.com).</span></span>
  
### <a name="step-2-list-the-members-for-the-site"></a><span data-ttu-id="15840-114">Étape 2 : liste des membres du site</span><span class="sxs-lookup"><span data-stu-id="15840-114">Step 2: List the members for the site</span></span>

<span data-ttu-id="15840-115">Choisissez les comptes d’utilisateur des membres du site d’équipe isolé, c’est-à-dire ceux qui collaboreront sur les ressources stockées sur le site.</span><span class="sxs-lookup"><span data-stu-id="15840-115">Determine the set of user accounts corresponding to the members for the isolated team site, those who will be collaborating on resources stored within the site.</span></span>
  
<span data-ttu-id="15840-p103">Si vous gérez des comptes d’utilisateur et des groupes via Office 365 et que vous souhaitez utiliser PowerShell, dressez une liste de leurs UPN. S’il existe un grand nombre de membres du site, vous pouvez enregistrer la liste de noms UPN dans un fichier texte et tous les ajouter avec une seule commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15840-p103">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
### <a name="step-3-list-the-viewers-for-the-site"></a><span data-ttu-id="15840-118">Étape 3 : liste des visiteurs du site</span><span class="sxs-lookup"><span data-stu-id="15840-118">Step 3: List the viewers for the site</span></span>

<span data-ttu-id="15840-119">Choisissez les comptes d’utilisateur des visiteurs du site d’équipe isolé, c’est-à-dire ceux qui peuvent afficher les ressources stockées sur le site sans pouvoir les modifier ou collaborer directement sur leur contenu.</span><span class="sxs-lookup"><span data-stu-id="15840-119">Determine the set of user accounts corresponding to the viewers of the isolated team site, those who can view the resources stored in the site but not modify them or directly collaborate on their contents.</span></span>
  
<span data-ttu-id="15840-p104">Si vous gérez des comptes d’utilisateur et des groupes via Office 365 et que vous souhaitez utiliser PowerShell, dressez une liste de leurs UPN. S’il existe un grand nombre de membres du site, vous pouvez enregistrer la liste de noms UPN dans un fichier texte et tous les ajouter avec une seule commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15840-p104">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
<span data-ttu-id="15840-122">Les visiteurs du site peuvent comprendre des membres de l’équipe de direction, du service juridique ou de plusieurs services.</span><span class="sxs-lookup"><span data-stu-id="15840-122">Viewers for the site might include executive management, legal counsel, or inter-departmental stakeholders.</span></span>
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a><span data-ttu-id="15840-123">Étape 4 : création des trois groupes d’accès du site dans Azure AD</span><span class="sxs-lookup"><span data-stu-id="15840-123">Step 4: Create the three access groups for the site in Azure AD</span></span>

<span data-ttu-id="15840-124">Vous devez créer les groupes d’accès suivants dans Azure AD :</span><span class="sxs-lookup"><span data-stu-id="15840-124">You need to create the following access groups in Azure AD:</span></span>
  
- <span data-ttu-id="15840-125">Administrateurs du site (qui contient la liste de l’étape 1)</span><span class="sxs-lookup"><span data-stu-id="15840-125">Site admins (which will contain the list from step 1)</span></span>
    
- <span data-ttu-id="15840-126">Membres du site (qui contient la liste de l’étape 2)</span><span class="sxs-lookup"><span data-stu-id="15840-126">Site members (which will contain the list from step 2)</span></span>
    
- <span data-ttu-id="15840-127">Visiteurs du site (qui contient la liste de l’étape 3)</span><span class="sxs-lookup"><span data-stu-id="15840-127">Site viewers (which will contain the list from step 3)</span></span>
    
1. <span data-ttu-id="15840-128">Dans votre navigateur, accédez au portail Azure à [https://portal.azure.com](https://portal.azure.com) et la connexion avec les informations d’identification d’un compte qui a été affectée avec le rôle d’administrateur de gestion des utilisateurs ou administrateur d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="15840-128">In your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com) and sign in with the credentials of an account that has been assigned with User Management Admin or Company Administrator role.</span></span>
    
2. <span data-ttu-id="15840-129">Dans le portail Azure, cliquez sur **Azure Active Directory > Groupes**.</span><span class="sxs-lookup"><span data-stu-id="15840-129">In the Azure portal, click **Azure Active Directory > Groups**.</span></span>
    
3. <span data-ttu-id="15840-130">Dans le panneau **Groupes - Tous les groupes**, cliquez sur **+ Nouveau groupe**.</span><span class="sxs-lookup"><span data-stu-id="15840-130">On the **Groups - All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="15840-131">Dans le panneau **Groupe** :</span><span class="sxs-lookup"><span data-stu-id="15840-131">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="15840-132">Sélectionnez **Office 365** dans **Type de groupe**.</span><span class="sxs-lookup"><span data-stu-id="15840-132">Select **Office 365** in **Group type**.</span></span>
    
  - <span data-ttu-id="15840-133">Dans **nom**, tapez le nom du groupe.</span><span class="sxs-lookup"><span data-stu-id="15840-133">Type the group name in **Name**.</span></span>
    
  - <span data-ttu-id="15840-134">Tapez une description du groupe dans la **description du groupe**.</span><span class="sxs-lookup"><span data-stu-id="15840-134">Type a description of the group in **Group description**.</span></span>
    
  - <span data-ttu-id="15840-135">Sélectionnez **Affecté** dans le champ **Type d’appartenance**.</span><span class="sxs-lookup"><span data-stu-id="15840-135">Select **Assigned** in **Membership type**.</span></span>
    
5. <span data-ttu-id="15840-136">Cliquez sur **Créer** et fermez le panneau **Groupe**.</span><span class="sxs-lookup"><span data-stu-id="15840-136">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="15840-137">Répétez les étapes 3 à 5 pour des groupes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="15840-137">Repeat steps 3-5 for your additional groups.</span></span>
    
> [!NOTE]
> <span data-ttu-id="15840-p105">Vous devez utiliser le portail Azure pour créer les groupes afin qu’ils disposent de fonctionnalités d’Office. Si un site SharePoint Online isolé est plus loin configuré comme un site hautement confidentielles avec une étiquette d’Azure informations Protection (AIP) pour chiffrer les fichiers et attribuer des autorisations à des groupes spécifiques, les groupes autorisés doivent avoir été créés avec des fonctionnalités d’Office activé. Vous ne pouvez pas modifier le paramètre de fonctionnalités Office d’un groupe d’Azure AD après que qu’elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="15840-p105">You need to use the Azure portal to create the groups so that they have Office features enabled. If a SharePoint Online isolated site is later configured as a Highly Confidential site with an Azure Information Protection (AIP) label to encrypt files and assign permission to specific groups, the permitted groups must have been created with Office features enabled. You cannot change the Office features setting of an Azure AD group after it has been created.</span></span> 
  
<span data-ttu-id="15840-141">Voici votre configuration résultante avec les groupes d’accès de trois sites.</span><span class="sxs-lookup"><span data-stu-id="15840-141">Here is your resulting configuration with the three site access groups.</span></span>
  
![Trois groupes d’accès pour le déploiement d’un site SharePoint Online isolé.](media/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a><span data-ttu-id="15840-p106">Étape 5. Ajouter les comptes d’utilisateurs aux groupes d’accès</span><span class="sxs-lookup"><span data-stu-id="15840-p106">Step 5. Add the user accounts to the access groups</span></span>

<span data-ttu-id="15840-145">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="15840-145">In this step, do the following:</span></span>
  
1. <span data-ttu-id="15840-146">Ajoutez la liste des utilisateurs de l’étape 1 au groupe d’accès Administrateurs du site</span><span class="sxs-lookup"><span data-stu-id="15840-146">Add the list of users from step 1 to the site admins access group</span></span>
    
2. <span data-ttu-id="15840-147">Ajoutez la liste des utilisateurs de l’étape 2 au groupe d’accès Membres du site</span><span class="sxs-lookup"><span data-stu-id="15840-147">Add the list of users from step 2 to the site members access group</span></span>
    
3. <span data-ttu-id="15840-148">Ajoutez la liste des utilisateurs de l’étape 3 au groupe d’accès Visiteurs du site</span><span class="sxs-lookup"><span data-stu-id="15840-148">Add the list of users from step 3 to the site viewers access group</span></span>
    
<span data-ttu-id="15840-149">Si vous gérez des comptes d’utilisateur et des groupes via Windows Server AD, ajoutez les utilisateurs aux groupes d’accès appropriés en suivant les procédures classiques de gestion des utilisateurs et des groupes Windows Server AD, puis attendez la synchronisation avec votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="15840-149">If you are managing user accounts and groups through Windows Server AD, add users to the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="15840-p107">Si vous gérez des comptes d’utilisateur et des groupes via Office 365, vous pouvez utiliser le Centre d’administration Office ou PowerShell. Si plusieurs groupes d’accès portent le même nom, utilisez le Centre d’administration Office.</span><span class="sxs-lookup"><span data-stu-id="15840-p107">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell. If you have duplicate group names for any of the access groups, you should use the Office Admin center.</span></span>
  
<span data-ttu-id="15840-152">Le centre d’administration d’Office, se connecter avec un compte d’utilisateur qui a été affecté le rôle d’administrateur de compte d’utilisateur ou administrateur d’entreprise et utilisez des groupes pour ajouter les comptes d’utilisateur et les groupes aux groupes un accès approprié.</span><span class="sxs-lookup"><span data-stu-id="15840-152">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate user accounts and groups to the appropriate access groups.</span></span>
  
<span data-ttu-id="15840-153">Pour PowerShell, consultez la rubrique [Se connecter à Office 365 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="15840-153">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="15840-154">Ensuite, utilisez le bloc de commande suivante pour ajouter un compte d’utilisateur à un groupe d’accès :</span><span class="sxs-lookup"><span data-stu-id="15840-154">Next, use the following command block to add an individual user account to an access group:</span></span>
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> <span data-ttu-id="15840-155">Pour un fichier texte qui contient toutes les commandes PowerShell et une feuille de calcul de configuration Excel qui génère des commandes PowerShell en fonction des noms de compte de vos utilisateurs et groupes, téléchargez le [kit de déploiement du site d'équipe SharePoint Online isolé](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span><span class="sxs-lookup"><span data-stu-id="15840-155">For a text file that contains all the PowerShell commands and an Excel configuration worksheet that generates PowerShell commands based on your group and user account names, download the [Isolated SharePoint Online Team Site Deployment Kit](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span></span> 
  
<span data-ttu-id="15840-156">Si vous avez stocké les UPN des comptes d’utilisateur des groupes d’accès dans un fichier texte, vous pouvez exécuter le bloc de commandes PowerShell suivant pour les ajouter tous en même temps :</span><span class="sxs-lookup"><span data-stu-id="15840-156">If you stored the UPNs of user accounts for any of the access groups in a text file, you can use the following PowerShell command block to add them all at one time:</span></span>
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

<span data-ttu-id="15840-157">Pour PowerShell, utilisez le bloc de commande suivante pour ajouter un groupe à un groupe d’accès :</span><span class="sxs-lookup"><span data-stu-id="15840-157">For PowerShell, use the following command block to add an individual group to an access group:</span></span>
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

<span data-ttu-id="15840-158">Voici les résultats que vous devriez obtenir :</span><span class="sxs-lookup"><span data-stu-id="15840-158">The results should be the following:</span></span>
  
- <span data-ttu-id="15840-159">Groupe d’Azure AD administrateurs du site contient les comptes d’utilisateur de site d’administration ou les groupes</span><span class="sxs-lookup"><span data-stu-id="15840-159">The site admins Azure AD group contains the site admin user accounts or groups</span></span>
    
- <span data-ttu-id="15840-160">Groupe membres Azure AD site contient les comptes d’utilisateur membre du site ou les groupes</span><span class="sxs-lookup"><span data-stu-id="15840-160">The site members Azure AD group contains the site member user accounts or groups</span></span>
    
- <span data-ttu-id="15840-161">Le groupe de visionneuses Azure AD site contient les comptes d’utilisateurs ou les groupes qui peuvent uniquement visualiser le contenu de site</span><span class="sxs-lookup"><span data-stu-id="15840-161">The site viewers Azure AD group contains the user accounts or groups that can only view the site contents</span></span>
    
<span data-ttu-id="15840-162">Validez la liste des membres de chaque groupe d’accès avec le Centre d’administration Office ou le bloc de commandes PowerShell suivant :</span><span class="sxs-lookup"><span data-stu-id="15840-162">Validate the list of group members for each access group with the Office Admin center or with the following PowerShell command block:</span></span>
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

<span data-ttu-id="15840-163">Voici votre configuration résultante avec les groupes d’accès trois sites rempli avec des comptes d’utilisateurs ou des groupes.</span><span class="sxs-lookup"><span data-stu-id="15840-163">Here is your resulting configuration with the three site access groups populated with user accounts or groups.</span></span>
  
![Les trois groupes d’accès renseignés avec les comptes d’utilisateurs.](media/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a><span data-ttu-id="15840-165">Phase 2 : création et configuration du site d’équipe isolé</span><span class="sxs-lookup"><span data-stu-id="15840-165">Phase 2: Create and configure the isolated team site</span></span>

<span data-ttu-id="15840-166">Au cours de cette phase, vous allez créer le site SharePoint Online isolé et configurer les niveaux d’autorisation SharePoint Online par défaut pour utiliser vos nouveaux groupes d’accès Azure AD.</span><span class="sxs-lookup"><span data-stu-id="15840-166">In this phase, you create the isolated SharePoint Online site and configure the permissions for the default SharePoint Online permission levels to use your new Azure AD-based access groups.</span></span>
  
<span data-ttu-id="15840-167">Commencez par créer le site d’équipe SharePoint Online en suivant ces étapes.</span><span class="sxs-lookup"><span data-stu-id="15840-167">First, create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="15840-p108">Connectez-vous au portail Office 365 avec un compte qui sera également utilisé pour administrer le site d’équipe SharePoint Online (un administrateur SharePoint Online). Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="15840-p108">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="15840-170">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="15840-170">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="15840-171">Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.</span><span class="sxs-lookup"><span data-stu-id="15840-171">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="15840-172">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="15840-172">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="15840-173">Dans **nom du Site**, tapez un nom pour le site d’équipe.</span><span class="sxs-lookup"><span data-stu-id="15840-173">In **Site name**, type a name for the team site.</span></span> 
    
6. <span data-ttu-id="15840-174">Dans la **description du site d’équipe,** tapez une description facultative de l’objectif du site.</span><span class="sxs-lookup"><span data-stu-id="15840-174">In **Team site description,** type an optional description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="15840-175">Dans **Paramètres de confidentialité**, sélectionnez **Privé - Seuls les membres peuvent accéder à ce site**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="15840-175">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="15840-176">Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="15840-176">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="15840-177">Ensuite, dans le nouveau site d’équipe SharePoint Online, configurez les autorisations.</span><span class="sxs-lookup"><span data-stu-id="15840-177">Next, from the new SharePoint Online team site, configure permissions.</span></span>
  
1. <span data-ttu-id="15840-178">Dans la barre d’outils, cliquez sur l’icône Paramètres, puis cliquez sur **Paramètres du site**.</span><span class="sxs-lookup"><span data-stu-id="15840-178">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
2. <span data-ttu-id="15840-179">Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.</span><span class="sxs-lookup"><span data-stu-id="15840-179">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
3. <span data-ttu-id="15840-180">Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.</span><span class="sxs-lookup"><span data-stu-id="15840-180">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
4. <span data-ttu-id="15840-181">Dans la boîte de dialogue **Paramètres de demandes d’accès** , désactivez **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les demandes d’accès** (de sorte que toutes les cases à cocher trois sont désactivées), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="15840-181">In the **Access Requests Settings** dialog box, clear **Allow member to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
5. <span data-ttu-id="15840-182">Dans l’onglet **autorisations** de votre navigateur, cliquez sur ** \<nom du site > membres** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="15840-182">On the **Permissions** tab of your browser, click **\<site name> Members** in the list.</span></span>
    
6. <span data-ttu-id="15840-183">Dans **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="15840-183">In **People and Groups**, click **New**.</span></span>
    
7. <span data-ttu-id="15840-184">Dans la boîte de dialogue **Partager**, saisissez le nom du groupe d’accès Membres du site, sélectionnez-le, puis cliquez sur **Partager**.</span><span class="sxs-lookup"><span data-stu-id="15840-184">In the **Share** dialog box, type the name of the site members access group, select it, and then click **Share**.</span></span>
    
8. <span data-ttu-id="15840-185">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="15840-185">Click the back button on your browser.</span></span>
    
9. <span data-ttu-id="15840-186">Cliquez sur ** \<nom du site > propriétaires** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="15840-186">Click **\<site name> Owners** in the list.</span></span>
    
10. <span data-ttu-id="15840-187">Dans **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="15840-187">In **People and Groups**, click **New**.</span></span>
    
11. <span data-ttu-id="15840-188">Dans la boîte de dialogue **Partager**, saisissez le nom du groupe d’accès Administrateurs du site, sélectionnez-le, puis cliquez sur **Partager**.</span><span class="sxs-lookup"><span data-stu-id="15840-188">In the **Share** dialog box, type the name of the site admins access group, select it, and then click **Share**.</span></span>
    
12. <span data-ttu-id="15840-189">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="15840-189">Click the back button on your browser.</span></span>
    
13. <span data-ttu-id="15840-190">Cliquez sur ** \<nom du site > visiteurs** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="15840-190">Click **\<site name> Visitors** in the list.</span></span>
    
14. <span data-ttu-id="15840-191">Dans **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="15840-191">In **People and Groups**, click **New**.</span></span>
    
15. <span data-ttu-id="15840-192">Dans la boîte de dialogue **Partager**, saisissez le nom du groupe d’accès Visiteurs du site, sélectionnez-le, puis cliquez sur **Partager**.</span><span class="sxs-lookup"><span data-stu-id="15840-192">In the **Share** dialog box, type the name of the site viewers access group, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="15840-193">Fermez l’onglet **Autorisations** de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="15840-193">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="15840-194">Voici les résultats que vous devez escompter :</span><span class="sxs-lookup"><span data-stu-id="15840-194">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="15840-195">Le ** \<nom du site > propriétaires** groupe SharePoint contient le groupe Administrateurs de l’accès, dans laquelle tous les membres ont le niveau d’autorisation **contrôle total** .</span><span class="sxs-lookup"><span data-stu-id="15840-195">The **\<site name> Owners** SharePoint group contains the site admins access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="15840-196">Le ** \<nom du site > membres** groupe SharePoint contient le groupe membres de l’accès, dans lequel tous les membres ont le niveau d’autorisation **Modifier** .</span><span class="sxs-lookup"><span data-stu-id="15840-196">The **\<site name> Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="15840-197">Le ** \<nom du site > visiteurs** groupe SharePoint contient le groupe utilisateurs affichant les accès, dans laquelle tous les membres ont le niveau d’autorisation **en lecture** .</span><span class="sxs-lookup"><span data-stu-id="15840-197">The **\<site name> Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="15840-198">L’option permettant aux membres d’inviter d’autres membres ou non membres à demander l’accès au site est désactivée.
</span><span class="sxs-lookup"><span data-stu-id="15840-198">The ability for members to invite other members or for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="15840-199">Voici votre configuration résultante avec les trois groupes SharePoint pour le site configuré pour utiliser les trois groupes d’accès sont remplies avec les comptes d’utilisateurs ou des groupes d’Azure AD.</span><span class="sxs-lookup"><span data-stu-id="15840-199">Here is your resulting configuration with the three SharePoint groups for the site configured to use the three access groups, which are populated with user accounts or Azure AD groups.</span></span>
  
![Configuration finale de votre site SharePoint Online isolé avec des comptes d’utilisateurs et groupes d’accès.](media/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
<span data-ttu-id="15840-201">Comme vous êtes membres de l’un des groupes d’accès, vous et les membres du site pouvez désormais collaborer sur les ressources du site.</span><span class="sxs-lookup"><span data-stu-id="15840-201">You and the members of the site, through group membership in one of the access groups, can now collaborate using the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="15840-202">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="15840-202">Next step</span></span>

<span data-ttu-id="15840-203">Si vous avez besoin de modifier les membres du groupe d’accès du site ou de créer un dossier de documents avec des autorisations personnalisées, consultez la rubrique [Manage an isolated SharePoint Online team site](manage-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="15840-203">When you need to change site access group membership or create a document folder with custom permissions, see [Manage an isolated SharePoint Online team site](manage-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="15840-204">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15840-204">See Also</span></span>

[<span data-ttu-id="15840-205">Sites d'équipe SharePoint Online isolés</span><span class="sxs-lookup"><span data-stu-id="15840-205">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="15840-206">Conception d'un site d'équipe SharePoint Online isolé</span><span class="sxs-lookup"><span data-stu-id="15840-206">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="15840-207">Gestion d'un site d'équipe SharePoint Online isolé</span><span class="sxs-lookup"><span data-stu-id="15840-207">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="15840-208">Solutions de sécurité</span><span class="sxs-lookup"><span data-stu-id="15840-208">Security solutions</span></span>](security-solutions.md)



