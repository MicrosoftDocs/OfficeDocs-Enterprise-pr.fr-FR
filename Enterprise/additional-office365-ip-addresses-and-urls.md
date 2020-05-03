---
title: Points de terminaison supplémentaires non inclus dans le service web pour URL et adresses IP Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/29/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: 'Résumé : Le nouveau service web de point de terminaison n’inclut pas certains points de terminaison pour des scénarios spécifiques.'
hideEdit: true
ms.openlocfilehash: 4d67d67c3f1c0eb6aa8079dbbdc0d964274af48b
ms.sourcegitcommit: 93d0cc401c9d910e115072c0229232765fbad75e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "43939599"
---
# <a name="additional-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>Points de terminaison supplémentaires non inclus dans le service web pour URL et adresses IP Office 365

Certains points de terminaison réseau ont été publiés précédemment et n’ont pas été inclus dans le [service web pour URL et adresse IP d’Office 365](office-365-ip-web-service.md). La portée du service web correspond aux points de terminaison réseau requis pour la connectivité à partir d’un utilisateur final d’Office 365 au sein d’un réseau de périmètre d’entreprise. À l’heure actuelle, ceci n’inclut pas les éléments suivants :

1. connectivité réseau pouvant être requise d’un centre de données Microsoft vers un réseau client (trafic réseau de serveur hybride entrant) ;
2. connectivité réseau de serveurs sur un réseau client au sein du périmètre d’entreprise (trafic réseau de serveur sortant) ;
3. rares scénarios d’exigences de connectivité réseau de la part d’un utilisateur ;
4. exigences en matière de connectivité de résolution DNS (non répertorié ci-dessous) ;
5. sites approuvés Internet Explorer ou Microsoft Edge.

À part le DNS, ces éléments sont tous facultatifs pour la plupart des clients, sauf si vous recherchez le scénario spécifique décrit.

