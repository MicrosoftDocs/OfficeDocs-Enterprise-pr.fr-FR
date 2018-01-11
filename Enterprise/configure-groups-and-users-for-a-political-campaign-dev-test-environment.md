---
title: "Configuration de groupes et d’utilisateurs pour un environnement de développement/test pour une campagne politique"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Résumé : Créer Office 365 et de mobilité d’entreprise + d’abonnements d’essai de sécurité (EMS) avec les utilisateurs et les groupes pour un environnement de développement/test de campagne politique."
ms.openlocfilehash: e876c8770651c3f23c06c9c499bdaabca52da353
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="9cbfe-103">Configuration de groupes et d’utilisateurs pour un environnement de développement/test pour une campagne politique</span><span class="sxs-lookup"><span data-stu-id="9cbfe-103">Configure groups and users for a political campaign dev/test environment</span></span>

 <span data-ttu-id="9cbfe-104">**Résumé :** Créer Office 365 et de mobilité d’entreprise + d’abonnements d’essai de sécurité (EMS) avec les utilisateurs et les groupes pour un environnement de développement/test de campagne politique.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-104">**Summary:** Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>
  
<span data-ttu-id="9cbfe-105">Suivez les instructions de cet article pour créer un environnement de développement/test qui inclut les comptes d’utilisateur simplifiée et des groupes pour la solution de [Conseils de sécurité de Microsoft pour les campagnes politiques, les organismes sans but lucratif et les autres organisations Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) .</span><span class="sxs-lookup"><span data-stu-id="9cbfe-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="9cbfe-106">Phase 1 : Création d’un environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="9cbfe-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="9cbfe-107">Dans cette phase, vous procurer des abonnements d’essai pour Office 365 E5 et mobilité d’entreprise + E5 de sécurité (EMS) pour une entreprise fictive représentant une campagne politique.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-107">In this phase, you obtain trial subscriptions for Office 365 E5 and Enterprise Mobility + Security (EMS) E5 for a fictional organization that represents a political campaign.</span></span>
  
<span data-ttu-id="9cbfe-108">Tout d’abord, suivez les instructions de la **Phase 2** de l' [environnement de développement/test d’Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="9cbfe-108">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="9cbfe-109">Ensuite, inscrivez-vous à l’abonnement d’évaluation EMS E5 et l’ajouter à la même organisation que votre abonnement d’évaluation d’Office 365.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-109">Next, sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="9cbfe-p101">Si nécessaire, connectez-vous au portail Office 365 avec les informations d’identification du compte d’administrateur global de votre abonnement d’évaluation. Pour de l’aide, consultez la rubrique [pour vous connecter à Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="9cbfe-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="9cbfe-112">Cliquez sur la mosaïque de **l’Admin** .</span><span class="sxs-lookup"><span data-stu-id="9cbfe-112">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="9cbfe-113">Dans l’onglet **Centre d’administration d’Office** dans votre navigateur, dans la navigation de gauche, cliquez sur **de facturation > acheter les services**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-113">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="9cbfe-p102">Dans la page **services d’achat** , trouver la **mobilité d’entreprise + E5 de la sécurité** . Placez le pointeur de la souris sur elle et cliquez sur **Démarrer la version d’évaluation gratuite**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="9cbfe-116">Dans la page **Confirmer votre commande** , cliquez sur **Essayer maintenant**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-116">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="9cbfe-117">Dans la page **reçu de commande** , cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-117">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="9cbfe-118">Ensuite, activez la licence EMS E5 pour votre compte d’administrateur global.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-118">Next, enable the EMS E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="9cbfe-119">Dans l’onglet **Centre d’administration d’Office 365** dans votre navigateur, dans la navigation de gauche, cliquez sur **les utilisateurs > utilisateurs actifs**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-119">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="9cbfe-120">Cliquez sur votre compte d’administrateur global, puis cliquez sur **Modifier** pour les **licences de produit**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-120">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="9cbfe-121">Dans le volet des **licences** , activer la licence du produit de **mobilité d’entreprise + sécurité E5** **on**et cliquez sur **Enregistrer,** puis cliquez deux fois sur **Fermer** .</span><span class="sxs-lookup"><span data-stu-id="9cbfe-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="9cbfe-122">Phase 2 : Création et configuration de vos groupes Azure Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="9cbfe-122">Phase 2: Create and configure your Azure Active Directory (AD) groups</span></span>

<span data-ttu-id="9cbfe-123">Dans cette phase, vous créez et configurez des groupes Azure AD pour votre campagne.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-123">In this phase, you create and configure the Azure AD groups for your campaign.</span></span>
  
<span data-ttu-id="9cbfe-124">Tout d’abord, créez un ensemble de groupes pour une campagne politique typique avec le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-124">First, create a set of groups for a typical political campaign with the Azure portal.</span></span>
  
