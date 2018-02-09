---
title: "Sécuriser les sites SharePoint Online dans un environnement de développement/test"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "Résumé : Créer des sites d’équipe SharePoint Online publiques, privées, sensibles et hautement confidentielles dans un environnement de développement/test."
ms.openlocfilehash: 55adc5f7cdbf197acf3ca68623139c01912c602f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="19d9b-103">Sécuriser les sites SharePoint Online dans un environnement de développement/test</span><span class="sxs-lookup"><span data-stu-id="19d9b-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="19d9b-104">**Résumé :** Créer des sites d’équipe SharePoint Online publiques, privées, sensibles et hautement confidentielles dans un environnement de développement/test.</span><span class="sxs-lookup"><span data-stu-id="19d9b-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="19d9b-105">Cet article fournit des instructions pas à pas pour créer un environnement de développement/test qui inclut les quatre types différents de sites d’équipe SharePoint Online pour la solution de [fichiers et des sites SharePoint Online de la sécuriser](secure-sharepoint-online-sites-and-files.md) .</span><span class="sxs-lookup"><span data-stu-id="19d9b-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![Les quatre sites d’équipe dans l’environnement de développement/test SharePoint Online sécurisé.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="19d9b-107">Cet environnement de développement/test permet de faire des essais avec les comportements de protection des informations et d’affiner les paramètres pour vos besoins avant de déployer des sites d’équipe SharePoint Online dans la production.</span><span class="sxs-lookup"><span data-stu-id="19d9b-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="19d9b-108">Phase 1 : Création d’un environnement de développement/test</span><span class="sxs-lookup"><span data-stu-id="19d9b-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="19d9b-109">Dans cette phase, vous obtenez des abonnements d’essai d’Office 365 et de mobilité d’entreprise + de sécurité pour une entreprise fictive.</span><span class="sxs-lookup"><span data-stu-id="19d9b-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="19d9b-110">Tout d’abord, suivez les instructions de la **Phase 2** de l' [environnement de développement/test d’Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="19d9b-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="19d9b-111">Ensuite, inscrivez-vous à l’abonnement d’évaluation EMS et ajoutez-le à la même organisation que votre abonnement d’évaluation Office 365.</span><span class="sxs-lookup"><span data-stu-id="19d9b-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="19d9b-p101">Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur global de votre abonnement d’évaluation. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="19d9b-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="19d9b-114">Cliquez sur la mosaïque de **l’Admin** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="19d9b-115">Dans l’onglet **Centre d’administration d’Office** dans votre navigateur, dans la navigation de gauche, cliquez sur **de facturation > acheter les services**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="19d9b-p102">Dans la page **services d’achat** , trouver la **mobilité d’entreprise + E5 de la sécurité** . Placez le pointeur de la souris sur elle et cliquez sur **Démarrer la version d’évaluation gratuite**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="19d9b-118">Dans la page **Confirmer votre commande** , cliquez sur **Essayer maintenant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="19d9b-119">Dans la page **reçu de commande** , cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="19d9b-120">Activez ensuite la licence Enterprise Mobility + Security E5 pour votre compte d’administrateur général.</span><span class="sxs-lookup"><span data-stu-id="19d9b-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="19d9b-121">Dans l’onglet **Centre d’administration d’Office 365** dans votre navigateur, dans la navigation de gauche, cliquez sur **les utilisateurs > utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="19d9b-122">Cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="19d9b-123">Dans le volet des **licences** , activer la licence du produit de **mobilité d’entreprise + sécurité E5** **on**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="19d9b-124">Phase 2 : Créer et configurer des groupes d’Azure Active Directory (AD) et des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="19d9b-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="19d9b-125">Dans cette phase, vous créez et configurez les groupes d’annonces Azure et les utilisateurs de votre organisation fictive.</span><span class="sxs-lookup"><span data-stu-id="19d9b-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="19d9b-126">Tout d’abord, créez un ensemble de groupes pour une organisation typique avec le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="19d9b-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="19d9b-127">Créer un onglet distinct dans votre navigateur et passez au portail Azure à [https://portal.azure.com](https://portal.azure.com). Si nécessaire, connectez-vous en utilisant les informations d’identification du compte d’administrateur global pour votre abonnement d’évaluation d’Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="19d9b-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="19d9b-128">Dans le portail Azure, cliquez sur **Azure Active Directory > utilisateurs et groupes > tous les groupes de**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-128">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="19d9b-129">Sur la lame de **tous les groupes** , cliquez sur **+ le nouveau groupe**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="19d9b-130">Sur la lame de **groupe** :</span><span class="sxs-lookup"><span data-stu-id="19d9b-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="19d9b-131">Type **C-Suite** dans la zone **nom**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-131">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="19d9b-132">Sélectionnez **affecté** dans **l’appartenance**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-132">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="19d9b-133">Cliquez sur **Oui** pour **activer Office fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-133">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="19d9b-134">Cliquez sur **créer**, puis fermez la lame du **groupe** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="19d9b-135">Répétez les étapes 3 à 5 pour les noms de groupe suivants :</span><span class="sxs-lookup"><span data-stu-id="19d9b-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="19d9b-136">IT staff</span><span class="sxs-lookup"><span data-stu-id="19d9b-136">IT staff</span></span>
    
  - <span data-ttu-id="19d9b-137">Personnel de recherche</span><span class="sxs-lookup"><span data-stu-id="19d9b-137">Research staff</span></span>
    
  - <span data-ttu-id="19d9b-138">Personnel normal</span><span class="sxs-lookup"><span data-stu-id="19d9b-138">Regular staff</span></span>
    
  - <span data-ttu-id="19d9b-139">Équipe marketing</span><span class="sxs-lookup"><span data-stu-id="19d9b-139">Marketing staff</span></span>
    
  - <span data-ttu-id="19d9b-140">Équipe de vente</span><span class="sxs-lookup"><span data-stu-id="19d9b-140">Sales staff</span></span>
    
