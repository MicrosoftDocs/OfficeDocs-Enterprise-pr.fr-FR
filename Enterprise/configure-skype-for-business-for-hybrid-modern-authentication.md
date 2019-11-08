---
title: Comment configurer Skype Entreprise en local pour utiliser l’authentification moderne hybride
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/4/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
description: L’authentification moderne est une méthode de gestion des identités qui offre une authentification et une autorisation utilisateur plus sécurisées, est disponible pour Skype entreprise Server en local et Exchange Server en local, ainsi qu’hybrides Skype entreprise mixtes.
ms.openlocfilehash: 17079ab5e47e2e739780d3df4a9a523edccda14f
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38029128"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="ae145-103">Comment configurer Skype Entreprise en local pour utiliser l’authentification moderne hybride</span><span class="sxs-lookup"><span data-stu-id="ae145-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="ae145-104">L’authentification moderne est une méthode de gestion des identités qui offre une authentification et une autorisation utilisateur plus sécurisées, est disponible pour Skype entreprise Server en local et Exchange Server en local, ainsi qu’hybrides Skype entreprise mixtes.</span><span class="sxs-lookup"><span data-stu-id="ae145-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="ae145-105">**Important** Souhaitez-vous en savoir plus sur l’authentification moderne (MA) et pourquoi choisir de l’utiliser dans votre entreprise ou organisation ?</span><span class="sxs-lookup"><span data-stu-id="ae145-105">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="ae145-106">Pour obtenir une vue d’ensemble, consultez [ce document](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="ae145-106">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="ae145-107">Si vous avez besoin de savoir quelles topologies Skype entreprise sont prises en charge avec MA, il est documenté ici.</span><span class="sxs-lookup"><span data-stu-id="ae145-107">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="ae145-108">**Avant de commencer**, j’appelle :</span><span class="sxs-lookup"><span data-stu-id="ae145-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="ae145-109">MA de \> l’authentification moderne</span><span class="sxs-lookup"><span data-stu-id="ae145-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="ae145-110">HMA d’authentification \> moderne hybride</span><span class="sxs-lookup"><span data-stu-id="ae145-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="ae145-111">Exch Exchange sur site \></span><span class="sxs-lookup"><span data-stu-id="ae145-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="ae145-112">Exchange Online \> exo</span><span class="sxs-lookup"><span data-stu-id="ae145-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="ae145-113">SFB locale \> Skype entreprise</span><span class="sxs-lookup"><span data-stu-id="ae145-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="ae145-114">et Skype entreprise Online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="ae145-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="ae145-115">En outre, \* si un graphique de cet article a un objet « grisé » ou « grisé », cela signifie que l’élément affiché en gris **n’est pas** inclus dans la configuration propre à ma.</span><span class="sxs-lookup"><span data-stu-id="ae145-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="ae145-116">Lire le résumé</span><span class="sxs-lookup"><span data-stu-id="ae145-116">Read the summary</span></span>

