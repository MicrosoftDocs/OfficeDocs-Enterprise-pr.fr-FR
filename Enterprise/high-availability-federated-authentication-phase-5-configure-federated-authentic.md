---
title: "Authentification fédérée haute disponibilité, phase 5  Configurer l'authentification fédérée pour Office 365"
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
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: "Résumé : Configurer Azure AD Connect pour votre authentification fédérée haute disponibilité pour Office 365 dans Microsoft Azure."
ms.openlocfilehash: 2c23ffa2e9f033018c5cc1fd016fb4ed76535605
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a><span data-ttu-id="e77ff-103">Authentification fédérée haute disponibilité, phase 5 : Configurer l'authentification fédérée pour Office 365</span><span class="sxs-lookup"><span data-stu-id="e77ff-103">High availability federated authentication Phase 5: Configure federated authentication for Office 365</span></span>

 <span data-ttu-id="e77ff-104">**Résumé :** Configurer Azure AD Connect pour votre authentification fédérée haute disponibilité pour Office 365 dans Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="e77ff-104">**Summary:** Configure Azure AD Connect for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
 
<span data-ttu-id="e77ff-p101">Au cours de cette phase finale du déploiement de l'authentification fédérée haute disponibilité pour Office 365 dans les services d'infrastructure Azure, vous obtenez et installez un certificat émis par une autorité de certification publique, vérifiez votre configuration et installez et exécutez Azure AD Connect sur le serveur DirSync. Azure AD Connect configure votre abonnement Office 365, vos services Active Directory Federation Services (AD FS) et les serveurs proxy d'application web pour l'authentification fédérée.</span><span class="sxs-lookup"><span data-stu-id="e77ff-p101">In this final phase of deploying high availability federated authentication for Office 365 in Azure infrastructure services, you get and install a certificate issued by a public certification authority, verify your configuration, and then install and run Azure AD Connect on the DirSync server. Azure AD Connect configures your Office 365 subscription and your Active Directory Federation Services (AD FS) and web application proxy servers for federated authentication.</span></span>
  
<span data-ttu-id="e77ff-107">Reportez-vous à la rubrique [Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) pour toutes les phases.</span><span class="sxs-lookup"><span data-stu-id="e77ff-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="get-a-public-certificate-and-copy-it-to-the-dirsync-server"></a><span data-ttu-id="e77ff-108">Obtenir un certificat public et le copier sur le serveur DirSync</span><span class="sxs-lookup"><span data-stu-id="e77ff-108">Get a public certificate and copy it to the DirSync server</span></span>

<span data-ttu-id="e77ff-109">Obtenez auprès d’une autorité de certification publique un certificat numérique avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="e77ff-109">Get a digital certificate from a public certification authority with the following properties:</span></span>
  
- <span data-ttu-id="e77ff-110">Un certificat X.509 approprié pour créer des connexions SSL.</span><span class="sxs-lookup"><span data-stu-id="e77ff-110">An X.509 certificate suitable for creating SSL connections.</span></span>
    
- <span data-ttu-id="e77ff-111">La propriété étendue d’autre nom de sujet (Subject Alternative Name, SAN) est définie sur le nom de domaine complet du service de fédération (exemple : fs.contoso.com).</span><span class="sxs-lookup"><span data-stu-id="e77ff-111">The Subject Alternative Name (SAN) extended property is set to your federation service FQDN (example: fs.contoso.com).</span></span>
    
- <span data-ttu-id="e77ff-112">Le certificat doit contenir la clé privée et être stocké au format PFX.</span><span class="sxs-lookup"><span data-stu-id="e77ff-112">The certificate must have the private key and be stored in PFX format.</span></span>
    