7. <span data-ttu-id="19d9b-141">Conserver l’onglet portail Azure dans ouvert de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="19d9b-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="19d9b-142">Ensuite, configurez l’octroi de licence automatique afin que des licences soient automatiquement attribuées aux membres de vos groupes pour les abonnements Office 365 et EMS.</span><span class="sxs-lookup"><span data-stu-id="19d9b-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="19d9b-143">Dans le portail Azure, cliquez sur **Azure Active Directory > licences > tous les produits**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="19d9b-144">Dans la liste, sélectionnez la **mobilité d’entreprise + sécurité E5** et **Office 365 entreprise E5**et puis cliquez sur **attribuer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="19d9b-145">De la lame **attribuer la licence** , cliquez sur **utilisateurs et groupes**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="19d9b-146">Dans la liste des groupes, sélectionnez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="19d9b-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="19d9b-147">C-Suite</span><span class="sxs-lookup"><span data-stu-id="19d9b-147">C-Suite</span></span>
    
  - <span data-ttu-id="19d9b-148">IT staff</span><span class="sxs-lookup"><span data-stu-id="19d9b-148">IT staff</span></span>
    
  - <span data-ttu-id="19d9b-149">Personnel de recherche</span><span class="sxs-lookup"><span data-stu-id="19d9b-149">Research staff</span></span>
    
  - <span data-ttu-id="19d9b-150">Personnel normal</span><span class="sxs-lookup"><span data-stu-id="19d9b-150">Regular staff</span></span>
    
  - <span data-ttu-id="19d9b-151">Équipe marketing</span><span class="sxs-lookup"><span data-stu-id="19d9b-151">Marketing staff</span></span>
    
  - <span data-ttu-id="19d9b-152">Équipe de vente</span><span class="sxs-lookup"><span data-stu-id="19d9b-152">Sales staff</span></span>
    
