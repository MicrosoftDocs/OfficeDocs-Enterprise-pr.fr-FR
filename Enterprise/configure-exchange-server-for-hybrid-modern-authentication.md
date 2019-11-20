---
title: Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: L’authentification moderne hybride (HMA), est une méthode de gestion des identités qui offre une authentification et une autorisation utilisateur plus sécurisées, et est disponible pour les déploiements hybrides Exchange Server locaux.
ms.openlocfilehash: 44061a8b75a07283c36d02812488441d40f9c9c3
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746217"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="f6f55-103">Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride</span><span class="sxs-lookup"><span data-stu-id="f6f55-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="f6f55-104">*Cet article s’applique à la fois à Office 365 entreprise et à Microsoft 365 entreprise.*</span><span class="sxs-lookup"><span data-stu-id="f6f55-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="f6f55-105">L’authentification moderne hybride (HMA), est une méthode de gestion des identités qui offre une authentification et une autorisation utilisateur plus sécurisées, et est disponible pour les déploiements hybrides Exchange Server locaux.</span><span class="sxs-lookup"><span data-stu-id="f6f55-105">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="f6f55-106">Pour info</span><span class="sxs-lookup"><span data-stu-id="f6f55-106">FYI</span></span>

<span data-ttu-id="f6f55-107">Avant de commencer, j’appelle :</span><span class="sxs-lookup"><span data-stu-id="f6f55-107">Before we begin, I call:</span></span>
  
