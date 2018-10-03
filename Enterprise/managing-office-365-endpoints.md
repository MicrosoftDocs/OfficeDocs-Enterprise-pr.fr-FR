---
title: Gestion des points de terminaison Office 365
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
ms.openlocfilehash: a1a658ff04bc7306cb953477798d3e32d894d695
ms.sourcegitcommit: 854653f927c9515024a1c9e0a86fd5f2fadb92f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "25359496"
---
# <a name="managing-office-365-endpoints"></a>Gestion des points de terminaison Office 365

## <a name="office-365-network-connectivity"></a>Connectivité du réseau Office 365

 Connexions à Office 365 se composent de volume élevé, les demandes de réseau approuvé qui fonctionnent mieux si vous avez créé sur une sortie faible latence qui est proche de l’utilisateur. Certaines connexions Office 365 peuvent bénéficier de l’optimisation de la connexion. 
  
1. Vérifiez votre pare-feu Autoriser les listes Autoriser pour la connectivité aux points de terminaison Office 365.
    
2. Utilisez votre infrastructure de serveur proxy pour autoriser la connectivité Internet à caractères génériques et destinations annulées.
    
3. Mettre à jour une configuration de réseau de périmètre optimales.
    
4. [Assurez-vous que vous obtenez la meilleure connectivité](https://aka.ms/o365perfprinciples).
    
5. Lisez les [Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md) pour comprendre les principes de connectivité pour gérer le trafic d’Office 365 en toute sécurité et d’obtenir les meilleures performances possibles. 
    
![Connexion à Office 365 par le biais de pare-feu et des proxys.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a>Mise à jour du pare-feu de le sortant autoriser les listes

Vous pouvez optimiser votre réseau par l’envoi de que tous les approuvés demandes du réseau Office 365 directement via votre pare-feu, en ignorant inspection de niveau tous les paquets supplémentaires ou traitement. Cela réduit la baisse des performances de la latence et vos besoins en capacité de périmètre. Pour choisir le réseau qui demande à approuver le plus simple consiste à utiliser nos [fichiers PAC prédéfinis](managing-office-365-endpoints.md#pacfiles). 
  
Si votre pare-feu bloque le trafic sortant, vous souhaiterez garantir l’adresse IP et noms de domaine complets répertorié comme **requis** dans ce [fichier XML](https://go.microsoft.com/fwlink/?LinkId=533185) se trouvent sur la liste verte. Reconnaître que tous les services nécessitent l’utilisation de certains services tiers 3e. Nous ne pas fournir des adresses IP pour ces services tiers 3e tels que les fournisseurs de certificats fournisseurs, les réseaux de distribution de contenu, DNS et ainsi de suite. Pour toutes les fonctionnalités Office 365, vous devez être en mesure d’atteindre toutes les destinations demandées par Office 365, quelle que soit la quantité nous publier des informations sur la destination. 
  
Nombreuses destinations n’ont pas d’une adresse IP publiée ou sont répertoriées sous un domaine générique sans nom de domaine complet spécifique, pour utiliser cette fonctionnalité, vous devez être en mesure de résoudre ces demandes réseau à l’adresse IP en cours d’adresses demandé et envoyer le requête réseau via Internet.
  
Automatiser à l’aide d’un pare-feu qui analyse le fichier XML en votre nom et met à jour vos règles automatiquement basés sur les services et fonctionnalités que vous souhaitez acheminer directement via votre pare-feu. Vous pouvez également utiliser l’outil [Azure plage](https://azurerange.azurewebsites.net/) qui a été généré par la Communauté et analyse le code XML pour vous avec les options d’exportation de la configuration de la liste ACL ou Cisco XE, texte brut ou CSV. 
  
Une explication plus complète des destinations réseau est disponible sur le [site de référence](urls-and-ip-address-ranges.md) par le biais de notre [flux RSS en fonction de journal des modifications](https://go.microsoft.com/fwlink/p/?linkid=236301) afin que vous pouvez vous abonner aux modifications apportées. 
  
<a name="pacfiles"> </a>
## <a name="configure-outbound-paths-with-pac-files"></a>Configurer les chemins d’accès sortants avec fichiers PAC

Fichiers PAC ou WPAD permet de gérer les demandes de réseau qui sont associés à Office 365, mais n’ont pas une adresse IP fournie. Demandes de réseau par défaut qui sont envoyées via un périphérique proxy ou périmètre provoquer latence supplémentaire. Alors que l’authentification de proxy entraîne la plus grande taxe, les autres services tels que la recherche de réputation et les tentatives d’inspecter les paquets peuvent entraîner une expérience utilisateur médiocre. En outre, ces appareils de réseau de périmètre besoin une capacité suffisante pour traiter toutes les demandes réseau. Nous vous recommandons de contournement de votre infrastructure de serveur proxy ou inspection pour les demandes de réseau directs Office 365.
  
Utilisez un des fichiers de notre PAC comme point de départ pour déterminer le trafic réseau est envoyé à un proxy et qui sera envoyé à un pare-feu. Si vous ne connaissez pas les fichiers PAC ou WPAD, lisez ce billet sur les [fichiers de déploiement PAC](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) parmi nos consultants Office 365. Vous souhaiterez passer en revue ces comme point de départ et modifier en fonction de votre environnement. 
  
 **Fichiers PAC 7/10/2018 de mise à jour**. 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a>#1 - fichier PAC : sépare requis des noms de domaine complets Internet à partir de connus Office 365 nom de domaine complet.

Le premier exemple est une démonstration de notre approche recommandée pour la gestion des points de terminaison via Internet uniquement. Ignore le proxy pour Office 365 destinations où l’adresse IP est publiée et envoie des demandes réseau restants au proxy.
  
Extrait de code :

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

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a>#2 - fichier PAC : se connecter à Office 365 via Internet et ExpressRoute
<a name="bkmk_inet-aer"> </a>

Le second exemple est une démonstration de notre approche recommandée pour la gestion des connexions lorsque des circuits ExpressRoute et Internet sont disponibles. Envoie ExpressRoute destinations le circuit ExpressRoute et Internet uniquement destinations au proxy.
  
Extrait de code :

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

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a>#3 - fichier PAC : gérer toutes les destinations d’Office 365 collectivement
<a name="bkmk_inet-direct"> </a>

Le troisième exemple illustre l’envoi de toutes les demandes du réseau associées à Office 365 vers une destination unique. Cela est généralement utilisé pour ignorer l’inspection toutes les demandes du réseau Office 365 et offre un format où tous les points de terminaison publiés êtes-vous dans le format PAC à utiliser pour la personnalisation de votre liste.
  
Extrait de code :

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

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a>Utiliser des scripts personnalisés ou manuellement créer vos propres fichiers PAC
<a name="pacfiles_manual"> </a>

Voici quelques autres outils de la Communauté, si vous avez créé quelque chose que vous souhaitez partager laisser une note dans les commentaires. None de la Communauté outils référencés dans cet article sont officiellement pris en charge ou mis à jour par Microsoft et sont fournies ici pour votre commodité.
  
- Il s’agit de l’outil généré par la Communauté le plus ancien pour aider à gérer le processus, un outil intégré par un membre de la Communauté Office 365. Voici le lien pour [Télécharger](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).
    
- Preuve de Concept avec des règles de pare-feu exportable : [API de Microsoft Cloud IP](https://mscloudips.azurewebsites.net/).
    
- À partir de l’informatique Praktyk : [Conversion RSS](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) et [conversion XML](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).
    
- À partir de Peter Abele : [Télécharger](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).
    
- Utilisez votre analyse réseau pour déterminer quel réseau demande doit ignorer votre infrastructure de serveur proxy. Noms de domaines complets les plus courantes utilisées pour contourner les proxys de client incluent les éléments suivants en raison du volume de trafic réseau envoyé et reçu à partir de ces points de terminaison.
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  ```

- Vérifiez que toutes les demandes de réseau en cours envoyées directement à votre pare-feu ont une entrée correspondante dans le pare-feu Autoriser la demande par le biais de liste verte.

## <a name="perimeter-network-integration"></a>Intégration de réseau de périmètre
<a name="BKMK_Perimeter"> </a>

Savez-vous de Microsoft WAN appartient aux plus grandes dorsales principales dans le monde ?
  
Il est vrai que ce réseau massif fait Office 365 et autres services en nuage fonctionne indépendamment où dans le monde, que vous êtes. Notre réseau se compose de bande passante élevée, faible latence, liens capables de basculement avec des milliers de kilomètres d’itinéraire de Fibre foncé privée et multi-to les connexions entre les nœuds de centres de données et le bord, toutes les rendre plus facile à utiliser les services en nuage.
  
Avec un réseau similaire à celle-ci, que vous souhaitez vous connecter à notre réseau dès que possible aux périphériques de votre organisation. Avec plus de 2500 relations homologation de fournisseur de services Internet global et 70 points de présence, prise en main de votre réseau de notre doit être transparente. Il ne peut pas nuire à quelques minutes assurant la que relation d’homologation votre fournisseur de services Internet est la plus optimale, [Voici quelques exemples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de bonnes et pas homologation livraisons à notre réseau. 
  
Vous pouvez manuellement ou automatiquement configurez les périphériques de votre réseau d’optimiser la gestion des demandes de réseau application Office 365, en fonction de votre matériel. Les modifications de configuration que vous devez apporter à mieux gérer le trafic réseau de Office 365 dépend de votre environnement. Office 365 réseau demandes peuvent bénéficier des configurations de réseau qui autorisent les éléments suivants :
  
- Priorité sur le trafic réseau moins importante.
    
- Routage vers une sortie locale pour éviter les backhauling sur un réseau étendu lent lien tout en tirant parti de la latence faible disponible sur le réseau Microsoft. [Voici une bonne description](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) selon les engagements clients. 
    
- Avec DNS vers une sortie locale pour s’assurer de la demande de réseau qui conserve la sortie locale arrive à l’emplacement homologation Microsoft le plus proche.
    
- Exclusion d’approfondie des paquets ou autres traitement pour répondre aux exigences de latence à l’échelle des paquets réseau intensive.
    
Périphériques réseau modernes incluent des fonctionnalités pour gérer les demandes de réseau pour les applications approuvées, tels qu’Office 365 différemment le trafic Internet générique, non approuvé. Avec le paysage émergent des solutions de réseau étendu SD, telle différenciation de sélection du trafic et le chemin d’accès peut également être effectuée avec le changement d’état du réseau comme point de la disponibilité du temps, la latence ou les performances des différents chemins d’accès de connectivité de sensibilisation entre l’utilisateur et le nuage.
  
Pour plus d’instructions sur la planification de votre configuration réseau, voir [réseau et planification de migration pour Office 365](network-and-migration-planning.md), [plan pour Office 365 dépannage des performances](performance-troubleshooting-plan.md)et [planification du pré-déploiement pour Office 365](deployment-planning-checklist.md) . 
  
### <a name="to-implement-this-scenario"></a>Pour implémenter ce scénario :

Renseignez-vous auprès de votre fournisseur de solution ou service réseau si ils peuvent utiliser des adresses URL dans Office 365 et définitions IP dans le fichier XML afin de faciliter faible local (à l’utilisateur), une surcharge réseau sortant pour le trafic d’Office 365, gérer sa priorité par rapport aux autres applications et ajuster le chemin d’accès réseau pour les connexions réseau Microsoft en fonction de la modification des conditions de réseau Office 365. Certaines solutions de téléchargent et automatisent Office 365 URL et IP XMLs définition dans leurs piles.
  
Assurez-vous de toujours que la mise en œuvre de la solution a besoin degré de résilience, redondance géographique appropriée le chemin d’accès réseau pour le trafic d’Office 365 et gère les modifications apportées à Office 365 URL et adresses IP lorsqu’elles sont publiées.

## <a name="faq"></a>FAQ

Questions fréquemment posées un administrateur sur la connectivité :
  
### <a name="how-do-i-submit-a-question"></a>Comment soumettre une question ?

Cliquez sur le lien en bas pour indiquer si l’article a été utile ou non et soumettre des questions supplémentaires. Nous surveiller les commentaires et mettre à jour les questions fréquemment posées.
  
### <a name="when-is-the-xml-file-updated"></a>Lorsque est le fichier XML mis à jour ?

Annonce de nouveaux points de terminaison, il est généralement un tampon de 30 jours avant qu’ils sont efficaces et commencent à atteindre les demandes de réseau. Cette mémoire tampon est de garantir des clients et partenaires ont la possibilité de mettre à jour leurs systèmes. Nom de domaine complet et IP préfixe ajouts et suppressions sont traitées dans le fichier XML en même temps que l’annonce, ce qui signifie qu'un nouveau nom de domaine complet sera 30 jours avant des utiliser dans le fichier XML. Dans la mesure où nous arrêter l’envoi de demandes réseau aux points de terminaison que nous allons suppression avant l’annonce leur suppression, lors de la suppression du point de terminaison à partir du XML en même temps que l’annonce est déjà inutilisé.
  
### <a name="how-can-i-be-notified-of-changes"></a>Comment puis-je être averti des modifications ?
<a name="bkmk_changes"> </a>

Points de terminaison Office 365 sont publiés à la fin de chaque mois à la notification de 30 jours. Il peut arriver que les modifications seront produit plusieurs fois par mois ou avec des périodes de notification. Lorsqu’un point de terminaison est ajouté, la date d’effet répertoriée dans le [flux RSS](https://go.microsoft.com/fwlink/p/?linkid=236301) correspond à la date après laquelle les demandes de réseau seront envoyés au point de terminaison. Si vous êtes au format RSS, voici comment [abonnez-vous via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) ou vous pouvez [faire](https://go.microsoft.com/fwlink/p/?LinkId=532417)en sorte envoyés par courrier électronique vous des mises à jour de flux RSS.
  
### <a name="how-do-i-read-the-rss-change-log"></a>Comment lire que RSS du journal des modifications ?
<a name="bkmk_changes"> </a>

Une fois que vous vous abonner au flux RSS, vous pouvez analyser les informations vous-même ou avec un script. Le tableau suivant décrit le format du RSS flux o rendre plus facile.
  
|**Section**|**Partie 1**|**Partie 2**|**Partie 3**|**Partie 4**|**Partie 5**|**Partie 6**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**Description** <br/> |Nombre  <br/> |Date après laquelle vous pouvez tirer les demandes réseau soient envoyées au point de terminaison.  <br/> |Description de la base de la fonctionnalité ou un service qui requiert le point de terminaison.  <br/> |Pouvez-vous vous connecter à ce point de terminaison sur un ExpressRoute Circuit outre internet ?  <br/> |**Oui** , vous pouvez vous connecter à ce point de terminaison sur internet et ExpressRoute.  <br/> **No** : vous pouvez uniquement vous connecter à ce point de terminaison sur internet.  <br/> |Nom de domaine complet ou l’adresse IP plage de destination est ajouté ou supprimé.  <br/> |
|**Exemple** <br/> |1 /  <br/> |[Xx/xx/xxx efficace.  <br/> |Requis : \<description\>.  <br/> |ExpressRoute :  <br/> |\<Oui/non\>.  <br/> |\<Nom de domaine complet/adresse IP\>],  <br/> |

Quelques éléments à noter, chaque entrée est un ensemble commun de délimiteurs :
  
- **/**-après le nombre
- **[-** pour indiquer l’entrée pour le nombre de
- **.** -utilisés entre chaque section distincte de l’entrée
- **],** - pour indiquer la fin d’une entrée unique
- **].** -Pour indiquer la fin de toutes les écritures

### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Comment déterminer l’emplacement de mon client ?

 **Emplacement du client** est déterminé mieux à l’aide de notre [mappage du centre de données](https://o365datacentermap.azurewebsites.net/).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Est-ce que je homologue correctement avec Microsoft ?

 **Emplacements Peering** sont décrites plus en détail dans [homologue avec Microsoft](https://www.microsoft.com/peering).
  
Avec plus de 2500 relations homologation de fournisseur de services Internet global et 70 points de présence, prise en main de votre réseau de notre doit être transparente. Il ne peut pas nuire à quelques minutes assurant la que relation d’homologation votre fournisseur de services Internet est la plus optimale, [Voici quelques exemples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) de bonnes et pas homologation livraisons à notre réseau. 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a>Comment déterminer quelles adresses IP accepter sur ExpressRoute ?

 **Itinéraires ExpressRoute acceptées** sont définies par [les plages d’adresses IP de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602) et Office 365 spécifiques [des Communautés BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a>Comment déterminer les points de terminaison ai-je besoin ?

Nous régulièrement ajouter des nouvelles fonctionnalités et services à la suite Office 365, développer le paysage de connectivité. Si vous êtes abonné à la E3 ou SKU E5, simplicité de réfléchir à la liste des points de terminaison est que vous avez besoin de les obtenir toutes les fonctionnalités de la suite de toutes. Si vous n’êtes pas abonné à une de ces références la différence est minime en termes de nombre de points de terminaison.
  
Lisez les [Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md) pour obtenir plus d’informations sur les catégories de point de terminaison Office 365 et de comprendre les principes de connectivité pour gérer le trafic d’Office 365 en toute sécurité et d’obtenir les meilleures performances possibles. 
  
Dans l’image ci-dessous, vous pouvez voir un exemple d’une partie de la table de nom de domaine complet dans la section Office Online. Les lignes sont organisées par fonction et les différences de connectivité. Les deux premières lignes indiquent Office Online s’appuie sur les points de terminaison marqués requis dans Office 365 authentification et identité les portail et les sections partagé. Il s’agit par défaut d’un service dans Office 365 à s’appuyer sur ces services partagés. La troisième ligne indique les ordinateurs clients doivent être en mesure d’atteindre \*. officeapps.live.com à utiliser Office Online et la quatrième ligne indique ordinateurs doivent également être en mesure d’atteindre \*. cdn.office.net à utiliser Office Online.
  
Bien que les deux de trois lignes et quatre sont requises pour utiliser Office Online, ils avoir été séparés pour indiquer que la destination est différente :
  
1. \*. officeapps.live.com ne représente pas un CDN, les demandes de sens à cet espace de noms seront affiche directement un centre de données Microsoft.
2. \*. officeapps.live.com est accessible sur circuits ExpressRoute à l’aide de Microsoft Peering.
3. Les adresses IP associées à Office Online et \*. officeapps.live.com sont accessibles en cliquant sur ce lien.
4. \*. cdn.office.net représente un CDN hébergé par Akamai, les demandes de sens à cet espace de noms seront dirigés vers un centre de données Akamai.
5. \*. cdn.office.net n’est pas accessible sur circuits ExpressRoute.
6. Les adresses IP associées à Office Online et \*. cdn.office.net ne sont pas disponibles.

![Capture d’écran de la page points de terminaison](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Je vois des demandes du réseau pour les adresses IP pas sur la liste publiée, ai-je besoin pour fournir leur accès ?
<a name="bkmk_MissingIP"> </a>

Nous fournissons uniquement des adresses IP pour les serveurs Office 365 que vous devez acheminer directement vers via Internet ou ExpressRoute. Ce n’est pas une liste complète de toutes les adresses IP que vous verrez demandes réseau. Vous verrez les demandes réseau Microsoft et de tiers détenus, non publiés, les adresses IP. Ces adresses IP sont dynamiquement générés ou gérés d’une manière qui empêche l’avis de temps lorsqu’ils sont modifiés. Si votre pare-feu ne peut pas autoriser l’accès basé sur les noms de domaines complets pour ces demandes réseau, utilisez un fichier PAC ou WPAD pour gérer les demandes.
  
Voir qu'une adresse IP associée à Office 365 que vous souhaitez plus d’informations ?
  
1. Vérifier si l’adresse IP est incluse dans un plus grand nombre de publié à l’aide d’une [Calculatrice CIDR](http://jodies.de/ipcalc).
2. Voir si un partenaire possède l’adresse IP avec une [requête whois](https://dnsquery.org/). S’il est propriété de Microsoft, il peut être un partenaire interne.
3. Vérifier le certificat, dans un navigateur se connecter à l’adresse IP à l’aide *HTTPS://\<adresse_IP\> * , vérifiez les domaines répertoriés dans le certificat de comprendre quels domaines associés avec l’adresse IP. S’il est Microsoft appartient l’adresse IP et pas dans la liste d’adresses IP de Office 365, il est probable que l’adresse IP associée à un CDN Microsoft tels que *MSOCDN.NET* ou un autre domaine Microsoft sans informations IP publiées. Si vous ne trouvez pas que le domaine sur le certificat est un où nous revendication à l’adresse IP, n’hésitez pas.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Je reçois des noms tels que nsatc.net ou akadns.net dans les noms de domaine Microsoft
<a name="bkmk_akamai"> </a>

Office 365 et autres services Microsoft utilisent plusieurs services de tiers tels que Akamai et MarkMonitor pour améliorer votre expérience avec Office 365. Pour conserver en donnant la meilleure expérience possible, nous pouvons modifier ces services à l’avenir. Ce faisant, nous publier souvent l’enregistrement CNAME qui pointe vers une tierce partie domaine détenu, un enregistrement ou l’adresse IP. Domaines de tiers peuvent héberger le contenu, comme un CDN, ou ils peuvent héberger un service, comme un service de gestion du trafic géographique. Lorsque vous voyez les connexions à des tiers, il se trouve sous la forme d’une redirection ou référence, pas une demande initiale à partir du client. Certains clients doivent s’assurer de cette forme de redirection et la redirection est autorisée à passer sans ajouter explicitement que la longue liste des services de tiers de noms de domaine complets potentiels peut utiliser.
  
La liste des services sujette à modification à tout moment. Les services en cours d’utilisation sont les suivantes :
  
[MarkMonitor](https://www.markmonitor.com/) est en cours d’utilisation lorsque vous voyez les demandes qui incluent * \*. nsatc.net* . Ce service fournit la protection des noms de domaine et de surveillance pour vous protéger contre les comportements malveillants.
  
[ExactTarget](https://www.marketingcloud.com/) est en cours d’utilisation lorsque vous voyez les demandes à * \*. exacttarget.com* . Ce service fournit la gestion de liens de messagerie et de surveillance par rapport à un comportement malveillant.
  
[Akamai](https://www.akamai.com/) est en cours d’utilisation lorsque vous voyez les demandes qui incluent un des noms de domaines complets suivants. Ce service offre géo-DNS et les services de réseau de distribution de contenu.
  
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

### <a name="what-are-the-three-types-of-office-365-endpoints"></a>Quelles sont les trois types de points de terminaison Office 365 ?
<a name="bkmk_akamai"> </a>

- Vous connecter à des services tiers pour récupérer des services internet de base telles que les recherches DNS et de récupération de contenu CDN. Vous également se connectez aux services de tiers pour intégrations telles que l’incorporation de vidéos YouTube dans votre bloc-notes OneNote.
- Vous connecter aux services secondaires hébergées et exécuté par Microsoft, tels que les nœuds edge qui permettent le réseau globale de Microsoft à l’emplacement internet le plus proche de votre demande de réseau à votre ordinateur. Comme le troisième plus grand réseau de la planète, il améliore votre connectivity. Vous également se connectez aux services Microsoft Azure tels que les Services de support Azure qui sont utilisés par de nombreux services Office 365.
- Vous connecter à des services Office 365 principales tel que le serveur de boîtes aux lettres Exchange Online ou le Skype pour Online Business server où résident vos données confidentielles et uniques. Vous pouvez vous connecter aux services Office 365 principales par nom de domaine complet ou l’adresse IP et utiliser internet ou circuits ExpressRoute. Vous pouvez vous connecter uniquement les services secondaires à l’aide de noms de domaine complets sur un circuit internet tiers.

Le diagramme suivant montre les différences entre ces zones service. Dans ce diagramme, le réseau du client local dans le coin inférieur gauche dispose de plusieurs périphériques réseau pour vous aider à gérer les connexions réseau. Configurations comme celui-ci sont courantes pour les clients en entreprise. Si votre réseau ne comporte qu’un pare-feu entre vos ordinateurs clients et internet, qui est également pris en charge, et vous souhaiterez Vérifiez que votre pare-feu peut prendre en charge des caractères génériques et les noms de domaines complets dans les règles de la liste verte.
  
Lisez les [Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md) pour obtenir plus d’informations sur les catégories de point de terminaison Office 365 et de comprendre les principes de connectivité pour gérer le trafic d’Office 365 en toute sécurité et d’obtenir les meilleures performances possibles. 
  
![Montre les trois types de points de terminaison de réseau lors de l’utilisation d’Office 365](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a>Je ne peut pas ou ne voulez pas utiliser n’importe quel service tiers
<a name="bkmk_thirdparty"> </a>

Office 365 est un ensemble de services intégrés à la fonction via internet, les fiabilité et disponibilité promesses basés sur de nombreux services internet standard disponibles. Par exemple, les services internet standard tels que DNS, révocation de certificats et CDN doivent être accessibles à utiliser Office 365 comme ils ne doivent être accessibles à utiliser les services internet plus modernes.
  
Outre ces services internet de base, il existe des services tiers qui ne sont utilisées pour intégrer les fonctionnalités. Par exemple, à l’aide de Giphy.com au sein de Microsoft Teams permet de clients à inclure en toute transparence GIF au sein des équipes. De même, YouTube et Flickr sont les services tiers qui permettent d’intégrer en toute transparence des vidéo et des images dans les clients Office à partir d’internet. Alors que ceux-ci sont nécessaires pour l’intégration, ils sont marqués comme étant facultatifs dans l’article de points de terminaison Office 365 qui signifie que les fonctionnalités principales du service continuera de fonctionner, si le point de terminaison n’est pas accessible.
  
Si vous tentez d’utiliser Office 365 et estiment services tiers ne sont pas accessibles, vous souhaiterez afin de [tous les noms de domaine complets marqués obligatoire ou facultatif dans cet article sont autorisées via le pare-feu et de proxy](urls-and-ip-address-ranges.md).
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a>Je ne peut pas ou ne voulez pas utiliser les services secondaires
<a name="bkmk_secondary"> </a>

Services secondaires sont Microsoft qui n’appartiennent pas à un contrôle Office 365. Il s’agit des éléments tels que le réseau de périmètre, Azure Media Services et réseaux de distribution de contenu Azure. Ceux-ci sont tous requis pour l’utilisation d’Office 365 et doivent être accessibles.
  
Si vous tentez d’utiliser Office 365 et estiment services tiers ne sont pas accessibles, vous souhaiterez afin de [tous les noms de domaine complets marqués obligatoire ou facultatif dans cet article sont autorisées via le pare-feu et de proxy](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Comment bloquer les accès aux services de consommateur de Microsoft ?
<a name="bkmk_consumer"> </a>

Restriction de l’accès à nos services consommateur doit être effectuée à vos propres risques, l’uniquement fiable pour bloquer consommateur services consiste à restreindre l’accès à la *login.live.com* le nom de domaine complet. Ce nom de domaine complet est utilisé par un large éventail de services, notamment les services non consommateur comme MSDN, TechNet et d’autres personnes. Restriction de l’accès à ce nom de domaine complet peut entraîner le besoin d’inclure également des exceptions à la règle pour les demandes réseau associés à ces services.
  
N’oubliez pas de blocage de l’accès aux services Microsoft consommateur uniquement ne sont pas empêcher la possibilité d’une personne de votre réseau aux informations exfiltrate à l’aide d’un client Office 365 ou un autre service.
  
## <a name="related-topics"></a>Voir aussi

[Service web d’URL et d’adresses IP Office 365](office-365-ip-web-service.md)

[Plages d’adresses IP du centre de données Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Espace d’adresse IP public de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Exigences relatives à l’infrastructure réseau pour Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute et power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Principes de connectivité réseau Office 365](office-365-network-connectivity-principles.md)