5. <span data-ttu-id="19d9b-153">Cliquez sur **Sélectionner**, puis cliquez sur **attribuer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="19d9b-154">Fermez l’onglet du portail Azure dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="19d9b-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="19d9b-155">Ensuite, vous [connecter avec le module PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="19d9b-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="19d9b-156">Renseignez le nom de votre organisation, votre emplacement et un mot de passe commun et puis exécuter ces commandes à partir de l’invite de commande PowerShell ou l’environnement de Script intégré (ISE) pour créer des comptes d’utilisateurs et de les ajouter à leurs groupes :</span><span class="sxs-lookup"><span data-stu-id="19d9b-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
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
> <span data-ttu-id="19d9b-p103">L’utilisation d’un mot de passe commun permet d’automatiser et de faciliter la configuration d’un environnement de développement/test. Il n’est pas recommandé de l’utiliser dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="19d9b-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="19d9b-159">Utilisez ces étapes pour vérifier que la gestion des licences basée sur un groupe fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="19d9b-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="19d9b-160">À partir de l’onglet **Accueil de Microsoft Office** de votre navigateur, cliquez sur la mosaïque de **l’Admin** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="19d9b-161">À partir de l’onglet nouveau **Centre d’administration d’Office** de votre navigateur, cliquez sur **utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="19d9b-162">Dans la liste des utilisateurs, cliquez sur **PDG**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="19d9b-163">Dans le volet qui répertorie les propriétés du compte d’utilisateur **PDG** , vérifiez qu’il a été attribué les licences de **mobilité d’entreprise + sécurité E5** et **Office 365 entreprise E5** (dans les **licences de produit**).</span><span class="sxs-lookup"><span data-stu-id="19d9b-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="19d9b-164">Phase 3 : Créer des étiquettes d’Office 365</span><span class="sxs-lookup"><span data-stu-id="19d9b-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="19d9b-165">Dans cette phase, vous allez créer les étiquettes correspondant aux différents niveaux de sécurité pour les dossiers de documents du site d’équipe SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="19d9b-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="19d9b-p104">Si nécessaire, utilisez une instance privée de votre navigateur Internet et vous connecter au portail Office 365 avec le compte d’administrateur global de votre abonnement d’évaluation d’Office 365 E5. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="19d9b-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="19d9b-168">À partir de l’onglet **Accueil de Microsoft Office** , cliquez sur la mosaïque de **l’Admin** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="19d9b-169">Dans l’onglet nouveau **Centre d’administration d’Office** de votre navigateur, cliquez sur **Centre d’administration > sécurité &amp; la conformité**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="19d9b-170">À partir du nouveau **maison - sécurité &amp; la conformité** onglet de votre navigateur, cliquez sur **les Classifications > étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="19d9b-171">À partir de le **Accueil > étiquettes** volet, cliquez sur **créer une étiquette**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="19d9b-172">Dans le volet **nom de votre étiquette** , tapez **Public interne**et puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="19d9b-173">Dans le volet **paramètres d’étiquette** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="19d9b-174">Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer cette étiquette**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="19d9b-175">Répétez les étapes 5 à 8 pour les autres étiquettes suivantes :</span><span class="sxs-lookup"><span data-stu-id="19d9b-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="19d9b-176">Privé</span><span class="sxs-lookup"><span data-stu-id="19d9b-176">Private</span></span>
    
  - <span data-ttu-id="19d9b-177">Sensible</span><span class="sxs-lookup"><span data-stu-id="19d9b-177">Sensitive</span></span>
    
  - <span data-ttu-id="19d9b-178">Hautement confidentiel</span><span class="sxs-lookup"><span data-stu-id="19d9b-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="19d9b-179">À partir de le **Accueil > étiquettes** volet, cliquez sur **publier les étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="19d9b-180">Dans le volet **Choisir les étiquettes à publier** , cliquez sur **Choisir les étiquettes à publier**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="19d9b-181">Dans le volet **Choisir étiquettes** , cliquez sur **Ajouter** et sélectionner toutes les étiquettes de quatre.</span><span class="sxs-lookup"><span data-stu-id="19d9b-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="19d9b-182">Cliquez sur **terminé**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="19d9b-183">Dans le volet **Choisir les étiquettes à publier** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="19d9b-184">Dans le volet **Choisir des emplacements** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="19d9b-185">Dans le volet **nom de votre stratégie** , tapez **exemple d’entreprise** dans la zone **nom**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="19d9b-186">Dans le volet de **passer en revue vos paramètres** , cliquez sur **publier les étiquettes**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="19d9b-187">Phase 4 : Créez vos sites d’équipe SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="19d9b-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="19d9b-188">Dans cette phase, vous créez et configurez les quatre types de sites d’équipe SharePoint Online pour votre exemple d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="19d9b-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="19d9b-189">Site d’équipe à l’échelle de l’organisation</span><span class="sxs-lookup"><span data-stu-id="19d9b-189">Organization wide team site</span></span>

