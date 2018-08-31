---
title: Comment configurer Skype Entreprise en local pour utiliser l’authentification moderne hybride
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: Authentification moderne, est une méthode de gestion des identités qui offre le plus sécurisée authentification et autorisation utilisateur, n’est disponible pour Skype pour Business server locaux et Exchange server locale, ainsi que-domaine fractionné Skype pour hybrides Business.
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540675"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="0ebfd-103">Comment configurer Skype Entreprise en local pour utiliser l’authentification moderne hybride</span><span class="sxs-lookup"><span data-stu-id="0ebfd-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="0ebfd-104">Authentification moderne, est une méthode de gestion des identités qui offre le plus sécurisée authentification et autorisation utilisateur, n’est disponible pour Skype pour Business server locaux et Exchange server locale, ainsi que-domaine fractionné Skype pour hybrides Business.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="0ebfd-p101">**Important** Vous souhaitez en savoir plus sur l’authentification moderne (MA) et pourquoi vous pouvez utiliser dans votre société ou organisation ? Vérifiez [ce document](hybrid-modern-auth-overview.md) pour une vue d’ensemble. Si vous avez besoin de savoir quels Skype pour les topologies d’entreprise sont pris en charge par MA, qui est décrite ici !</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p101">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization? Check [this document](hybrid-modern-auth-overview.md) for an overview. If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="0ebfd-108">**Avant de commencer**, appeler :</span><span class="sxs-lookup"><span data-stu-id="0ebfd-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="0ebfd-109">Authentification moderne \> MA</span><span class="sxs-lookup"><span data-stu-id="0ebfd-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="0ebfd-110">Authentification moderne hybride \> zone</span><span class="sxs-lookup"><span data-stu-id="0ebfd-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="0ebfd-111">Exchange local \> EXCH</span><span class="sxs-lookup"><span data-stu-id="0ebfd-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="0ebfd-112">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="0ebfd-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="0ebfd-113">Skype pour Business local \> SFB</span><span class="sxs-lookup"><span data-stu-id="0ebfd-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="0ebfd-114">et Skype pour les entreprises en ligne \> SFBO</span><span class="sxs-lookup"><span data-stu-id="0ebfd-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="0ebfd-115">En outre, \* si un graphique dans cet article dispose d’un objet qui a « grisé » ou « estompé » qui signifie que l’élément indiqué dans gris **n’est pas** inclus dans une configuration spécifique à l’agent de gestion.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="0ebfd-116">Lisez le résumé</span><span class="sxs-lookup"><span data-stu-id="0ebfd-116">Read the summary</span></span>

