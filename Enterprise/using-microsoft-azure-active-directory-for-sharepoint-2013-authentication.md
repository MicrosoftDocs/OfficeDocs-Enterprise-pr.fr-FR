---
title: "Utilisation de Microsoft Azure Active Directory pour l’authentification SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: "Résumé : Apprenez à utiliser le Service de contrôle d'accès pour authentifier les utilisateurs de SharePoint Server 2013 avec Azure Active Directory."
ms.openlocfilehash: c4c8c4a2c35018b9e4eef2ce32502c4ba67585ca
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="using-microsoft-azure-active-directory-for-sharepoint-2013-authentication"></a><span data-ttu-id="c0ddb-103">Utilisation de Microsoft Azure Active Directory pour l’authentification SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c0ddb-103">Using Microsoft Azure Active Directory for SharePoint 2013 authentication</span></span>

 <span data-ttu-id="c0ddb-104">**Résumé :** Apprenez à utiliser le Service de contrôle d'accès pour authentifier les utilisateurs de SharePoint Server 2013 avec Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-104">**Summary:** Learn how to use the Azure Access Control Service to authenticate your SharePoint Server 2013 users with Azure Active Directory.</span></span>
  
<span data-ttu-id="c0ddb-p101">Il peut s'avérer plus facile de gérer vos utilisateurs en les authentifiant avec des fournisseurs d'identité différents. Si vous y pensez, il peut être pratique d'utiliser un fournisseur d'identité de confiance tandis qu'une autre personne s'occupe de la gestion. Par exemple, vous pouvez disposer d'un type d'authentification pour les utilisateurs qui accèdent à SharePoint Server 2013 dans le cloud et d'un autre pour les utilisateurs SharePoint 2013 dans votre environnement local. Le Service de contrôle d'accès Azure rend ces choix possibles.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p101">It can be easier to manage your users by authenticating them with different identity providers. Consider how convenient it can be to use an identity provider that you trust, but someone else manages. For example, you could have one type of authentication for users who access SharePoint Server 2013 in the cloud and another for SharePoint 2013 users in your on-premises environment. The Azure Access Control Service makes these choices possible.</span></span> 
  