<span data-ttu-id="19d9b-190">Pour créer un site d’équipe SharePoint Online public de référence, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="19d9b-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="19d9b-p105">Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 à l’aide de votre compte d’administrateur global. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="19d9b-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="19d9b-193">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="19d9b-194">Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="19d9b-195">Dans la page **créer un site** , cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="19d9b-196">Dans la zone **nom du Site**, tapez **l’échelle de l’organisation**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="19d9b-197">Dans **description de site d’équipe**, tapez le **site SharePoint pour toute l’organisation**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="19d9b-198">Dans les **paramètres de confidentialité**, sélectionnez **Public - tout le monde dans l’organisation peut accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="19d9b-199">Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="19d9b-200">Ensuite, configurez le dossier documents du site d’équipe grande organisation pour l’étiquette publics internes.</span><span class="sxs-lookup"><span data-stu-id="19d9b-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="19d9b-201">Dans l’onglet de **L’échelle de l’entreprise - accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="19d9b-202">Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="19d9b-203">Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="19d9b-204">Dans les **Paramètres à appliquer une étiquette**, sélectionnez **Public interne**et puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="19d9b-205">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="19d9b-205">Here is your resulting configuration.</span></span>
  
![Protection de base pour le site d’équipe SharePoint Online consultable par les membres de l’organisation.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="19d9b-207">Site d’équipe 1 du projet</span><span class="sxs-lookup"><span data-stu-id="19d9b-207">Project 1 team site</span></span>

<span data-ttu-id="19d9b-208">Pour créer un site d’équipe SharePoint Online privé de référence pour un projet au sein de l’organisation, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="19d9b-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="19d9b-p106">Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 à l’aide de votre compte d’administrateur global. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="19d9b-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="19d9b-211">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="19d9b-212">Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="19d9b-213">Dans la page **créer un site** , cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="19d9b-214">Dans la zone **nom du Site**, tapez **1 du projet**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="19d9b-215">Dans la **description de site d’équipe,** tapez le **site SharePoint pour le projet 1**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="19d9b-216">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="19d9b-217">Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="19d9b-218">Ensuite, configurez le dossier de documents du site d’équipe Projet 1 pour l’étiquette Privé.</span><span class="sxs-lookup"><span data-stu-id="19d9b-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="19d9b-219">Dans l’onglet **projet 1-accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="19d9b-220">Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="19d9b-221">Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="19d9b-222">Dans **Les paramètres à appliquer une étiquette**, sélectionnez **privé**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="19d9b-223">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="19d9b-223">Here is your resulting configuration.</span></span>
  
![Protection de base pour le site d’équipe SharePoint Online privé concernant Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="19d9b-225">Site d’équipe des campagnes marketing</span><span class="sxs-lookup"><span data-stu-id="19d9b-225">Marketing campaigns team site</span></span>

<span data-ttu-id="19d9b-226">Pour créer un site d’équipe SharePoint Online isolé pour les données sensibles des ressources de campagne marketing, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="19d9b-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="19d9b-p107">À l’aide d’un navigateur sur votre ordinateur local, connectez-vous au portail Office 365 à l’aide de votre compte d’administrateur global. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="19d9b-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="19d9b-229">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="19d9b-230">Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="19d9b-231">Dans la page **créer un site** , cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="19d9b-232">Dans la zone **nom du site d’équipe**, tapez **les campagnes Marketing**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="19d9b-233">Dans la **description de site d’équipe**, tapez le **site SharePoint pour les ressources de campagne marketing (la casse)**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="19d9b-234">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="19d9b-235">Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="19d9b-236">Dans l’onglet **campagnes de Marketing** de nouveau dans votre navigateur, dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="19d9b-237">Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="19d9b-238">Dans l’onglet **autorisations** de nouveau dans votre navigateur, cliquez sur **Paramètres de demande d’accès**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="19d9b-239">Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez les cases à cocher **Autoriser les membres à partager le site et les fichiers et dossiers individuels** et **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** , tapez **ITAdmin1 @**\<votre nom de l’organisation >**. onmicrosoft.com** dans la zone **Envoyer toutes les demandes d’accès**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="19d9b-240">Dans la liste, cliquez sur **campagnes de Marketing les membres** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="19d9b-241">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="19d9b-242">Dans la boîte de dialogue de **partage** , tapez **équipe Marketing**, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="19d9b-243">Répétez les étapes 14 et 15 pour le compte d’utilisateur **Researcher1** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="19d9b-244">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="19d9b-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="19d9b-245">Dans la liste, cliquez sur **campagnes de Marketing propriétaires** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="19d9b-246">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="19d9b-247">Dans la boîte de dialogue de **partage** , tapez le **personnel informatique**, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="19d9b-248">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="19d9b-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="19d9b-249">Fermer l’onglet **personnes et groupes** dans votre navigateur et cliquez sur l’onglet **accueil-campagnes de Marketing** dans votre navigateur, puis fermez le volet **autorisations de Site** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="19d9b-250">Voici les résultats de la configuration des autorisations :</span><span class="sxs-lookup"><span data-stu-id="19d9b-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="19d9b-251">Le groupe SharePoint des **Membres de campagnes Marketing** contient uniquement le groupe de **campagnes de Marketing** (qui contient le compte d’utilisateur administrateur global), le groupe de **l’équipe Marketing** (qui contient l’utilisateur Marketing1 et Marketing2 comptes) et le compte d’utilisateur **Researcher1** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="19d9b-252">Le groupe de **Propriétaires de campagnes de Marketing** SharePoint contient uniquement le groupe de **service informatique** (qui contienne uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="19d9b-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="19d9b-253">Le groupe de **Campagnes de Marketing - les visiteurs** SharePoint ne contient aucun groupe ou compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="19d9b-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="19d9b-254">Les membres ne peuvent pas modifier les autorisations au niveau du site (cela n’est possible par les membres du groupe **Propriétaires de campagnes de Marketing** ).</span><span class="sxs-lookup"><span data-stu-id="19d9b-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="19d9b-255">Les autres comptes d’utilisateurs ne peuvent pas accéder au site ni à ses ressources, mais peuvent demander d’avoir accès au site. Un courrier électronique sera envoyé à la boîte aux lettres du compte d’utilisateur ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="19d9b-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="19d9b-256">Ensuite, configurez le dossier de documents du site d’équipe Campagnes marketing pour l’étiquette Sensible.</span><span class="sxs-lookup"><span data-stu-id="19d9b-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="19d9b-257">Dans l’onglet **accueil-campagnes de commercialisation** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="19d9b-258">Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="19d9b-259">Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="19d9b-260">Dans **Les paramètres à appliquer une étiquette**, sélectionnez **sensibles**, puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="19d9b-261">Ensuite, configurez une stratégie de prévention des pertes de données qui avertit les utilisateurs lorsqu’ils partagent un document sur un site d’équipe SharePoint Online avec l’étiquette Sensible, dont notamment le site Campagnes marketing, à l’extérieur de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="19d9b-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="19d9b-262">À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; la conformité** en mosaïque.</span><span class="sxs-lookup"><span data-stu-id="19d9b-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="19d9b-263">Sur la nouvelle **sécurité &amp; la conformité** dans votre navigateur, cliquez sur **prévention des fuites de données > stratégie de**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="19d9b-264">Dans le volet de la **prévention des fuites de données** , cliquez sur **+ créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="19d9b-265">Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisée**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="19d9b-266">Dans le volet **nom de votre stratégie** , tapez des **sites d’équipe SharePoint Online étiquette sensibles** dans la zone **nom**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="19d9b-267">Dans le volet **Choisir des emplacements** , cliquez sur **me laisser choisir des emplacements spécifiques**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="19d9b-268">Dans la liste des emplacements, désactivez les emplacements **des comptes de OneDrive** et de la **messagerie Exchange** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="19d9b-269">Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="19d9b-270">Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="19d9b-271">Dans le volet **d’étiquettes** , cliquez sur **+ Ajouter**, sélectionnez l’étiquette **sensibles** , cliquez sur **Ajouter**, puis cliquez sur **terminé**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="19d9b-272">Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="19d9b-273">Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="19d9b-274">Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="19d9b-275">Dans le volet de **conseils de stratégie de personnaliser et de notifications par courrier électronique** , cliquez sur **Personnaliser le texte d’info-bulle de stratégie**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="19d9b-276">Dans la zone de texte, tapez ou collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="19d9b-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="19d9b-p108">Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.</span><span class="sxs-lookup"><span data-stu-id="19d9b-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="19d9b-280">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="19d9b-281">Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, désactivez la case à cocher **bloquer le partage, des personnes et de restreindre l’accès au contenu partagé** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="19d9b-282">Dans le **vous souhaitez activer les opérations de test ou de stratégie en premier ?** volet, cliquez sur **Oui, activer tout de suite**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="19d9b-283">Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="19d9b-284">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="19d9b-284">Here is your resulting configuration.</span></span>
  
![Protection des données sensibles pour les sites d’équipe SharePoint Online isolés des campagnes marketing.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="19d9b-286">Site d’équipe de stratégie d’entreprise</span><span class="sxs-lookup"><span data-stu-id="19d9b-286">Company strategy team site</span></span>

<span data-ttu-id="19d9b-287">Pour créer un site d’équipe SharePoint Online isolé au niveau hautement confidentiel pour les ressources stratégiques de l’entreprise des cadres dirigeants de l’organisation, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="19d9b-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="19d9b-p109">Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 à l’aide de votre compte d’administrateur global. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="19d9b-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="19d9b-290">Dans la liste des mosaïques, cliquez sur **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="19d9b-291">Dans l’onglet nouveau **SharePoint** dans votre navigateur, cliquez sur **+ créer le site**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="19d9b-292">Dans la page **créer un site** , cliquez sur **site d’équipe**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="19d9b-293">Dans la zone **nom du site d’équipe**, tapez **stratégie de la société**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="19d9b-294">Dans la **description de site d’équipe**, tapez le **site SharePoint pour la stratégie d’entreprise (hautement confidentielle)**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="19d9b-295">Dans **les paramètres de confidentialité**, sélectionnez **privé - uniquement les membres peuvent accéder à ce site**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="19d9b-296">Sur le **qui voulez-vous ajouter ?** volet, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="19d9b-297">Dans l’onglet **stratégie de la société** de nouveau dans votre navigateur, dans la barre d’outils, cliquez sur l’icône de paramètres, puis cliquez sur **autorisations du Site**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="19d9b-298">Dans le volet **autorisations de Site** , cliquez sur **autorisations avancées**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="19d9b-299">Dans l’onglet **autorisations** de nouveau dans votre navigateur, cliquez sur **Paramètres de demande d’accès**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="19d9b-300">Dans la boîte de dialogue **Paramètres de demande d’accès** , désactivez **Autoriser les membres à inviter d’autres personnes au groupe de membres du site** et **permettre aux membres de partager le site et les fichiers et dossiers individuels** (de sorte que toutes les trois cases à cocher sont désactivées), puis cliquez sur ** OK**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="19d9b-301">Dans la liste, cliquez sur **stratégie membres de la société** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="19d9b-302">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="19d9b-303">Dans la boîte de dialogue de **partage** , tapez **C-Suite**, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="19d9b-304">Dans la liste, cliquez sur **stratégie d’entreprise propriétaires** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="19d9b-305">Dans la page **personnes et groupes** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="19d9b-306">Dans la boîte de dialogue de **partage** , tapez le **personnel informatique**, sélectionnez-le, puis cliquez sur **partage**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="19d9b-307">Cliquez sur le bouton de retour de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="19d9b-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="19d9b-308">Fermer l’onglet **personnes et groupes** dans votre navigateur et cliquez sur l’onglet de **Stratégie d’entreprise - accueil** dans votre navigateur, puis fermez le volet **autorisations de Site** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="19d9b-309">Voici les résultats de la configuration des autorisations :</span><span class="sxs-lookup"><span data-stu-id="19d9b-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="19d9b-310">Le groupe SharePoint **Membres de stratégie d’entreprise** contient uniquement le groupe **C-Suite** (qui contienne uniquement les comptes d’utilisateurs PDG, directeur financier et directeur de l’information) et le groupe de la **stratégie de la société** (qui contient uniquement le compte d’utilisateur administrateur global).</span><span class="sxs-lookup"><span data-stu-id="19d9b-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="19d9b-311">Le groupe SharePoint **Propriétaires de stratégie de société** contient uniquement le groupe de **service informatique** (qui contienne uniquement les comptes d’utilisateurs ITAdmin1 et ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="19d9b-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="19d9b-312">Le groupe SharePoint **Visiteurs-stratégie de société** ne contient aucun groupe ou compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="19d9b-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="19d9b-313">Les membres ne peuvent pas modifier les autorisations au niveau du site (cela n’est possible par les membres du groupe **Propriétaires de stratégie de société** ).</span><span class="sxs-lookup"><span data-stu-id="19d9b-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="19d9b-p110">Autres comptes d’utilisateur ne peut pas accéder au site ou ses ressources ou demander l’accès au site. Des autorisations supplémentaires sur le site doivent être effectuées par l’administrateur global ou par un membre du groupe **Stratégie-propriétaires de sociétés** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="19d9b-316">Ensuite, configurez le dossier de documents du site d’équipe Stratégie d’entreprise pour l’étiquette Hautement confidentiel.</span><span class="sxs-lookup"><span data-stu-id="19d9b-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="19d9b-317">Dans l’onglet **Stratégie d’entreprise - accueil** de votre navigateur, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="19d9b-318">Cliquez sur l’icône de paramètres, puis cliquez sur **paramètres de la bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="19d9b-319">Sous **autorisations et gestion**, cliquez sur **étiquette d’appliquer aux éléments de cette bibliothèque**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="19d9b-320">Dans les **Paramètres à appliquer une étiquette**, sélectionnez **Hautement confidentielles**et puis cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="19d9b-321">Configurez ensuite une stratégie DLP qui empêche les utilisateurs lorsqu’ils partagent un document sur un site d’équipe SharePoint Online avec l’étiquette hautement confidentielles, ce qui inclut le site de stratégie d’entreprise, à l’extérieur de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="19d9b-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="19d9b-p111">Si nécessaire, utilisez un navigateur sur votre ordinateur local et vous connecter au portail Office 365 avec un compte qui possède le rôle d’administrateur de sécurité ou l’administrateur de la société. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="19d9b-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="19d9b-324">À partir de l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur le **sécurité &amp; la conformité** en mosaïque.</span><span class="sxs-lookup"><span data-stu-id="19d9b-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="19d9b-325">Sur la nouvelle **sécurité &amp; la conformité** dans votre navigateur, cliquez sur **prévention des fuites de données > stratégie de**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="19d9b-326">Dans le volet de la **prévention des fuites de données** , cliquez sur **+ créer une stratégie**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="19d9b-327">Dans la **Démarrer avec un modèle ou créer une stratégie personnalisée** volet, cliquez sur **personnalisée**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="19d9b-328">Dans le volet **nom de votre stratégie** , tapez **hautement confidentielles sites d’équipe SharePoint Online étiquette** dans la zone **nom**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="19d9b-329">Dans le volet **Choisir des emplacements** , cliquez sur **me laisser choisir des emplacements spécifiques**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="19d9b-330">Dans la liste des emplacements, désactivez les emplacements **des comptes de OneDrive** et de la **messagerie Exchange** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="19d9b-331">Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="19d9b-332">Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Ajouter** dans la zone de liste déroulante, puis cliquez sur **étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="19d9b-333">Dans le volet **d’étiquettes** , cliquez sur **+ Ajouter**, sélectionnez l’étiquette **Hautement confidentielles** , cliquez sur **Ajouter**, puis cliquez sur **terminé**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="19d9b-334">Dans le volet **Choisir les types de contenu à protéger** , cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="19d9b-335">Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="19d9b-336">Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, cliquez sur **Personnaliser l’info-bulle et la messagerie électronique**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="19d9b-337">Dans le volet de **conseils de stratégie de personnaliser et de notifications par courrier électronique** , cliquez sur **Personnaliser le texte d’info-bulle de stratégie**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="19d9b-338">Dans la zone de texte, tapez ou collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="19d9b-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="19d9b-p112">Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.</span><span class="sxs-lookup"><span data-stu-id="19d9b-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="19d9b-342">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="19d9b-343">Dans la **ce que vous voulez faire si nous détectons des informations sensibles ?** volet, sélectionnez **Exiger une justification à remplacer**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="19d9b-344">Dans le **vous souhaitez activer les opérations de test ou de stratégie en premier ?** volet, cliquez sur **Oui, activer tout de suite**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="19d9b-345">Dans le volet de **passer en revue vos paramètres** , cliquez sur **créer**, puis cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="19d9b-346">Ensuite, suivez les instructions de [RMS d’Azure activer avec le centre d’administration Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="19d9b-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="19d9b-347">Ensuite, configurez la Protection des informations Azure avec une nouvelle stratégie étendue et une étiquette secondaire pour la protection et d’autorisations avec les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="19d9b-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="19d9b-p113">Connectez-vous au portail Office 365 avec un compte disposant du rôle Administrateur de sécurité ou Administrateur d’entreprise. Pour obtenir de l’aide, consultez la rubrique [Se connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="19d9b-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="19d9b-350">Dans un onglet séparé de votre navigateur, accédez au portail Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="19d9b-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="19d9b-351">Si vous configurez Azure Information Protection pour la première fois, consultez ces [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="19d9b-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="19d9b-352">Dans le volet Liste, cliquez sur **Plus de services**, saisissez **Informations**, puis cliquez sur **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="19d9b-353">Sur le panneau **Azure Information Protection**, cliquez sur **Stratégies étendues > + Ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="19d9b-354">Dans **nom de la stratégie** et l' **étiquette pour les documents dans le site d’équipe stratégie société** dans la zone **Description**, tapez **CompanyStrategy** .</span><span class="sxs-lookup"><span data-stu-id="19d9b-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="19d9b-355">Cliquez sur **Sélectionner les utilisateurs ou les groupes d’obtiennent cette stratégie > groupes d’utilisateurs**, puis sélectionnez la **Suite de la C**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="19d9b-356">Cliquez sur **Sélectionner > OK**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="19d9b-357">Pour l’étiquette **Hautement confidentiel**, cliquez sur les points de suspension (...), puis sur **Ajouter une sous-étiquette**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="19d9b-358">Entrez le nom de la sous-étiquette dans **Nom** et sa description dans **Description**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="19d9b-359">Cliquez sur **Protéger** dans **Définir les autorisations pour les documents et les e-mails contenant cette étiquette**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="19d9b-360">Dans la section **Protection**, cliquez sur **Azure (clé cloud)**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="19d9b-361">Dans le panneau **Protection**, cliquez sur **+ Ajouter des autorisations** sous **Paramètres de protection**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="19d9b-362">Dans le panneau **Ajouter des autorisations**, sous **Spécifier les utilisateurs et les groupes**, cliquez sur **+ Parcourir le répertoire**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="19d9b-363">Dans le volet **DAS utilisateurs et des groupes** , sélectionnez **C-Suite**, puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="19d9b-364">Sous **Choisir des autorisations à partir de valeurs prédéfinies**, désactivez les cases à cocher **Imprimer **, **Copier et extraire le contenu** et **Transférer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="19d9b-365">Cliquez deux fois sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="19d9b-366">Dans le panneau **Sous-étiquette**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="19d9b-367">Fermez le panneau de la nouvelle stratégie étendue.</span><span class="sxs-lookup"><span data-stu-id="19d9b-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="19d9b-368">Sur la lame de **protection des informations de Azure - stratégies étendues** , cliquez sur **Publier**, puis cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="19d9b-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="19d9b-369">Pour protéger un document avec la Protection des informations Azure et cette nouvelle étiquette, vous devez [installer le client de Protection d’informations Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) sur un ordinateur de test, installez Office à partir du portail Office 365 et puis vous connecter à partir de Microsoft Word avec un compte dans le ** C-Suite** groupe de votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="19d9b-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="19d9b-370">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="19d9b-370">Here is your resulting configuration.</span></span>
  
![Protection avec un niveau de confidentialité élevé pour le site d’équipe SharePoint Online isolé de la stratégie d’entreprise.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="19d9b-372">Vous êtes maintenant prêt à créer des documents dans ces quatre sites et tester l’accès pour les différents comptes d’utilisateur dans votre abonnement d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="19d9b-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="19d9b-373">Voici la configuration globale pour tous les sites d’équipe SharePoint Online quatre.</span><span class="sxs-lookup"><span data-stu-id="19d9b-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![Les quatre sites d’équipe dans l’environnement de développement/test SharePoint Online sécurisé.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="19d9b-375">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="19d9b-375">Next step</span></span>

<span data-ttu-id="19d9b-376">Lorsque vous êtes prêt pour le déploiement de production des sites SharePoint en ligne sécurisés, voir les [fichiers et les sites SharePoint sécurisé en ligne](secure-sharepoint-online-sites-and-files.md) pour obtenir des informations détaillées et des liens vers des articles de déploiement étape par étape.</span><span class="sxs-lookup"><span data-stu-id="19d9b-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="19d9b-377">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19d9b-377">See Also</span></span>

[<span data-ttu-id="19d9b-378">Sécuriser les fichiers et sites SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="19d9b-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="19d9b-379">Solutions de sécurité</span><span class="sxs-lookup"><span data-stu-id="19d9b-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="19d9b-380">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="19d9b-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="19d9b-381">Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles</span><span class="sxs-lookup"><span data-stu-id="19d9b-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