|||||
|:-----|:-----|:-----|:-----|
| **Ligne** | **Objectif** | **Destination** | **Type** |
| 1  | [Importer un service](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) pour l’ingestion de fichier et de fichiers PST | Reportez-vous au [service d’importation](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) pour obtenir les exigences supplémentaires. | Scénario sortant rare |
| 2  | [Assistant Support et récupération de Microsoft pour Office 365](https://diagnostics.office.com/#/)  | https<span>://</span>autodiscover.outlook.com <BR> <span>https://</span>officecdn.microsoft.com <BR> <span>https://</span>api.diagnostics.office.com <BR> <span>https://</span>apibasic.diagnostics.office.com <BR> <span>https://</span>autodiscover-s.outlook.com <BR> <span>https://</span>cloudcheckenabler.azurewebsites.net <BR> <span>https://</span>dcs-staging.azure-api.net <BR> <span>https://</span>login.live.com <BR> <span>https://</span>login.microsoftonline.com <BR> <span>https://</span>login.windows.net <BR> <span>https://</span>o365diagtelemetry.trafficmanager.net <BR> <span>https://</span>odc.officeapps.live.com <BR> <span>https://</span>offcatedge.azureedge.net <BR> <span>https://</span>officeapps.live.com <BR> <span>https://</span>outlook.office365.com <BR> <span>https://</span>outlookdiagnostics.azureedge.net | Trafic serveur sortant |
| 3  | Azure AD Connect (avec option d’authentification unique) - WinRM et PowerShell distant | Environnement STS client (serveur AD FS et proxy AD FS) \| Ports TCP 80 et 443 | Trafic serveur entrant |
| 4  | STS, comme des serveurs proxy AD FS (pour les clients fédérés uniquement) | STS client (comme un proxy AD FS) \| Ports TCP 443 ou TCP 49443 avec ClientTLS | Trafic serveur entrant |
| 5  | [Intégration de la messagerie unifiée Exchange Online/SBC](https://technet.microsoft.com/library/jj673565.aspx) | Bidirectionnel entre le contrôleur de bordure de session local et *.um.outlook.com | Trafic serveur sortant uniquement |
| 6  | Migration de la boîte aux lettres. Lorsque la migration de la boîte aux lettres est établie à partir de la version locale [Exchange hybride](https://docs.microsoft.com/exchange/exchange-deployment-assistant) vers Office 365, Office 365 se connecte à votre serveur de services web Exchange (EWS)/services de réplication de boîte aux lettres (MRS) publiés. Si vous souhaitez que les adresses IP NAT utilisées par les serveurs Exchange Online restreignent les connexions entrantes à partir de plages d’adresses IP source spécifiques, celles-ci sont répertoriées dans [plages URL et IP Office 365](urls-and-ip-address-ranges.md) sous la zone de service "Exchange Online". Des précautions particulières doivent être prises pour garantir que l’accès aux points de terminaison EWS publiés comme OWA n’est pas impacté en vérifiant que le proxy MRS se résolve en un nom de domaine complet et adresse IP publique distincts avant de restreindre les connexions TCP 443 à partir de plages d’adresses IP source spécifiques. | Proxy EWS/MRS local client<br> Port TCP 443. | Trafic serveur entrant |
| 7  | Fonctions de coexistence [Exchange hybride](https://docs.microsoft.com/exchange/exchange-deployment-assistant) telles que le partage de disponibilité. | Serveur Exchange client local | Trafic serveur entrant |
| 8  | Authentification de proxy [Exchange hybride](https://docs.microsoft.com/exchange/exchange-deployment-assistant) | STS local client | Trafic serveur entrant |
| 9  | Utilisé pour configurer [Exchange hybride](https://docs.microsoft.com/exchange/exchange-deployment-assistant), à l’aide de [l’Assistant Configuration d’Exchange hybride](https://docs.microsoft.com/exchange/hybrid-configuration-wizard) <br> Remarque : ces points de terminaison sont uniquement nécessaires pour configurer Exchange hybride  | domains.live.com sur les ports TCP 80 et 443, obligatoire uniquement pour l’Assistant Configuration hybride Exchange 2010 SP3.<BR> <BR> GCC High, DoD IP addresses: 40.118.209.192/32; 168.62.190.41/32 <BR> <BR> Commercial dans le monde entier & GCC : *.store.core.windows.net; asl.configure.office.com; mshrcstorageprod.blob.core.windows.net; tds.configure.office.com; mshybridservice.trafficmanager.net <BR>  | Trafic serveur sortant uniquement |
| 10  | Le service de détection automatique est utilisé dans des scénarios [Exchange hybride](https://docs.microsoft.com/exchange/exchange-deployment-assistant) avec [l’authentification moderne hybride avec Outlook pour iOS et Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth). <BR> <BR> ```*.acompli.net``` <BR> <BR> ```*.outlookmobile.com``` <BR> <BR> ```*.outlookmobile.us``` <BR> <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> | Serveur Exchange client local sur TCP 443 | Trafic serveur entrant |
| 11  | Skype Entreprise dans Office 2016 inclut un partage d’écran vidéo qui utilise des ports UDP. Les clients Skype Entreprise précédents dans Office 2013 et versions antérieures ont utilisé RDP sur le port TCP 443. | Port TCP 443 s’ouvrant sur 52.112.0.0/14 | Versions de clients plus anciens Skype Entreprise dans Office 2013 et versions antérieures |
| 12  | Connectivité de serveur local hybride Skype Entreprise à Skype Entreprise Online | 13.107.64.0/18, 52.112.0.0/14  <BR> Ports UDP 50,000-59,999 <BR>  Ports TCP 50,000-59,999 ; 5061 | Connectivité sortante de serveur local Skype Entreprise |
| 13  | Le RTC sur le cloud avec une connectivité hybride locale nécessite une connectivité réseau ouverte aux hôtes locaux. Pour plus d’informations sur les configurations hybrides pour Skype Entreprise Online  | Consultez la rubrique [Planification de la connectivité hybride entre Skype Entreprise Server et Office 365](https://docs.microsoft.com/skypeforbusiness/hybrid/plan-hybrid-connectivity). | Entrée hybride locale pour Skype Entreprise |
| 14  | **Noms de domaine complets d’authentification et d’identité** <br> Le nom de domaine complet ```secure.aadcdn.microsoftonline-p.com``` doit apparaître dans la zone de sites Internet Explorer ou Edge approuvés de votre client pour fonctionner. |  | Sites de confiance |
| 15  |  **Noms de domaine complets Microsoft Teams** <br> Si vous utilisez Internet Explorer ou Microsoft Edge, vous devez activer les cookies propriétaires et tiers, et ajouter les noms de domaine complets des équipes à vos sites de confiance. Cela s’ajoute aux noms de domaine complets, aux CDN et à la télémétrie répertoriés à la ligne 14. Reportez-vous à la rubrique [Problèmes connus pour Microsoft Teams](https://docs.microsoft.com/microsoftteams/known-issues) pour plus d’informations. |  | Sites de confiance |
| 16  |  **Noms de domaine complets Sharepoint Online et OneDrive Entreprise** <br> Tous les noms de domaine complets « .sharepoint.com » comportant « \<tenant> » doivent se trouver dans la zone de sites Internet Explorer ou Edge de confiance de votre client pour fonctionner. Outre les noms de domaine complets, les CDN et la télémétrie répertoriés à la ligne 14, vous devrez également ajouter ces points de terminaison. |  | Sites de confiance |
| 17  | **Yammer**  <br> Yammer est uniquement disponible dans le navigateur et nécessite que l’utilisateur soit authentifié via un proxy. Tous les FQDN Yammer doivent se trouver dans la zone de sites Internet Explorer ou Edge de confiance de votre client pour fonctionner. |  | Sites de confiance |
| 18  | Utilisez [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/) pour synchroniser les comptes d’utilisateurs locaux avec Azure AD. | Consultez [Ports et protocoles nécessaires pour l’identité hybride](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-ports), [Résoudre les problèmes de connectivité Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity) et [Installation de l’agent Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-agent-install#outbound-connectivity-to-the-azure-service-endpoints). | Trafic serveur sortant uniquement |
| 19  | [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/) avec 21 ViaNet en Chine pour synchroniser les comptes d’utilisateur locaux avec Azure AD. | \*.digicert.com:80 <BR> \*.entrust.net:80 <BR> \*. chinacloudapi.cn:443 <BR> secure.aadcdn.partner.microsoftonline-p.cn:443 <BR>*.partner.microsoftonline.cn:443 <BR> <BR>Pour plus d’informations, voir [Résoudre les problèmes de connectivité Azure AD](https://docs.azure.cn/zh-cn/active-directory/hybrid/tshoot-connect-connectivity). | Trafic serveur sortant uniquement |
| 20  | Microsoft Stream (nécessite le jeton utilisateur Azure AD) <BR> Office 365 dans le monde (notamment GCC) | \**.cloudapp.net <BR> \*api.microsoftstream.com <BR> \**.notification.api.microsoftstream.com <BR> amp.azure.net <BR> api.microsoftstream.com <BR> az416426.vo.msecnd.net <BR> s0.assets-yammer.com <BR> vortex.data.microsoft.com <BR> web.microsoftstream.com <BR> Port TCP 443.  | Trafic serveur entrant |
| 21  | Utilisez le serveur MFA pour les demandes d’authentification multifacteur, les deux nouvelles installations du serveur et la configuration avec Active Directory Domain Services (AD DS). | Voir [Prise en main du serveur Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfaserver-deploy#plan-your-deployment).  | Trafic serveur sortant uniquement |
| 22  | Notifications de modifications Microsoft Graph | Les développeurs peuvent tirer parti des [notifications de modifications](https://docs.microsoft.com/graph/webhooks?context=graph%2Fapi%2F1.0&view=graph-rest-1.0) pour s’abonner aux événements dans Microsoft Graph. | *.cloudapp.net<BR> 104.43.130.21, 137.116.169.230, 13.79.38.63, 104.214.39.228, Cloud public : 168.63.250.205, 52.161.9.202, 40.68.103.62, 13.89.60.223, 23.100.95.104, 40.113.95.219, 104.214.32.10, 168.63.237.145, 52.161.110.176, 52.174.177.183 <BR> Microsoft Cloud for US Government : 52.244.231.173, 52.238.76.151, 52.244.250.211, 52.238.78.108 <BR> Microsoft Cloud Allemagne : 51.4.231.136, 51.5.243.223, 51.4.226.154, 51.5.244.215 <BR> Microsoft Graph en Chine géré par 21Vianet : 139.219.15.33, 42.159.154.223, 42.159.88.79, 42.159.155.77<BR> Port TCP 443. <BR> Remarque : les développeurs peuvent spécifier des ports différents lors de la création des abonnements.  | Trafic serveur entrant |
|||||

## <a name="related-topics"></a>Rubriques connexes

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)
  
[Résolution des problèmes de connectivité Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[Connectivité des clients](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Réseaux de distribution de contenu](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Plages d’adresses IP du centre de données Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Espace d’adresse IP public de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
