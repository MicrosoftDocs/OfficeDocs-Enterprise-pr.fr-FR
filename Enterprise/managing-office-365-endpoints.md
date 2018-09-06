---
title: Gestion des points de terminaison Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/18/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Certains réseaux est conçus pour restreindre l’accès à internet, afin d’ordinateurs sur des réseaux tels que ceux-ci peuvent accéder à Office 365, les administrateurs réseau et le proxy doivent gérer la liste des noms de domaine complets, URL, et les adresses IP qui constituent la liste des points de terminaison Office 365. Ces doivent figurer dans les règles de pare-feu ou de proxy et PAC fichiers pour vous assurer de demandes réseau sont en mesure d’atteindre Office 365.
ms.openlocfilehash: 42613b45b8395c3f81064bbc2171866bc922a657
ms.sourcegitcommit: ca4d3ec34300d7d39f1a42dc6f29a34915de5c87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "23831919"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="504b1-104">Gestion des points de terminaison Office 365</span><span class="sxs-lookup"><span data-stu-id="504b1-104">Managing Office 365 endpoints</span></span>

## <a name="office-365-network-connectivity"></a><span data-ttu-id="504b1-105">Connectivité du réseau Office 365</span><span class="sxs-lookup"><span data-stu-id="504b1-105">Office 365 network connectivity</span></span>

 <span data-ttu-id="504b1-p102">Connexions à Office 365 se composent de volume élevé, les demandes de réseau approuvé qui fonctionnent mieux si vous avez créé sur une sortie faible latence qui est proche de l’utilisateur. Certaines connexions Office 365 peuvent bénéficier de l’optimisation de la connexion.</span><span class="sxs-lookup"><span data-stu-id="504b1-p102">Connections to Office 365 consist of high volume, trusted network requests that perform best when they're made over a low-latency egress that is near the user. Some Office 365 connections can benefit from optimizing the connection.</span></span> 
  
1. <span data-ttu-id="504b1-108">Vérifiez votre pare-feu Autoriser les listes Autoriser pour la connectivité aux points de terminaison Office 365.</span><span class="sxs-lookup"><span data-stu-id="504b1-108">Ensure your firewall allow lists allow for connectivity to Office 365 endpoints.</span></span>
    
2. <span data-ttu-id="504b1-109">Utilisez votre infrastructure de serveur proxy pour autoriser la connectivité Internet à caractères génériques et destinations annulées.</span><span class="sxs-lookup"><span data-stu-id="504b1-109">Use your proxy infrastructure to allow Internet connectivity to wildcard and unpublished destinations.</span></span>
    
3. <span data-ttu-id="504b1-110">Mettre à jour une configuration de réseau de périmètre optimales.</span><span class="sxs-lookup"><span data-stu-id="504b1-110">Maintain an optimal perimeter network configuration.</span></span>
    
