---
title: Requêtes réseau dans Office pour Mac
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Les applications Office pour Mac fournissent une expérience d’application native sur la plateforme macOS. Chaque application est conçue pour fonctionner dans un grand nombre de scénarios, dont les États quand aucun accès réseau n’est disponible. Lorsqu’un ordinateur est connecté à un réseau, les applications se connectent automatiquement à une série de services Web pour offrir des fonctionnalités améliorées. Cet article décrit les points de terminaison et les URL que les applications essaient d’atteindre, ainsi que les services fournis. Ces informations sont utiles lors de la résolution des problèmes de configuration réseau et de la définition d’une stratégie pour les serveurs proxy réseau. Les informations de cet article sont destinées à compléter l’article sur les plages d’adresses et l’URL Office 365.
ms.openlocfilehash: 0493fcc0954456ed190791b089fe4e0a568e82d7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069653"
---
# <a name="network-requests-in-office-for-mac"></a>Requêtes réseau dans Office pour Mac

Les applications Office pour Mac fournissent une expérience d’application native sur la plateforme macOS. Chaque application est conçue pour fonctionner dans un grand nombre de scénarios, dont les États quand aucun accès réseau n’est disponible. Lorsqu’un ordinateur est connecté à un réseau, les applications se connectent automatiquement à une série de services Web pour offrir des fonctionnalités améliorées. Les informations suivantes décrivent les points de terminaison et les URL que les applications essaient d’atteindre, ainsi que les services fournis. Ces informations sont utiles lors de la résolution des problèmes de configuration réseau et des stratégies de paramétrage pour les serveurs proxy réseau. Les détails dans cet article sont destinés à compléter l' [article sur les plages d’adresses et l’URL Office 365](urls-and-ip-address-ranges.md), qui inclut des points de terminaison pour les ordinateurs exécutant Microsoft Windows. Sauf indication contraire, les informations contenues dans cet article s’appliquent également à Office 2019 pour Mac et Office 2016 pour Mac, qui sont disponibles en tant qu’achat unique auprès d’un détaillant ou par le biais d’un contrat de licence en volume. 

  
La plupart de cet article est un tableau détaillant les URL réseau, le type et la description du service ou de la fonctionnalité fourni par ce point de terminaison. Chacune des applications Office peut différer dans son utilisation de service et de point de terminaison. Les applications suivantes sont définies dans les tableaux ci-dessous:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: Outlook
- N: OneNote
   
Le type d’URL est défini comme suit:
  
- ST: static-l’URL est codée en dur dans l’application cliente.
    
- SS: semi-statique-l’URL est codée dans le cadre d’une page Web ou d’un redirecteur.
    
- CS: service de configuration-l’URL est renvoyée dans le cadre du service de configuration d’Office.

    
## <a name="office-for-mac-default-configuration"></a>Configuration par défaut d’Office pour Mac

 **Installation et mises à jour**
  
Les points de terminaison réseau suivants sont utilisés pour télécharger le programme d’installation d’Office pour Mac à partir du réseau de distribution de contenu (CDN) de Microsoft.
  
|**URL**|**Type**|**Description**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ER  <br/> |Service de liaison de transfert du portail d’installation d’Office 365 vers les derniers packages d’installation.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SOCIALE  <br/> |Emplacement des packages d’installation sur le réseau de distribution de contenu.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SOCIALE  <br/> |Emplacement des packages d’installation sur le réseau de distribution de contenu.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ER  <br/> |Point de terminaison de contrôle de gestion pour Microsoft AutoUpdate  <br/> |
   
 **Premier lancement d’application**
  
