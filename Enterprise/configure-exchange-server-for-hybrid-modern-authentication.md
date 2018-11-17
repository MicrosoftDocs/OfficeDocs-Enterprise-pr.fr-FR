---
title: Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: Hybride modernes d’authentification (zone), est une méthode de gestion des identités qui offre le plus sécurisé authentification et autorisation utilisateur et est disponible pour les déploiements de hybride Exchange server sur site.
ms.openlocfilehash: df5ea03b06ee1c101b03e19c7acb445c9543586b
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547156"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="c9493-103">Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride</span><span class="sxs-lookup"><span data-stu-id="c9493-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="c9493-104">Hybride modernes d’authentification (zone), est une méthode de gestion des identités qui offre le plus sécurisé authentification et autorisation utilisateur et est disponible pour les déploiements de hybride Exchange server sur site.</span><span class="sxs-lookup"><span data-stu-id="c9493-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="c9493-105">MONEY</span><span class="sxs-lookup"><span data-stu-id="c9493-105">FYI</span></span>

<span data-ttu-id="c9493-106">Avant de commencer, appeler :</span><span class="sxs-lookup"><span data-stu-id="c9493-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="c9493-107">Authentification moderne hybride \> zone</span><span class="sxs-lookup"><span data-stu-id="c9493-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="c9493-108">Exchange local \> EXCH</span><span class="sxs-lookup"><span data-stu-id="c9493-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="c9493-109">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="c9493-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="c9493-110">En outre, *que si un graphique dans cet article est un objet qui a « grisé » ou « estompé » ce qui signifie que l’élément en gris n’est pas inclus dans la configuration de la zone spécifique* .</span><span class="sxs-lookup"><span data-stu-id="c9493-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="c9493-111">Activation de l’authentification moderne hybride</span><span class="sxs-lookup"><span data-stu-id="c9493-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="c9493-112">Activation de zone signifie :</span><span class="sxs-lookup"><span data-stu-id="c9493-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="c9493-113">En vérifiant que vous remplissez les conditions préalables avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="c9493-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="c9493-p101">Depuis de nombreuses **conditions préalables** sont courants pour les deux Skype pour les entreprises et Exchange, [vue d’ensemble de l’authentification moderne hybride et les conditions préalables pour l’utiliser avec locale Skype pour l’entreprise et les serveurs Exchange](hybrid-modern-auth-overview.md). Cela avant de commencer une des étapes de cet article.</span><span class="sxs-lookup"><span data-stu-id="c9493-p101">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="c9493-116">Ajout de local URL du service web en tant que des noms principaux de Service (SPN) dans Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c9493-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="c9493-117">En vous assurant de tous les répertoires virtuels sont activés pour la zone</span><span class="sxs-lookup"><span data-stu-id="c9493-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="c9493-118">Vérification de l’objet serveur d’authentification EvoSTS</span><span class="sxs-lookup"><span data-stu-id="c9493-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="c9493-119">Activation de la zone de change</span><span class="sxs-lookup"><span data-stu-id="c9493-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="c9493-p102">**Remarque** Votre version de Microsoft Office ne prend en charge MA ? Voir [moderne comment fonctionne l’authentification pour les applications clientes Office 2013 et Office 2016](modern-auth-for-office-2013-and-2016.md).</span><span class="sxs-lookup"><span data-stu-id="c9493-p102">**Note** Does your version of Office support MA? See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="c9493-122">Assurez-vous que vous disposez de tous les préalables</span><span class="sxs-lookup"><span data-stu-id="c9493-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="c9493-p103">Étant donné que plusieurs conditions préalables sont courants pour les deux Skype pour les entreprises et Exchange, consultez [hybride moderne Authentication overview et les conditions préalables pour l’utiliser avec Skype sur site pour les professionnels et les serveurs Exchange](hybrid-modern-auth-overview.md). Cette *avant de* commencer l’une des étapes de cet article.</span><span class="sxs-lookup"><span data-stu-id="c9493-p103">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="c9493-125">Ajoutez sur site web service URL en tant que des noms principaux de service dans Azure AD</span><span class="sxs-lookup"><span data-stu-id="c9493-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="c9493-p104">Exécutez les commandes qu’attribuer à votre site web local des URL de service que Azure AD SPN. noms principaux de service sont utilisés par les ordinateurs clients et périphériques durant l’authentification et d’autorisation. Toutes les URL qui peuvent être utilisés pour se connecter à partir de locaux pour Azure Active Directory (DAS) doivent être inscrit dans DAS (Cela inclut les espaces de noms internes et externes).</span><span class="sxs-lookup"><span data-stu-id="c9493-p104">Run the commands that assign your on-premises web service URLs as Azure AD SPNs. SPNs are used by client machines and devices during authentication and authorization. All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="c9493-p105">Tout d’abord, rassemblez toutes les URL que vous devez ajouter dans DAS. Exécutez ces commandes locale :</span><span class="sxs-lookup"><span data-stu-id="c9493-p105">First, gather all the URLs that you need to add in AAD. Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="c9493-131">Vérifiez que les URL que les clients peuvent se connecter à sont répertoriées sous les noms principaux de service HTTPS dans DAS.</span><span class="sxs-lookup"><span data-stu-id="c9493-131">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="c9493-132">Tout d’abord, connectez-vous à DAS avec [ces instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="c9493-132">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="c9493-133">**Remarque** Vous devez utiliser l’option Connect-MsolService à partir de cette page pour être en mesure d’utiliser la commande ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c9493-133">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="c9493-134">Pour Exchange URL associées, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="c9493-134">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="c9493-p106">Prendre note des (et la capture d’écran pour comparaison ultérieure) le résultat de cette commande, qui doit contenir un https:// *autodiscover.yourdomain.com* et l’URL de *mail.yourdomain.com* https://, mais se composent principalement des noms principaux de service commençant par 00000002-0000-0ff1-CE00-000000000000 /. Si l’URL https:// votre sur site qui ne figurent pas nous vous devrez ajouter ces enregistrements spécifiques à cette liste.</span><span class="sxs-lookup"><span data-stu-id="c9493-p106">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/. If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="c9493-137">Si vous ne voyez pas vos enregistrements MAPI/HTTP, EWS, ActiveSync, carnet d’adresses et de découverte automatique internes et externes dans cette liste, vous devez les ajouter à l’aide de la commande ci-dessous (URL de l’exemple sont '`mail.corp.contoso.com`'et'`owa.contoso.com`», mais vous avez **Remplacer les exemples d’URL avec vos propres** ) :</span><span class="sxs-lookup"><span data-stu-id="c9493-137">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="c9493-p107">Vérifiez que vos nouveaux enregistrements ont été ajoutés à exécuter à nouveau la commande Get-MsolServicePrincipal à l’étape 2 et la recherche par le biais de la sortie. Comparez la liste / capture d’écran d’avant à la nouvelle liste des noms principaux de service (vous pouvez également capture d’écran de la nouvelle liste de vos enregistrements). Si vous avez réussi, vous verrez les deux nouvelles URL dans la liste. Allez dans notre exemple, la liste des noms principaux de service système incluent désormais les URL spécifiques `https://mail.corp.contoso.com` et `https://owa.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="c9493-p107">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="c9493-142">Vérifier que les répertoires virtuels sont configurés correctement</span><span class="sxs-lookup"><span data-stu-id="c9493-142">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="c9493-143">Vérifiez maintenant OAuth est correctement activé dans Exchange sur tous les répertoires virtuels Outlook peut utiliser en exécutant les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c9493-143">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="c9493-144">Vérification de la sortie pour vous assurer que **OAuth** est activée sur chacun de ces VDirs, il doit ressembler à ceci (et l’essentiel à examiner est « OAuth ») ;</span><span class="sxs-lookup"><span data-stu-id="c9493-144">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

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
  
