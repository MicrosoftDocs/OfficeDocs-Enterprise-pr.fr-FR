---
title: Sécuriser les sites SharePoint Online dans un environnement de développement/test
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Résumé : Créez des sites d’équipe SharePoint Online publics, private, sensibles et hautement confidentielles dans un environnement de développement/test.'
ms.openlocfilehash: 8c02f1416cb00150e68dcc27dc7afb41bf82ed21
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="13cbc-103">Sécuriser des sites SharePoint Online dans un environnement de développement et de test</span><span class="sxs-lookup"><span data-stu-id="13cbc-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="13cbc-104">**Résumé :** Créer des sites d’équipe SharePoint Online publics, private, sensibles et hautement confidentielles dans un environnement de développement/test.</span><span class="sxs-lookup"><span data-stu-id="13cbc-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="13cbc-105">Cet article fournit des instructions détaillées pour créer un environnement de développement/test qui inclut quatre types de sites d’équipe SharePoint Online pour la solution de [fichiers et des sites d’informations sécurisé SharePoint Online](secure-sharepoint-online-sites-and-files.md) .</span><span class="sxs-lookup"><span data-stu-id="13cbc-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![Les quatre sites d’équipe dans l’environnement de développement/test SharePoint Online sécurisé.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="13cbc-107">Utilisez cet environnement de développement/test pour expérimenter les comportements de protection des informations et optimiser les paramètres en fonction de vos besoins avant de déployer des sites d’équipe SharePoint Online en production.</span><span class="sxs-lookup"><span data-stu-id="13cbc-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="13cbc-108">Phase 1 : Créer votre environnement de développement et de test</span><span class="sxs-lookup"><span data-stu-id="13cbc-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="13cbc-109">Dans cette phase, vous obtenez des abonnements d’essai pour Office 365 et Enterprise Mobility + Security pour une entreprise fictive.</span><span class="sxs-lookup"><span data-stu-id="13cbc-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="13cbc-110">Suivez d’abord les instructions de la **Phase 2** de [l’environnement de développement et de test Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="13cbc-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="13cbc-111">Ensuite, inscrivez-vous à l’abonnement d’évaluation EMS et ajoutez-le à la même organisation que votre abonnement d’évaluation Office 365.</span><span class="sxs-lookup"><span data-stu-id="13cbc-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="13cbc-p101">Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur global de votre abonnement d’évaluation. Pour une assistance, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="13cbc-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="13cbc-114">Cliquez sur la vignette **Administration**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="13cbc-115">Sous l’onglet **Centre d’administration Office** de votre navigateur, dans le volet de navigation gauche, cliquez sur **Facturation > Acheter des services**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="13cbc-p102">Dans la page **services d’achat** , trouver l’élément de la **mobilité d’entreprise + E5 de la sécurité** . Placez le pointeur de la souris au-dessus de celle-ci, cliquez sur **Démarrer la version d’évaluation gratuite**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="13cbc-118">Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="13cbc-119">Dans la page **Réception de la commande**, cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="13cbc-120">Ensuite, activez la licence Enterprise Mobility + Security E5 pour votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="13cbc-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="13cbc-121">Sous l’onglet **Centre d’administration Office 365** de votre navigateur, dans le volet de navigation gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="13cbc-122">Cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="13cbc-123">Dans le volet de **licences** , activer la licence de produit pour la **mobilité d’entreprise + sécurité E5** **activé**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .</span><span class="sxs-lookup"><span data-stu-id="13cbc-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="13cbc-124">Phase 2 : Créer et configurer vos groupes et vos utilisateurs Azure Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="13cbc-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="13cbc-125">Dans cette phase, vous créez et vous configurez les groupes et les utilisateurs Azure AD de votre organisation fictive.</span><span class="sxs-lookup"><span data-stu-id="13cbc-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="13cbc-126">Commencez par créer un ensemble de groupes pour une organisation standard avec le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="13cbc-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="13cbc-127">Créer un onglet séparé dans votre navigateur, puis accédez au portail Azure à [https://portal.azure.com](https://portal.azure.com). Si nécessaire, connectez-vous à l’aide les informations d’identification du compte d’administrateur global de votre abonnement d’évaluation Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="13cbc-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="13cbc-128">Dans le portail Azure, cliquez sur **Azure Active Directory > Utilisateurs et groupes > Tous les groupes**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-128">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="13cbc-129">Dans le panneau **Tous les groupes**, cliquez sur **+ Nouveau groupe**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="13cbc-130">Dans le panneau **Groupe** :</span><span class="sxs-lookup"><span data-stu-id="13cbc-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="13cbc-131">Tapez **C-Suite** dans le champ **Nom**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-131">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="13cbc-132">Sélectionnez **Affecté** dans le champ **Appartenance**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-132">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="13cbc-133">Cliquez sur **Oui** pour **Activer les fonctionnalités Office**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-133">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="13cbc-134">Cliquez sur **Créer** et fermez le panneau **Groupe**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="13cbc-135">Répétez les étapes 3 à 5 pour les noms de groupe suivants :</span><span class="sxs-lookup"><span data-stu-id="13cbc-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="13cbc-136">Équipe Informatique</span><span class="sxs-lookup"><span data-stu-id="13cbc-136">IT staff</span></span>
    
  - <span data-ttu-id="13cbc-137">Équipe Recherche</span><span class="sxs-lookup"><span data-stu-id="13cbc-137">Research staff</span></span>
    
  - <span data-ttu-id="13cbc-138">Équipe Standard</span><span class="sxs-lookup"><span data-stu-id="13cbc-138">Regular staff</span></span>
    
  - <span data-ttu-id="13cbc-139">Équipe Marketing</span><span class="sxs-lookup"><span data-stu-id="13cbc-139">Marketing staff</span></span>
    
  - <span data-ttu-id="13cbc-140">Équipe Ventes</span><span class="sxs-lookup"><span data-stu-id="13cbc-140">Sales staff</span></span>
    
7. <span data-ttu-id="13cbc-141">Gardez ouvert l’onglet du portail Azure dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="13cbc-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="13cbc-142">Ensuite, configurez l’octroi de licence automatique afin que des licences soient automatiquement attribuées aux membres de vos groupes pour les abonnements Office 365 et EMS.</span><span class="sxs-lookup"><span data-stu-id="13cbc-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="13cbc-143">Dans le portail Azure, cliquez sur **Azure Active Directory > Licences > Tous les produits**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="13cbc-144">Dans la liste, sélectionnez la **mobilité d’entreprise + sécurité E5** et **Office 365 entreprise E5**, puis cliquez sur **affecter**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="13cbc-145">Dans le panneau **Affecter une licence**, cliquez sur **Utilisateurs et groupes**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="13cbc-146">Dans la liste des groupes, sélectionnez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="13cbc-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="13cbc-147">C-Suite</span><span class="sxs-lookup"><span data-stu-id="13cbc-147">C-Suite</span></span>
    
  - <span data-ttu-id="13cbc-148">Équipe Informatique</span><span class="sxs-lookup"><span data-stu-id="13cbc-148">IT staff</span></span>
    
  - <span data-ttu-id="13cbc-149">Équipe Recherche</span><span class="sxs-lookup"><span data-stu-id="13cbc-149">Research staff</span></span>
    
  - <span data-ttu-id="13cbc-150">Équipe Standard</span><span class="sxs-lookup"><span data-stu-id="13cbc-150">Regular staff</span></span>
    
  - <span data-ttu-id="13cbc-151">Équipe Marketing</span><span class="sxs-lookup"><span data-stu-id="13cbc-151">Marketing staff</span></span>
    
  - <span data-ttu-id="13cbc-152">Équipe Ventes</span><span class="sxs-lookup"><span data-stu-id="13cbc-152">Sales staff</span></span>
    
5. <span data-ttu-id="13cbc-153">Cliquez sur **Sélectionner**, puis cliquez sur **affecter**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="13cbc-154">Fermez l’onglet du portail Azure dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="13cbc-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="13cbc-155">Ensuite, vous vous [connectez au module PowerShell Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="13cbc-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="13cbc-156">Renseignez nom de votre organisation, votre emplacement et un mot de passe commun, puis exécutez les commandes suivantes à partir de l’invite de commandes PowerShell ou Integrated Script Environment (ISE) pour créer des comptes d’utilisateurs et les ajouter à leurs groupes :</span><span class="sxs-lookup"><span data-stu-id="13cbc-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> <span data-ttu-id="13cbc-p103">L’utilisation d’un mot de passe commun permet d’automatiser et de faciliter la configuration d’un environnement de développement/test. Il n’est pas recommandé de l’utiliser dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="13cbc-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="13cbc-159">Utilisez ces étapes pour vérifier que la gestion des licences basée sur un groupe fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="13cbc-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="13cbc-160">Sous l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur la vignette **Administration**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="13cbc-161">Sous le nouvel onglet **Centre d’administration Office** de votre navigateur, cliquez sur **Utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="13cbc-162">Dans la liste des utilisateurs, cliquez sur **PDG**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="13cbc-163">Dans le volet qui affiche les propriétés du compte d’utilisateur **PDG**, vérifiez que les licences **Enterprise Mobility + Security E5** et **Office 365 Enterprise E5** lui ont été affectées (dans **Licences de produit**).</span><span class="sxs-lookup"><span data-stu-id="13cbc-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="13cbc-164">Phase 3 : Créer des étiquettes Office 365</span><span class="sxs-lookup"><span data-stu-id="13cbc-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="13cbc-165">Dans cette phase, vous créez les étiquettes pour les différents niveaux de sécurité des dossiers de documents du site d’équipe SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="13cbc-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="13cbc-p104">Si nécessaire, utilisez une instance privée de votre navigateur Internet et connectez-vous au portail Office 365 avec le compte d’administrateur global de votre abonnement d’évaluation Office 365 E5. Pour une assistance, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="13cbc-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="13cbc-168">Sous l’onglet **Accueil Microsoft Office**, cliquez sur la vignette **Administration**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="13cbc-169">À partir de l’onglet nouveau **Centre d’administration d’Office** de votre navigateur, cliquez sur **centres d’administration > sécurité &amp; conformité**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="13cbc-170">À partir du nouveau **Accueil - sécurité &amp; conformité** onglet de votre navigateur, cliquez sur **Classifications > étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="13cbc-171">Dans le volet **Accueil > Étiquettes**, cliquez sur **Créer une étiquette**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="13cbc-172">Dans le volet de **l’étiquette de nom** , tapez **Public interne**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="13cbc-173">Dans le volet **Paramètres de l’étiquette**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="13cbc-174">Dans le volet **passez en revue vos paramètres** , cliquez sur **créer cette étiquette**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="13cbc-175">Répétez les étapes 5 à 8 pour ces étiquettes supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="13cbc-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="13cbc-176">Privé</span><span class="sxs-lookup"><span data-stu-id="13cbc-176">Private</span></span>
    
  - <span data-ttu-id="13cbc-177">Sensible</span><span class="sxs-lookup"><span data-stu-id="13cbc-177">Sensitive</span></span>
    
  - <span data-ttu-id="13cbc-178">Hautement confidentiel</span><span class="sxs-lookup"><span data-stu-id="13cbc-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="13cbc-179">Dans le volet **Accueil > Étiquettes**, cliquez sur **Publier des étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="13cbc-180">Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Choisir les étiquettes à publier**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="13cbc-181">Dans le volet **Choisir des étiquettes**, cliquez sur **Ajouter** et sélectionnez les quatre étiquettes.</span><span class="sxs-lookup"><span data-stu-id="13cbc-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="13cbc-182">Cliquez sur **Terminé**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="13cbc-183">Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="13cbc-184">Dans le volet **Choisir les emplacements**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="13cbc-185">Dans le volet **nom de votre stratégie** , tapez **exemple d’entreprise** dans **nom**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="13cbc-186">Dans le volet **passez en revue vos paramètres** , cliquez sur **publier les étiquettes**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="13cbc-187">Phase 4 : Créer vos sites d’équipe SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="13cbc-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="13cbc-188">Dans cette phase, vous créez et vous configurez les quatre types de sites d’équipe SharePoint Online pour votre exemple d’organisation.</span><span class="sxs-lookup"><span data-stu-id="13cbc-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="13cbc-189">Site d’équipe au niveau de l’organisation</span><span class="sxs-lookup"><span data-stu-id="13cbc-189">Organization wide team site</span></span>

<span data-ttu-id="13cbc-190">Pour créer une base de référence de site d’équipe SharePoint Online public, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="13cbc-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="13cbc-p105">Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 en utilisant votre compte d’administrateur général. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="13cbc-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="13cbc-193">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="13cbc-194">Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="13cbc-195">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="13cbc-196">Dans **Nom du site**, tapez **Toute l’organisation**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="13cbc-197">Dans **Description du site d’équipe**, tapez **Site SharePoint pour toute l’organisation**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="13cbc-198">Dans **les paramètres de confidentialité**, sélectionnez **Public - tout le monde dans l’organisation permettre accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="13cbc-199">Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="13cbc-200">Ensuite, configurez le dossier des documents du site d’équipe Toute l’organisation pour l’étiquette Publique interne.</span><span class="sxs-lookup"><span data-stu-id="13cbc-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="13cbc-201">Dans l’onglet **Organisation wide-d’accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="13cbc-202">Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="13cbc-203">Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="13cbc-204">Dans **Les paramètres s’appliquent une étiquette**, sélectionnez **Public interne**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="13cbc-205">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="13cbc-205">Here is your resulting configuration.</span></span>
  
![Protection de base pour le site d’équipe SharePoint Online consultable par les membres de l’organisation.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="13cbc-207">Site d’équipe Projet 1</span><span class="sxs-lookup"><span data-stu-id="13cbc-207">Project 1 team site</span></span>

<span data-ttu-id="13cbc-208">Pour créer un site d’équipe SharePoint Online privé de base de référence pour un projet au sein de l’organisation, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="13cbc-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="13cbc-p106">Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 en utilisant votre compte d’administrateur général. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="13cbc-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="13cbc-211">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="13cbc-212">Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="13cbc-213">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="13cbc-214">Dans **Nom du site**, tapez **Projet 1**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="13cbc-215">Dans la **description du site d’équipe,** tapez **le site SharePoint pour le projet 1**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="13cbc-216">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="13cbc-217">Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="13cbc-218">Ensuite, configurez le dossier des documents du site d’équipe Projet 1 pour l’étiquette Privé.</span><span class="sxs-lookup"><span data-stu-id="13cbc-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="13cbc-219">Sous l’onglet **Projet 1 - Accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="13cbc-220">Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="13cbc-221">Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="13cbc-222">Dans **Les paramètres s’appliquent une étiquette**, sélectionnez **privée**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="13cbc-223">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="13cbc-223">Here is your resulting configuration.</span></span>
  
![Protection de base pour le site d’équipe SharePoint Online privé concernant Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="13cbc-225">Site d’équipe des campagnes marketing</span><span class="sxs-lookup"><span data-stu-id="13cbc-225">Marketing campaigns team site</span></span>

<span data-ttu-id="13cbc-226">Pour créer un site d’équipe SharePoint Online isolé de niveau sensible pour les ressources des campagnes marketing, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="13cbc-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="13cbc-p107">À l’aide d’un navigateur sur votre ordinateur local, connectez-vous au portail Office 365 à l’aide de votre compte d’administrateur global. Pour une assistance, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="13cbc-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="13cbc-229">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="13cbc-230">Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="13cbc-231">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="13cbc-232">Dans **Nom du site d’équipe**, tapez **Campagnes marketing**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="13cbc-233">Dans **Description du site d’équipe**, tapez **Site SharePoint pour les ressources des campagnes marketing (sensible)**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="13cbc-234">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="13cbc-235">Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="13cbc-236">Sous l’onglet Nouveau de **campagnes Marketing** dans votre navigateur, dans la barre d’outils, cliquez sur l’icône Paramètres, puis cliquez sur **autorisations de Site**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="13cbc-237">Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="13cbc-238">Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="13cbc-239">Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez les cases à cocher **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** , tapez **ITAdmin1 @**\<votre nom de l’organisation >**. onmicrosoft.com** dans **Envoyer toutes les demandes d’accès**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="13cbc-240">Cliquez sur **Membres de Campagnes marketing** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="13cbc-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="13cbc-241">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="13cbc-242">Dans la boîte de dialogue **partager** , tapez **équipe Marketing**, sélectionnez-le, puis cliquez sur **partager**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="13cbc-243">Répétez les étapes 14 et 15 pour le compte d’utilisateur **Researcher1** .</span><span class="sxs-lookup"><span data-stu-id="13cbc-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="13cbc-244">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="13cbc-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="13cbc-245">Dans la liste, cliquez sur **campagnes Marketing propriétaires** .</span><span class="sxs-lookup"><span data-stu-id="13cbc-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="13cbc-246">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="13cbc-247">Dans la boîte de dialogue **partager** , tapez **personnel informatique**, sélectionnez-le, puis cliquez sur **partager**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="13cbc-248">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="13cbc-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="13cbc-249">Fermez l’onglet **personnes et groupes** dans votre navigateur, cliquez sur l’onglet **accueil-campagnes de Marketing** dans votre navigateur, puis fermez le volet **autorisations de Site** .</span><span class="sxs-lookup"><span data-stu-id="13cbc-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="13cbc-250">Voici les résultats de la configuration des autorisations :</span><span class="sxs-lookup"><span data-stu-id="13cbc-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="13cbc-251">Le groupe SharePoint **Campagnes marketing - Membres** contient seulement le groupe **Campagnes marketing** (qui contient le compte d’utilisateur Administrateur global), le groupe **Équipe Marketing** (qui contient les comptes d’utilisateur Marketing1 et Marketing2) et le compte d’utilisateur **Chercheur1**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="13cbc-252">Le groupe SharePoint **Campagnes marketing - Propriétaires** contient seulement le groupe **Équipe Informatique** (qui contient seulement les comptes d’utilisateur ITAdmin1 et ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="13cbc-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="13cbc-253">Le groupe SharePoint **Campagnes marketing - Visiteurs** ne contient aucun groupe ni compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="13cbc-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="13cbc-254">Les membres ne peuvent pas modifier les autorisations au niveau du site (ceci peut être fait seulement par les membres du groupe **Campagnes marketing - Propriétaires**).</span><span class="sxs-lookup"><span data-stu-id="13cbc-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="13cbc-255">Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, mais peuvent demander d’avoir accès au site. Un courrier électronique sera envoyé à la boîte aux lettres du compte d’utilisateur ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="13cbc-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="13cbc-256">Ensuite, configurez le dossier des documents du site d’équipe Campagnes marketing pour l’étiquette Sensible.</span><span class="sxs-lookup"><span data-stu-id="13cbc-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="13cbc-257">Sous l’onglet **Campagne marketing - Accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="13cbc-258">Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="13cbc-259">Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="13cbc-260">Dans **Les paramètres s’appliquent une étiquette**, sélectionnez **sensibles**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="13cbc-261">Ensuite, configurez une stratégie de protection contre la perte de données qui avertit les utilisateurs quand ils partagent un document à l’extérieur de l’organisation sur un site d’équipe SharePoint Online avec l’étiquette Sensible, qui inclut le site Campagnes marketing.</span><span class="sxs-lookup"><span data-stu-id="13cbc-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="13cbc-262">Sous l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; conformité** mosaïque.</span><span class="sxs-lookup"><span data-stu-id="13cbc-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="13cbc-263">Sur la nouvelle **sécurité &amp; conformité** dans votre navigateur, cliquez sur **prévention des pertes de données > stratégie**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="13cbc-264">Dans le volet **Protection contre la perte de données**, cliquez sur **+ Créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="13cbc-265">Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisé**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="13cbc-266">Dans le volet **nom de votre stratégie** , tapez les **sites d’équipe SharePoint Online étiquette sensibles** dans **nom**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="13cbc-267">Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="13cbc-268">Dans la liste des emplacements, désactiver les emplacements des **comptes de OneDrive** et de **messagerie Exchange** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="13cbc-269">Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="13cbc-270">Dans le volet **Sélectionner les types de contenu pour protéger** , cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="13cbc-271">Dans le volet **d’étiquettes** , cliquez sur **+ Ajouter**, sélectionnez l’étiquette **sensibles** , cliquez sur **Ajouter**, puis cliquez sur **terminé**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="13cbc-272">Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="13cbc-273">Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="13cbc-274">Dans le volet **Que voulez-vous faire si nous détectons des informations confidentielles ?**, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="13cbc-275">Dans le volet **Personnaliser les conseils et les notifications par e-mail de la stratégie**, cliquez sur **Personnaliser le texte de l’info-bulle de la stratégie**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="13cbc-276">Dans la zone de texte, tapez ou collez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="13cbc-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="13cbc-p108">Pour partager avec un utilisateur à l’extérieur de l’organisation, téléchargez le fichier, puis ouvrez-le. Cliquez sur Fichier, sur Protéger le document et sur Chiffrer avec mot de passe, puis spécifiez un mot de passe fort. Envoyez le mot de passe dans un e-mail distinct ou via un autre moyen de communication.</span><span class="sxs-lookup"><span data-stu-id="13cbc-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="13cbc-280">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="13cbc-281">Dans la **que voulez-vous faire si nous détecter des informations sensibles ?** volet, désactivez la case à cocher **bloquer les personnes de partager et restreindre l’accès au contenu partagé** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="13cbc-282">Dans la **vous souhaitez activer les opérations de test ou de stratégie extraire au préalable ?** volet, cliquez sur **Oui, activer immédiatement**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="13cbc-283">Dans le volet **passez en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="13cbc-284">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="13cbc-284">Here is your resulting configuration.</span></span>
  
![Protection des données sensibles pour les sites d’équipe SharePoint Online isolés des campagnes marketing.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="13cbc-286">Site d’équipe Stratégie d’entreprise</span><span class="sxs-lookup"><span data-stu-id="13cbc-286">Company strategy team site</span></span>

<span data-ttu-id="13cbc-287">Pour créer un site d’équipe SharePoint Online isolé au niveau Hautement confidentiel pour les ressources d’entreprise stratégiques des dirigeants de l’organisation, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="13cbc-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="13cbc-p109">Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 en utilisant votre compte d’administrateur général. Pour obtenir de l’aide, consultez [Où se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="13cbc-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="13cbc-290">Dans la liste des vignettes, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="13cbc-291">Sous le nouvel onglet **SharePoint** de votre navigateur, cliquez sur **+ Créer un site**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="13cbc-292">Dans la page **Créer un site**, cliquez sur **Site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="13cbc-293">Dans **Nom du site d’équipe**, tapez **Stratégie de l’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="13cbc-294">Dans **Description du site d’équipe**, tapez **Site SharePoint pour la stratégie de l’entreprise (Hautement confidentiel)**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="13cbc-295">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="13cbc-296">Dans le volet **Qui voulez-vous ajouter ?**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="13cbc-297">Sous l’onglet **stratégie de la société** de nouveau dans votre navigateur, dans la barre d’outils, cliquez sur l’icône Paramètres, puis cliquez sur **autorisations de Site**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="13cbc-298">Dans le volet **Autorisations du site**, cliquez sur **Paramètres d’autorisations avancés**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="13cbc-299">Sous le nouvel onglet **Autorisations** dans votre navigateur, cliquez sur **Paramètres des demandes d’accès**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="13cbc-300">Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** et **permettre aux membres de partager le site et les fichiers et dossiers individuels** (de sorte que toutes les cases à cocher trois sont désactivées), puis cliquez sur ** OK**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="13cbc-301">Dans la liste, cliquez sur **stratégie d’entreprise membres** .</span><span class="sxs-lookup"><span data-stu-id="13cbc-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="13cbc-302">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="13cbc-303">Dans la boîte de dialogue **partager** , tapez **C-Suite**, sélectionnez-le, puis cliquez sur **partager**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="13cbc-304">Dans la liste, cliquez sur **stratégie d’entreprise propriétaires** .</span><span class="sxs-lookup"><span data-stu-id="13cbc-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="13cbc-305">Dans la page **Personnes et groupes**, cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="13cbc-306">Dans la boîte de dialogue **partager** , tapez **personnel informatique**, sélectionnez-le, puis cliquez sur **partager**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="13cbc-307">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="13cbc-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="13cbc-308">Fermez l’onglet **personnes et groupes** dans votre navigateur, cliquez sur l’onglet **Accueil stratégie de la société** dans votre navigateur, puis fermez le volet **autorisations de Site** .</span><span class="sxs-lookup"><span data-stu-id="13cbc-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="13cbc-309">Voici les résultats de la configuration des autorisations :</span><span class="sxs-lookup"><span data-stu-id="13cbc-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="13cbc-310">Le groupe SharePoint **Stratégie de l’entreprise - Membres** contient seulement le groupe **C-Suite** (qui contient uniquement les comptes d’utilisateur PDG, Directeur financier et Directeur informatique) et le groupe **Stratégie de l’entreprise** (qui contient uniquement le compte d’utilisateur de l’administrateur général).</span><span class="sxs-lookup"><span data-stu-id="13cbc-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="13cbc-311">Le groupe SharePoint **Propriétaires de stratégie de sociétés** contient uniquement le groupe de **personnel informatique** (qui contienne uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="13cbc-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="13cbc-312">Le groupe SharePoint **Stratégie de l’entreprise - Visiteurs** ne contient aucun groupe ni compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="13cbc-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="13cbc-313">Les membres ne peuvent pas modifier les autorisations au niveau du site (ceci peut être fait seulement par les membres du groupe **Stratégie de l’entreprise - Propriétaires**).</span><span class="sxs-lookup"><span data-stu-id="13cbc-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="13cbc-p110">Les autres comptes d’utilisateur ne peuvent ni accéder au site ou à ses ressources, ni demander l’accès au site. Des autorisations supplémentaires pour le site doivent être octroyées par l’administrateur général ou un membre du groupe **Stratégie de l’entreprise - Propriétaires**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="13cbc-316">Ensuite, configurez le dossier des documents du site d’équipe Stratégie de l’entreprise pour l’étiquette Hautement confidentiel.</span><span class="sxs-lookup"><span data-stu-id="13cbc-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="13cbc-317">Sous l’onglet **Stratégie de l’entreprise - Accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="13cbc-318">Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="13cbc-319">Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="13cbc-320">Dans **Les paramètres s’appliquent une étiquette**, sélectionnez **Hautement confidentielles**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="13cbc-321">Ensuite, configurez une stratégie de protection contre la perte de données qui bloque les utilisateurs quand ils partagent un document à l’extérieur de l’organisation sur un site d’équipe SharePoint Online avec l’étiquette Hautement confidentiel, qui inclut le site Stratégie de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="13cbc-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="13cbc-p111">Si nécessaire, utilisez un navigateur sur votre ordinateur local et connectez-vous au portail Office 365 avec un compte qui dispose du rôle d’administrateur de sécurité ou administrateur d’entreprise. Pour une assistance, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="13cbc-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="13cbc-324">Sous l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; conformité** mosaïque.</span><span class="sxs-lookup"><span data-stu-id="13cbc-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="13cbc-325">Sur la nouvelle **sécurité &amp; conformité** dans votre navigateur, cliquez sur **prévention des pertes de données > stratégie**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="13cbc-326">Dans le volet **Protection contre la perte de données**, cliquez sur **+ Créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="13cbc-327">Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisé**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="13cbc-328">Dans le volet **nom de votre stratégie** , tapez les **sites d’équipe SharePoint Online hautement confidentielles étiquette** dans **nom**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="13cbc-329">Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="13cbc-330">Dans la liste des emplacements, désactiver les emplacements des **comptes de OneDrive** et de **messagerie Exchange** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="13cbc-331">Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="13cbc-332">Dans le volet **Sélectionner les types de contenu pour protéger** , cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="13cbc-333">Dans le volet **d’étiquettes** , cliquez sur **+ Ajouter**, sélectionnez l’étiquette **Hautement confidentielles** , cliquez sur **Ajouter**, puis cliquez sur **terminé**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="13cbc-334">Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="13cbc-335">Dans le volet **Personnaliser les types d’informations sensibles que vous voulez protéger**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="13cbc-336">Dans le volet **Que voulez-vous faire si nous détectons des informations confidentielles ?**, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="13cbc-337">Dans le volet **Personnaliser les conseils et les notifications par e-mail de la stratégie**, cliquez sur **Personnaliser le texte de l’info-bulle de la stratégie**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="13cbc-338">Dans la zone de texte, tapez ou collez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="13cbc-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="13cbc-p112">Pour partager avec un utilisateur à l’extérieur de l’organisation, téléchargez le fichier, puis ouvrez-le. Cliquez sur Fichier, sur Protéger le document et sur Chiffrer avec mot de passe, puis spécifiez un mot de passe fort. Envoyez le mot de passe dans un e-mail distinct ou via un autre moyen de communication.</span><span class="sxs-lookup"><span data-stu-id="13cbc-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="13cbc-342">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="13cbc-343">Dans la **que voulez-vous faire si nous détecter des informations sensibles ?** volet, sélectionnez **Exiger une justification à remplacer**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="13cbc-344">Dans la **vous souhaitez activer les opérations de test ou de stratégie extraire au préalable ?** volet, cliquez sur **Oui, activer immédiatement**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="13cbc-345">Dans le volet **passez en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="13cbc-346">Suivez ensuite les instructions contenues dans [Comment activer Azure Rights Management à partir du centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="13cbc-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="13cbc-347">Ensuite, configurez Azure Information Protection avec une nouvelle stratégie délimitée et une sous-étiquette pour la protection et les autorisations en suivant ces étapes :</span><span class="sxs-lookup"><span data-stu-id="13cbc-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="13cbc-p113">Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="13cbc-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="13cbc-350">Dans un onglet séparé de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="13cbc-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="13cbc-351">Si vous configurez Azure Information Protection pour la première fois, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="13cbc-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="13cbc-352">Dans le volet Liste, cliquez sur **Plus de services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="13cbc-353">Sur le panneau **Azure Information Protection**, cliquez sur **Stratégies étendues > + Ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="13cbc-354">Tapez **CompanyStrategy** dans **Nom de la stratégie** et **Étiquette pour les documents dans le site d’équipe Stratégie d’entreprise** dans **Description**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="13cbc-355">Cliquez sur **Sélectionner les utilisateurs ou groupes devant recevoir cette stratégie > Utilisateurs/Groupes**, puis sélectionnez **C-Suite**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="13cbc-356">Cliquez sur **Sélectionner > OK**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="13cbc-357">Pour l’étiquette **Hautement confidentiel**, cliquez sur les points de suspension (...), puis sur **Ajouter une sous-étiquette**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="13cbc-358">Entrez le nom de la sous-étiquette dans **Nom** et sa description dans **Description**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="13cbc-359">Cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="13cbc-360">Dans la section **Protection**, cliquez sur **Azure (clé cloud)**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="13cbc-361">Dans le panneau **Protection**, sous **Paramètres de protection**, cliquez sur **+ Ajouter des autorisations**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="13cbc-362">Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="13cbc-363">Dans le volet **DAS utilisateurs et groupes** , sélectionnez **C-Suite**, puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="13cbc-364">Sous **Choisir des autorisations à partir de valeurs prédéfinies**, désactivez les cases à cocher **Imprimer **, **Copier et extraire le contenu** et **Transférer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="13cbc-365">Cliquez deux fois sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="13cbc-366">Dans le panneau **Sous-étiquette**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="13cbc-367">Fermez le panneau de la nouvelle stratégie étendue.</span><span class="sxs-lookup"><span data-stu-id="13cbc-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="13cbc-368">Sur le serveur lame **Azure Information protection - stratégies d’étendue** , cliquez sur **Publier**, puis cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="13cbc-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="13cbc-369">Pour protéger un document avec la Protection des informations Azure et cette nouvelle étiquette, vous devez [installer le client Azure la Protection des informations](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur un ordinateur de test, installez Office à partir du portail Office 365 et puis se connecter à partir de Microsoft Word avec un compte dans le ** C-Suite** groupe de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="13cbc-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="13cbc-370">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="13cbc-370">Here is your resulting configuration.</span></span>
  
![Protection avec un niveau de confidentialité élevé pour le site d’équipe SharePoint Online isolé de la stratégie d’entreprise.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="13cbc-372">Vous êtes maintenant prêt à créer des documents dans ces quatre sites et à tester l’accès à ceux-ci avec différents comptes d’utilisateur de votre abonnement d’essai.</span><span class="sxs-lookup"><span data-stu-id="13cbc-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="13cbc-373">Voici la configuration globale pour les quatre sites d’équipe SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="13cbc-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![Les quatre sites d’équipe dans l’environnement de développement/test SharePoint Online sécurisé.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="13cbc-375">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="13cbc-375">Next step</span></span>

<span data-ttu-id="13cbc-376">Quand vous êtes prêt à effectuer le déploiement en production de sites SharePoint Online sécurisés, consultez [Sécuriser des sites et des fichiers SharePoint Online](secure-sharepoint-online-sites-and-files.md) pour obtenir des informations détaillées et des liens vers des articles sur le déploiement étape par étape.</span><span class="sxs-lookup"><span data-stu-id="13cbc-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="13cbc-377">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13cbc-377">See Also</span></span>

[<span data-ttu-id="13cbc-378">Sécuriser les fichiers et sites SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="13cbc-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="13cbc-379">Solutions de sécurité</span><span class="sxs-lookup"><span data-stu-id="13cbc-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="13cbc-380">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="13cbc-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="13cbc-381">Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles</span><span class="sxs-lookup"><span data-stu-id="13cbc-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