Les points de terminaison réseau suivants sont contactés lors du premier lancement d’une application Office. Ces points de terminaison fournissent des fonctionnalités Office améliorées pour les utilisateurs, et les URL sont contactées quel que soit le type de licence (y compris les installations de licence en volume).
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ER  <br/> |Configuration de la «vol»: permet la mise en place d’une fonctionnalité et d’une expérimentation.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ER  <br/> |Test de configuration du réseau «vol»  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ER  <br/> |Test de configuration du réseau «vol»  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ER  <br/> |Service de configuration Office: liste principale des points de terminaison de service.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ER  <br/> |Service de télémétrie de règles Office: informe le client des données et des événements à télécharger vers le service de télémétrie.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |ADMISSIBLE  <br/> |Service de télémétrie OneNote  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ER  <br/> |Le rapport de téléchargement de télémétrie Office-«Heartbeart» et les événements d’erreur qui se produisent sur le client sont téléchargés vers le service de télémétrie.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |ADMISSIBLE  <br/> |Service de modèle Office Online: fournit aux utilisateurs des modèles de documents en ligne.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |ADMISSIBLE  <br/> |Téléchargements de modèles Office-stockage des images de modèles PNG.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |ADMISSIBLE  <br/> |Stocker la configuration des applications Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |ADMISSIBLE  <br/> |Catalogue des services d’intégration de documents Office (liste de services et points de terminaison) et découverte de domaine d’accueil.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |ADMISSIBLE  <br/> |Ressources pour la découverte de domaine d’accueil v2 (15,40 et versions ultérieures)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ER  <br/> |Manifestes de mise à jour AutoUpdate: vérifie s’il existe des mises à jour disponibles  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SOCIALE  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |Emboîtement  <br/> |SOCIALE  <br/> |Application Wikipédia pour la configuration et les ressources Office.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SOCIALE  <br/> |Application Bing Map pour la configuration et les ressources Office.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SOCIALE  <br/> |Application Graph Graph pour la configuration et les ressources Office.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ER  <br/> |Nouveautés de OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ER  <br/> |Nouveau contenu pour OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SOCIALE  <br/> |Quelles sont les nouvelles images pour OneNote?  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ER  <br/> |Service de prise en charge dans l’application.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ER  <br/> |Service de détection de compte de messagerie.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ER  <br/> |Découverte automatique d’Outlook  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ER  <br/> |Point de terminaison Outlook pour le service Office 365.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ER  <br/> |Icônes pour les compléments Outlook.  <br/> |
   
> [!NOTE]
> Le service de configuration office agit comme un service de découverte automatique pour tous les clients Microsoft Office, pas seulement pour Mac. Les points de terminaison renvoyés dans la réponse sont semi-statiques dans la mesure où cette modification est très peu fréquente, mais néanmoins possible. 
  
 **Connexion**
  
Les points de terminaison réseau suivants sont contactés lors de la connexion au stockage informatique. En fonction de votre type de compte, différents services peuvent être contactés. Par exemple :
  
- **MSA: compte Microsoft** : généralement utilisé pour les scénarios des particuliers et des détaillants 
    
