---
title: Autres URL et adresses IP Office 365 non incluses dans les services web
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 9/13/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: 'Résumé : Les nouveaux services web de point de terminaison n’incluent pas quelques points de terminaison pour des scénarios spécifiques.'
hideEdit: true
ms.openlocfilehash: 4711f9b9560b0fab6d18700fcf3e933150861946
ms.sourcegitcommit: 0f98c342f80ffa21ec35bbf4ae5619b5e3271da5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2018
ms.locfileid: "23977349"
---
# <a name="additional-office-365-ip-addresses-and-urls-not-included-in-the-web-services"></a>Autres URL et adresses IP Office 365 non incluses dans les services web

Certains points de terminaison réseau ont été publiés précédemment et n’ont pas été inclus dans les services web. La portée des services web correspond aux points de terminaison réseau requis pour la connectivité à partir d’un utilisateur final d’Office 365 au sein d’un réseau de périmètre d’entreprise. À l’heure actuelle, ceci n’inclut pas les éléments suivants :

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
| 2  | [Assistant Support et récupération Office 365 Microsoft](https://diagnostics.office.com/#/) - Valider les informations d’identification utilisateur d’authentification unique. Source :<br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | service d’émission de jeton de sécurité local | Trafic serveur entrant |
| 3  | Azure AD Connect (avec option d’authentification unique) - WinRM et PowerShell distant | Environnement STS client (serveur AD FS et proxy AD FS) \| Ports TCP 80 et 443 | Trafic serveur entrant |
| 4  | STS, comme des serveurs proxy AD FS (pour les clients fédérés uniquement) | STS client (comme un proxy AD FS) \| Ports TCP 443 ou TCP 49443 avec ClientTLS | Trafic serveur entrant |
| 5  | [Intégration de la messagerie unifiée Exchange Online/SBC](https://technet.microsoft.com/library/jj673565.aspx) | Bidirectionnel entre le contrôleur de bordure de session local et *.um.outlook.com | Trafic serveur sortant uniquement |
| 6  | Fonctions de coexistence [Exchange hybride](https://docs.microsoft.com/exchange/exchange-deployment-assistant) telles que le partage de disponibilité. | Serveur Exchange client local | Trafic serveur entrant |
| 7  | Authentification de proxy [Exchange hybride](https://docs.microsoft.com/exchange/exchange-deployment-assistant) | STS local client | Trafic serveur entrant |
| 8  | Utilisé pour configurer [Exchange hybride](https://docs.microsoft.com/exchange/exchange-deployment-assistant), à l’aide de l’Assistant Configuration d’Exchange hybride. <br> Remarque : ces points de terminaison sont uniquement nécessaires pour configurer Exchange hybride  | ```domains.live.com``` sur les ports TCP 80 et 443, obligatoire uniquement pour l’Assistant Configuration hybride Exchange 2010 SP3. | Trafic serveur sortant uniquement |
| 9  | Le service de détection automatique est utilisé dans des scénarios [Exchange hybride](https://docs.microsoft.com/exchange/exchange-deployment-assistant) avec [l’authentification moderne hybride avec Outlook pour iOS et Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth). <BR> <BR> ```*.acompli.net``` <BR> ```*.outlookmobile.us``` <BR> <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> | Serveur Exchange client local sur TCP 443 | Trafic serveur entrant |
| 10  | **Noms de domaine complets d’authentification et d’identité** <br> Le nom de domaine complet ```secure.aadcdn.microsoftonline-p.com``` doit apparaître dans la zone de sites Internet Explorer ou Edge approuvés de votre client pour fonctionner. |  | Sites de confiance |
| 11  |  **Noms de domaine complets Microsoft Teams** <br> Si vous utilisez Internet Explorer ou Microsoft Edge, vous devez activer les cookies propriétaires et tiers, et ajouter les noms de domaine complets des équipes à vos sites de confiance. Cela s’ajoute aux noms de domaine complets, aux CDN et à la télémétrie répertoriés ci-dessus. Reportez-vous à la rubrique [Problèmes connus pour Microsoft Teams](https://docs.microsoft.com/microsoftteams/known-issues) pour plus d’informations. |  | Sites de confiance |
| 12  |  **Noms de domaine complets Sharepoint Online et OneDrive Entreprise** <br> Tous les noms de domaine complets « .sharepoint.com » comportant « \<tenant> » doivent se trouver dans la zone de sites Internet Explorer ou Edge de confiance de votre client pour fonctionner. Outre les noms de domaine complets, les CDN et la télémétrie répertoriés ci-dessus, vous devez également ajouter ces points de terminaison. |  | Sites de confiance |
| 13  | **Yammer**  <br> Yammer est uniquement disponible dans le navigateur et nécessite que l’utilisateur soit authentifié via un proxy. Tous les FQDN Yammer doivent se trouver dans la zone de sites Internet Explorer ou Edge de confiance de votre client pour fonctionner. |  | Sites de confiance |

## <a name="related-topics"></a>Voir aussi

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)
  
[Résolution des problèmes de connectivité Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[Connectivité des clients](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Réseaux de distribution de contenu](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Plages d’adresses IP du centre de données Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Espace d’adresse IP public de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)