4. <span data-ttu-id="504b1-111">[Assurez-vous que vous obtenez la meilleure connectivité](https://aka.ms/o365perfprinciples).</span><span class="sxs-lookup"><span data-stu-id="504b1-111">[Ensure you're getting the best connectivity](https://aka.ms/o365perfprinciples).</span></span>
    
5. <span data-ttu-id="504b1-112">Lisez les [Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md) pour comprendre les principes de connectivité pour gérer le trafic d’Office 365 en toute sécurité et d’obtenir les meilleures performances possibles.</span><span class="sxs-lookup"><span data-stu-id="504b1-112">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
    
![Connexion à Office 365 par le biais de pare-feu et des proxys.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a><span data-ttu-id="504b1-114">Mise à jour du pare-feu de le sortant autoriser les listes</span><span class="sxs-lookup"><span data-stu-id="504b1-114">Update your firewall's outbound allow lists</span></span>

<span data-ttu-id="504b1-p103">Vous pouvez optimiser votre réseau par l’envoi de que tous les approuvés demandes du réseau Office 365 directement via votre pare-feu, en ignorant inspection de niveau tous les paquets supplémentaires ou traitement. Cela réduit la baisse des performances de la latence et vos besoins en capacité de périmètre. Pour choisir le réseau qui demande à approuver le plus simple consiste à utiliser nos fichiers PAC prédéfinis dans l’onglet **Proxies** ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="504b1-p103">You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces slow performance from latency and reduces your perimeter capacity requirements. The easiest way to choose which network requests to trust is to use our pre-built PAC files on the **Proxies** tab above.</span></span> 
  
<span data-ttu-id="504b1-p104">Si votre pare-feu bloque le trafic sortant, vous souhaiterez garantir l’adresse IP et noms de domaine complets répertorié comme **requis** dans ce [fichier XML](https://go.microsoft.com/fwlink/?LinkId=533185) se trouvent sur la liste verte. Reconnaître que tous les services nécessitent l’utilisation de certains services tiers 3e. Nous ne pas fournir des adresses IP pour ces services tiers 3e tels que les fournisseurs de certificats fournisseurs, les réseaux de distribution de contenu, DNS et ainsi de suite. Pour toutes les fonctionnalités Office 365, vous devez être en mesure d’atteindre toutes les destinations demandées par Office 365, quelle que soit la quantité nous publier des informations sur la destination.</span><span class="sxs-lookup"><span data-stu-id="504b1-p104">If your firewall blocks outbound traffic, you'll want to ensure all of the IP and FQDNs listed as **Required** in this [XML file](https://go.microsoft.com/fwlink/?LinkId=533185) are on the allow list. Recognize all services require the use of some 3rd party services. We don't provide IP addresses for these 3rd party services such as certificate providers, Content Delivery Networks, DNS providers, and so on. For full Office 365 functionality, you must be able to reach all destinations requested by Office 365 regardless of how much information we publish about the destination.</span></span> 
  
<span data-ttu-id="504b1-122">Nombreuses destinations n’ont pas d’une adresse IP publiée ou sont répertoriées sous un domaine générique sans nom de domaine complet spécifique, pour utiliser cette fonctionnalité, vous devez être en mesure de résoudre ces demandes réseau à l’adresse IP en cours d’adresses demandé et envoyer le requête réseau via Internet.</span><span class="sxs-lookup"><span data-stu-id="504b1-122">Many destinations do not have an IP address published or are listed as a wildcard domain with no specific fully qualified domain name, to use this functionality you must be able to resolve these network requests to the current IP address being requested and send the network request over the Internet.</span></span>
  
<span data-ttu-id="504b1-p105">Automatiser à l’aide d’un pare-feu qui analyse le fichier XML en votre nom et met à jour vos règles automatiquement basés sur les services et fonctionnalités que vous souhaitez acheminer directement via votre pare-feu. Vous pouvez également utiliser l’outil [Azure plage](https://azurerange.azurewebsites.net/) qui a été généré par la Communauté et analyse le code XML pour vous avec les options d’exportation de la configuration de la liste ACL ou Cisco XE, texte brut ou CSV.</span><span class="sxs-lookup"><span data-stu-id="504b1-p105">Automate your process by using a firewall that parses the XML file on your behalf and updates your rules automatically based on the services or features you plan to route directly through your firewall. You can also use the [Azure Range](https://azurerange.azurewebsites.net/) tool that has been built by the community and parses the XML for you with export options for Cisco XE Route or ACL list configuration, plain text, or CSV.</span></span> 
  
<span data-ttu-id="504b1-125">Une explication plus complète des destinations réseau est disponible sur le [site de référence](urls-and-ip-address-ranges.md) par le biais de notre [flux RSS en fonction de journal des modifications](https://go.microsoft.com/fwlink/p/?linkid=236301) afin que vous pouvez vous abonner aux modifications apportées.</span><span class="sxs-lookup"><span data-stu-id="504b1-125">A longer explanation of the network destinations is available on our [reference site](urls-and-ip-address-ranges.md) as well through our [RSS based change log](https://go.microsoft.com/fwlink/p/?linkid=236301) so you can subscribe to changes.</span></span> 
  
<span data-ttu-id="504b1-126"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-126"></span></span>
## <a name="configure-outbound-paths-with-pac-files"></a><span data-ttu-id="504b1-127">Configurer les chemins d’accès sortants avec fichiers PAC</span><span class="sxs-lookup"><span data-stu-id="504b1-127">Configure outbound paths with PAC files</span></span>

<span data-ttu-id="504b1-p106">Fichiers PAC ou WPAD permet de gérer les demandes de réseau qui sont associés à Office 365, mais n’ont pas une adresse IP fournie. Demandes de réseau par défaut qui sont envoyées via un périphérique proxy ou périmètre provoquer latence supplémentaire. Alors que l’authentification de proxy entraîne la plus grande taxe, les autres services tels que la recherche de réputation et les tentatives d’inspecter les paquets peuvent entraîner une expérience utilisateur médiocre. En outre, ces appareils de réseau de périmètre besoin une capacité suffisante pour traiter toutes les demandes réseau. Nous vous recommandons de contournement de votre infrastructure de serveur proxy ou inspection pour les demandes de réseau directs Office 365.</span><span class="sxs-lookup"><span data-stu-id="504b1-p106">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address provided. Typical network requests that are sent through a proxy or perimeter device incur additional latency. While proxy authentication incurs the largest tax, other services such as reputation lookup and attempts to inspect packets can cause a poor user experience. Additionally, these perimeter network devices need enough capacity to process all of the network requests. We recommend bypassing your proxy or inspection infrastructure for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="504b1-p107">Utilisez un des fichiers de notre PAC comme point de départ pour déterminer le trafic réseau est envoyé à un proxy et qui sera envoyé à un pare-feu. Si vous ne connaissez pas les fichiers PAC ou WPAD, lisez ce billet sur les [fichiers de déploiement PAC](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) parmi nos consultants Office 365. Vous souhaiterez passer en revue ces comme point de départ et modifier en fonction de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="504b1-p107">Use one of our PAC files as a starting place to determine what network traffic will be sent to a proxy and which will be sent to a firewall. If you're new to PAC or WPAD files, read this post about [deploying PAC files](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) from one of our Office 365 consultants. You'll want to review these as a starting place and edit to suit your environment.</span></span> 
  
 <span data-ttu-id="504b1-136">**Fichiers PAC 7/10/2018 de mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="504b1-136">**PAC files updated 7/10/2018**.</span></span> 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a><span data-ttu-id="504b1-137">#1 - fichier PAC : sépare requis des noms de domaine complets Internet à partir de connus Office 365 nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="504b1-137">#1 - PAC file: Separates required Internet FQDNs from known Office 365 FQDN.</span></span>

<span data-ttu-id="504b1-p108">Le premier exemple est une démonstration de notre approche recommandée pour la gestion des points de terminaison via Internet uniquement. Ignore le proxy pour Office 365 destinations où l’adresse IP est publiée et envoie des demandes réseau restants au proxy.</span><span class="sxs-lookup"><span data-stu-id="504b1-p108">The first example is a demonstration of our recommended approach to managing endpoints over the Internet only. Bypasses the proxy for Office 365 destinations where the IP address is published and sends remaining network requests to the proxy.</span></span>
  
<span data-ttu-id="504b1-140">Extrait de code :</span><span class="sxs-lookup"><span data-stu-id="504b1-140">Code snippet:</span></span>

```javascript
// JavaScript source code
//July 2018 - Updates go live 1st August2018
//This PAC file contains all FQDNs needed for all services and splits the traffic between those which Microsoft can provide IPs for (so can be sent through a managed firewall with conditional access if desired) and those which IPs cannot be provided for, so need to go to an unrestricted proxy or egress. 
//Due to the use of wildcards, some extra logic is provided to send traffic to the proxy before a 'direct' wildcard is hit.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    var proxyserver2 = "PROXY 10.10.10.11:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //Catch explicit FQDNs which need the proxy but are covered under wildcarded FQDNs which have IPs. This has to be done first before the wildcard is hit
    if ((shExpMatch(host, "quicktips.skypeforbusiness.com"))    
        || (shExpMatch(host, "*.um.outlook.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r1.res.office365.com")))
    {
        return proxyserver;
    }
        //Send FQDNs which Microsoft provide IPs for direct, so they can be sent via a firewall
    else if ((isPlainHostName(host))
    || (shExpMatch(host, "*.aria.microsoft.com"))    
    || (shExpMatch(host, "*.dc.trouter.io"))
    || (shExpMatch(host, "*.lync.com"))
    || (shExpMatch(host, "*.manage.office.com"))
    || (shExpMatch(host, "*.office365.com"))
    || (shExpMatch(host, "*.onenote.com"))
    || (shExpMatch(host, "*.outlook.com"))
    || (shExpMatch(host, "*.outlook.office.com"))
    || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
    || (shExpMatch(host, "*.protection.office.com"))
    || (shExpMatch(host, "*.sharepoint.com"))
    || (shExpMatch(host, "*.skype.com"))
    || (shExpMatch(host, "*.skypeforbusiness.com"))
    || (shExpMatch(host, "*.svc.ms"))
    || (shExpMatch(host, "*.teams.microsoft.com"))
    || (shExpMatch(host, "*.yammer.com"))
    || (shExpMatch(host, "*.yammerusercontent.com"))    
    || (shExpMatch(host, "*broadcast.officeapps.live.com"))
    || (shExpMatch(host, "*excel.officeapps.live.com"))
    || (shExpMatch(host, "*onenote.officeapps.live.com"))
    || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
    || (shExpMatch(host, "*view.officeapps.live.com"))
    || (shExpMatch(host, "*visio.officeapps.live.com"))
    || (shExpMatch(host, "*word-edit.officeapps.live.com"))
    || (shExpMatch(host, "*word-view.officeapps.live.com"))
    || (shExpMatch(host, "admin.microsoft.com"))    
    || (shExpMatch(host, "account.office.net"))
    || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
    || (shExpMatch(host, "agent.office.net"))
    || (shExpMatch(host, "api.login.microsoftonline.com"))
    || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "apc.delve.office.com"))
    || (shExpMatch(host, "aus.delve.office.com"))
    || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
    || (shExpMatch(host, "becws.microsoftonline.com"))
    || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
    || (shExpMatch(host, "can.delve.office.com"))
    || (shExpMatch(host, "ccs.login.microsoftonline.com"))
    || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
    || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
    || (shExpMatch(host, "clientlog.portal.office.com"))
    || (shExpMatch(host, "companymanager.microsoftonline.com"))
    || (shExpMatch(host, "cus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "delve.office.com"))
    || (shExpMatch(host, "device.login.microsoftonline.com"))    
    || (shExpMatch(host, "ea-000.tasks.osi.office.net"))
    || (shExpMatch(host, "eur.delve.office.com"))
    || (shExpMatch(host, "eus-zzz.tasks.osi.office.net"))
    || (shExpMatch(host, "gbr.delve.office.com"))    
    || (shExpMatch(host, "hip.microsoftonline-p.net"))
    || (shExpMatch(host, "hipservice.microsoftonline.com"))
    || (shExpMatch(host, "home.office.com"))
    || (shExpMatch(host, "ind.delve.office.com"))
    || (shExpMatch(host, "jpn.delve.office.com"))
    || (shExpMatch(host, "kor.delve.office.com"))
    || (shExpMatch(host, "lam.delve.office.com"))
    || (shExpMatch(host, "login.microsoft.com"))
    || (shExpMatch(host, "login.microsoftonline.com"))
    || (shExpMatch(host, "login.microsoftonline-p.com"))
    || (shExpMatch(host, "login.windows.net"))
    || (shExpMatch(host, "logincert.microsoftonline.com"))
    || (shExpMatch(host, "loginex.microsoftonline.com"))
    || (shExpMatch(host, "login-us.microsoftonline.com"))     
    || (shExpMatch(host, "manage.office.com"))
    || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
    || (shExpMatch(host, "nam.delve.office.com"))
    || (shExpMatch(host, "neu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "nexus.microsoftonline-p.com"))
    || (shExpMatch(host, "nexus.officeapps.live.com"))
    || (shExpMatch(host, "nexusrules.officeapps.live.com"))
    || (shExpMatch(host, "office.live.com"))
    || (shExpMatch(host, "officeapps.live.com"))
    || (shExpMatch(host, "passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "portal.microsoftonline.com"))
    || (shExpMatch(host, "portal.office.com"))
    || (shExpMatch(host, "protection.office.com"))
    || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
    || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net"))   
    || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))
    || (shExpMatch(host, "sea-000.tasks.osi.office.net"))    
    || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
    || (shExpMatch(host, "suite.office.net"))    
    || (shExpMatch(host, "tasks.office.com"))
    || (shExpMatch(host, "teams.microsoft.com"))
    || (shExpMatch(host, "testconnectivity.microsoft.com"))
    || (shExpMatch(host, "webshell.suite.office.com"))
    || (shExpMatch(host, "weu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "wus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "www.office.com")))

    {
        return "DIRECT";
    }
    else
        // Send all unknown IP traffic to Proxy for unrestricted access. This section is not necessary if you have a catchall for all other traffic to go to an unfiltered proxy. 
        //However the fqdns required, but for which we dont have IPs for, are listed here incase you need an explicit list.
   if          ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com")) 
        || (shExpMatch(host, "*.adl.windows.com"))   
        || (shExpMatch(host, "*.api.microsoftstream.com"))      
        || (shExpMatch(host, "*.assets-yammer.com"))   
        || (shExpMatch(host, "*.azureedge.net"))            
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))   
        || (shExpMatch(host, "*.helpshift.com"))   
        || (shExpMatch(host, "*.hockeyapp.net"))    
        || (shExpMatch(host, "*.localytics.com"))    
        || (shExpMatch(host, "*.log.optimizely.com"))    
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))      
        || (shExpMatch(host, "*.msocdn.com")) 
        || (shExpMatch(host, "*.mstea.ms"))    
        || (shExpMatch(host, "*.notification.api.microsoftstream.com")) 
        || (shExpMatch(host, "*.o365weve.com"))     
        || (shExpMatch(host, "*.office.com"))   
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.phonefactor.net"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))  
        || (shExpMatch(host, "*.sfbassets.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.teams.microsoft.com"))  
        || (shExpMatch(host, "*.tenor.com"))  
        || (shExpMatch(host, "*.symcd.com"))     
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))  
        || (shExpMatch(host, "apps.identrust.com"))  
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))        
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com")) 
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))
        || (shExpMatch(host, "connect.facebook.net"))        
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))          
        || (shExpMatch(host, "ecn.dev.virtualearth.net "))   
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))             
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))        
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))   
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))   
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))        
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))      
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))       
        || (shExpMatch(host, "ocsp2.globalsign.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))            
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))              
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net")) 
        || (shExpMatch(host, "r1.res.office365.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))         
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))   
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))  
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "sway.com")) 
        || (shExpMatch(host, "teams.microsoft.com"))              
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))         
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))    
        || (shExpMatch(host, "web.microsoftstream.com"))         
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))   
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com"))
        || (shExpMatch(host, "xsi.outlook.com")))

    {
        return proxyserver;
    }
    //Catchall for all other traffic to another proxy 
else return proxyserver;
}

```

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a><span data-ttu-id="504b1-141">#2 - fichier PAC : se connecter à Office 365 via Internet et ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="504b1-141">#2 - PAC file: Connect to Office 365 over the Internet and ExpressRoute</span></span>
<span data-ttu-id="504b1-142"><a name="bkmk_inet-aer"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-142"></span></span>

<span data-ttu-id="504b1-p109">Le second exemple est une démonstration de notre approche recommandée pour la gestion des connexions lorsque des circuits ExpressRoute et Internet sont disponibles. Envoie ExpressRoute destinations le circuit ExpressRoute et Internet uniquement destinations au proxy.</span><span class="sxs-lookup"><span data-stu-id="504b1-p109">The second example is a demonstration of our recommended approach to managing connections when ExpressRoute and Internet circuits are available. Sends ExpressRoute advertised destinations to the ExpressRoute circuit and Internet only advertised destinations to the proxy.</span></span>
  
<span data-ttu-id="504b1-145">Extrait de code :</span><span class="sxs-lookup"><span data-stu-id="504b1-145">Code snippet:</span></span>

```javascript
// JavaScript source code
//July 2018 Update
// Consolidated FQDNs of URLS which are reachable via Microsoft peering over ExpressRoute. All other traffic sent to a proxy in this example. 
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your traffic flow needs and the Office 365 URL &amp; IP page. 
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
//PAC presumes all Office 365 BGP communities/route filters are allowed.
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //SUB-FQDNs of ExpressRoutable wildcards which need to be explicitly sent to the proxy at the top of the PAC because they arent ER routable
    if ((shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "quicktips.skypeforbusiness.com"))
        || (shExpMatch(host, "*.um.outlook.com")))                  
    {
        return proxyserver;
    }
        //EXPRESS ROUTE DIRECT
    else if ((isPlainHostName(host))  
            || (shExpMatch(host, "*.aria.microsoft.com"))             
            || (shExpMatch(host, "*.dc.trouter.io"))
            || (shExpMatch(host, "*.lync.com"))
            || (shExpMatch(host, "*.manage.office.com"))
            || (shExpMatch(host, "*.outlook.com"))
            || (shExpMatch(host, "*.outlook.office.com"))
            || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
            || (shExpMatch(host, "*.protection.office.com"))
            || (shExpMatch(host, "*.protection.outlook.com"))
            || (shExpMatch(host, "*.sharepoint.com")) 
            || (shExpMatch(host, "*.skype.com")) 
            || (shExpMatch(host, "*.skypeforbusiness.com")) 
            || (shExpMatch(host, "*.svc.ms"))   
            || (shExpMatch(host, "*.teams.microsoft.com"))  
            || (shExpMatch(host, "*broadcast.officeapps.live.com"))
            || (shExpMatch(host, "*excel.officeapps.live.com"))
            || (shExpMatch(host, "*onenote.officeapps.live.com"))
            || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
            || (shExpMatch(host, "*view.officeapps.live.com"))                                 
            || (shExpMatch(host, "*visio.officeapps.live.com"))
            || (shExpMatch(host, "*word-edit.officeapps.live.com"))
            || (shExpMatch(host, "*word-view.officeapps.live.com"))
            || (shExpMatch(host, "account.office.net"))
            || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
            || (shExpMatch(host, "agent.office.net"))  
            || (shExpMatch(host, "apc.delve.office.com"))
            || (shExpMatch(host, "api.login.microsoftonline.com"))
            || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "aus.delve.office.com"))
            || (shExpMatch(host, "autologon.microsoftazuread-sso.com")) 
            || (shExpMatch(host, "becws.microsoftonline.com"))
            || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
            || (shExpMatch(host, "can.delve.office.com")) 
            || (shExpMatch(host, "ccs.login.microsoftonline.com"))  
            || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
            || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
            || (shExpMatch(host, "companymanager.microsoftonline.com"))
            || (shExpMatch(host, "delve.office.com"))
            || (shExpMatch(host, "device.login.microsoftonline.com"))
            || (shExpMatch(host, "domains.live.com")) 
            || (shExpMatch(host, "eur.delve.office.com"))
            || (shExpMatch(host, "gbr.delve.office.com"))
            || (shExpMatch(host, "hip.microsoftonline-p.net"))
            || (shExpMatch(host, "hipservice.microsoftonline.com"))
            || (shExpMatch(host, "home.office.com"))
            || (shExpMatch(host, "ind.delve.office.com"))
            || (shExpMatch(host, "jpn.delve.office.com"))
            || (shExpMatch(host, "kor.delve.office.com"))
            || (shExpMatch(host, "lam.delve.office.com"))
            || (shExpMatch(host, "login.microsoft.com"))
            || (shExpMatch(host, "login.microsoftonline.com"))
            || (shExpMatch(host, "login.microsoftonline-p.net"))
            || (shExpMatch(host, "login.windows.net"))
            || (shExpMatch(host, "logincert.microsoftonline.com"))
            || (shExpMatch(host, "loginex.microsoftonline.com"))
            || (shExpMatch(host, "login-us.microsoftonline.com"))
            || (shExpMatch(host, "manage.office.com"))
            || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
            || (shExpMatch(host, "nam.delve.office.com"))
            || (shExpMatch(host, "nexus.microsoftonline-p.net"))
            || (shExpMatch(host, "office.live.com")) 
            || (shExpMatch(host, "officeapps.live.com")) 
            || (shExpMatch(host, "outlook.office365.com")) 
            || (shExpMatch(host, "passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "portal.office.com"))
            || (shExpMatch(host, "protection.office.com"))
            || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
            || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
            || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))  
            || (shExpMatch(host, "signup.microsoft.com"))
            || (shExpMatch(host, "smtp.office365.com"))  
            || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
            || (shExpMatch(host, "suite.office.net")) 
            || (shExpMatch(host, "teams.microsoft.com")) 
            || (shExpMatch(host, "webshell.suite.office.com")) 
            || (shExpMatch(host, "www.office.com")))             
       
    {
        return "DIRECT";
    }
        //Catchall for all other traffic to proxy
    else
    {
        return proxyserver;
    }
}

```

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a><span data-ttu-id="504b1-146">#3 - fichier PAC : gérer toutes les destinations d’Office 365 collectivement</span><span class="sxs-lookup"><span data-stu-id="504b1-146">#3 - PAC file: Manage all Office 365 destinations collectively</span></span>
<span data-ttu-id="504b1-147"><a name="bkmk_inet-direct"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-147"></span></span>

<span data-ttu-id="504b1-p110">Le troisième exemple illustre l’envoi de toutes les demandes du réseau associées à Office 365 vers une destination unique. Cela est généralement utilisé pour ignorer l’inspection toutes les demandes du réseau Office 365 et offre un format où tous les points de terminaison publiés êtes-vous dans le format PAC à utiliser pour la personnalisation de votre liste.</span><span class="sxs-lookup"><span data-stu-id="504b1-p110">The third example demonstrates sending all network requests associated with Office 365 to a single destination. This is commonly used to bypass all inspection of Office 365 network requests and offers you a format where all published endpoints are in list in the PAC format to use for your customization.</span></span>
  
<span data-ttu-id="504b1-150">Extrait de code :</span><span class="sxs-lookup"><span data-stu-id="504b1-150">Code snippet:</span></span>

```javascript
// JavaScript source code
//July 2018 Update new URLS go live 1st August 2018 -
//Consolidated FQDNs required to access Office 365 - All services including optional components covered and elements covered under wildcards removed. 
//Some repeated domains have been consoliodated into unpublished wildcards in order to keep the file as small as possible.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
   if  ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com"))
        || (shExpMatch(host, "*.adl.windows.com"))
        || (shExpMatch(host, "*.api.microsoftstream.com"))  
        || (shExpMatch(host, "*.assets-yammer.com"))
        || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
        || (shExpMatch(host, "*.azureedge.net"))   
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net")) 
        || (shExpMatch(host, "*.dc.trouter.io"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))
        || (shExpMatch(host, "*.helpshift.com"))
        || (shExpMatch(host, "*.hockeyapp.net"))       
        || (shExpMatch(host, "*.localytics.com"))
        || (shExpMatch(host, "*.log.optimizely.com"))     
        || (shExpMatch(host, "*.lync.com"))
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))
        || (shExpMatch(host, "*.msocdn.com"))
        || (shExpMatch(host, "*.mstea.ms"))
        || (shExpMatch(host, "*.o365weve.com"))
        || (shExpMatch(host, "*.office.com"))
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.office365.com"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onenote.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.outlook.com"))
        || (shExpMatch(host, "*.phonefactor.net")) 
        || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))
        || (shExpMatch(host, "*.sfbassets.com"))  
        || (shExpMatch(host, "*.sharepoint.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.skype.com"))
        || (shExpMatch(host, "*.skypeforbusiness.com"))
        || (shExpMatch(host, "*.svc.ms")) 
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.symcd.com"))
        || (shExpMatch(host, "*.tenor.com"))
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*.yammer.com"))
        || (shExpMatch(host, "*.yammerusercontent.com"))         
        || (shExpMatch(host, "*broadcast.officeapps.live.com"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "*excel.officeapps.live.com"))
        || (shExpMatch(host, "*onenote.officeapps.live.com"))
        || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
        || (shExpMatch(host, "*view.officeapps.live.com"))
        || (shExpMatch(host, "*visio.officeapps.live.com"))
        || (shExpMatch(host, "*word-edit.officeapps.live.com"))
        || (shExpMatch(host, "*word-view.officeapps.live.com"))    
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))
        || (shExpMatch(host, "apps.identrust.com")) 
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))    
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com"))
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))     
        || (shExpMatch(host, "connect.facebook.net"))
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))      
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))           
        || (shExpMatch(host, "ecn.dev.virtualearth.net"))
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))               
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))   
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))     
        || (shExpMatch(host, "ocsp2.globalsign.com")) 
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "office.live.com"))
        || (shExpMatch(host, "officeapps.live.com"))
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))              
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "s0.assets-yammer.com"))  
        || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
        || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))              
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))    
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "web.microsoftstream.com"))   
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))  
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))        
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com")))
    {
        return proxyserver;
    }
        //Catchall for all other traffic to another proxy
    else return "PROXY 10.10.10.11:8080";
}

```

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a><span data-ttu-id="504b1-151">Utiliser des scripts personnalisés ou manuellement créer vos propres fichiers PAC</span><span class="sxs-lookup"><span data-stu-id="504b1-151">Use custom scripts or manually create your own PAC files</span></span>
<span data-ttu-id="504b1-152"><a name="pacfiles_manual"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-152"></span></span>

<span data-ttu-id="504b1-p111">Voici quelques autres outils de la Communauté, si vous avez créé quelque chose que vous souhaitez partager laisser une note dans les commentaires. None de la Communauté outils référencés dans cet article sont officiellement pris en charge ou mis à jour par Microsoft et sont fournies ici pour votre commodité.</span><span class="sxs-lookup"><span data-stu-id="504b1-p111">Here's a few more tools from the community, if you've built something you'd like to share leave a note in the comments. None of the community tools referenced in this article are officially supported or maintained by Microsoft and are provided here for your convenience.</span></span>
  
- <span data-ttu-id="504b1-p112">Il s’agit de l’outil généré par la Communauté le plus ancien pour aider à gérer le processus, un outil intégré par un membre de la Communauté Office 365. Voici le lien pour [Télécharger](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span><span class="sxs-lookup"><span data-stu-id="504b1-p112">This is the oldest community generated tool to help manage the process, a tool built by a member of the Office 365 community. Here is link to [download](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span></span>
    
- <span data-ttu-id="504b1-157">Preuve de Concept avec des règles de pare-feu exportable : [API de Microsoft Cloud IP](https://mscloudips.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="504b1-157">Proof of Concept with exportable firewall rules: [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/).</span></span>
    
- <span data-ttu-id="504b1-158">À partir de l’informatique Praktyk : [Conversion RSS](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) et [conversion XML](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span><span class="sxs-lookup"><span data-stu-id="504b1-158">From IT Praktyk: [RSS conversion](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) and [XML conversion](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span></span>
    
- <span data-ttu-id="504b1-159">À partir de Peter Abele : [Télécharger](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span><span class="sxs-lookup"><span data-stu-id="504b1-159">From Peter Abele: [Download](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span></span>
    
- <span data-ttu-id="504b1-p113">Utilisez votre analyse réseau pour déterminer quel réseau demande doit ignorer votre infrastructure de serveur proxy. Noms de domaines complets les plus courantes utilisées pour contourner les proxys de client incluent les éléments suivants en raison du volume de trafic réseau envoyé et reçu à partir de ces points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="504b1-p113">Use your network analysis to determine which network requests should bypass your proxy infrastructure. The most common FQDNs used to bypass customer proxies include the following due to the volume of network traffic sent and received from these endpoints.</span></span>
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  ```

- <span data-ttu-id="504b1-162">Vérifiez que toutes les demandes de réseau en cours envoyées directement à votre pare-feu ont une entrée correspondante dans le pare-feu Autoriser la demande par le biais de liste verte.</span><span class="sxs-lookup"><span data-stu-id="504b1-162">Ensure any network requests being sent to your firewall directly have a corresponding entry in the firewall allow list to allow the request to go through.</span></span>

## <a name="perimeter-network-integration"></a><span data-ttu-id="504b1-163">Intégration de réseau de périmètre</span><span class="sxs-lookup"><span data-stu-id="504b1-163">Perimeter network integration</span></span>
<span data-ttu-id="504b1-164"><a name="BKMK_Perimeter"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-164"></span></span>

<span data-ttu-id="504b1-165">Savez-vous de Microsoft WAN appartient aux plus grandes dorsales principales dans le monde ?</span><span class="sxs-lookup"><span data-stu-id="504b1-165">Did you know Microsoft's WAN is one of the largest backbones in the world?</span></span>
  
<span data-ttu-id="504b1-p114">Il est vrai que ce réseau massif fait Office 365 et autres services en nuage fonctionne indépendamment où dans le monde, que vous êtes. Notre réseau se compose de bande passante élevée, faible latence, liens capables de basculement avec des milliers de kilomètres d’itinéraire de Fibre foncé privée et multi-to les connexions entre les nœuds de centres de données et le bord, toutes les rendre plus facile à utiliser les services en nuage.</span><span class="sxs-lookup"><span data-stu-id="504b1-p114">It's true, this massive network is what makes Office 365 and our other cloud services work regardless of where in the world you are. Our network consists of high bandwidth, low latency, fail-over capable links with thousands of route miles of privately owned dark fiber, and multi-Terabit connections between datacenters and edge nodes, all to make it easier to use our cloud services.</span></span>
  
<span data-ttu-id="504b1-p115">Avec un réseau similaire à celle-ci, que vous souhaitez vous connecter à notre réseau dès que possible aux périphériques de votre organisation. Avec plus de 2500 relations homologation de fournisseur de services Internet global et 70 points de présence, prise en main de votre réseau de notre doit être transparente. Il ne peut pas nuire à quelques minutes assurant la que relation d’homologation votre fournisseur de services Internet est la plus optimale, [Voici quelques exemples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de bonnes et pas homologation livraisons à notre réseau.</span><span class="sxs-lookup"><span data-stu-id="504b1-p115">With a network like this, you want your organization's devices to connect to our network as soon as possible. With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
<span data-ttu-id="504b1-p116">Vous pouvez manuellement ou automatiquement configurez les périphériques de votre réseau d’optimiser la gestion des demandes de réseau application Office 365, en fonction de votre matériel. Les modifications de configuration que vous devez apporter à mieux gérer le trafic réseau de Office 365 dépend de votre environnement. Office 365 réseau demandes peuvent bénéficier des configurations de réseau qui autorisent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="504b1-p116">You can manually or automatically configure the devices on your network to optimally handle Office 365 application network requests, depending on your equipment. What configuration changes you need to make to optimally handle Office 365 network traffic will depend on your environment. Office 365 network requests may benefit from network configurations that allow the following:</span></span>
  
- <span data-ttu-id="504b1-174">Priorité sur le trafic réseau moins importante.</span><span class="sxs-lookup"><span data-stu-id="504b1-174">Priority over less critical network traffic.</span></span>
    
- <span data-ttu-id="504b1-p117">Routage vers une sortie locale pour éviter les backhauling sur un réseau étendu lent lien tout en tirant parti de la latence faible disponible sur le réseau Microsoft. [Voici une bonne description](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) selon les engagements clients.</span><span class="sxs-lookup"><span data-stu-id="504b1-p117">Routing to a local egress to avoid backhauling over a slow WAN link while taking advantage of the low latency available on the Microsoft network. [Here's a good discussion](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) based on customer engagements.</span></span> 
    
- <span data-ttu-id="504b1-177">Avec DNS vers une sortie locale pour s’assurer de la demande de réseau qui conserve la sortie locale arrive à l’emplacement homologation Microsoft le plus proche.</span><span class="sxs-lookup"><span data-stu-id="504b1-177">Using DNS near a local egress to ensure the network request that leaves the local egress arrives at the nearest Microsoft peering location.</span></span>
    
- <span data-ttu-id="504b1-178">Exclusion d’approfondie des paquets ou autres traitement pour répondre aux exigences de latence à l’échelle des paquets réseau intensive.</span><span class="sxs-lookup"><span data-stu-id="504b1-178">Exclusion from deep packet inspection or other intensive network packet processing to meet latency requirements at scale.</span></span>
    
<span data-ttu-id="504b1-p118">Périphériques réseau modernes incluent des fonctionnalités pour gérer les demandes de réseau pour les applications approuvées, tels qu’Office 365 différemment le trafic Internet générique, non approuvé. Avec le paysage émergent des solutions de réseau étendu SD, telle différenciation de sélection du trafic et le chemin d’accès peut également être effectuée avec le changement d’état du réseau comme point de la disponibilité du temps, la latence ou les performances des différents chemins d’accès de connectivité de sensibilisation entre l’utilisateur et le nuage.</span><span class="sxs-lookup"><span data-stu-id="504b1-p118">Modern network devices include capabilities to manage network requests for trusted applications such as Office 365 differently than generic, untrusted Internet traffic. With the emerging landscape of SD-WAN solutions, such differentiation of traffic and path selection can also be performed with awareness of the changing state of the network, such as point in time availability, latency or performance of various connectivity paths between the user and the cloud.</span></span>
  
<span data-ttu-id="504b1-181">Pour plus d’instructions sur la planification de votre configuration réseau, voir [réseau et planification de migration pour Office 365](network-and-migration-planning.md), [plan pour Office 365 dépannage des performances](performance-troubleshooting-plan.md)et [planification du pré-déploiement pour Office 365](deployment-planning-checklist.md) .</span><span class="sxs-lookup"><span data-stu-id="504b1-181">See [Network and migration planning for Office 365](network-and-migration-planning.md), [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md), and [Deployment planning checklist for Office 365](deployment-planning-checklist.md) for additional guidance on planning your network configuration.</span></span> 
  
### <a name="to-implement-this-scenario"></a><span data-ttu-id="504b1-182">Pour implémenter ce scénario :</span><span class="sxs-lookup"><span data-stu-id="504b1-182">To implement this scenario:</span></span>

<span data-ttu-id="504b1-p119">Renseignez-vous auprès de votre fournisseur de solution ou service réseau si ils peuvent utiliser des adresses URL dans Office 365 et définitions IP dans le fichier XML afin de faciliter faible local (à l’utilisateur), une surcharge réseau sortant pour le trafic d’Office 365, gérer sa priorité par rapport aux autres applications et ajuster le chemin d’accès réseau pour les connexions réseau Microsoft en fonction de la modification des conditions de réseau Office 365. Certaines solutions de téléchargent et automatisent Office 365 URL et IP XMLs définition dans leurs piles.</span><span class="sxs-lookup"><span data-stu-id="504b1-p119">Check with your network solution or service provider if they can use Office 365 URL and IP definitions from XML to facilitate local (to the user), low overhead network egress for Office 365 traffic, manage its priority relative to other applications and adjust the network path for Office 365 connections into Microsoft network depending on changing network conditions. Some solutions download and automate Office 365 URL and IP XMLs definition in their stacks.</span></span>
  
<span data-ttu-id="504b1-185">Assurez-vous de toujours que la mise en œuvre de la solution a besoin degré de résilience, redondance géographique appropriée le chemin d’accès réseau pour le trafic d’Office 365 et gère les modifications apportées à Office 365 URL et adresses IP lorsqu’elles sont publiées.</span><span class="sxs-lookup"><span data-stu-id="504b1-185">Always ensure that the implemented solution has necessary degree of resiliency, appropriate geo-redundancy of the network path for Office 365 traffic and accommodates changes to Office 365 URLs and IPs as they become published.</span></span>

## <a name="faq"></a><span data-ttu-id="504b1-186">FAQ</span><span class="sxs-lookup"><span data-stu-id="504b1-186">FAQ</span></span>

<span data-ttu-id="504b1-187">Questions fréquemment posées un administrateur sur la connectivité :</span><span class="sxs-lookup"><span data-stu-id="504b1-187">Frequently-asked administrator questions about connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="504b1-188">Comment soumettre une question ?</span><span class="sxs-lookup"><span data-stu-id="504b1-188">How do I submit a question?</span></span>

<span data-ttu-id="504b1-p120">Cliquez sur le lien en bas pour indiquer si l’article a été utile ou non et soumettre des questions supplémentaires. Nous surveiller les commentaires et mettre à jour les questions fréquemment posées.</span><span class="sxs-lookup"><span data-stu-id="504b1-p120">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="when-is-the-xml-file-updated"></a><span data-ttu-id="504b1-191">Lorsque est le fichier XML mis à jour ?</span><span class="sxs-lookup"><span data-stu-id="504b1-191">When is the XML file updated?</span></span>

<span data-ttu-id="504b1-p121">Annonce de nouveaux points de terminaison, il est généralement un tampon de 30 jours avant qu’ils sont efficaces et commencent à atteindre les demandes de réseau. Cette mémoire tampon est de garantir des clients et partenaires ont la possibilité de mettre à jour leurs systèmes. Nom de domaine complet et IP préfixe ajouts et suppressions sont traitées dans le fichier XML en même temps que l’annonce, ce qui signifie qu'un nouveau nom de domaine complet sera 30 jours avant des utiliser dans le fichier XML. Dans la mesure où nous arrêter l’envoi de demandes réseau aux points de terminaison que nous allons suppression avant l’annonce leur suppression, lors de la suppression du point de terminaison à partir du XML en même temps que l’annonce est déjà inutilisé.</span><span class="sxs-lookup"><span data-stu-id="504b1-p121">When new endpoints are announced, there is usually a 30+ day buffer before they are effective and network requests begin going to them. This buffer is to ensure customers and partners have an opportunity to update their systems. FQDN and IP prefix additions and removals are processed in the XML file at the same time as the announcement, meaning a new FQDN will be in the XML file 30 days before use. Since we stop sending network requests to endpoints we're removing prior to announcing their removal, when we remove the endpoint from the XML at the same time as the announcement it is already unused.</span></span>
  
### <a name="how-can-i-be-notified-of-changes"></a><span data-ttu-id="504b1-196">Comment puis-je être averti des modifications ?</span><span class="sxs-lookup"><span data-stu-id="504b1-196">How can I be notified of changes?</span></span>
<span data-ttu-id="504b1-197"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-197"></span></span>

<span data-ttu-id="504b1-p122">Points de terminaison Office 365 sont publiés à la fin de chaque mois à la notification de 30 jours. Il peut arriver que les modifications seront produit plusieurs fois par mois ou avec des périodes de notification. Lorsqu’un point de terminaison est ajouté, la date d’effet répertoriée dans le [flux RSS](https://go.microsoft.com/fwlink/p/?linkid=236301) correspond à la date après laquelle les demandes de réseau seront envoyés au point de terminaison. Si vous êtes au format RSS, voici comment [abonnez-vous via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) ou vous pouvez [faire](https://go.microsoft.com/fwlink/p/?LinkId=532417)en sorte envoyés par courrier électronique vous des mises à jour de flux RSS.</span><span class="sxs-lookup"><span data-stu-id="504b1-p122">Office 365 endpoints are published at the end of each month with 30 days notice. Occasionally changes will occur more than once a month or with shorter notice periods. When an endpoint is added, the effective date listed in the [RSS feed](https://go.microsoft.com/fwlink/p/?linkid=236301) is the date after which network requests will be sent to the endpoint. If you're new to RSS, here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>
  
### <a name="how-do-i-read-the-rss-change-log"></a><span data-ttu-id="504b1-202">Comment lire que RSS du journal des modifications ?</span><span class="sxs-lookup"><span data-stu-id="504b1-202">How do I read the RSS change log?</span></span>
<span data-ttu-id="504b1-203"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-203"></span></span>

<span data-ttu-id="504b1-p123">Une fois que vous vous abonner au flux RSS, vous pouvez analyser les informations vous-même ou avec un script. Le tableau suivant décrit le format du RSS flux o rendre plus facile.</span><span class="sxs-lookup"><span data-stu-id="504b1-p123">After you subscribe to the RSS feed, you can parse the information yourself or with a script. The following table describes the format of the RSS feed o make it easier.</span></span>
  
|<span data-ttu-id="504b1-206">**Section**</span><span class="sxs-lookup"><span data-stu-id="504b1-206">**Section**</span></span>|<span data-ttu-id="504b1-207">**Partie 1**</span><span class="sxs-lookup"><span data-stu-id="504b1-207">**Part 1**</span></span>|<span data-ttu-id="504b1-208">**Partie 2**</span><span class="sxs-lookup"><span data-stu-id="504b1-208">**Part 2**</span></span>|<span data-ttu-id="504b1-209">**Partie 3**</span><span class="sxs-lookup"><span data-stu-id="504b1-209">**Part 3**</span></span>|<span data-ttu-id="504b1-210">**Partie 4**</span><span class="sxs-lookup"><span data-stu-id="504b1-210">**Part 4**</span></span>|<span data-ttu-id="504b1-211">**Partie 5**</span><span class="sxs-lookup"><span data-stu-id="504b1-211">**Part 5**</span></span>|<span data-ttu-id="504b1-212">**Partie 6**</span><span class="sxs-lookup"><span data-stu-id="504b1-212">**Part 6**</span></span>|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="504b1-213">**Description**</span><span class="sxs-lookup"><span data-stu-id="504b1-213">**Description**</span></span> <br/> |<span data-ttu-id="504b1-214">Nombre</span><span class="sxs-lookup"><span data-stu-id="504b1-214">Count</span></span>  <br/> |<span data-ttu-id="504b1-215">Date après laquelle vous pouvez tirer les demandes réseau soient envoyées au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="504b1-215">Date after which you can expect network requests to be sent to the endpoint.</span></span>  <br/> |<span data-ttu-id="504b1-216">Description de la base de la fonctionnalité ou un service qui requiert le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="504b1-216">Basic description of the feature or service that requires the endpoint.</span></span>  <br/> |<span data-ttu-id="504b1-217">Pouvez-vous vous connecter à ce point de terminaison sur un ExpressRoute Circuit outre internet ?</span><span class="sxs-lookup"><span data-stu-id="504b1-217">Can you connect to this endpoint on an ExpressRoute Circuit in addition to the internet?</span></span>  <br/> |<span data-ttu-id="504b1-218">**Oui** , vous pouvez vous connecter à ce point de terminaison sur internet et ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="504b1-218">**Yes** - you can connect to this endpoint on both the internet and ExpressRoute.</span></span>  <br/> <span data-ttu-id="504b1-219">**No** : vous pouvez uniquement vous connecter à ce point de terminaison sur internet.</span><span class="sxs-lookup"><span data-stu-id="504b1-219">**No** - you can only connect to this endpoint on the internet.</span></span>  <br/> |<span data-ttu-id="504b1-220">Nom de domaine complet ou l’adresse IP plage de destination est ajouté ou supprimé.</span><span class="sxs-lookup"><span data-stu-id="504b1-220">The destination FQDN or IP range being added or removed.</span></span>  <br/> |
|<span data-ttu-id="504b1-221">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="504b1-221">**Example**</span></span> <br/> |<span data-ttu-id="504b1-222">1 /</span><span class="sxs-lookup"><span data-stu-id="504b1-222">1/</span></span>  <br/> |<span data-ttu-id="504b1-223">[Xx/xx/xxx efficace.</span><span class="sxs-lookup"><span data-stu-id="504b1-223">[Effective xx/xx/xxx.</span></span>  <br/> |<span data-ttu-id="504b1-224">Requis : \<description\>.</span><span class="sxs-lookup"><span data-stu-id="504b1-224">Required: \<description\>.</span></span>  <br/> |<span data-ttu-id="504b1-225">ExpressRoute :</span><span class="sxs-lookup"><span data-stu-id="504b1-225">ExpressRoute:</span></span>  <br/> |<span data-ttu-id="504b1-226">\<Oui/non\>.</span><span class="sxs-lookup"><span data-stu-id="504b1-226">\<Yes/No\>.</span></span>  <br/> |<span data-ttu-id="504b1-227">\<Nom de domaine complet/adresse IP\>],</span><span class="sxs-lookup"><span data-stu-id="504b1-227">\<FQDN/IP\>],</span></span>  <br/> |

<span data-ttu-id="504b1-228">Quelques éléments à noter, chaque entrée est un ensemble commun de délimiteurs :</span><span class="sxs-lookup"><span data-stu-id="504b1-228">A couple other things to note, every entry has a common set of delimiters:</span></span>
  
- <span data-ttu-id="504b1-229">**/**-après le nombre</span><span class="sxs-lookup"><span data-stu-id="504b1-229">**/** - after the count</span></span>
- <span data-ttu-id="504b1-230">**[-** pour indiquer l’entrée pour le nombre de</span><span class="sxs-lookup"><span data-stu-id="504b1-230">**[** - to indicate the entry for the count</span></span>
- <span data-ttu-id="504b1-p124">**.** -utilisés entre chaque section distincte de l’entrée</span><span class="sxs-lookup"><span data-stu-id="504b1-p124">**.** - used in between each distinct section of the entry</span></span>
- <span data-ttu-id="504b1-233">**],** - pour indiquer la fin d’une entrée unique</span><span class="sxs-lookup"><span data-stu-id="504b1-233">**],** - to indicate the end of a single entry</span></span>
- <span data-ttu-id="504b1-p125">**].** -Pour indiquer la fin de toutes les écritures</span><span class="sxs-lookup"><span data-stu-id="504b1-p125">**].** - To indicate the end of all the entries</span></span>

### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="504b1-236">Comment déterminer l’emplacement de mon client ?</span><span class="sxs-lookup"><span data-stu-id="504b1-236">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="504b1-237">**Emplacement du client** est déterminé mieux à l’aide de notre [mappage du centre de données](https://o365datacentermap.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="504b1-237">**Tenant location** is best determined using our [datacenter map](https://o365datacentermap.azurewebsites.net/).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="504b1-238">Est-ce que je homologue correctement avec Microsoft ?</span><span class="sxs-lookup"><span data-stu-id="504b1-238">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="504b1-239">**Emplacements Peering** sont décrites plus en détail dans [homologue avec Microsoft](https://www.microsoft.com/peering).</span><span class="sxs-lookup"><span data-stu-id="504b1-239">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="504b1-p126">Avec plus de 2500 relations homologation de fournisseur de services Internet global et 70 points de présence, prise en main de votre réseau de notre doit être transparente. Il ne peut pas nuire à quelques minutes assurant la que relation d’homologation votre fournisseur de services Internet est la plus optimale, [Voici quelques exemples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de bonnes et pas homologation livraisons à notre réseau.</span><span class="sxs-lookup"><span data-stu-id="504b1-p126">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a><span data-ttu-id="504b1-242">Comment déterminer quelles adresses IP accepter sur ExpressRoute ?</span><span class="sxs-lookup"><span data-stu-id="504b1-242">How do I determine which IP addresses to accept over ExpressRoute?</span></span>

 <span data-ttu-id="504b1-243">**Itinéraires ExpressRoute acceptées** sont définies par [les plages d’adresses IP de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602) et Office 365 spécifiques [des Communautés BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).</span><span class="sxs-lookup"><span data-stu-id="504b1-243">**Accepted ExpressRoute routes** are defined by [Microsoft's IP ranges](https://www.microsoft.com/download/details.aspx?id=53602) and the specific Office 365 [BGP communities](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).</span></span>
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a><span data-ttu-id="504b1-244">Comment déterminer les points de terminaison ai-je besoin ?</span><span class="sxs-lookup"><span data-stu-id="504b1-244">How do I determine which endpoints I need?</span></span>

<span data-ttu-id="504b1-p127">Nous régulièrement ajouter des nouvelles fonctionnalités et services à la suite Office 365, développer le paysage de connectivité. Si vous êtes abonné à la E3 ou SKU E5, simplicité de réfléchir à la liste des points de terminaison est que vous avez besoin de les obtenir toutes les fonctionnalités de la suite de toutes. Si vous n’êtes pas abonné à une de ces références la différence est minime en termes de nombre de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="504b1-p127">We regularly add new features and services to the Office 365 suite, expanding the connectivity landscape. If you're subscribed to the E3 or E5 SKU, the simple way to think about the list of endpoints is that you need all of them to get full functionality for the suite. If you aren't subscribed to either of these SKUs the difference is minimal in terms of the number of endpoints.</span></span>
  
<span data-ttu-id="504b1-248">Lisez les [Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md) pour obtenir plus d’informations sur les catégories de point de terminaison Office 365 et de comprendre les principes de connectivité pour gérer le trafic d’Office 365 en toute sécurité et d’obtenir les meilleures performances possibles.</span><span class="sxs-lookup"><span data-stu-id="504b1-248">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
<span data-ttu-id="504b1-p128">Dans l’image ci-dessous, vous pouvez voir un exemple d’une partie de la table de nom de domaine complet dans la section Office Online. Les lignes sont organisées par fonction et les différences de connectivité. Les deux premières lignes indiquent Office Online s’appuie sur les points de terminaison marqués requis dans Office 365 authentification et identité les portail et les sections partagé. Il s’agit par défaut d’un service dans Office 365 à s’appuyer sur ces services partagés. La troisième ligne indique les ordinateurs clients doivent être en mesure d’atteindre \*. officeapps.live.com à utiliser Office Online et la quatrième ligne indique ordinateurs doivent également être en mesure d’atteindre \*. cdn.office.net à utiliser Office Online.</span><span class="sxs-lookup"><span data-stu-id="504b1-p128">In the image below, you can see an example from a portion of the FQDN table in the Office Online section. The rows are organized by feature and differences in connectivity. The first two rows indicate Office Online relies on the endpoints marked Required in the Office 365 Authentication and Identity and portal and shared sections. This is typical for a service within Office 365 to rely on these shared services. The third row indicates client computers must be able to reach \*.officeapps.live.com to use Office Online and the fourth row indicates computers must also be able to reach \*.cdn.office.net to use Office Online.</span></span>
  
<span data-ttu-id="504b1-254">Bien que les deux de trois lignes et quatre sont requises pour utiliser Office Online, ils avoir été séparés pour indiquer que la destination est différente :</span><span class="sxs-lookup"><span data-stu-id="504b1-254">Even though both row three and four are required to use Office Online, they've been separated to indicate the destination is different:</span></span>
  
1. <span data-ttu-id="504b1-255">\*. officeapps.live.com ne représente pas un CDN, les demandes de sens à cet espace de noms seront affiche directement un centre de données Microsoft.</span><span class="sxs-lookup"><span data-stu-id="504b1-255">\*.officeapps.live.com does not represent a CDN, meaning requests to this namespace will go directly to a Microsoft datacenter.</span></span>
2. <span data-ttu-id="504b1-256">\*. officeapps.live.com est accessible sur circuits ExpressRoute à l’aide de Microsoft Peering.</span><span class="sxs-lookup"><span data-stu-id="504b1-256">\*.officeapps.live.com is accessible on ExpressRoute circuits using Microsoft Peering.</span></span>
3. <span data-ttu-id="504b1-257">Les adresses IP associées à Office Online et \*. officeapps.live.com sont accessibles en cliquant sur ce lien.</span><span class="sxs-lookup"><span data-stu-id="504b1-257">The IP addresses associated with Office Online and \*.officeapps.live.com can be found by following this link.</span></span>
4. <span data-ttu-id="504b1-258">\*. cdn.office.net représente un CDN hébergé par Akamai, les demandes de sens à cet espace de noms seront dirigés vers un centre de données Akamai.</span><span class="sxs-lookup"><span data-stu-id="504b1-258">\*.cdn.office.net represents a CDN hosted by Akamai, meaning requests to this namespace will go to an Akamai datacenter.</span></span>
5. <span data-ttu-id="504b1-259">\*. cdn.office.net n’est pas accessible sur circuits ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="504b1-259">\*.cdn.office.net is not accessible on ExpressRoute circuits.</span></span>
6. <span data-ttu-id="504b1-260">Les adresses IP associées à Office Online et \*. cdn.office.net ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="504b1-260">The IP addresses associated with Office Online and \*.cdn.office.net are not available.</span></span>

![Capture d’écran de la page points de terminaison](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="504b1-262">Je vois des demandes du réseau pour les adresses IP pas sur la liste publiée, ai-je besoin pour fournir leur accès ?</span><span class="sxs-lookup"><span data-stu-id="504b1-262">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="504b1-263"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-263"></span></span>

<span data-ttu-id="504b1-p129">Nous fournissons uniquement des adresses IP pour les serveurs Office 365 que vous devez acheminer directement vers via Internet ou ExpressRoute. Ce n’est pas une liste complète de toutes les adresses IP que vous verrez demandes réseau. Vous verrez les demandes réseau Microsoft et de tiers détenus, non publiés, les adresses IP. Ces adresses IP sont dynamiquement générés ou gérés d’une manière qui empêche l’avis de temps lorsqu’ils sont modifiés. Si votre pare-feu ne peut pas autoriser l’accès basé sur les noms de domaines complets pour ces demandes réseau, utilisez un fichier PAC ou WPAD pour gérer les demandes.</span><span class="sxs-lookup"><span data-stu-id="504b1-p129">We only provide IP addresses for the Office 365 servers you should route directly to over the Internet or ExpressRoute. This isn't a comprehensive list of all IP addresses you'll see network requests for. You'll see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="504b1-269">Voir qu'une adresse IP associée à Office 365 que vous souhaitez plus d’informations ?</span><span class="sxs-lookup"><span data-stu-id="504b1-269">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="504b1-270">Vérifier si l’adresse IP est incluse dans un plus grand nombre de publié à l’aide d’une [Calculatrice CIDR](http://jodies.de/ipcalc).</span><span class="sxs-lookup"><span data-stu-id="504b1-270">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
2. <span data-ttu-id="504b1-p130">Voir si un partenaire possède l’adresse IP avec une [requête whois](https://dnsquery.org/). S’il est propriété de Microsoft, il peut être un partenaire interne.</span><span class="sxs-lookup"><span data-stu-id="504b1-p130">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
3. <span data-ttu-id="504b1-p131">Vérifier le certificat, dans un navigateur se connecter à l’adresse IP à l’aide *HTTPS://\<adresse_IP\> * , vérifiez les domaines répertoriés dans le certificat de comprendre quels domaines associés avec l’adresse IP. S’il est Microsoft appartient l’adresse IP et pas dans la liste d’adresses IP de Office 365, il est probable que l’adresse IP associée à un CDN Microsoft tels que *MSOCDN.NET* ou un autre domaine Microsoft sans informations IP publiées. Si vous ne trouvez pas que le domaine sur le certificat est un où nous revendication à l’adresse IP, n’hésitez pas.</span><span class="sxs-lookup"><span data-stu-id="504b1-p131">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span>

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="504b1-276">Je reçois des noms tels que nsatc.net ou akadns.net dans les noms de domaine Microsoft</span><span class="sxs-lookup"><span data-stu-id="504b1-276">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="504b1-277"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-277"></span></span>

<span data-ttu-id="504b1-p132">Office 365 et autres services Microsoft utilisent plusieurs services de tiers tels que Akamai et MarkMonitor pour améliorer votre expérience avec Office 365. Pour conserver en donnant la meilleure expérience possible, nous pouvons modifier ces services à l’avenir. Ce faisant, nous publier souvent l’enregistrement CNAME qui pointe vers une tierce partie domaine détenu, un enregistrement ou l’adresse IP. Domaines de tiers peuvent héberger le contenu, comme un CDN, ou ils peuvent héberger un service, comme un service de gestion du trafic géographique. Lorsque vous voyez les connexions à des tiers, il se trouve sous la forme d’une redirection ou référence, pas une demande initiale à partir du client. Certains clients doivent s’assurer de cette forme de redirection et la redirection est autorisée à passer sans ajouter explicitement que la longue liste des services de tiers de noms de domaine complets potentiels peut utiliser.</span><span class="sxs-lookup"><span data-stu-id="504b1-p132">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="504b1-p133">La liste des services sujette à modification à tout moment. Les services en cours d’utilisation sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="504b1-p133">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="504b1-p134">[MarkMonitor](https://www.markmonitor.com/) est en cours d’utilisation lorsque vous voyez les demandes qui incluent \* \*. nsatc.net\* . Ce service fournit la protection des noms de domaine et de surveillance pour vous protéger contre les comportements malveillants.</span><span class="sxs-lookup"><span data-stu-id="504b1-p134">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span>
  
<span data-ttu-id="504b1-p135">[ExactTarget](https://www.marketingcloud.com/) est en cours d’utilisation lorsque vous voyez les demandes à \* \*. exacttarget.com\* . Ce service fournit la gestion de liens de messagerie et de surveillance par rapport à un comportement malveillant.</span><span class="sxs-lookup"><span data-stu-id="504b1-p135">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span>
  
<span data-ttu-id="504b1-p136">[Akamai](https://www.akamai.com/) est en cours d’utilisation lorsque vous voyez les demandes qui incluent un des noms de domaines complets suivants. Ce service offre géo-DNS et les services de réseau de distribution de contenu.</span><span class="sxs-lookup"><span data-stu-id="504b1-p136">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span>
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="what-are-the-three-types-of-office-365-endpoints"></a><span data-ttu-id="504b1-292">Quelles sont les trois types de points de terminaison Office 365 ?</span><span class="sxs-lookup"><span data-stu-id="504b1-292">What are the three types of Office 365 endpoints?</span></span>
<span data-ttu-id="504b1-293"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-293"></span></span>

- <span data-ttu-id="504b1-p137">Vous connecter à des services tiers pour récupérer des services internet de base telles que les recherches DNS et de récupération de contenu CDN. Vous également se connectez aux services de tiers pour intégrations telles que l’incorporation de vidéos YouTube dans votre bloc-notes OneNote.</span><span class="sxs-lookup"><span data-stu-id="504b1-p137">You connect to third-party services to retrieve basic internet services such as DNS lookups and CDN content retrieval. You also connect to third-party services for integrations such as incorporating YouTube videos in your OneNote notebooks.</span></span>
- <span data-ttu-id="504b1-p138">Vous connecter aux services secondaires hébergées et exécuté par Microsoft, tels que les nœuds edge qui permettent le réseau globale de Microsoft à l’emplacement internet le plus proche de votre demande de réseau à votre ordinateur. Comme le troisième plus grand réseau de la planète, il améliore votre connectivity. Vous également se connectez aux services Microsoft Azure tels que les Services de support Azure qui sont utilisés par de nombreux services Office 365.</span><span class="sxs-lookup"><span data-stu-id="504b1-p138">You connect to secondary services hosted and run by Microsoft such as edge nodes that enable your network request to enter Microsoft's global network at the closest internet location to your computer. As the third largest network on the planet, this improves your connectivity experience. You also connect to Microsoft Azure services such as Azure Media Services which are used by a variety of Office 365 services.</span></span>
- <span data-ttu-id="504b1-p139">Vous connecter à des services Office 365 principales tel que le serveur de boîtes aux lettres Exchange Online ou le Skype pour Online Business server où résident vos données confidentielles et uniques. Vous pouvez vous connecter aux services Office 365 principales par nom de domaine complet ou l’adresse IP et utiliser internet ou circuits ExpressRoute. Vous pouvez vous connecter uniquement les services secondaires à l’aide de noms de domaine complets sur un circuit internet tiers.</span><span class="sxs-lookup"><span data-stu-id="504b1-p139">You connect to primary Office 365 services such as the Exchange Online mailbox server or the Skype for Business Online server where your unique and proprietary data lives. You can connect to the primary Office 365 services by FQDN or IP address and use internet or ExpressRoute circuits. You can only connect to the third party and secondary services using FQDNs on an internet circuit.</span></span>

<span data-ttu-id="504b1-p140">Le diagramme suivant montre les différences entre ces zones service. Dans ce diagramme, le réseau du client local dans le coin inférieur gauche dispose de plusieurs périphériques réseau pour vous aider à gérer les connexions réseau. Configurations comme celui-ci sont courantes pour les clients en entreprise. Si votre réseau ne comporte qu’un pare-feu entre vos ordinateurs clients et internet, qui est également pris en charge, et vous souhaiterez Vérifiez que votre pare-feu peut prendre en charge des caractères génériques et les noms de domaines complets dans les règles de la liste verte.</span><span class="sxs-lookup"><span data-stu-id="504b1-p140">The following diagram shows the differences between these service areas. In this diagram, the customer on-premises network in the lower left has multiple network devices to assist in managing network connectivity. Configurations like this one are common for enterprise customers. If your network only has a firewall between your client computers and the internet, that's supported as well, and you'll want to ensure your firewall can support FQDNs and wildcards in the allow list rules.</span></span>
  
<span data-ttu-id="504b1-306">Lisez les [Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md) pour obtenir plus d’informations sur les catégories de point de terminaison Office 365 et de comprendre les principes de connectivité pour gérer le trafic d’Office 365 en toute sécurité et d’obtenir les meilleures performances possibles.</span><span class="sxs-lookup"><span data-stu-id="504b1-306">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
![Montre les trois types de points de terminaison de réseau lors de l’utilisation d’Office 365](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a><span data-ttu-id="504b1-308">Je ne peut pas ou ne voulez pas utiliser n’importe quel service tiers</span><span class="sxs-lookup"><span data-stu-id="504b1-308">I can't or don't want to use any third-party service</span></span>
<span data-ttu-id="504b1-309"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-309"></span></span>

<span data-ttu-id="504b1-p141">Office 365 est un ensemble de services intégrés à la fonction via internet, les fiabilité et disponibilité promesses basés sur de nombreux services internet standard disponibles. Par exemple, les services internet standard tels que DNS, révocation de certificats et CDN doivent être accessibles à utiliser Office 365 comme ils ne doivent être accessibles à utiliser les services internet plus modernes.</span><span class="sxs-lookup"><span data-stu-id="504b1-p141">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>
  
<span data-ttu-id="504b1-p142">Outre ces services internet de base, il existe des services tiers qui ne sont utilisées pour intégrer les fonctionnalités. Par exemple, à l’aide de Giphy.com au sein de Microsoft Teams permet de clients à inclure en toute transparence GIF au sein des équipes. De même, YouTube et Flickr sont les services tiers qui permettent d’intégrer en toute transparence des vidéo et des images dans les clients Office à partir d’internet. Alors que ceux-ci sont nécessaires pour l’intégration, ils sont marqués comme étant facultatifs dans l’article de points de terminaison Office 365 qui signifie que les fonctionnalités principales du service continuera de fonctionner, si le point de terminaison n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="504b1-p142">In addition to these basic internet services, there are third-party services that are only used to integrate functionality. For example, using Giphy.com within Microsoft Teams allows customers to seamlessly include Gifs within Teams. Similarly, YouTube and Flickr are third-party services that are used to seamlessly integrate video and images into Office clients from the internet. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible.</span></span>
  
<span data-ttu-id="504b1-316">Si vous tentez d’utiliser Office 365 et estiment services tiers ne sont pas accessibles, vous souhaiterez afin de [tous les noms de domaine complets marqués obligatoire ou facultatif dans cet article sont autorisées via le pare-feu et de proxy](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="504b1-316">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a><span data-ttu-id="504b1-317">Je ne peut pas ou ne voulez pas utiliser les services secondaires</span><span class="sxs-lookup"><span data-stu-id="504b1-317">I can't or don't want to use any secondary services</span></span>
<span data-ttu-id="504b1-318"><a name="bkmk_secondary"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-318"></span></span>

<span data-ttu-id="504b1-p143">Services secondaires sont Microsoft qui n’appartiennent pas à un contrôle Office 365. Il s’agit des éléments tels que le réseau de périmètre, Azure Media Services et réseaux de distribution de contenu Azure. Ceux-ci sont tous requis pour l’utilisation d’Office 365 et doivent être accessibles.</span><span class="sxs-lookup"><span data-stu-id="504b1-p143">Secondary services are Microsoft services that don't fall within Office 365 control. These are things like the edge network, Azure Media Services, and Azure Content Delivery Networks. These are all required to use Office 365 and must be reachable.</span></span>
  
<span data-ttu-id="504b1-322">Si vous tentez d’utiliser Office 365 et estiment services tiers ne sont pas accessibles, vous souhaiterez afin de [tous les noms de domaine complets marqués obligatoire ou facultatif dans cet article sont autorisées via le pare-feu et de proxy](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="504b1-322">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="504b1-323">Comment bloquer les accès aux services de consommateur de Microsoft ?</span><span class="sxs-lookup"><span data-stu-id="504b1-323">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="504b1-324"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="504b1-324"></span></span>

<span data-ttu-id="504b1-p144">Restriction de l’accès à nos services consommateur doit être effectuée à vos propres risques, l’uniquement fiable pour bloquer consommateur services consiste à restreindre l’accès à la *login.live.com* le nom de domaine complet. Ce nom de domaine complet est utilisé par un large éventail de services, notamment les services non consommateur comme MSDN, TechNet et d’autres personnes. Restriction de l’accès à ce nom de domaine complet peut entraîner le besoin d’inclure également des exceptions à la règle pour les demandes réseau associés à ces services.</span><span class="sxs-lookup"><span data-stu-id="504b1-p144">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span>
  
<span data-ttu-id="504b1-328">N’oubliez pas de blocage de l’accès aux services Microsoft consommateur uniquement ne sont pas empêcher la possibilité d’une personne de votre réseau aux informations exfiltrate à l’aide d’un client Office 365 ou un autre service.</span><span class="sxs-lookup"><span data-stu-id="504b1-328">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="504b1-329">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="504b1-329">Related Topics</span></span>

[<span data-ttu-id="504b1-330">Adresse IP de Office 365 et URL du service Web</span><span class="sxs-lookup"><span data-stu-id="504b1-330">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="504b1-331">Plages IP du centre de données Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="504b1-331">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="504b1-332">Espace d’adressage IP publique de Microsoft</span><span class="sxs-lookup"><span data-stu-id="504b1-332">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="504b1-333">Exigences relatives à l’infrastructure réseau pour Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="504b1-333">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="504b1-334">ExpressRoute et power BI</span><span class="sxs-lookup"><span data-stu-id="504b1-334">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="504b1-335">URL et plages d’adresses IP Office 365</span><span class="sxs-lookup"><span data-stu-id="504b1-335">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="504b1-336">Gestion d’ExpressRoute pour la connectivité d’Office 365</span><span class="sxs-lookup"><span data-stu-id="504b1-336">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="504b1-337">Principes de connectivité réseau Office 365</span><span class="sxs-lookup"><span data-stu-id="504b1-337">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)