- **OrgID: compte d’organisation** -généralement utilisé pour les scénarios commerciaux 
    
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ER  <br/> |Service d’autorisation Windows  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ER  <br/> |Service de connexion Office 365 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ER  <br/> |Service de connexion de compte Microsoft (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |ADMISSIBLE  <br/> |Application d’assistance de service de connexion de compte Microsoft (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SOCIALE  <br/> |Personnalisation de la connexion Office 365 (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |ADMISSIBLE  <br/> |Emplacement des documents et des emplacements de stockage  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |ADMISSIBLE  <br/> |Service de documents le plus récemment utilisé (MRU)  <br/> |
   
> [!NOTE]
> Pour les licences basées sur les abonnements et les détaillants, la connexion à l’activation du produit et l’accès aux ressources cloud telles que OneDrive. Pour les installations avec licence en volume, les utilisateurs sont toujours invités à se connecter (par défaut), mais cela n’est requis que pour accéder aux ressources Cloud, car le produit est déjà activé. 
  
 **Activation de produit**
  
Les points de terminaison réseau suivants s’appliquent aux activations d’abonnement et de licence de vente au détail d’Office 365. Plus précisément, cette opération ne s’applique pas aux installations avec licence en volume.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |ADMISSIBLE  <br/> |Service de gestion des licences Office  <br/> |
   
 **Nouveautés**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Office 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SOCIALE  <br/> |Nouveautés contenu de la page JSON.  <br/> |
   
 **Recherche**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Office 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |Emboîtement  <br/> |ADMISSIBLE  <br/> |Service Web de l’Organise-notes  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |Emboîtement  <br/> |ADMISSIBLE  <br/> |Contenu statique de l’Organise-notes  <br/> |
|```https://www.bing.com/```  <br/> |Emboîtement  <br/> |ADMISSIBLE  <br/> |Fournisseur de contenu de l’Organise-notes  <br/> |
   
 **Recherche intelligente**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Office 365 et de licence en volume.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |ADMISSIBLE  <br/> |Service Web Insights  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |ADMISSIBLE  <br/> |Bibliothèque JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |ADMISSIBLE  <br/> |Bibliothèque JavaScript de prise en charge  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |ADMISSIBLE  <br/> |Fournisseur de contenu Insights  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |ADMISSIBLE  <br/> |Fournisseur de contenu Insights  <br/> |
   
 **Concepteur PowerPoint**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Office 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |ADMISSIBLE  <br/> |Service Web du concepteur PowerPoint  <br/> |
   
 **Aide au démarrage de PowerPoint**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Office 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |ADMISSIBLE  <br/> |Service Web QuickStart de PowerPoint  <br/> |
   
 **Envoyer un sourire/Smiley**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Office 365 et de licence en volume.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |ADMISSIBLE  <br/> |Envoyer un service SMIL  <br/> |
   
 **Contacter le support technique**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Office 365 et de licence en volume.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |ADMISSIBLE  <br/> |Contacter le service d’assistance  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ADMISSIBLE  <br/> |Service de prise en charge dans l’application  <br/> |
   
 **Enregistrer au format PDF**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Office 365 et de licence en volume.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |Emboîtement  <br/> |ADMISSIBLE  <br/> |Service de conversion de documents Word (PDF)  <br/> |
   
 **Applications Office (alias)**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Office 365 et de licence de volume/volume lorsque les compléments d’applications Office sont approuvés.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |ADMISSIBLE  <br/> |Configuration du magasin d’applications Office  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |Emboîtement  <br/> |SOCIALE  <br/> |Ressources de l’application Wikipédia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SOCIALE  <br/> |Ressources d’application Bing Map  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SOCIALE  <br/> |Ressources de l’application Graph Graph  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SOCIALE  <br/> |Service de redirection Office  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SOCIALE  <br/> |Bibliothèques JavaScript Office  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SOCIALE  <br/> |Télémétrie et service de création de rapports pour les applications Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |Emboîtement  <br/> |SOCIALE  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SOCIALE  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SOCIALE  <br/> |Bibliothèques JavaScript Office  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SOCIALE  <br/> |Ressources de support  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SOCIALE  <br/> |Ressources de support  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SOCIALE  <br/> |Ressources de support  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SOCIALE  <br/> |Bibliothèque JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SOCIALE  <br/> |Rapports d'erreurs  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SOCIALE  <br/> |Ressources de police  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SOCIALE  <br/> |Service de télémétrie  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SOCIALE  <br/> |Création de rapports de télémétrie  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SOCIALE  <br/> |Bibliothèque de biens Microsoft Store  <br/> |
|```https://*.wikipedia.org/```  <br/> |Emboîtement  <br/> |SOCIALE  <br/> |Ressources de la page Wikipédia  <br/> |
|```https://upload.wikimedia.org/```  <br/> |Emboîtement  <br/> |SOCIALE  <br/> |Ressources multimédia Wikipédia  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |Emboîtement  <br/> |SOCIALE  <br/> |Cadre de bac à sable (sandbox)  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SOCIALE  <br/> |Modèles de carte  <br/> |
   
 **Liens fiables**
  
Le point de terminaison réseau suivant s’applique à toutes les applications Office pour l’abonnement Office 365 uniquement.
  
|**URL**|**Type**|**Description**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |ADMISSIBLE  <br/> |Service lien sécurisé Microsoft  <br/> |
   
 **Signalement des incidents**
  
Le point de terminaison réseau suivant s’applique à toutes les applications Office pour les activations d’abonnement et de licence en volume d’Office 365. Lorsqu’un processus se bloque inopinément, un rapport est généré et envoyé au service Watson.
  
|**URL**|**Type**|**Description**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ER  <br/> |Service de rapport d’erreurs Microsoft  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ER  <br/> |Service Office collaborative Insights  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Options permettant de réduire le trafic et les demandes réseau

La configuration par défaut d’Office pour Mac offre la meilleure expérience utilisateur, à la fois en termes de fonctionnalités et de mise à jour de l’ordinateur. Dans certains cas, vous souhaiterez peut-être empêcher les applications de contacter les points de terminaison réseau. Cette section décrit les options permettant d’effectuer cette opération.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Désactivation de la connexion Cloud et des compléments Office
  
Les clients de licence en volume peuvent avoir des stratégies strictes quant à l’enregistrement des documents dans un stockage informatique. La préférence suivante par application peut être définie de façon à désactiver la connexion MSA/OrgID et l’accès aux compléments Office.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Si les utilisateurs essaient d’accéder à la fonction de connexion, ils verront une erreur indiquant qu’il n’y a pas de connexion réseau. Étant donné que cette préférence bloque également l’activation de produit en ligne, elle doit être utilisée uniquement pour les installations avec licence en volume. En particulier, l’utilisation de cette préférence empêchera les applications Office d’accéder aux points de terminaison suivants:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Tous les points de terminaison figurant dans la section «connexion» ci-dessus.
    
- Tous les points de terminaison figurant dans la section «recherche intelligente» ci-dessus.
    
- Tous les points de terminaison figurant dans la section «activation de produit» ci-dessus.
    
- Tous les points de terminaison figurant dans la section «applications Office (alias)» ci-dessus.
    
Pour rétablir toutes les fonctionnalités de l’utilisateur, définissez sa préférence sur «2» ou supprimez-le.
  
> [!NOTE]
> Cette préférence nécessite Office pour Mac Build 15,25 [160726] ou une version ultérieure. 
  
### <a name="telemetry"></a>Télémétrie
  
Office pour Mac envoie des informations de télémétrie à Microsoft à intervalles réguliers. Les données sont téléchargées vers le point de terminaison «de la tentative». Les données de télémétrie aident l’équipe technique à évaluer l’intégrité et les comportements inattendus de chaque application Office. Il existe deux catégories de télémétrie:
  
- La **pulsation** contient des informations sur la version et la licence. Ces données sont envoyées immédiatement lors du lancement de l’application. 
    
- **Utilisation** : contient des informations sur la façon dont les applications sont utilisées et des erreurs récupérables. Ces données sont envoyées toutes les 60 minutes. 
    
Microsoft prend votre confidentialité très sérieusement. Vous pouvez consulter la rubrique relative à la stratégie de [https://privacy.microsoft.com](https://privacy.microsoft.com)collecte de données de Microsoft à l’adresse. Pour empêcher les applications d’envoyer des télémétries «utilisation», la préférence **SendAllTelemetryEnabled** peut être ajustée. La préférence est par application et peut être définie via des profils de configuration macOS ou manuellement à partir de terminal: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

La télémétrie de pulsations est toujours envoyée et ne peut pas être désactivée.
  
### <a name="crash-reporting"></a>Signalement des incidents
  
Lorsqu’une erreur d’application irrécupérable se produit, l’application se ferme de manière inattendue et télécharge un rapport d’incident vers le service «Watson». Le rapport d’incident se compose d’une pile d’appels, qui correspond à la liste des étapes de traitement de l’application conduisant au blocage. Ces étapes aident l’équipe d’ingénierie à identifier la fonction exacte qui a échoué et pourquoi.
  
Dans certains cas, le contenu d’un document entraîne le blocage de l’application. Si l’application identifie le document comme étant la cause, il demande à l’utilisateur s’il souhaite également envoyer le document avec la pile d’appels. Les utilisateurs peuvent faire un choix éclairé à cette question. Les administrateurs informatiques peuvent avoir des exigences strictes quant à la transmission des documents et prendre la décision au nom de l’utilisateur pour ne jamais envoyer de documents. La préférence suivante peut être définie pour empêcher l’envoi de documents et pour supprimer l’invite à l’utilisateur:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Si **SendAllTelemetryEnabled** est défini sur **false**, tous les rapports d’incident pour ce processus sont désactivés. Pour activer la création de rapports d’incident sans envoyer de télémétrie d’utilisation, la préférence suivante peut être définie:```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Updates
  
Microsoft publie les mises à jour d’Office pour Mac à intervalles réguliers (généralement une fois par mois). Nous encourageons vivement les utilisateurs et les administrateurs informatiques à tenir à jour les machines afin de s’assurer que les correctifs de sécurité les plus récents sont installés. Dans les cas où les administrateurs informatiques veulent contrôler et gérer étroitement les mises à jour des ordinateurs, la préférence suivante peut être définie pour empêcher le processus AutoUpdate de détecter et d’utiliser automatiquement les mises à jour des produits:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Blocage des demandes avec un pare-feu/proxy
  
Si votre organisation bloque les requêtes d’URL via un pare-feu ou un serveur proxy, veillez à configurer les URL indiquées dans ce document comme étant autorisées ou bloquées avec une réponse 40X (par exemple 403 ou 404). Une réponse 40X permet aux applications Office d’accepter normalement l’impossibilité d’accéder à la ressource et de fournir une expérience utilisateur plus rapide, que de simplement déposer la connexion, ce qui entraîne une nouvelle tentative du client.
  
Si votre serveur proxy requiert une authentification, une réponse 407 sera renvoyée au client. Pour une expérience optimale, vérifiez que vous utilisez Office pour Mac builds 15,27 ou version ultérieure, car ils incluent des correctifs spécifiques pour utiliser les serveurs NTLM et Kerberos.
  
  
## <a name="see-also"></a>Voir aussi

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