<span data-ttu-id="e77ff-p102">Par ailleurs, les ordinateurs et appareils de votre organisation doivent approuver l'autorité de certification publique qui émet le certificat numérique. Pour cela, vous devez installer un certificat racine de l'autorité de certification publique dans la banque Autorités de certification racines de confiance de vos ordinateurs et appareils. Sur les ordinateurs exécutant Microsoft Windows, un ensemble de certificats de ce type est installé pour les autorités de certification couramment utilisées. Si le certificat racine de votre autorité de certification publique n'est pas déjà installé, vous devez le déployer sur les ordinateurs et les appareils de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="e77ff-p102">Additionally, your organization computers and devices must trust the public certification authority that is issuing the digital certificate. This trust is established by having a root certificate from the public certification authority installed in the trusted root certification authorities store on your computers and devices. Computers running Microsoft Windows typically have a set of these types of certificates installed from commonly-used certification authorities. If the root certificate from your public certification authority is not already installed, you must deploy this to the computers and devices of your organization.</span></span>
  
<span data-ttu-id="e77ff-117">Pour plus d'informations sur les certificats requis pour l'authentification fédérée, consultez la rubrique [Configuration requise pour l'installation et la configuration de la fédération](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span><span class="sxs-lookup"><span data-stu-id="e77ff-117">For more information about certificate requirements for federated authentication, see [Prerequisites for federation installation and configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span></span>
  
<span data-ttu-id="e77ff-p103">Lorsque vous recevez le certificat, copiez-le dans un dossier sur le lecteur C: du serveur DirSync. Par exemple, nommez le fichier SSL.pfx et stockez-le dans le dossier C:\\Certs du serveur DirSync.</span><span class="sxs-lookup"><span data-stu-id="e77ff-p103">When you receive the certificate, copy it to a folder on the C: drive of the DirSync server. For example, name the file SSL.pfx and store it in the C:\\Certs folder on the DirSync server.</span></span>
  
## <a name="verify-your-configuration"></a><span data-ttu-id="e77ff-120">Vérifier votre configuration</span><span class="sxs-lookup"><span data-stu-id="e77ff-120">Verify your configuration</span></span>

<span data-ttu-id="e77ff-p104">Vous devez maintenant être prêt à configurer Azure AD Connect et l'authentification fédérée pour Office 365. Pour vous en assurer, utilisez la liste de vérification suivante :</span><span class="sxs-lookup"><span data-stu-id="e77ff-p104">You should now be ready to configure Azure AD Connect and federated authentication for Office 365. To ensure that you are, here is a checklist:</span></span>
  
- <span data-ttu-id="e77ff-123">Le domaine public de votre organisation a été ajouté à votre abonnement Office 365.</span><span class="sxs-lookup"><span data-stu-id="e77ff-123">Your organization's public domain is added to your Office 365 subscription.</span></span>
    
- <span data-ttu-id="e77ff-124">Les comptes d'utilisateur Office 365 de votre organisation sont configurés sur le nom de domaine public de votre organisation et peuvent se connecter.</span><span class="sxs-lookup"><span data-stu-id="e77ff-124">Your organization's Office 365 user accounts are configured to your organization's public domain name and can successfully sign in.</span></span>
    
- <span data-ttu-id="e77ff-125">Vous avez déterminé le nom de domaine complet d’un service de fédération à partir de votre nom de domaine public.</span><span class="sxs-lookup"><span data-stu-id="e77ff-125">You have determined a federation service FQDN based your public domain name.</span></span>
    
- <span data-ttu-id="e77ff-126">Un enregistrement DNS A public au nom de domaine complet de votre service de fédération pointe vers l’adresse IP publique de l’équilibreur de charge Azure connecté à Internet pour les serveurs proxy d’application web.</span><span class="sxs-lookup"><span data-stu-id="e77ff-126">A public DNS A record for your federation service FQDN points to the public IP address of the Internet-facing Azure load balancer for the web application proxy servers.</span></span>
    
- <span data-ttu-id="e77ff-127">Un enregistrement DNS A privé au nom de domaine complet de votre service de fédération pointe vers l’adresse IP privée de l’équilibreur de charge Azure interne pour les serveurs AD FS.</span><span class="sxs-lookup"><span data-stu-id="e77ff-127">A private DNS A record for your federation service FQDN points to the private IP address of the internal Azure load balancer for the AD FS servers.</span></span>
    
- <span data-ttu-id="e77ff-128">Un certificat numérique émis par une autorité de certification publique pour les connexions SSL avec le SAN défini sur le nom de domaine complet de votre service de fédération est un fichier PFX stocké sur votre serveur DirSync.</span><span class="sxs-lookup"><span data-stu-id="e77ff-128">A public certification authority-isssued digital certificate suitable for SSL connections with the SAN set to your federation service FQDN is a PFX file stored on your DirSync server.</span></span>
    
- <span data-ttu-id="e77ff-129">Le certificat racine de l'autorité de certification publique est installé dans la banque Autorités de certification racines de confiance de vos ordinateurs et appareils.</span><span class="sxs-lookup"><span data-stu-id="e77ff-129">The root certificate for the public certification authority is installed in the Trusted Root Certification Authorities store on your computers and devices.</span></span>
    
<span data-ttu-id="e77ff-130">Voici un exemple pour l’organisation Contoso :</span><span class="sxs-lookup"><span data-stu-id="e77ff-130">Here is an example for the Contoso organization:</span></span>
  
<span data-ttu-id="e77ff-131">**Exemple de configuration pour une infrastructure d'authentification fédérée haute disponibilité dans Azure**</span><span class="sxs-lookup"><span data-stu-id="e77ff-131">**An example configuration for a high availability federated authentication infrastructure in Azure**</span></span>

![Exemple de configuration de l’infrastructure d’authentification fédérée haute disponibilité Office 365 dans Azure](images/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a><span data-ttu-id="e77ff-133">Exécutez Azure AD Connect pour configurer l’authentification fédérée</span><span class="sxs-lookup"><span data-stu-id="e77ff-133">Run Azure AD Connect to configure federated authentication</span></span>

<span data-ttu-id="e77ff-134">L’outil Azure AD Connect configure les serveurs AD FS, les serveurs proxy d’application web et Office 365 pour l’authentification fédérée en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="e77ff-134">The Azure AD Connect tool configures the AD FS servers, the web application proxy servers, and Office 365 for federated authentication with these steps:</span></span>
  
1. <span data-ttu-id="e77ff-135">Créez une connexion Bureau à distance vers votre serveur DirSync avec un compte de domaine qui possède des privilèges d'administrateur local.</span><span class="sxs-lookup"><span data-stu-id="e77ff-135">Create a remote desktop connection to your DirSync server with a domain account that has local administrator privileges.</span></span>
    
2. <span data-ttu-id="e77ff-136">Sur le bureau du serveur DirSync, ouvrez Internet Explorer et accédez à [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="e77ff-136">From the desktop of the DirSync server, open Internet Explorer and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
3. <span data-ttu-id="e77ff-137">Sur la page de **Microsoft Azure Active Directory Connect**, cliquez sur **Télécharger**, puis cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-137">On the **Microsoft Azure Active Directory Connect** page, click **Download**, and then click **Run**.</span></span>
    
4. <span data-ttu-id="e77ff-138">Sur la page **Bienvenue dans Azure AD Connect**, cliquez sur **J'accepte**, puis sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-138">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
5. <span data-ttu-id="e77ff-139">Sur la page **Configuration rapide**, cliquez sur **Personnaliser**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-139">On the **Express Settings** page, click **Customize**.</span></span>
    
6. <span data-ttu-id="e77ff-140">Sur la page **Installer les composants nécessaires**, cliquez sur **Installer**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-140">On the **Install required components** page, click **Install**.</span></span>
    
7. <span data-ttu-id="e77ff-141">Sur la page **Connexion utilisateur**, cliquez sur **Fédération avec AD FS**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-141">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e77ff-142">Sur la page **Connexion à Azure AD**, saisissez le nom et le mot de passe d'un administrateur général de votre abonnement Office 365, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-142">On the **Connect to Azure AD** page, type the name and password of a global administrator account for your Office 365 subscription, and then click **Next**.</span></span>
    
9. <span data-ttu-id="e77ff-143">Sur la page **Connecter vos répertoires**, assurez-vous que votre forêt Windows Server AD locale est sélectionnée dans **Forêt**, entrez le nom et le mot de passe d'un compte d'administrateur de domaine, cliquez sur **Ajouter un répertoire**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-143">On the **Connect your directories** page, ensure that your on-premises Windows Server AD forest is selected in **Forest**, type the name and password of a domain administrator account, click **Add Directory**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="e77ff-144">Sur la page **Configuration la connexion à Azure AD**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-144">On the **Azure AD sign-in configuration** page, click **Next**.</span></span>
    
11. <span data-ttu-id="e77ff-145">Sur la page **Filtrage par domaine ou unité d'organisation**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-145">On the **Domain and OU filtering** page, click **Next**.</span></span>
    
12. <span data-ttu-id="e77ff-146">Sur la page **Identification de manière unique de vos utilisateurs**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-146">On the **Uniquely identifying your users** page, click **Next**.</span></span>
    
13. <span data-ttu-id="e77ff-147">Sur la page **Filtrer les utilisateurs et appareils**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-147">On the **Filter users and devices** page, click **Next**.</span></span>
    
14. <span data-ttu-id="e77ff-148">Sur la page **Fonctionnalités facultatives**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-148">On the **Optional features** page, click **Next**.</span></span>
    
15. <span data-ttu-id="e77ff-149">Sur la page **Batterie de serveurs AD FS**, cliquez sur **Configurer une nouvelle batterie AD FS**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-149">On the **AD FS farm** page, click **Configure a new AD FS farm**.</span></span>
    
16. <span data-ttu-id="e77ff-150">Cliquez sur **Parcourir** et spécifiez l'emplacement et le nom du certificat SSL de l''autorité de certification publique.</span><span class="sxs-lookup"><span data-stu-id="e77ff-150">Click **Browse** and specify the location and name of the SSL certificate from the public certification authority.</span></span>
    
17. <span data-ttu-id="e77ff-151">Lorsque vous y êtes invité, entrez le mot de passe du certificat, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-151">When prompted, type the certificate password, and then click **OK**.</span></span>
    
18. <span data-ttu-id="e77ff-152">Vérifiez que le **nom de sujet** et le **nom du service de fédération** sont définis sur le nom de domaine complet de votre service de fédération, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-152">Verify that the **Subject Name** and **Federation Service Name** are set to your federation service FQDN, and then click **Next**.</span></span>
    
19. <span data-ttu-id="e77ff-153">Sur la page **Serveurs AD FS**, entrez le nom de votre premier serveur AD FS (Tableau M - Élément 4 - Colonne Nom de machine virtuelle), puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-153">On the **AD FS servers** page, type your first AD FS server's name (Table M - Item 4 - Virtual machine name column), and then click **Add**.</span></span>
    
20. <span data-ttu-id="e77ff-154">Entrez le nom de votre deuxième serveur AD FS deuxième (Tableau M - élément 5 - colonne Nom de machine virtuelle), cliquez sur **Ajouter**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-154">Type your second AD FS server's name (Table M - Item 5 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
21. <span data-ttu-id="e77ff-155">Sur la page **Serveurs proxy d'application Web**, entrez le nom de votre premier serveur proxy d'application Web (Tableau M - Élément 6 - Colonne Nom de machine virtuelle), puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-155">On the **Web Application Proxy servers** page, type your first web application proxy server's name (Table M - Item 6 - Virtual machine name column), and then click **Add**.</span></span>
    
22. <span data-ttu-id="e77ff-156">Entrez le nom de votre deuxième serveur proxy d'application web (Tableau M - élément 7 - colonne Nom de machine virtuelle), cliquez sur **Ajouter**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-156">Type your second web application proxy server's name (Table M - Item 7 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
23. <span data-ttu-id="e77ff-157">Sur la page **Informations d'identification d'administrateur de domaine**, saisissez le nom d'utilisateur et le mot de passe d'un compte d'administrateur de domaine, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-157">On the **Domain Administrator credentials** page, type the user name and password of a domain administrator account, and then click **Next**.</span></span>
    
24. <span data-ttu-id="e77ff-158">Sur la page **Compte de service AD DS**, saisissez le nom d'utilisateur et le mot de passe d'un compte d'administrateur d'entreprise, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-158">On the **AD FS service account** page, type the user name and password of an enterprise administrator account, and then click **Next**.</span></span>
    
25. <span data-ttu-id="e77ff-159">Sur la page **Domaine Azure AD**, sous **Domaine**, sélectionnez le nom de domaine DNS de votre organisation, puis sur cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-159">On the **Azure AD Domain** page, in **Domain**, select your organization's DNS domain name, and then click **Next**.</span></span>
    
26. <span data-ttu-id="e77ff-160">Sur la page **Prêt à configurer**, cliquez sur **Installer**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-160">On the **Ready to configure** page, click **Install**.</span></span>
    
27. <span data-ttu-id="e77ff-p105">Sur la page **Installation terminée**, cliquez sur **Vérifier**. Vous devriez voir deux messages vous indiquant que les configurations intranet et Internet ont été vérifiées.</span><span class="sxs-lookup"><span data-stu-id="e77ff-p105">On the **Installation complete** page, click **Verify**. You should see two messages indicating that both the intranet and Internet configuration was successfully verified.</span></span>
    
  - <span data-ttu-id="e77ff-163">Le message intranet doit répertorier l’adresse IP privée de l’équilibreur de charge Azure interne pour vos serveurs AD FS.</span><span class="sxs-lookup"><span data-stu-id="e77ff-163">The intranet message should list the private IP address of your Azure internal load balancer for your AD FS servers.</span></span>
    
  - <span data-ttu-id="e77ff-164">Le message Internet doit répertorier l’adresse IP publique de l’équilibreur de charge Azure connecté à Internet pour vos serveurs proxy d’application web.</span><span class="sxs-lookup"><span data-stu-id="e77ff-164">The Internet message should list the public IP address of your Azure Internet-facing load balancer for your web application proxy servers.</span></span>
    
28. <span data-ttu-id="e77ff-165">Sur la page **Installation terminée**, cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="e77ff-165">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="e77ff-166">Voici la configuration finale, avec les noms d’espace réservé pour les serveurs.</span><span class="sxs-lookup"><span data-stu-id="e77ff-166">Here is the final configuration, with placeholder names for the servers.</span></span>
  
<span data-ttu-id="e77ff-167">**Phase 5 : Configuration finale d'une infrastructure d'authentification fédérée haute disponibilité dans Azure**</span><span class="sxs-lookup"><span data-stu-id="e77ff-167">**Phase 5: The final configuration of a high availability federated authentication infrastructure in Azure**</span></span>

![Configuration finale de l’infrastructure d’authentification fédérée haute disponibilité Office 365 dans Azure](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="e77ff-169">Votre infrastructure d’authentification fédérée haute disponibilité pour Office 365 dans Azure est prête.</span><span class="sxs-lookup"><span data-stu-id="e77ff-169">Your high availability federated authentication infrastructure for Office 365 in Azure is complete.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e77ff-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e77ff-170">See Also</span></span>

[<span data-ttu-id="e77ff-171">Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure</span><span class="sxs-lookup"><span data-stu-id="e77ff-171">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="e77ff-172">Identité fédérée pour votre environnement de développement/test Office 365</span><span class="sxs-lookup"><span data-stu-id="e77ff-172">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="e77ff-173">Adoption du cloud et solutions hybrides</span><span class="sxs-lookup"><span data-stu-id="e77ff-173">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="e77ff-174">Identité fédérée pour Office 365</span><span class="sxs-lookup"><span data-stu-id="e77ff-174">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