<span data-ttu-id="ae145-117">Cette synthèse fait bouillir le processus en des étapes qui pourraient autrement être perdues pendant l’exécution, et est utile pour une liste de vérification globale pour assurer le suivi de l’endroit où vous vous trouvez dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ae145-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="ae145-118">Tout d’abord, assurez-vous que vous remplissez toutes les conditions préalables.</span><span class="sxs-lookup"><span data-stu-id="ae145-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="ae145-119">Étant donné que de nombreuses **conditions préalables** sont communes pour Skype entreprise et Exchange, [consultez l’article de vue d’ensemble pour votre liste de vérification pré-req](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae145-119">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="ae145-120">Procédez comme suit *avant* de commencer l’une des étapes décrites dans cet article.</span><span class="sxs-lookup"><span data-stu-id="ae145-120">Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="ae145-121">Collectez les informations propres à la HMA dont vous aurez besoin dans un fichier, ou OneNote.</span><span class="sxs-lookup"><span data-stu-id="ae145-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="ae145-122">Activez l’authentification moderne pour EXO (si elle n’est pas déjà activée).</span><span class="sxs-lookup"><span data-stu-id="ae145-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="ae145-123">Activez l’authentification moderne pour SFBO (si elle n’est pas déjà activée).</span><span class="sxs-lookup"><span data-stu-id="ae145-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="ae145-124">Activez l’authentification moderne hybride pour Exchange sur site.</span><span class="sxs-lookup"><span data-stu-id="ae145-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="ae145-125">Activez l’authentification moderne hybride pour Skype entreprise en local.</span><span class="sxs-lookup"><span data-stu-id="ae145-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="ae145-126">Remarque ces étapes activent MA pour SFB, SFBO, EXCH et EXO, autrement dit, tous les produits pouvant participer à une configuration HMA de SFB et SFBO (y compris les dépendances de EXCH/EXO).</span><span class="sxs-lookup"><span data-stu-id="ae145-126">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="ae145-127">En d’autres termes, si vos utilisateurs sont hébergés dans ou si des boîtes aux lettres sont créées dans n’importe quelle partie de l’environnement hybride (EXO + SFBO, EXO + SFB, EXCH + SFBO ou EXCH + SFB), votre produit fini se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="ae145-127">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Une topologie de 6 Skype entreprise HMA mixte est associée aux quatre emplacements possibles.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="ae145-129">Comme vous pouvez le constater, il y a quatre emplacements différents pour activer MA !</span><span class="sxs-lookup"><span data-stu-id="ae145-129">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="ae145-130">Pour une expérience utilisateur optimale, nous vous recommandons d’activer MA dans les quatre emplacements.</span><span class="sxs-lookup"><span data-stu-id="ae145-130">For the best user experience we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="ae145-131">Si vous ne pouvez pas activer l’agent de session sur tous ces emplacements, ajustez les étapes de façon à activer MA uniquement aux emplacements nécessaires pour votre environnement.</span><span class="sxs-lookup"><span data-stu-id="ae145-131">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="ae145-132">Consultez la rubrique relative à la [prise en charge de Skype entreprise avec ma](https://technet.microsoft.com/library/mt803262.aspx) pour les topologies prises en charge.</span><span class="sxs-lookup"><span data-stu-id="ae145-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="ae145-133">**Important** Vérifiez que vous avez rempli toutes les conditions préalables avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="ae145-133">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="ae145-134">Ces informations s’affichent [ici](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae145-134">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="ae145-135">Collecter toutes les informations propres à la HMA</span><span class="sxs-lookup"><span data-stu-id="ae145-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="ae145-136">Une fois que vous avez vérifié que vous répondez aux [conditions préalables](hybrid-modern-auth-overview.md) pour utiliser l’authentification moderne (voir la remarque ci-dessus), vous devez créer un fichier pour conserver les informations dont vous aurez besoin pour configurer la mémoire haute définition dans les étapes à venir.</span><span class="sxs-lookup"><span data-stu-id="ae145-136">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="ae145-137">Exemples utilisés dans cet article :</span><span class="sxs-lookup"><span data-stu-id="ae145-137">Examples used in this article:</span></span> 
  
- <span data-ttu-id="ae145-138">**Domaine SIP/SMTP**</span><span class="sxs-lookup"><span data-stu-id="ae145-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="ae145-139">Ex.</span><span class="sxs-lookup"><span data-stu-id="ae145-139">Ex.</span></span> <span data-ttu-id="ae145-140">contoso.com (est fédéré avec Office 365)</span><span class="sxs-lookup"><span data-stu-id="ae145-140">contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="ae145-141">**ID client**</span><span class="sxs-lookup"><span data-stu-id="ae145-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="ae145-142">GUID qui représente votre client Office 365 (à la connexion de contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="ae145-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="ae145-143">**URL du service Web SFB 2015 CU5**</span><span class="sxs-lookup"><span data-stu-id="ae145-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="ae145-144">Vous aurez besoin d’une URL de service Web interne et externe pour tous les pools SfB 2015 déployés.</span><span class="sxs-lookup"><span data-stu-id="ae145-144">You will need internal and external web service URL's for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="ae145-145">Pour obtenir ces informations, exécutez la commande suivante à partir de Skype entreprise Management Shell :</span><span class="sxs-lookup"><span data-stu-id="ae145-145">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="ae145-146">Ex.</span><span class="sxs-lookup"><span data-stu-id="ae145-146">Ex.</span></span> <span data-ttu-id="ae145-147">Internehttps://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="ae145-147">Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="ae145-148">Ex.</span><span class="sxs-lookup"><span data-stu-id="ae145-148">Ex.</span></span> <span data-ttu-id="ae145-149">Façonhttps://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="ae145-149">External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="ae145-150">Si vous utilisez un serveur Standard Edition, l’URL interne sera vide.</span><span class="sxs-lookup"><span data-stu-id="ae145-150">If you are using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="ae145-151">Dans ce cas, utilisez le nom de domaine complet du pool pour l’URL interne.</span><span class="sxs-lookup"><span data-stu-id="ae145-151">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="ae145-152">Activer l’authentification moderne pour EXO</span><span class="sxs-lookup"><span data-stu-id="ae145-152">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="ae145-153">Suivez les instructions ci-dessous : [Exchange Online : comment activer votre client pour l’authentification moderne.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="ae145-153">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="ae145-154">Activer l’authentification moderne pour SFBO</span><span class="sxs-lookup"><span data-stu-id="ae145-154">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="ae145-155">Suivez les instructions ci-dessous : [Skype entreprise Online : activez votre client pour l’authentification moderne](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="ae145-155">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="ae145-156">Activer l’authentification moderne hybride pour Exchange sur site</span><span class="sxs-lookup"><span data-stu-id="ae145-156">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="ae145-157">Suivez les instructions ci-dessous : [procédure de configuration d’Exchange Server local pour utiliser l’authentification moderne hybride](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ae145-157">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="ae145-158">Activer l’authentification moderne hybride pour Skype entreprise en local</span><span class="sxs-lookup"><span data-stu-id="ae145-158">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="ae145-159">Ajouter des URL de service Web sur site en tant que SPN dans Azure AD</span><span class="sxs-lookup"><span data-stu-id="ae145-159">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="ae145-160">À présent, vous devez exécuter des commandes pour ajouter les URL (collectées précédemment) en tant que principaux de service dans SFBO.</span><span class="sxs-lookup"><span data-stu-id="ae145-160">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="ae145-161">**Note** Les noms de principaux du service (SPN) identifient les services Web et les associent à un principal de sécurité (par exemple, un nom de compte ou un groupe) afin que le service puisse agir au nom d’un utilisateur autorisé.</span><span class="sxs-lookup"><span data-stu-id="ae145-161">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="ae145-162">Les clients qui s’authentifient sur un serveur utilisent les informations contenues dans les noms principaux de client.</span><span class="sxs-lookup"><span data-stu-id="ae145-162">Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="ae145-163">Tout d’abord, connectez-vous à AAD en utilisant [ces instructions](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).</span><span class="sxs-lookup"><span data-stu-id="ae145-163">First, connect to AAD with [these instructions](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>
    
2. <span data-ttu-id="ae145-164">Exécutez cette commande, en local, pour obtenir la liste des URL de service Web SFB.</span><span class="sxs-lookup"><span data-stu-id="ae145-164">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="ae145-165">Notez que le AppPrincipalId commence par `00000004`.</span><span class="sxs-lookup"><span data-stu-id="ae145-165">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="ae145-166">Cela correspond à Skype entreprise online.</span><span class="sxs-lookup"><span data-stu-id="ae145-166">This corresponds to Skype for Business Online.</span></span>
    
   <span data-ttu-id="ae145-167">Notez (et capture d’écran pour une comparaison ultérieure) la sortie de cette commande, qui inclura une URL SE et WS, mais qui se composent essentiellement `00000004-0000-0ff1-ce00-000000000000/`de noms principaux de service qui commencent par.</span><span class="sxs-lookup"><span data-stu-id="ae145-167">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>
    
```
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```
    
3. <span data-ttu-id="ae145-168">Si les URL SFB internes **ou** externes de l’organisation locale sont manquantes (par exemple https://lyncwebint01.contoso.com , https://lyncwebext01.contoso.com) nous devons ajouter ces enregistrements spécifiques à cette liste.</span><span class="sxs-lookup"><span data-stu-id="ae145-168">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="ae145-169">N’oubliez pas de remplacer *les exemples d’URL* ci-dessous par vos URL réelles dans la commande Add Commands !</span><span class="sxs-lookup"><span data-stu-id="ae145-169">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
  
```  
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="ae145-170">Vérifiez que vos nouveaux enregistrements ont été ajoutés en exécutant de nouveau la commande Get-MsolServicePrincipal à partir de l’étape 2 et en examinant la sortie.</span><span class="sxs-lookup"><span data-stu-id="ae145-170">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="ae145-171">Comparez la liste/capture d’écran de l’avant à la nouvelle liste de noms principaux de vente (vous pouvez également créer une capture d’écran de la nouvelle liste pour vos enregistrements).</span><span class="sxs-lookup"><span data-stu-id="ae145-171">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="ae145-172">Si vous avez réussi, vous verrez les deux nouvelles URL dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ae145-172">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="ae145-173">À l’aide de notre exemple, la liste des SPN inclut désormais les URL https://lyncwebint01.contoso.com spécifiques https://lyncwebext01.contoso.com/et.</span><span class="sxs-lookup"><span data-stu-id="ae145-173">Going by our example, the list of SPNs will now include the specific URLs https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="ae145-174">Créer l’objet serveur d’authentification EvoSTS</span><span class="sxs-lookup"><span data-stu-id="ae145-174">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="ae145-175">Exécutez la commande suivante dans Skype entreprise Management Shell.</span><span class="sxs-lookup"><span data-stu-id="ae145-175">Run the following command in the Skype for Business Management Shell.</span></span>
  
```
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="ae145-176">Activer l’authentification moderne hybride</span><span class="sxs-lookup"><span data-stu-id="ae145-176">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="ae145-177">Il s’agit de l’étape qui active l’agent de session.</span><span class="sxs-lookup"><span data-stu-id="ae145-177">This is the step that actually turns MA on.</span></span> <span data-ttu-id="ae145-178">Toutes les étapes précédentes peuvent être exécutées à l’avance sans modifier le flux d’authentification du client.</span><span class="sxs-lookup"><span data-stu-id="ae145-178">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="ae145-179">Lorsque vous êtes prêt à modifier le flux d’authentification, exécutez la commande suivante dans Skype for Business Management Shell.</span><span class="sxs-lookup"><span data-stu-id="ae145-179">When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
```
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```
    
## <a name="verify"></a><span data-ttu-id="ae145-180">Vérifié</span><span class="sxs-lookup"><span data-stu-id="ae145-180">Verify</span></span>

<span data-ttu-id="ae145-181">Une fois que vous activez HMA, la prochaine connexion d’un client utilisera le nouveau flux d’authentification.</span><span class="sxs-lookup"><span data-stu-id="ae145-181">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="ae145-182">Notez que l’activation de la mémoire HMA ne déclenche pas une nouvelle authentification pour un client.</span><span class="sxs-lookup"><span data-stu-id="ae145-182">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="ae145-183">Les clients se ré-authentifient en fonction de la durée de vie des jetons d’authentification et/ou des certificats dont ils disposent.</span><span class="sxs-lookup"><span data-stu-id="ae145-183">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="ae145-184">Pour tester que la haute-dernière fonctionne après l’avoir activée, déconnectez-vous d’un client Windows SFB de test et veillez à cliquer sur « supprimer mes informations d’identification ».</span><span class="sxs-lookup"><span data-stu-id="ae145-184">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="ae145-185">Reconnectez-vous.</span><span class="sxs-lookup"><span data-stu-id="ae145-185">Sign in again.</span></span> <span data-ttu-id="ae145-186">Le client doit maintenant utiliser le flux d’authentification moderne et votre connexion inclut désormais une invite **Office 365** pour un compte professionnel ou scolaire, vu juste avant que le client ne contacte le serveur et vous connecte.</span><span class="sxs-lookup"><span data-stu-id="ae145-186">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="ae145-187">Vous devez également vérifier les « informations de configuration » pour les clients Skype entreprise pour une « autorité OAuth ».</span><span class="sxs-lookup"><span data-stu-id="ae145-187">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="ae145-188">Pour effectuer cette action sur votre ordinateur client, maintenez la touche CTRL enfoncée simultanément en cliquant avec le bouton droit sur l’icône Skype entreprise dans le bac de notification Windows.</span><span class="sxs-lookup"><span data-stu-id="ae145-188">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="ae145-189">Cliquez sur informations de configuration dans le menu qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ae145-189">Click Configuration Information in the menu that appears.</span></span> <span data-ttu-id="ae145-190">Dans la fenêtre « informations de configuration de Skype entreprise » qui s’affichent sur le bureau, recherchez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ae145-190">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![Les informations de configuration d’un client Skype entreprise qui utilisent l’authentification moderne indiquent une URL d’autorisation OAUTH Lync https://login.windows.net/common/oauth2/authorizeet EWS de.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="ae145-192">Vous devez également maintenir la touche CTRL enfoncée en même temps que vous cliquez avec le bouton droit sur l’icône du client Outlook (également dans le bac Windows notifications) et cliquez sur « état de la connexion ».</span><span class="sxs-lookup"><span data-stu-id="ae145-192">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="ae145-193">Recherchez l’adresse SMTP du client par rapport à un type d’authentification « porteur\*», qui représente le jeton du porteur utilisé dans OAuth.</span><span class="sxs-lookup"><span data-stu-id="ae145-193">Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="ae145-194">Articles connexes</span><span class="sxs-lookup"><span data-stu-id="ae145-194">Related articles</span></span>

<span data-ttu-id="ae145-195">[Revenez à la vue d’ensemble de l’authentification moderne](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="ae145-195">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="ae145-196">Avez-vous besoin de savoir comment utiliser l’authentification moderne (ADAL) pour vos clients Skype entreprise ?</span><span class="sxs-lookup"><span data-stu-id="ae145-196">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="ae145-197">Nous avons les étapes à suivre [ici](https://technet.microsoft.com/library/mt710548.aspx).</span><span class="sxs-lookup"><span data-stu-id="ae145-197">We've got steps [here](https://technet.microsoft.com/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="ae145-198">Souhaitez-vous lire ces étapes telles qu’elles apparaissent pour Exchange Server, en local, sans SFB ?</span><span class="sxs-lookup"><span data-stu-id="ae145-198">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB?</span></span> <span data-ttu-id="ae145-199">Ces étapes sont disponibles ici.</span><span class="sxs-lookup"><span data-stu-id="ae145-199">Those steps are available here.</span></span>
  