<span data-ttu-id="c0ddb-p102">Cet article vous explique comment utiliser le service de contrôle d'accès Azure pour authentifier vos utilisateurs SharePoint 2013 avec Azure AD, au lieu d'utiliser votre instance Active Directory locale. Dans cette configuration, Azure AD devient un fournisseur d'identité approuvé pour SharePoint 2013. Cette configuration ajoute une méthode d'authentification utilisateur distincte de l'authentification Active Directory utilisée par l'installation SharePoint 2013 proprement dite. Pour pouvoir tirer parti de cet article, vous devez connaître WS-Federation. Pour plus d'informations, voir l'article de [présentation de WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p102">This article explains how you can use the Azure Access Control Service to authenticate your SharePoint 2013 users with Azure AD, instead of your on-premises Active Directory. In this configuration, Azure AD becomes a trusted identity provider for SharePoint 2013. This configuration adds a user authentication method that is separate from Active Directory authentication used by the SharePoint 2013 installation itself. To benefit from this article, you should be familiar with WS-Federation. For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span>
  
<span data-ttu-id="c0ddb-114">Le schéma suivant illustre le fonctionnement de l'authentification pour les utilisateurs SharePoint 2013 dans cette configuration.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-114">The following figure shows how authentication works for SharePoint 2013 users in this configuration.</span></span>
  
![Utilisateurs authentifiés via Azure Active Directory](images/SP_AzureAD.png)
  
<span data-ttu-id="c0ddb-116">L'exemple utilisé dans cet article est fourni par Kirk Evans, architecte Microsoft pour le centre d'excellence Azure.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-116">The example used in this article is provided by Kirk Evans, Microsoft Architect for the Azure Center of Excellence.</span></span> 
  
<span data-ttu-id="c0ddb-117">Pour plus d'informations sur l'accessibilité SharePoint 2013, voir [Accessibilité pour SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span><span class="sxs-lookup"><span data-stu-id="c0ddb-117">For information about SharePoint 2013 accessibility, see [Accessibility for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>
  
## <a name="configuration-overview"></a><span data-ttu-id="c0ddb-118">Vue d’ensemble de la configuration</span><span class="sxs-lookup"><span data-stu-id="c0ddb-118">Configuration overview</span></span>

<span data-ttu-id="c0ddb-119">Suivez la procédure générale suivante pour configurer votre environnement pour utiliser Azure AD comme fournisseur d'identité SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-119">Follow these general steps to set up your environment to use Azure AD as a SharePoint 2013 identity provider.</span></span>
  
1. <span data-ttu-id="c0ddb-120">Créez un nouveau client et espace de noms Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-120">Create a new Azure AD tenant and namespace.</span></span>
    
2. <span data-ttu-id="c0ddb-121">Ajoutez un fournisseur d’identité WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-121">Add a WS-Federation identity provider.</span></span>
    
3. <span data-ttu-id="c0ddb-122">Ajoutez une application par partie de confiance SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-122">Add SharePoint as a relying party application.</span></span>
    
4. <span data-ttu-id="c0ddb-123">Créez un certificat auto-signé à utiliser pour SSL.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-123">Create a self-signed certificate to use for SSL.</span></span>
    
5. <span data-ttu-id="c0ddb-124">Créez un groupe de règles pour l’authentification basée sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-124">Create a rule group for claims-based authentication.</span></span>
    
6. <span data-ttu-id="c0ddb-125">Configurez le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-125">Configure the X.509 certificate.</span></span>
    
7. <span data-ttu-id="c0ddb-126">Créez un mappage de revendications.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-126">Create a claim mapping.</span></span>
    
8. <span data-ttu-id="c0ddb-127">Configurez SharePoint pour le nouveau fournisseur d’identité.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-127">Configure SharePoint for the new identity provider.</span></span>
    
9. <span data-ttu-id="c0ddb-128">Définissez les autorisations.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-128">Set the permissions.</span></span>
    
10. <span data-ttu-id="c0ddb-129">Vérifiez le nouveau fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-129">Verify the new provider.</span></span>
    
## <a name="create-azure-ad-tenant-and-namespace"></a><span data-ttu-id="c0ddb-130">Création du client et de l’espace de noms Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-130">Create Azure AD tenant and namespace</span></span>

<span data-ttu-id="c0ddb-p103">Procédez comme suit pour créer un client Azure AD et un espace de noms associé. Dans cet exemple, nous utilisons l'espace de noms « blueskyabove ».</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p103">Use the following steps to create a new Azure AD tenant and an associated namespace. In this example, we use the namespace "blueskyabove."</span></span> 
  
1. <span data-ttu-id="c0ddb-133">Dans le portail de gestion Azure, cliquez sur **Active Directory**, puis créez un client Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-133">In the Azure Management Portal, click **Active Directory**, and then create a new Azure AD tenant.</span></span>
    
2. <span data-ttu-id="c0ddb-134">Cliquez sur **Espaces de noms Access Control** et créez un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-134">Click **Access Control Namespaces**, and create a new namespace.</span></span> 
    
3. <span data-ttu-id="c0ddb-p104">Cliquez sur **Gérer** dans la barre du bas pour ouvrir cet emplacement : https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p104">Click **Manage** on the bottom bar. This should open this location, https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span></span>
    
4. <span data-ttu-id="c0ddb-p105">Ouvrez Windows PowerShell. Utilisez le Module Microsoft Online Services pour Windows PowerShell, qui est requis pour l'installation de Azure pour les cmdlets Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p105">Open Windows PowerShell. Use the Microsoft Online Services Module for Windows PowerShell, which is a prerequisite for installing the Azure for Windows PowerShell cmdlets.</span></span>
    
5. <span data-ttu-id="c0ddb-139">Dans l'invite de commandes Windows PowerShell, saisissez la commande  `Connect-Msolservice`, puis saisissez vos informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-139">From the Windows PowerShell command prompt, type the command:  `Connect-Msolservice`, and then type your credentials.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="c0ddb-140">Pour plus d'informations sur l'utilisation de Azure pour les cmdlets Windows PowerShell, voir [Gestion d'Azure AD à l'aide de Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span><span class="sxs-lookup"><span data-stu-id="c0ddb-140">For additional information about how to use Azure for Windows PowerShell cmdlets, see [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span></span> 
  
6. <span data-ttu-id="c0ddb-141">Dans l'invite de commandes Windows PowerShell, saisissez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c0ddb-141">From a Windows PowerShell command prompt, type the following commands:</span></span>
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    <span data-ttu-id="c0ddb-142">L’illustration suivante montre les données obtenues.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-142">The following figure illustrates the output result.</span></span>
    
     ![Création de noms de principal de service](images/ServicePrincipalNames.jpg)
  
## <a name="add-a-ws-federation-identity-provider-to-the-namespace"></a><span data-ttu-id="c0ddb-144">Ajout d’un fournisseur d’identité WS-Federation à l’espace de noms</span><span class="sxs-lookup"><span data-stu-id="c0ddb-144">Add a WS-Federation identity provider to the namespace</span></span>

<span data-ttu-id="c0ddb-145">Procédez comme suit pour ajouter un nouveau fournisseur d’identité WS-Federation à l’espace de noms blueskyabove.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-145">Use the following steps to add a new WS-Federation identity provider to the blueskyabove namespace.</span></span>
  
1. <span data-ttu-id="c0ddb-146">Dans le portail de gestion Azure, accédez à **Active Directory** > **Espaces de noms Access Control**, cliquez sur **Créer une nouvelle instance**, puis cliquez sur **Gérer**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-146">From the Azure management portal, go to **Active Directory** > **Access Control Namespaces**, click **Create a new instance**, and then click **Manage**.</span></span>
    
2. <span data-ttu-id="c0ddb-147">Dans le portail Azure Access Control, cliquez sur **Fournisseurs d'identité** > **Ajouter**, comme illustré dans la capture suivante.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-147">From the Azure Access Control portal, click **Identity Providers** > **Add**, as illustrated in the following figure.</span></span>
    
     ![Boîte de dialogue des fournisseurs d’identité dans Azure](images/Identity.jpg)
  
3. <span data-ttu-id="c0ddb-149">Cliquez sur **Fournisseur d'identité WS-Federation**, comme illustré dans la figure suivante, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-149">Click **WS-Federation identity provider**, as illustrated in the following figure, and then click **Next**.</span></span>
    
     ![Paramètres d’ajout de fournisseur d’identité](images/AddIdentity.jpg)
  
4. <span data-ttu-id="c0ddb-p106">Indiquez le nom complet et le texte du lien d'ouverture de session, puis cliquez sur **Enregistrer**. Pour l'URL des métadonnées WS-Federation, saisissez https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. La capture suivante illustre la définition des paramètres.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p106">Fill out the display name and logon link text, and then click **Save**. For the WS-Federation metadata URL, type https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. The following figure illustrates the setting.</span></span>
    
     ![Fournisseur d’identité de la fédération](images/FederationIdentity.jpg)
  
## <a name="add-sharepoint-as-a-relying-party-application"></a><span data-ttu-id="c0ddb-155">Ajoutez SharePoint comme application par partie de confiance.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-155">Add SharePoint as a relying party application</span></span>

<span data-ttu-id="c0ddb-156">Procédez comme suit pour ajouter SharePoint comme application par partie de confiance.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-156">Use the following steps to add SharePoint as a relying party application.</span></span>
  
<span data-ttu-id="c0ddb-157">Pour plus d'informations sur les paramètres des applications par partie de confiance, voir [Applications par partie de confiance](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span><span class="sxs-lookup"><span data-stu-id="c0ddb-157">For additional information about relying party application settings, see [Relying Party Applications](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span></span>
  
1. <span data-ttu-id="c0ddb-158">Dans le portail Azure Access Control, cliquez sur **Applications par partie de confiance**, puis cliquez sur **Ajouter**, comme illustré dans la capture suivante.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-158">From the Azure Access Control portal, click **Relying party applications**, and then click **Add**, as illustrated in the following figure.</span></span>
    
     ![Paramètres d’application de partie de confiance](images/RelyingPartyApplications.jpg)
  
## <a name="create-a-self-signed-certificate-to-use-for-ssl"></a><span data-ttu-id="c0ddb-160">Création d’un certificat auto-signé à utiliser pour SSL</span><span class="sxs-lookup"><span data-stu-id="c0ddb-160">Create a self-signed certificate to use for SSL</span></span>

<span data-ttu-id="c0ddb-161">Procédez comme suit pour créer un certificat auto-signé à utiliser pour sécuriser les communications sur SSL.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-161">Use the following steps to create a new, self-signed certificate to use for secure communications over SSL.</span></span>
  
1. <span data-ttu-id="c0ddb-162">Étendez l’application web pour utiliser la même URL que le site de publication, mais utilisez SSL avec le port 443, comme illustré dans la capture suivante.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-162">Extend the web application to use the same URL as PublishingSite, but use SSL with port 443, as illustrated in the following figure.</span></span>
    
     ![Paramètres permettant d’étendre l’application](images/ExtendWebApp.jpg)
  
2. <span data-ttu-id="c0ddb-164">Dans le Gestionnaire des services Internet (IIS), double-cliquez sur **Certificats de serveur**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-164">In IIS Manager, double-click **Server Certificates**.</span></span>
    
3. <span data-ttu-id="c0ddb-p107">Dans le volet **Actions**, cliquez sur **Créer un certificat auto-signé**. Saisissez un nom convivial pour le certificat dans la case **Indiquer un nom convivial pour le certificat**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p107">In the **Actions** pane, click **Create Self-Signed Certificate**. Type a friendly name for the certificate in the **Specify a friendly name for the certificate** box, and then click **OK**.</span></span>
    
4. <span data-ttu-id="c0ddb-167">Dans la boîte de dialogue **Modifier la liaison de site**, vérifiez que le nom d'hôte est le même que le nom convivial, comme illustré dans les captures suivantes.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-167">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following figures.</span></span>
    
     ![Assistant Créer un certificat auto-signé](images/SelfSignedCert.jpg)
  
     ![Nom d’hôte dans la boîte de dialogue Modifier les liaisons](images/SelfSignedCert1.jpg)
  
5. <span data-ttu-id="c0ddb-170">Dans le portail de gestion Azure, cliquez sur la machine virtuelle que vous souhaitez configurer, puis cliquez sur **Points de terminaison**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-170">From the Azure management portal, click the virtual machine that you want to configure, and then click **Endpoints**.</span></span>
    
6. <span data-ttu-id="c0ddb-171">Cliquez sur **Ajouter**, puis cliquez sur **-->** (pour Suivant).</span><span class="sxs-lookup"><span data-stu-id="c0ddb-171">Click **Add**, and then click **-->** (for Next).</span></span>
    
7. <span data-ttu-id="c0ddb-172">Dans **Nom**, saisissez le nom du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-172">In **Name**, type a name for the endpoint.</span></span>
    
8. <span data-ttu-id="c0ddb-p108">Dans **Port public** et **Port privé**, saisissez les numéros de port que vous souhaitez utiliser, puis cliquez sur la coche pour terminer. Ces numéros peuvent être différents. Pour les besoins de cet article, nous utilisons le port 443, comme indiqué dans la capture suivante.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p108">In **Public Port** and **Private Port**, type the port numbers that you want to use, and then click the check mark to complete. These numbers can be different. For the purposes of this article, we are using 443, as illustrated in the following figure.</span></span>
    
     ![Paramètres de point de terminaison dans Azure](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="c0ddb-177">Pour plus d'informations sur l'ajout d'un point de terminaison à une machine virtuelle dans Azure, voir [Comment configurer des points de terminaison sur une machine virtuelle](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span><span class="sxs-lookup"><span data-stu-id="c0ddb-177">For additional information about how to add an endpoint to a virtual machine in Azure, see [How to Set Up Endpoints to a Virtual Machine](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span></span> 
  
9. <span data-ttu-id="c0ddb-178">Dans le portail de services Access Control, ajoutez une partie de confiance, comme illustré dans la capture suivante.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-178">From the Access Control services portal, add a relying party, as illustrated in the following figure.</span></span>
    
     ![Paramètres d’application d’ajout de partie de confiance](images/AddRelyingParty.jpg)
  
## <a name="create-a-rule-group-for-claims-based-authentication"></a><span data-ttu-id="c0ddb-180">Créez un groupe de règles pour l’authentification basée sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-180">Create a rule group for claims-based authentication</span></span>

<span data-ttu-id="c0ddb-181">Procédez comme suit pour créer un groupe de règles pour contrôler l’authentification basée sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-181">Use the following steps to create a new rule group to control claims-based authentication.</span></span>
  
1. <span data-ttu-id="c0ddb-182">Dans le volet gauche, cliquez sur **Groupes de règles**, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-182">In the left pane, click **Rule groups**, and then click **Add**.</span></span>
    
2. <span data-ttu-id="c0ddb-p109">Saisissez le nom du groupe de règles, cliquez sur **Enregistrer**, puis cliquez sur **Générer**. Pour les besoins de cet article, nous utilisons le **Default Rule Group for. spvms.cloudapp.net**, comme illustré dans la capture suivante.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p109">Type a name for the rule group, click **Save**, and then click **Generate**. For the purposes of this article, we are using **Default Rule Group for. spvms.cloudapp.net**, as illustrated in the following figure.</span></span>
    
     ![Paramètres de groupe de règles dans Azure](images/RuleGroup.jpg)
  
     ![Règles après sélection de l’option Générer](images/GenerateRules.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="c0ddb-187">Pour plus d'informations sur la création de groupes de règles, voir [Règles et groupes de règles](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span><span class="sxs-lookup"><span data-stu-id="c0ddb-187">For additional information about how to create rule groups, see [Rule Groups and Rules](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span></span> 
  
3. <span data-ttu-id="c0ddb-p110">Cliquez sur le groupe de règles que vous souhaitez modifier, puis cliquez sur la règle de revendication que vous souhaitez modifier. Pour les besoins de cet article, nous ajoutons une règle de revendication au groupe pour transmettre la règle **name** en tant que règle **upn**, comme illustré dans la capture suivante.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p110">Click the rule group that you want to change, and then click the claim rule that you want to change. For the purposes of this article, we add a claim rule to the group to pass **name** as **upn**, as illustrated by the following figure.</span></span>
    
     ![Règles de revendication dans le contrôle d’accès Azure](images/ClaimRules.jpg)
  
4. <span data-ttu-id="c0ddb-191">Supprimez la règle de revendication existante nommée **upn** et laissez la règle de **Name Claim to UPN**, comme illustré dans la capture suivante.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-191">Delete the existing claim rule named **upn**, and leave the **Name Claim to UPN** rule, as illustrated by the following figure.</span></span>
    
     ![Paramètres de règles dans le contrôle d’accès Azure](images/ClaimToUPN.jpg)
  
## <a name="configure-the-x509-certificate"></a><span data-ttu-id="c0ddb-193">Configurer le certificat X.509</span><span class="sxs-lookup"><span data-stu-id="c0ddb-193">Configure the X.509 certificate</span></span>

<span data-ttu-id="c0ddb-194">Procédez comme suit pour configurer le certificat X.509 à utiliser pour la signature des jetons.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-194">Use the following steps to configure the X.509 certificate to use for token signing.</span></span>
  
1. <span data-ttu-id="c0ddb-195">Dans le volet Service du contrôle d'accès, sous **Développement**, cliquez sur **Intégration d'applications**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-195">In the Access Control Service pane, under **Development**, click **Application integration**.</span></span>
    
2. <span data-ttu-id="c0ddb-196">Dans **Référence du point de terminaison**, localisez le fichier **Federation.xml** qui est associé à votre client Azure, puis copiez l'emplacement dans la barre d'adresses d'un navigateur.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-196">In **Endpoint Reference**, locate the **Federation.xml** that is associated with your Azure tenant, and then copy the location in the address bar of a browser.</span></span>
    
3. <span data-ttu-id="c0ddb-197">Dans le fichier **Federation.xml**, recherchez la section **RoleDescriptor** et copiez les informations de l'élément _<X509Certificate>_, comme illustré dans la capture suivante.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-197">In the **Federation.xml** file, locate the **RoleDescriptor** section, and copy the information from the _<X509Certificate>_ element, as illustrated in the following figure.</span></span>
    
     ![Élément de certificat X509 du fichier Federation.xml](images/X509Cert.jpg)
  
4. <span data-ttu-id="c0ddb-199">À la racine du lecteur C:\\, créez un dossier nommé **Certificates**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-199">From the root of drive C:\\, create a folder named **Certificates**.</span></span>
    
5. <span data-ttu-id="c0ddb-200">Enregistrez les informations de l'élément X509Certificate dans le dossier C:\\Certificats avec le nom de fichier **AcsTokenSigning.cer**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-200">Save the X509Certificate information to the folder C:\\Certificates with the file name, **AcsTokenSigning.cer**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="c0ddb-201">Le nom de fichier doit être enregistré avec une extension .cer.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-201">The file name must be saved with a .cer extension.</span></span> 
  
     ![Sauvegarde de l’élément X509Certificate en tant que fichier](images/X509Cert_Save.jpg)
  
## <a name="create-a-claim-mapping-by-using-windows-powershell"></a><span data-ttu-id="c0ddb-203">Création d'un mappage de revendications à l'aide de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0ddb-203">Create a claim mapping by using Windows PowerShell</span></span>

<span data-ttu-id="c0ddb-204">Procédez comme suit pour créer un mappage de revendications à l'aide de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-204">Use the following steps to create a claim mapping by using Windows PowerShell.</span></span>
  
<span data-ttu-id="c0ddb-205">Vérifiez que vous disposez des appartenances suivantes :</span><span class="sxs-lookup"><span data-stu-id="c0ddb-205">Verify that you have the following memberships:</span></span>
  
1. <span data-ttu-id="c0ddb-206">du rôle serveur fixe **securityadmin** sur l'instance SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-206">**securityadmin** fixed server role on the SQL Server instance.</span></span>
    
2. <span data-ttu-id="c0ddb-207">du rôle de base de données fixe **db_owner** sur toutes les bases de données à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-207">**db_owner** fixed database role on all databases that will be updated.</span></span>
    
3. <span data-ttu-id="c0ddb-208">du groupe Administrateurs sur le serveur sur lequel vous exécutez les cmdlets Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-208">Administrators group on the server on which you are running the Windows PowerShell cmdlets.</span></span>
    
<span data-ttu-id="c0ddb-209">Un administrateur peut utiliser l'applet de commande **Add-SPShellAdmin** pour accorder des autorisations d'utilisation des applets de commande SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-209">An administrator can use the **Add-SPShellAdmin** cmdlet to grant permissions to use SharePoint 2013 cmdlets.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c0ddb-p111">Si vous ne disposez pas des autorisations, contactez votre administrateur d'installation ou votre administrateur SQL Server afin de les demander. Pour plus d'informations sur les autorisations Windows PowerShell, voir [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p111">If you do not have permissions, contact your Setup administrator or SQL Server administrator to request permissions. For additional information about Windows PowerShell permissions, see [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx).</span></span> 
  
1. <span data-ttu-id="c0ddb-212">Dans le menu **Démarrer**, cliquez sur **Tous les programmes**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-212">From the **Start** menu, click **All Programs**.</span></span>
    
2. <span data-ttu-id="c0ddb-213">Cliquez sur **Produits Microsoft SharePoint 2013**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-213">Click **Microsoft SharePoint 2013 Products**.</span></span>
    
3. <span data-ttu-id="c0ddb-214">Cliquez sur **SharePoint 2013 Management Shell**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-214">Click **SharePoint 2013 Management Shell**.</span></span>
    
4. <span data-ttu-id="c0ddb-215">À l'invite de commandes Windows PowerShell, entrez les commandes suivantes pour créer un mappage de revendications :</span><span class="sxs-lookup"><span data-stu-id="c0ddb-215">At the Windows PowerShell command prompt, type the following commands to create a claim mapping:</span></span>
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## <a name="configure-sharepoint-for-the-new-identity-provider"></a><span data-ttu-id="c0ddb-216">Configuration de SharePoint pour le nouveau fournisseur d’identité</span><span class="sxs-lookup"><span data-stu-id="c0ddb-216">Configure SharePoint for the new identity provider</span></span>

<span data-ttu-id="c0ddb-217">Procédez comme suit pour configurer votre installation SharePoint avec le nouveau fournisseur d'identité pour Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-217">Use the following steps to configure your SharePoint installation to the new identity provider for Azure AD.</span></span>
  
1. <span data-ttu-id="c0ddb-218">Vérifiez que le compte d’utilisateur qui exécute cette procédure est membre du groupe SharePoint Administrateurs de batterie.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-218">Verify that the user account that is performing this procedure is a member of the Farm Administrators SharePoint group.</span></span>
    
2. <span data-ttu-id="c0ddb-219">Dans la page d'accueil de l'Administration centrale, cliquez sur **Gestion des applications**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-219">In Central Administration, on the home page, click **Application Management**.</span></span>
    
3. <span data-ttu-id="c0ddb-220">Dans la section **Applications web** de la page **Gestion des applications**, cliquez sur **Gérer les applications web**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-220">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
4. <span data-ttu-id="c0ddb-221">Cliquez sur l’application Web appropriée.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-221">Click the appropriate web application.</span></span>
    
5. <span data-ttu-id="c0ddb-222">Dans le ruban, cliquez sur **Fournisseurs d'authentification**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-222">From the ribbon, click **Authentication Providers**.</span></span>
    
6. <span data-ttu-id="c0ddb-p112">Sous **Zone**, cliquez sur le nom de la zone. Par exemple, **Par défaut**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p112">Under **Zone**, click the name of the zone. For example, **Default**.</span></span>
    
7. <span data-ttu-id="c0ddb-p113">Dans la section **Types d'authentification basée sur les revendications** de la page **Modifier l'authentification**, sélectionnez **Fournisseur d'identité approuvé**, puis cliquez sur le nom de votre fournisseur, **ACS Provider** aux fins de cet article. Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p113">On the **Edit Authentication** page, in the **Claims Authentication Types** section, select **Trusted Identity provider**, and then click the name of your provider, which for purposes of this article is **ACS Provider**. Click **OK**.</span></span>
    
8. <span data-ttu-id="c0ddb-227">La capture suivante illustre le paramètre de **Trusted Provider**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-227">The following figure illustrates the **Trusted Provider** setting.</span></span>
    
![Paramètre de fournisseur approuvé dans une application web](images/AddProvider_Azure.jpg)
  
## <a name="set-the-permissions"></a><span data-ttu-id="c0ddb-229">Définition des autorisations</span><span class="sxs-lookup"><span data-stu-id="c0ddb-229">Set the permissions</span></span>

<span data-ttu-id="c0ddb-230">Procédez comme suit pour définir les autorisations pour accéder à l’application web.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-230">Use the following steps to set the permissions to access the web application.</span></span>
  
1. <span data-ttu-id="c0ddb-231">Sur la page d'accueil de l'Administration centrale, cliquez sur **Gestion des applications**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-231">In Central Administration, on the home page, click **Application Management**.</span></span>
    
2. <span data-ttu-id="c0ddb-232">Dans la section **Applications web** de la page **Gestion des applications**, cliquez sur **Gérer les applications web**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-232">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
3. <span data-ttu-id="c0ddb-233">Cliquez sur l'application web appropriée, puis sur **Stratégie de l'utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-233">Click the appropriate web application, and then click **User Policy**.</span></span>
    
4. <span data-ttu-id="c0ddb-234">Dans **Stratégie de l'application web**, cliquez sur **Ajouter des utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-234">In **Policy for Web Application**, click **Add Users**.</span></span>
    
5. <span data-ttu-id="c0ddb-235">Dans la boîte de dialogue **Ajouter des utilisateurs**, cliquez sur la zone appropriée dans **Zones**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-235">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="c0ddb-236">Dans la boîte de dialogue **Ajouter des utilisateurs**, saisissez user2@blueskyabove.onmicrosoft.com (fournisseur ACS).</span><span class="sxs-lookup"><span data-stu-id="c0ddb-236">In the **Add Users** dialog box, typeuser2@blueskyabove.onmicrosoft.com (ACS Provider).</span></span>
    
7. <span data-ttu-id="c0ddb-237">Dans **Autorisations**, cliquez sur **Contrôle total**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-237">In **Permissions**, click **Full Control**.</span></span>
    
8. <span data-ttu-id="c0ddb-238">Cliquez sur **Terminer**, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-238">Click **Finish**, and then click **OK**.</span></span>
    
<span data-ttu-id="c0ddb-239">La capture suivante illustre la section **Ajouter des utilisateurs** d'une application web existante.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-239">The following figure illustrates the **Add Users** section of an existing web application.</span></span>
  
![Ajout d’utilisateurs à une application web existante](images/AddUsers_Azure.jpg)
  
## <a name="verify-the-new-provider"></a><span data-ttu-id="c0ddb-241">Vérification du nouveau fournisseur</span><span class="sxs-lookup"><span data-stu-id="c0ddb-241">Verify the new provider</span></span>

<span data-ttu-id="c0ddb-242">Procédez comme suit pour vérifier que le nouveau fournisseur d’identité fonctionne en vous assurant que le nouveau fournisseur d’authentification s’affiche à l’invite de connexion.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-242">Use the following steps to verify that the new identity provider is working by ensuring that the new authentication provider appears on the sign-in prompt.</span></span>
  
1. <span data-ttu-id="c0ddb-243">Connectez-vous en utilisant le nouveau fournisseur nommé **Blue Sky Above**, comme illustré dans la capture suivante.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-243">Sign in by using the new provider named **Blue Sky Above**, as illustrated in the following figure.</span></span>
    
     ![Boîte de dialogue de connexion affichant le nouveau fournisseur approuvé](images/BlueSkyAbove.jpg)
  
## <a name="additional-resources"></a><span data-ttu-id="c0ddb-245">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="c0ddb-245">Additional resources</span></span>

[<span data-ttu-id="c0ddb-246">Présentation de WS-Federation</span><span class="sxs-lookup"><span data-stu-id="c0ddb-246">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="c0ddb-247">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="c0ddb-247">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="c0ddb-248">Participer à la discussion</span><span class="sxs-lookup"><span data-stu-id="c0ddb-248">Join the discussion</span></span>

|<span data-ttu-id="c0ddb-249">**Contactez-nous**</span><span class="sxs-lookup"><span data-stu-id="c0ddb-249">**Contact us**</span></span>|<span data-ttu-id="c0ddb-250">**Description**</span><span class="sxs-lookup"><span data-stu-id="c0ddb-250">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c0ddb-251">**De quelles solutions avez-vous besoin ?**</span><span class="sxs-lookup"><span data-stu-id="c0ddb-251">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="c0ddb-p114">Nous sommes en train de créer du contenu pour les solutions qui s'étendent sur plusieurs produits et services Microsoft. Donnez-nous votre avis sur nos solutions entre serveurs ou demandez des solutions spécifiques en envoyant un courrier électronique à [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p114">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="c0ddb-254">**Participer à la discussion sur les solutions**</span><span class="sxs-lookup"><span data-stu-id="c0ddb-254">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="c0ddb-p115">Si vous êtes passionné par les solutions basées sur le cloud, rejoignez le conseil consultatif de l’adoption cloud (CAAB) pour interagir avec une communauté vaste et dynamique de développeurs de contenu Microsoft, de professionnels du secteur et de clients venant du monde entier. Pour participer, ajoutez-vous en tant que membre de l’espace [CAAB (Conseil consultatif de l’adoption cloud)](https://aka.ms/caab) de la communauté Microsoft Tech et envoyez-nous un message électronique à l’adresse [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Tout le monde peut lire le contenu lié à la communauté sur le [blog CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Toutefois, les membres CAAB reçoivent des invitations à des webinaires privés qui décrivent les nouvelles solutions et ressources relatives à l’adoption cloud.</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p115">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="c0ddb-258">**Obtenir l'image que vous voyez ici**</span><span class="sxs-lookup"><span data-stu-id="c0ddb-258">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="c0ddb-p116">Si vous voulez obtenir une copie modifiable de l’image que vous voyez dans cet article, nous serons ravis de vous l’envoyer. Envoyez-nous votre demande par courrier électronique, en incluant l’URL et le titre de l’illustration, à [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).</span><span class="sxs-lookup"><span data-stu-id="c0ddb-p116">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