<span data-ttu-id="c9493-145">Si OAuth est manquant à partir de n’importe quel serveur et n’importe lequel des quatre répertoires virtuels que vous souhaitez ajouter à l’aide des commandes avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c9493-145">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="c9493-146">Vérifiez que l’objet de serveur d’authentification EvoSTS est établie.</span><span class="sxs-lookup"><span data-stu-id="c9493-146">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="c9493-p108">Revenez à locale Exchange Management Shell pour cette dernière commande. Vous pouvez maintenant valider que votre site dispose d’une entrée pour le fournisseur d’authentification evoSTS :</span><span class="sxs-lookup"><span data-stu-id="c9493-p108">Return to the on-premises Exchange Management Shell for this last command. Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="c9493-p109">La sortie doit s’afficher une AuthServer de l’EvoSts nom et l’état « Activé » doit avoir la valeur True. Si vous ne voyez pas cela, vous devez téléchargez et exécutez la version la plus récente de l’Assistant Configuration hybride.</span><span class="sxs-lookup"><span data-stu-id="c9493-p109">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True. If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="c9493-151">**Important** Si vous exécutez Exchange 2010 dans votre environnement, le fournisseur d’authentification EvoSTS n’est créé.</span><span class="sxs-lookup"><span data-stu-id="c9493-151">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="c9493-152">Activer la zone de mémoire haute</span><span class="sxs-lookup"><span data-stu-id="c9493-152">Enable HMA</span></span>

<span data-ttu-id="c9493-153">Exécutez la commande suivante dans Exchange Management Shell, locale :</span><span class="sxs-lookup"><span data-stu-id="c9493-153">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="c9493-154">Vérifier</span><span class="sxs-lookup"><span data-stu-id="c9493-154">Verify</span></span>

<span data-ttu-id="c9493-p110">Une fois que vous activez la zone, la prochaine connexion d’un client utilise le nouveau flux d’authentification. Notez que le mise en marche de zone ne déclenche une nouvelle authentification pour les clients. Le clients réauthentifier en fonction de la durée de vie des jetons d’authentification ou qu’ils ont des certificats.</span><span class="sxs-lookup"><span data-stu-id="c9493-p110">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="c9493-p111">Vous devez également maintenez enfoncée la touche CTRL ENFONCÉE en même temps que vous avec le bouton droit sur l’icône pour le client Outlook (également dans la barre d’état Windows Notifications), cliquez sur état de la connexion. Recherchez l’adresse du client SMTP par rapport à un type de « Authentification » de ' illimitées\*», qui représente le jeton de support utilisé dans OAuth.</span><span class="sxs-lookup"><span data-stu-id="c9493-p111">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="c9493-p112">**Remarque** Nécessaire de configurer Skype pour les entreprises avec zone ? Vous aurez besoin de deux articles : une qui répertorie les [topologies prises en charge](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)et une qui vous montre [comment effectuer la configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c9493-p112">**Note** Need to configure Skype for Business with HMA? You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="c9493-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9493-162">Related topics</span></span>

[<span data-ttu-id="c9493-163">Vue d’ensemble de l’authentification moderne hybride et conditions requises pour l’utiliser avec Skype sur site pour les professionnels et les serveurs Exchange</span><span class="sxs-lookup"><span data-stu-id="c9493-163">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