1. <span data-ttu-id="9cbfe-125">Sous un onglet distinct dans votre navigateur, accédez au portail Azure à [https://portal.azure.com](https://portal.azure.com). Si nécessaire, connectez-vous en utilisant les informations d’identification du compte d’administrateur global pour votre abonnement d’évaluation d’Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-125">On a separate tab in your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="9cbfe-126">Dans le portail Azure, cliquez sur **Azure Active Directory > utilisateurs et groupes > tous les groupes de**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-126">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="9cbfe-127">Effectuez les étapes suivantes pour chaque nom de groupe dans cette liste :</span><span class="sxs-lookup"><span data-stu-id="9cbfe-127">Do the following steps for each group name in this list:</span></span>
    
  - <span data-ttu-id="9cbfe-128">Senior and strategic staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-128">Senior and strategic staff</span></span>
    
  - <span data-ttu-id="9cbfe-129">IT staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-129">IT staff</span></span>
    
  - <span data-ttu-id="9cbfe-130">Analytics staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-130">Analytics staff</span></span>
    
  - <span data-ttu-id="9cbfe-131">Regular core staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-131">Regular core staff</span></span>
    
  - <span data-ttu-id="9cbfe-132">Operations staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-132">Operations staff</span></span>
    
  - <span data-ttu-id="9cbfe-133">Field staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-133">Field staff</span></span>
    
1. <span data-ttu-id="9cbfe-134">Sur la lame de **tous les groupes** , cliquez sur **+ le nouveau groupe**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-134">On the **All groups** blade, click **+ New group**.</span></span>
    
2. <span data-ttu-id="9cbfe-135">Dans la zone **nom**, tapez le nom du groupe dans la liste.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-135">Type the group name from the list in **Name**.</span></span>
    
3. <span data-ttu-id="9cbfe-136">Sélectionnez **dynamique utilisateur** **d’appartenance**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-136">Select **Dynamic user** in **Membership**.</span></span>
    
4. <span data-ttu-id="9cbfe-137">Cliquez sur **Oui** pour **activer Office fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-137">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="9cbfe-138">Cliquez sur **Ajouter des requêtes dynamiques**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-138">Click **Add dynamic query**.</span></span>
    
6. <span data-ttu-id="9cbfe-139">Dans **Ajouter des utilisateurs où**, sélectionnez le **département**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-139">In **Add users where**, select **department**.</span></span>
    
7. <span data-ttu-id="9cbfe-140">Dans le champ suivant, sélectionnez **est égal à**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-140">In the next field, select **Equals**.</span></span>
    
8. <span data-ttu-id="9cbfe-141">Dans le champ suivant, tapez le nom du groupe dans la liste.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-141">In the next field, type the group name from the list.</span></span>
    
9. <span data-ttu-id="9cbfe-142">Cliquez sur **Ajouter la requête**, puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-142">Click **Add query**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="9cbfe-143">Cliquez sur **utilisateurs et groupes : tous les groupes**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-143">Click **Users and groups - All groups**.</span></span>
    
<span data-ttu-id="9cbfe-144">Ensuite, vous configurez les groupes pour que les membres reçoivent automatiquement des licences Office 365 E5 et EMS E5.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-144">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>
  
1. <span data-ttu-id="9cbfe-145">Dans le portail Azure, cliquez sur **Azure Active Directory > licences > tous les produits**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-145">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="9cbfe-146">Dans la liste, sélectionnez la **mobilité d’entreprise + sécurité E5** et **Office 365 entreprise E5**, puis cliquez sur **+ affecter**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-146">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **+ Assign**.</span></span>
    
3. <span data-ttu-id="9cbfe-147">De la lame **attribuer la licence** , cliquez sur **utilisateurs et groupes**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-147">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="9cbfe-148">Dans la liste des groupes, sélectionnez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9cbfe-148">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="9cbfe-149">Analytics staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-149">Analytics staff</span></span>
    
  - <span data-ttu-id="9cbfe-150">Field staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-150">Field staff</span></span>
    
  - <span data-ttu-id="9cbfe-151">IT staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-151">IT staff</span></span>
    
  - <span data-ttu-id="9cbfe-152">Operations staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-152">Operations staff</span></span>
    
  - <span data-ttu-id="9cbfe-153">Regular core staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-153">Regular core staff</span></span>
    
  - <span data-ttu-id="9cbfe-154">Senior and strategic staff</span><span class="sxs-lookup"><span data-stu-id="9cbfe-154">Senior and strategic staff</span></span>
    
5. <span data-ttu-id="9cbfe-155">Cliquez sur **Sélectionner**, puis cliquez sur **attribuer**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-155">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="9cbfe-156">Fermez l’onglet du portail Azure dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-156">Close the Azure portal tab in your browser.</span></span>
    
## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="9cbfe-157">Phase 3 : Ajout de comptes d’utilisateurs</span><span class="sxs-lookup"><span data-stu-id="9cbfe-157">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="9cbfe-158">Dans cette phase, vous ajoutez les comptes d’utilisateurs de l’exemple pour votre campagne politique.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-158">In this phase, you add the example user accounts for your political campaign.</span></span>
  
<span data-ttu-id="9cbfe-159">Tout d’abord, vous [connecter avec le module PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="9cbfe-159">First, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="9cbfe-160">Ensuite, renseignez le nom de votre organisation, votre emplacement et un mot de passe commun, puis exécutez les commandes suivantes à partir de l’invite de commandes PowerShell ou de l’environnement de script intégré (ISE) :</span><span class="sxs-lookup"><span data-stu-id="9cbfe-160">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> <span data-ttu-id="9cbfe-p103">L’utilisation d’un mot de passe commun ici est pour l’automatisation et la facilité de configuration d’un environnement de développement/test. Ce n’est pas recommandé pour les abonnements de la production. Que vous vous connectez avec chacun de ces nouveaux comptes d’utilisateurs, vous devrez modifier le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span> 
  
<span data-ttu-id="9cbfe-164">Utilisez ces étapes pour vérifier que l’appartenance au groupe dynamique et l’octroi de licence selon le groupe fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-164">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>
  
1. <span data-ttu-id="9cbfe-165">À partir de l’onglet **Accueil de Microsoft Office** de votre navigateur, cliquez sur la mosaïque de **l’Admin** .</span><span class="sxs-lookup"><span data-stu-id="9cbfe-165">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="9cbfe-166">À partir de l’onglet nouveau **Centre d’administration d’Office** de votre navigateur, cliquez sur **utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-166">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="9cbfe-167">Dans la liste des utilisateurs, cliquez sur **candidat**.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-167">In the list of users, click **Candidate**.</span></span>
    
4. <span data-ttu-id="9cbfe-168">Dans le volet qui répertorie les propriétés du compte d’utilisateur **candidats** , vérifiez que :</span><span class="sxs-lookup"><span data-stu-id="9cbfe-168">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>
    
  - <span data-ttu-id="9cbfe-169">Il est membre du groupe **Senior et personnel stratégique** (dans les **appartenances aux groupes**).</span><span class="sxs-lookup"><span data-stu-id="9cbfe-169">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>
    
  - <span data-ttu-id="9cbfe-170">Il a été affecté aux **mobilité d’entreprise + sécurité E5** et **Office 365 entreprise E5** licences ( **licences**).</span><span class="sxs-lookup"><span data-stu-id="9cbfe-170">It has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
5. <span data-ttu-id="9cbfe-171">Fermez le volet de compte d’utilisateur **candidat** .</span><span class="sxs-lookup"><span data-stu-id="9cbfe-171">Close the **Candidate** user account pane.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="9cbfe-172">Enregistrez les valeurs, vous en aurez besoin plus tard.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-172">Record values for future reference</span></span>

<span data-ttu-id="9cbfe-173">Enregistrez ces valeurs pour travailler avec les abonnements aux versions d’évaluation d’Office 365 et d’EMS pour cet environnement de développement/test :</span><span class="sxs-lookup"><span data-stu-id="9cbfe-173">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>
  
- <span data-ttu-id="9cbfe-174">Nom de l’organisation bénéficiant de l’abonnement à la version d’évaluation : _______________________________________________ </span><span class="sxs-lookup"><span data-stu-id="9cbfe-174">Your trial subscription organization name: _______________________________________________</span></span> 
    
    <span data-ttu-id="9cbfe-175">Par exemple, pour le nom de domaine pour l’abonnement à la version d’évaluation de contoso.onmicrosoft.com, le nom de l’organisation est « contoso ».</span><span class="sxs-lookup"><span data-stu-id="9cbfe-175">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>
    
- <span data-ttu-id="9cbfe-176">Le nom d’administrateur global de Office 365 : ___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="9cbfe-176">The Office 365 global administrator name: ____________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="9cbfe-177">Enregistrer le mot de passe pour ce compte et le mot de passe initial commun pour les autres comptes d’utilisateur dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-177">Record the password for this account and the common initial password for the other user accounts in a secure location.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="9cbfe-178">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="9cbfe-178">Next step</span></span>

<span data-ttu-id="9cbfe-179">Générer les quatre types différents de sites d’équipe SharePoint Online dans cet environnement de développement/test avec les [sites d’équipe de créer dans un environnement de développement/test de campagne politique](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="9cbfe-179">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9cbfe-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9cbfe-180">See Also</span></span>

[<span data-ttu-id="9cbfe-181">Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles</span><span class="sxs-lookup"><span data-stu-id="9cbfe-181">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="9cbfe-182">Créer des sites d’équipe dans un environnement de développement/test de campagne politique</span><span class="sxs-lookup"><span data-stu-id="9cbfe-182">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="9cbfe-183">Guides de laboratoire de test d’adoption cloud</span><span class="sxs-lookup"><span data-stu-id="9cbfe-183">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="9cbfe-184">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="9cbfe-184">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