- <span data-ttu-id="f6f55-108">HMA d’authentification \> moderne hybride</span><span class="sxs-lookup"><span data-stu-id="f6f55-108">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="f6f55-109">Exch Exchange sur site \></span><span class="sxs-lookup"><span data-stu-id="f6f55-109">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="f6f55-110">Exchange Online \> exo</span><span class="sxs-lookup"><span data-stu-id="f6f55-110">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="f6f55-111">En outre, *si un graphisme de cet article a un objet « grisé » ou « grisé », cela signifie que l’élément affiché en gris n’est pas inclus dans la configuration spécifique* à la HMA.</span><span class="sxs-lookup"><span data-stu-id="f6f55-111">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="f6f55-112">Activation de l’authentification moderne hybride</span><span class="sxs-lookup"><span data-stu-id="f6f55-112">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="f6f55-113">L’activation de la haute-HMA sur signifie :</span><span class="sxs-lookup"><span data-stu-id="f6f55-113">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="f6f55-114">Assurez-vous que vous remplissez les configuration requise avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="f6f55-114">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="f6f55-115">Étant donné que de nombreux **éléments prérequis** sont communs à la fois à Skype entreprise et à Exchange, une [vue d’ensemble de l’authentification moderne hybride et des prérequis pour l’utiliser avec des serveurs Skype entreprise et Exchange locaux](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f6f55-115">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="f6f55-116">Procédez comme suit avant de commencer l’une des étapes décrites dans cet article.</span><span class="sxs-lookup"><span data-stu-id="f6f55-116">Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="f6f55-117">Ajout d’URL de service Web sur site sous forme de noms principaux de service (SPN) dans Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f6f55-117">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="f6f55-118">Vérifier que tous les répertoires virtuels sont activés pour HMA</span><span class="sxs-lookup"><span data-stu-id="f6f55-118">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="f6f55-119">Vérification de l’objet serveur d’authentification EvoSTS</span><span class="sxs-lookup"><span data-stu-id="f6f55-119">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="f6f55-120">Activation de la haute HMA dans EXCH.</span><span class="sxs-lookup"><span data-stu-id="f6f55-120">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="f6f55-121">**Note** Votre version de l’agent de gestion du support Office est-elle ?</span><span class="sxs-lookup"><span data-stu-id="f6f55-121">**Note** Does your version of Office support MA?</span></span> <span data-ttu-id="f6f55-122">Découvrez [le fonctionnement de l’authentification moderne pour les applications clientes office 2013 et office 2016](modern-auth-for-office-2013-and-2016.md).</span><span class="sxs-lookup"><span data-stu-id="f6f55-122">See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="f6f55-123">Vérifier que vous remplissez toutes les conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f6f55-123">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="f6f55-124">Étant donné que de nombreuses conditions préalables sont communes à la fois pour Skype entreprise et Exchange, consultez la [rubrique vue d’ensemble de l’authentification moderne hybride et conditions préalables pour l’utiliser avec des serveurs Skype entreprise et Exchange locaux](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f6f55-124">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="f6f55-125">Procédez comme suit *avant* de commencer l’une des étapes décrites dans cet article.</span><span class="sxs-lookup"><span data-stu-id="f6f55-125">Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="f6f55-126">Ajouter des URL de service Web sur site en tant que SPN dans Azure AD</span><span class="sxs-lookup"><span data-stu-id="f6f55-126">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="f6f55-127">Exécutez les commandes qui affectent vos URL de service Web local en tant que SPN Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f6f55-127">Run the commands that assign your on-premises web service URLs as Azure AD SPNs.</span></span> <span data-ttu-id="f6f55-128">Les SPN sont utilisés par les ordinateurs clients et les appareils au cours de l’authentification et de l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f6f55-128">SPNs are used by client machines and devices during authentication and authorization.</span></span> <span data-ttu-id="f6f55-129">Toutes les URL pouvant être utilisées pour se connecter à Azure Active Directory (AAD) doivent être enregistrées dans AAD (cela inclut les espaces de noms internes et externes).</span><span class="sxs-lookup"><span data-stu-id="f6f55-129">All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="f6f55-130">Tout d’abord, Rassemblez toutes les URL que vous devez ajouter dans AAD.</span><span class="sxs-lookup"><span data-stu-id="f6f55-130">First, gather all the URLs that you need to add in AAD.</span></span> <span data-ttu-id="f6f55-131">Exécutez ces commandes en local :</span><span class="sxs-lookup"><span data-stu-id="f6f55-131">Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="f6f55-132">Assurez-vous que les URL auxquelles les clients peuvent se connecter sont répertoriées en tant que noms principaux du service HTTPs dans AAD.</span><span class="sxs-lookup"><span data-stu-id="f6f55-132">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="f6f55-133">Tout d’abord, connectez-vous à AAD en utilisant [ces instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="f6f55-133">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="f6f55-134">**Note** Vous devez utiliser l’option Connect-MsolService à partir de cette page pour pouvoir utiliser la commande ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="f6f55-134">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="f6f55-135">Pour vos URL liées à Exchange, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f6f55-135">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="f6f55-136">Prenez note de (et de capture d’écran pour une comparaison ultérieure) la sortie de cette commande, qui doit inclure une URL https:// *autodiscover.yourdomain.com* et https:// *mail.yourdomain.com* , mais qui se composent principalement de noms principaux de contenu commençant par 00000002-0000-0ff1-CE00-000000000000/.</span><span class="sxs-lookup"><span data-stu-id="f6f55-136">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/.</span></span> <span data-ttu-id="f6f55-137">S’il existe des URL https://de votre local qui ne sont pas disponibles, nous devons ajouter ces enregistrements spécifiques à cette liste.</span><span class="sxs-lookup"><span data-stu-id="f6f55-137">If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="f6f55-138">Si vos enregistrements MAPI/HTTP, EWS, ActiveSync, OAB et Autodiscover internes et externes ne s’affichent pas dans cette liste, vous devez les ajouter à l’aide de la commande ci-`mail.corp.contoso.com`dessous (les`owa.contoso.com`exemples d’URL sont « » et « », mais vous pouvez **remplacer les URL d’exemple par les vôtres** ) :</span><span class="sxs-lookup"><span data-stu-id="f6f55-138">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="f6f55-139">Vérifiez que vos nouveaux enregistrements ont été ajoutés en exécutant de nouveau la commande Get-MsolServicePrincipal à partir de l’étape 2 et en examinant la sortie.</span><span class="sxs-lookup"><span data-stu-id="f6f55-139">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="f6f55-140">Comparez la liste/capture d’écran de l’avant à la nouvelle liste de noms principaux de vente (vous pouvez également créer une capture d’écran de la nouvelle liste pour vos enregistrements).</span><span class="sxs-lookup"><span data-stu-id="f6f55-140">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="f6f55-141">Si vous avez réussi, vous verrez les deux nouvelles URL dans la liste.</span><span class="sxs-lookup"><span data-stu-id="f6f55-141">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="f6f55-142">À l’aide de notre exemple, la liste des SPN inclut désormais les URL `https://mail.corp.contoso.com` spécifiques `https://owa.contoso.com`et.</span><span class="sxs-lookup"><span data-stu-id="f6f55-142">Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="f6f55-143">Vérifier que les répertoires virtuels sont correctement configurés</span><span class="sxs-lookup"><span data-stu-id="f6f55-143">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="f6f55-144">Maintenant, vérifiez que OAuth est correctement activé dans Exchange sur tous les répertoires virtuels qu’Outlook peut utiliser en exécutant les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f6f55-144">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="f6f55-145">Vérifiez la sortie pour vous assurer que le protocole **OAuth** est activé sur chacune de ces VDirs, il ressemblera à ceci (et la clé à examiner est « OAuth »);</span><span class="sxs-lookup"><span data-stu-id="f6f55-145">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
<span data-ttu-id="f6f55-146">Si OAuth est absent de n’importe quel serveur et de l’un des quatre répertoires virtuels, vous devez l’ajouter à l’aide des commandes appropriées avant de poursuivre.</span><span class="sxs-lookup"><span data-stu-id="f6f55-146">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="f6f55-147">Vérifiez que l’objet serveur d’authentification EvoSTS est présent.</span><span class="sxs-lookup"><span data-stu-id="f6f55-147">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="f6f55-148">Revenez à l’environnement de commande Exchange Management Shell pour cette dernière commande.</span><span class="sxs-lookup"><span data-stu-id="f6f55-148">Return to the on-premises Exchange Management Shell for this last command.</span></span> <span data-ttu-id="f6f55-149">À présent, vous pouvez vérifier que votre site local dispose d’une entrée pour le fournisseur d’authentification evoSTS :</span><span class="sxs-lookup"><span data-stu-id="f6f55-149">Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="f6f55-150">Votre sortie doit afficher un AuthServer du nom EvoSts et l’État « Enabled » doit être true.</span><span class="sxs-lookup"><span data-stu-id="f6f55-150">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True.</span></span> <span data-ttu-id="f6f55-151">Si ce n’est pas le cas, vous devez télécharger et exécuter la version la plus récente de l’Assistant Configuration hybride.</span><span class="sxs-lookup"><span data-stu-id="f6f55-151">If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="f6f55-152">**Important** Si vous utilisez Exchange 2010 dans votre environnement, le fournisseur d’authentification EvoSTS n’est pas créé.</span><span class="sxs-lookup"><span data-stu-id="f6f55-152">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="f6f55-153">Activer la HMA</span><span class="sxs-lookup"><span data-stu-id="f6f55-153">Enable HMA</span></span>

<span data-ttu-id="f6f55-154">Exécutez la commande suivante dans l’environnement de commande Exchange Management Shell :</span><span class="sxs-lookup"><span data-stu-id="f6f55-154">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="f6f55-155">Vérifié</span><span class="sxs-lookup"><span data-stu-id="f6f55-155">Verify</span></span>

<span data-ttu-id="f6f55-156">Une fois que vous activez HMA, la prochaine connexion d’un client utilisera le nouveau flux d’authentification.</span><span class="sxs-lookup"><span data-stu-id="f6f55-156">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="f6f55-157">Notez que l’activation de la mémoire HMA ne déclenche pas une nouvelle authentification pour un client.</span><span class="sxs-lookup"><span data-stu-id="f6f55-157">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="f6f55-158">Les clients se ré-authentifient en fonction de la durée de vie des jetons d’authentification et/ou des certificats dont ils disposent.</span><span class="sxs-lookup"><span data-stu-id="f6f55-158">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="f6f55-159">Vous devez également maintenir la touche CTRL enfoncée en même temps que vous cliquez avec le bouton droit sur l’icône du client Outlook (également dans le bac Windows notifications) et cliquez sur « état de la connexion ».</span><span class="sxs-lookup"><span data-stu-id="f6f55-159">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="f6f55-160">Recherchez l’adresse SMTP du client par rapport à un « type d’authentification » de «\*porteur », qui représente le jeton du porteur utilisé dans OAuth.</span><span class="sxs-lookup"><span data-stu-id="f6f55-160">Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="f6f55-161">**Note** Vous avez besoin de configurer Skype entreprise avec HMA ?</span><span class="sxs-lookup"><span data-stu-id="f6f55-161">**Note** Need to configure Skype for Business with HMA?</span></span> <span data-ttu-id="f6f55-162">Vous aurez besoin de deux articles : un qui répertorie les [topologies prises en charge](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)et un autre qui vous montre [Comment effectuer la configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f6f55-162">You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="f6f55-163">Sujets associés</span><span class="sxs-lookup"><span data-stu-id="f6f55-163">Related topics</span></span>

[<span data-ttu-id="f6f55-164">Vue d’ensemble de l’authentification moderne hybride et conditions préalables à son utilisation avec des serveurs Skype entreprise et Exchange locaux</span><span class="sxs-lookup"><span data-stu-id="f6f55-164">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