<span data-ttu-id="0ebfd-117">Ce résumé limite le processus en étapes qui pourraient sinon perdues lors de l’exécution et sont adapté à une liste de contrôle globale d’effectuer le suivi d’où vous vous trouvez dans le processus.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="0ebfd-118">Tout d’abord, assurez-vous que vous disposez de tous les éléments prérequis.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="0ebfd-p102">Depuis de nombreuses **conditions préalables** sont courants pour les deux Skype pour les entreprises et Exchange, [consultez l’article vue d’ensemble de votre liste de vérification de condition requise](hybrid-modern-auth-overview.md). Cette *avant de* commencer l’une des étapes de cet article.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p102">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="0ebfd-121">Collecter les informations spécifiques à la zone que vous avez besoin dans un fichier ou OneNote.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="0ebfd-122">Activer sur moderne Authentication for EXO (si elle n’est pas déjà activée).</span><span class="sxs-lookup"><span data-stu-id="0ebfd-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="0ebfd-123">Activer sur moderne Authentication for SFBO (si elle n’est pas déjà activée).</span><span class="sxs-lookup"><span data-stu-id="0ebfd-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="0ebfd-124">Activer l’authentification de moderne hybride pour Exchange local.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="0ebfd-125">Activer l’authentification de moderne hybride pour Skype pour l’entreprise locale.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="0ebfd-p103">Notez que ces étapes activer MA pour SFB, SFBO, EXCH et EXO--autrement dit, tous les produits qui peuvent participer à une configuration de zone de SFB et SFBO (y compris les dépendances sur EXCH/EXO). En d’autres termes, si vos utilisateurs sont hébergés dans les boîtes aux lettres créés dans n’importe quelle partie du hybride (EXO + SFBO, EXO + SFB, EXCH + SFBO, ou EXCH + SFB), votre produit fini ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p103">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO). In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![Un Skype 6 mixte pour la topologie de zone business a MA tous les emplacements possibles quatre.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="0ebfd-p104">Comme vous pouvez le constater, il existe quatre emplacements différents pour activer MA ! Pour une expérience utilisateur optimale, nous vous recommandons de que vous allumez MA dans les quatre de ces emplacements. Si vous ne pouvez pas activer MA dans tous les emplacements de ces, ajustez les étapes afin que vous allumez MA uniquement dans les emplacements qui sont nécessaires pour votre environnement.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p104">As you can see there are four different places to turn on MA! For the best user experience we recommend you turn on MA in all four of these locations. If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="0ebfd-132">Consultez la [rubrique prise en charge pour Skype pour les entreprises avec MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) pour les topologies prises en charge.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="0ebfd-p105">**Important** Vérifiez que vous avez répondu à toutes les conditions préalables avant de commencer. Vous trouverez ces informations [ici](hybrid-modern-auth-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p105">**Important** Double-check that you've met all the prerequisites before you begin. You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="0ebfd-135">Collecte toutes les informations spécifiques à la zone dont vous aurez besoin</span><span class="sxs-lookup"><span data-stu-id="0ebfd-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="0ebfd-p106">Une fois que vous avez à double contrôle que vous remplissez les [conditions requises](hybrid-modern-auth-overview.md) pour utiliser l’authentification moderne (voir la Remarque ci-dessus), vous devez créer un fichier pour contenir les informations nécessaires pour la configuration de zone dans les étapes à venir. Exemples de cet article :</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p106">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead. Examples used in this article:</span></span> 
  
- <span data-ttu-id="0ebfd-138">**Domaine SIP/SMTP**</span><span class="sxs-lookup"><span data-stu-id="0ebfd-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="0ebfd-p107">Par exemple contoso.com (est fédéré avec Office 365)</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p107">Ex. contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="0ebfd-141">**ID de client**</span><span class="sxs-lookup"><span data-stu-id="0ebfd-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="0ebfd-142">GUID qui représente votre client Office 365 (lors de la connexion de contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="0ebfd-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="0ebfd-143">**URL du Service Web SFB 2015 CU5**</span><span class="sxs-lookup"><span data-stu-id="0ebfd-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="0ebfd-p108">Vous aurez besoin d’URL du service web internes et externes pour tous les pools SfB 2015 déployés. Pour obtenir ces, exécutez ce qui suit à partir de Skype pour Business Management Shell :</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p108">You will need internal and external web service URL's for all SfB 2015 pools deployed. To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
<span data-ttu-id="0ebfd-146">Get-CsService - WebServer | Nom PoolFqdn Select-Object, InternalFqdn, | FL</span><span class="sxs-lookup"><span data-stu-id="0ebfd-146">Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL</span></span>
  
- <span data-ttu-id="0ebfd-p109">Exemple interne :https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p109">Ex. Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="0ebfd-p110">Exemple : externe :https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p110">Ex. External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="0ebfd-p111">Si vous utilisez un serveur Standard Edition server, l’URL interne est vide. Dans ce cas, utilisez le nom complet du pool de l’URL interne.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p111">If you are using a Standard Edition server, the internal URL will be blank. In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="0ebfd-153">Activer l’authentification moderne pour EXO</span><span class="sxs-lookup"><span data-stu-id="0ebfd-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="0ebfd-154">Suivez les instructions fournies ici : [Exchange Online : l’activation de votre client pour l’authentification moderne.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="0ebfd-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="0ebfd-155">Activer l’authentification moderne pour SFBO</span><span class="sxs-lookup"><span data-stu-id="0ebfd-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="0ebfd-156">Suivez les instructions fournies ici : [Skype pour Business Online : activer votre client pour l’authentification moderne](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span><span class="sxs-lookup"><span data-stu-id="0ebfd-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="0ebfd-157">Activer l’authentification de moderne hybride pour Exchange local</span><span class="sxs-lookup"><span data-stu-id="0ebfd-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="0ebfd-158">Suivez les instructions fournies ici : [comment configurer le serveur Exchange local pour utiliser l’authentification moderne hybride](configure-exchange-server-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0ebfd-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="0ebfd-159">Activer l’authentification de moderne hybride pour Skype pour l’entreprise locale</span><span class="sxs-lookup"><span data-stu-id="0ebfd-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="0ebfd-160">Ajoutez sur site web service URL en tant que des noms principaux de service dans Azure AD</span><span class="sxs-lookup"><span data-stu-id="0ebfd-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="0ebfd-161">Vous devez maintenant exécuter des commandes pour ajouter les URL (précédemment collectées) en tant qu’entités de Service dans SFBO.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="0ebfd-p112">**Remarque** Noms principaux de service (SPN) identifient les services web et les associer à une entité de sécurité (telles que le nom de compte ou groupe) afin que le service peut agir pour le compte d’un utilisateur autorisé. Clients s’authentifier sur un serveur de tirer parti des informations de noms principaux de service contenues dans.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p112">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user. Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="0ebfd-164">Tout d’abord, connectez-vous à DAS avec [ces instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="0ebfd-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span></span>
    
2. <span data-ttu-id="0ebfd-165">Exécutez cette commande sur site, pour obtenir une liste d’URL de service web SFB.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>
    
  - <span data-ttu-id="0ebfd-166">Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Sélectionnez ServicePrincipalNames - ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="0ebfd-166">Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames</span></span>
    
    <span data-ttu-id="0ebfd-p113">Notez que le AppPrincipalId commence par '00000004'. Ceci correspond à Skype pour Business Online.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p113">Notice that the AppPrincipalId begins with '00000004'. This corresponds to Skype for Business Online.</span></span>
    
    <span data-ttu-id="0ebfd-169">Prendre note des (et la capture d’écran pour comparaison ultérieure) le résultat de cette commande, qui sera inclure une SE et l’URL de WS, mais se composent principalement des noms principaux de service qui commencent par 00000004-0000-0ff1-ce00-000000000000 /.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-169">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with 00000004-0000-0ff1-ce00-000000000000/.</span></span>
    
3. <span data-ttu-id="0ebfd-170">Si interne **ou** externe SFB URL locale sont manquantes (par exemple, https://lyncwebint01.contoso.com et https://lyncwebext01.contoso.com) nous devons ajouter ces enregistrements spécifiques à cette liste.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-170">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="0ebfd-171">Veillez à remplacer *les URL de l’exemple* ci-dessous, avec vos URL réelle dans les commandes Ajouter !</span><span class="sxs-lookup"><span data-stu-id="0ebfd-171">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
    
  - <span data-ttu-id="0ebfd-172">$x = get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span><span class="sxs-lookup"><span data-stu-id="0ebfd-172">$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span></span>
    
  - <span data-ttu-id="0ebfd-173">$x.ServicePrincipalnames.Add (« *https://lyncwebint01.contoso.com/* »)</span><span class="sxs-lookup"><span data-stu-id="0ebfd-173">$x.ServicePrincipalnames.Add(" *https://lyncwebint01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="0ebfd-174">$x.ServicePrincipalnames.Add (« *https://lyncwebext01.contoso.com/* »)</span><span class="sxs-lookup"><span data-stu-id="0ebfd-174">$x.ServicePrincipalnames.Add(" *https://lyncwebext01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="0ebfd-175">Set-MSOLServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 - ServicePrincipalNames $x.ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="0ebfd-175">Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames</span></span>
    
4. <span data-ttu-id="0ebfd-p114">Vérifiez que vos nouveaux enregistrements ont été ajoutés à exécuter à nouveau la commande Get-MsolServicePrincipal à l’étape 2 et la recherche par le biais de la sortie. Comparez la liste / capture d’écran d’avant à la nouvelle liste des noms principaux de service (vous pouvez également capture d’écran de la nouvelle liste de vos enregistrements). Si vous avez réussi, vous verrez les deux nouvelles URL dans la liste. Allez dans notre exemple, la liste des noms principaux de service système incluent désormais les URL spécifiques https://lyncweb01.contoso.com et https://autodiscover.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p114">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://autodiscover.contoso.com.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="0ebfd-180">Créer l’objet de serveur d’authentification EvoSTS</span><span class="sxs-lookup"><span data-stu-id="0ebfd-180">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="0ebfd-181">Exécutez la commande suivante dans le Skype pour Business Management Shell.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-181">Run the following command in the Skype for Business Management Shell.</span></span>
  
- <span data-ttu-id="0ebfd-182">New-CsOAuthServer-Identity evoSTS - MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml AcceptSecurityIdentifierInformation - $true-Type AzureAD</span><span class="sxs-lookup"><span data-stu-id="0ebfd-182">New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD</span></span>
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="0ebfd-183">Activer l’authentification moderne hybride</span><span class="sxs-lookup"><span data-stu-id="0ebfd-183">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="0ebfd-p115">Il s’agit de l’étape qui active réellement MA. Toutes les étapes précédentes peuvent être exécutées à l’avance sans modifier le flux d’authentification client. Lorsque vous êtes prêt à modifier le flux d’authentification, exécutez cette commande dans le Skype pour Business Management Shell.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p115">This is the step that actually turns MA on. All the previous steps can be run ahead of time without changing the client authentication flow. When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
- <span data-ttu-id="0ebfd-187">Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity evoSTS</span><span class="sxs-lookup"><span data-stu-id="0ebfd-187">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS</span></span>
    
## <a name="verify"></a><span data-ttu-id="0ebfd-188">Vérifier</span><span class="sxs-lookup"><span data-stu-id="0ebfd-188">Verify</span></span>

<span data-ttu-id="0ebfd-p116">Une fois que vous activez la zone, la prochaine connexion d’un client utilise le nouveau flux d’authentification. Notez que le mise en marche de zone ne déclenche une nouvelle authentification pour les clients. Le clients réauthentifier en fonction de la durée de vie des jetons d’authentification ou qu’ils ont des certificats.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p116">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="0ebfd-p117">Pour vérifier que la zone fonctionne une fois que vous avez activé cette fonction, vous déconnecter d’un client Windows SFB test et veillez à cliquer sur « Supprimer mes informations d’identification ». Connectez-vous à nouveau. Le client doit désormais utiliser le flux d’authentification moderne et votre nom d’utilisateur inclut une invite **Office 365** pour un bureau ou une école compte, vu juste avant le client contacte le serveur et vous connecte.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p117">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'. Sign in again. The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="0ebfd-p118">Vous devez également vérifier les informations de Configuration pour Skype pour les Clients d’entreprise pour une autorité de OAuth. Pour ce faire, sur l’ordinateur client, maintenez la touche CTRL ENFONCÉE en même temps que vous avec le bouton droit le Skype pour entreprise icône dans la barre de Notification Windows. Dans le menu qui apparaît, cliquez sur informations de Configuration. Dans la fenêtre « Skype pour les informations de Configuration de Business » qui s’affiche sur le bureau, recherchez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p118">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'. To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray. Click Configuration Information in the menu that appears. In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![Les informations de Configuration d’un Skype pour Business Client en utilisant l’authentification moderne indiquent un Lync et les URL d’autorité OAUTH EWS de https://login.windows.net/common/oauth2/authorize.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="0ebfd-p119">Vous devez également maintenez enfoncée la touche CTRL ENFONCÉE en même temps que vous avec le bouton droit sur l’icône pour le client Outlook (également dans la barre d’état Windows Notifications), cliquez sur état de la connexion. Recherchez l’adresse du client SMTP par rapport à un type d’authentification de ' illimitées\*», qui représente le jeton de support utilisé dans OAuth.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p119">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="0ebfd-202">Articles connexes</span><span class="sxs-lookup"><span data-stu-id="0ebfd-202">Related articles</span></span>

<span data-ttu-id="0ebfd-203">[Lien vers la vue d’ensemble de l’authentification moderne](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="0ebfd-203">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="0ebfd-p120">Vous devez savoir comment utiliser l’authentification moderne (ADAL) pour votre Skype pour les clients d’entreprise ? Nous avons étapes [ici](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p120">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients? We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="0ebfd-p121">Voulez-vous pour lire comme suit lorsqu’ils s’affichent pour Exchange Server, sur site, en cours d’exécution sans SFB ? Ces étapes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="0ebfd-p121">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB? Those steps are available here.</span></span>
  

