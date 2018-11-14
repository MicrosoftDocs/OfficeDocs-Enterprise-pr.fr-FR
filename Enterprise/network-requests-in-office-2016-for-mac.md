---
title: Demandes de réseau dans Office pour Mac
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Applications Office pour Mac offrent une expérience de l’application native sur la plate-forme Mac OS. Chaque application est conçue pour fonctionner dans de nombreux scénarios, y compris les États lorsqu’aucun accès réseau n’est disponible. Lorsqu’un ordinateur est connecté à un réseau, les applications de se connectent automatiquement à une série de services web pour fournir des fonctionnalités améliorées. Ce livre blanc décrit les points de terminaison et les applications essaient d’atteindre les URL et les services fournis. Cette information est utile lors de la résolution des problèmes réseau les problèmes de configuration et en définissant une stratégie pour les serveurs proxy de réseau. Les détails de cet article sont conçus pour compléter l’URL dans Office 365 et l’article de plages d’adresses.
ms.openlocfilehash: 929b93433f5d990952b540a1b28fe2ac74edfb5d
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219894"
---
# <a name="network-requests-in-office-for-mac"></a>Demandes de réseau dans Office pour Mac

Applications Office pour Mac offrent une expérience de l’application native sur la plate-forme Mac OS. Chaque application est conçue pour fonctionner dans de nombreux scénarios, y compris les États lorsqu’aucun accès réseau n’est disponible. Lorsqu’un ordinateur est connecté à un réseau, les applications de se connectent automatiquement à une série de services web pour fournir des fonctionnalités améliorées. Les informations suivantes décrivent les points de terminaison et les applications essaient d’atteindre les URL et les services fournis. Cette information est utile lors de la résolution des problèmes de configuration réseau et définition de stratégies pour les serveurs proxy de réseau. Les détails de cet article sont conçus pour compléter l' [URL de Office 365 et l’adresse article plages](urls-and-ip-address-ranges.md), qui inclut des points de terminaison pour les ordinateurs qui exécutent Microsoft Windows. Sauf contraire, les informations contenues dans cet article s’applique également à 2019 Office pour Mac et 2016 Office pour Mac, qui sont disponibles en tant qu’achat unique à partir d’un magasin de vente au détail ou via un contrat de licence en volume. 

  
La plupart de cet article est tables détaillant réseau URL, type et la description de service ou la fonctionnalité fournie par ce point de terminaison. Chacune des applications Office peut-être différer dans son utilisation du service et le point de terminaison. Les applications suivantes sont définies dans les tableaux ci-dessous :
  
- W : Word
- P : PowerPoint
- X : Excel
- O : outlook
- N: OneNote
   
Le type d’URL est défini comme suit :
  
- ST : Statique - l’URL est codée en dur dans l’application cliente.
    
- SS : Statique séparées-URL est codée dans le cadre d’une page web ou d’un redirecteur.
    
- CS : Service de configuration - l’URL est renvoyée dans le cadre du Service de Configuration d’Office.

    
## <a name="office-for-mac-default-configuration"></a>Office pour la configuration par défaut de Mac

 **Installation et mises à jour**
  
Les points de terminaison de réseau suivants sont utilisés pour télécharger le programme Office pour Mac installation à partir du Microsoft réseau CDN (Content Delivery).
  
|**URL**|**Type**|**Description**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Service de lien avant de portail d’Installation Office 365 pour les packages d’installation le plus récent.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Emplacement des packages d’installation sur le réseau de livraison de contenu.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Emplacement des packages d’installation sur le réseau de livraison de contenu.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Le point de terminaison du contrôle de gestion pour Microsoft AutoUpdate  <br/> |
   
 **Premier lancement d’application**
  
Les points de terminaison réseau suivantes sont contactés premier lancement d’une application Office. Ces points de terminaison fournissent des fonctionnalités d’Office pour les utilisateurs et les URL sont contactés quel que soit le type de licence (y compris les installations de licence en Volume).
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |La Configuration 'Flighting' - permet de fonctionnalité clair à distance et l’expérimentation.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test de la Configuration réseau 'Flighting'  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test de la Configuration réseau 'Flighting'  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Service de Configuration Office - maîtres liste des points de terminaison de service.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Téléchargement de règles télémétrie Office - informe le client les données et les événements pour télécharger vers le service de télémétrie.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |Service de télémétrie OneNote  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Télémétrie Office télécharger Création de rapports - « Heartbeart » et les événements d’erreur qui se produisent sur le client sont téléchargés vers le service de télémétrie.  <br/> |
|```https://templateservice.office.com/```  <br/> |WINDOWS XP ÉDITION  <br/> |CS  <br/> |Service de modèle Office Online - fournit aux utilisateurs des modèles de documents en ligne.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WINDOWS XP ÉDITION  <br/> |CS  <br/> |Téléchargement de modèles Office - stockage des images de modèle PNG.  <br/> |
|```https://store.office.com/```  <br/> |WINDOWS XP ÉDITION  <br/> |CS  <br/> |Configuration de la banque pour les applications Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Catalogue de Services de l’intégration Office Document (liste des services et des points de terminaison) et découverte de domaine d’accueil.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Ressources pour la découverte de domaine accueil v2 (15.40 et ultérieure)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Manifestes Microsoft AutoUpdate - vérifie si des mises à jour sont disponibles  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft Ajax Library de JavaScript  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Application Wikipédia pour la configuration d’Office et les ressources.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Application de carte Bing pour la configuration d’Office et les ressources.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Graphique d’application pour la configuration d’Office et les ressources de personnes.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |Quel est le nouveau contenu pour OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |Nouveau contenu pour OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |Nouveautés de nouvelles images pour OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |Service de prise en charge dans l’application.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |Service de détection de compte de messagerie.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Découverte automatique Outlook  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Point de terminaison Outlook pour le service Office 365.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Icônes pour des compléments Outlook.  <br/> |
   
> [!NOTE]
> Le Service de Configuration d’Office se comporte comme un service de découverte automatique pour tous les clients Microsoft Office, et pas seulement pour Mac. Les points de terminaison retournés dans la réponse sont partiel statiques dans cette modification est très rarement, mais reste possible. 
  
 **Se connecter**
  
Les points de terminaison réseau suivantes sont contactés lors de la connexion au stockage en nuage. Selon votre type de compte, les différents services peuvent être contactés. Par exemple :
  
- **MSA : Account Microsoft** - généralement utilisés pour les scénarios de consommateur et de vente au détail 
    
- **OrgID : organisation compte** - généralement utilisés pour les scénarios commerciaux 
    
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Service d’autorisation de Windows  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Service de connexion Office 365 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Service de connexion de compte Microsoft (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Assistance de Service connexion de compte Microsoft (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Connexion à Office 365 personnalisation (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Documents et emplacements stockage Locator  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |La plupart des service de documents utilisés Récemment  <br/> |
   
> [!NOTE]
> Pour les licences d’abonnement et de détail, les deux connexion active le produit et permet d’accéder aux ressources de cloud telles que OneDrive. Pour les installations de licence en Volume, les utilisateurs sont toujours invités à la connexion (par défaut), mais qui n’est requis pour accéder aux ressources dans le nuage, comme le produit est déjà activé. 
  
 **Activation du produit**
  
Les points de terminaison réseau suivantes s’appliquent aux activations d’abonnement à Office 365 et de licence de vente au détail. En particulier, il ne s’applique pas aux installations de licence en Volume.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Service de gestion des licences Office  <br/> |
   
 **Quel est le nouveau contenu**
  
Les points de terminaison réseau suivantes s’appliquent uniquement à l’abonnement à Office 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |Quel est le contenu de la page Nouveau JSON.  <br/> |
   
 **Recherche**
  
Les points de terminaison réseau suivantes s’appliquent uniquement à l’abonnement à Office 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Service Web d’enquêteur  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Organise le contenu statique  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Fournisseur de contenu enquêteur  <br/> |
   
 **Recherche intelligente**
  
Les points de terminaison réseau suivantes s’appliquent à Office 365 abonnement et licence de vente au détail/Volume activations.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Service Web de Insights  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |Bibliothèque JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Prise en charge de bibliothèque JavaScript  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Fournisseur de contenu Insights  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Fournisseur de contenu Insights  <br/> |
   
 **Concepteur PowerPoint**
  
Les points de terminaison réseau suivantes s’appliquent uniquement à l’abonnement à Office 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |Service web de concepteur PowerPoint  <br/> |
   
 **Aide au démarrage de PowerPoint**
  
Les points de terminaison réseau suivantes s’appliquent uniquement à l’abonnement à Office 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |Service web de PowerPoint QuickStarter  <br/> |
   
 **Envoyer un sourire/froncé**
  
Les points de terminaison réseau suivantes s’appliquent à Office 365 abonnement et licence de vente au détail/Volume activations.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Envoyer un sourire  <br/> |
   
 **Contactez le support technique**
  
Les points de terminaison réseau suivantes s’appliquent à Office 365 abonnement et licence de vente au détail/Volume activations.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Contactez le Service d’assistance  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |Service de prise en charge dans l’application  <br/> |
   
 **Enregistrer en tant que PDF**
  
Les points de terminaison réseau suivantes s’appliquent à Office 365 abonnement et licence de vente au détail/Volume activations.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Service de conversion de documents Word (PDF)  <br/> |
   
 **Office applications (également appelées compléments)**
  
Les points de terminaison réseau suivantes s’appliquent à Office 365 abonnement et licence de vente au détail/Volume activations lorsque des compléments d’application Office sont autorisées.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Configuration de magasin d’application Office  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Ressources d’application Wikipédia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Ressources d’application carte Bing  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Ressources d’application personnes graphique  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Service de Redirection d’Office  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WINDOWS XP ÉDITION  <br/> |SS  <br/> |Bibliothèques JavaScript Office  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Télémétrie et le Service de création de rapports pour les applications Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Microsoft Ajax Library de JavaScript  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Microsoft Ajax Library de JavaScript  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Bibliothèques JavaScript Office  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de support  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de support  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de support  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |Bibliothèque JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Rapport d’erreurs  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de police  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Service de télémétrie  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Création de rapports de télémétrie  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Bibliothèque de biens banque Microsoft  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Ressources de pages Wikipedia  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Ressources de support Wikipedia  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Cadre de bac à sable Wikipedia  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Modèles de carte  <br/> |
   
 **Liens fiables**
  
Le point de terminaison réseau suivante s’applique à toutes les applications Office pour Office 365 abonnement uniquement.
  
|**URL**|**Type**|**Description**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Service de liaison sécurisé de Microsoft  <br/> |
   
 **Bloquer la création de rapports**
  
Le point de terminaison réseau suivante s’applique à toutes les applications Office pour Office 365 abonnement et licence de vente au détail/Volume activations. Lorsqu’un processus de manière inattendue tombe en panne, un rapport est généré et envoyé au service de Dr Watson.
  
|**URL**|**Type**|**Description**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Service de rapport d’erreurs Microsoft  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Service de collaboration Insights Office  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Options permettant de réduire le trafic et les demandes de réseau

La configuration par défaut d’Office pour Mac fournit la meilleure expérience utilisateur, à la fois en termes de fonctionnalités et de maintien de l’ordinateur à jour. Dans certains scénarios, vous pouvez souhaiter empêcher les applications de communication avec des points de terminaison réseau. Cette section décrit les options pour le faire.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Désactivation des compléments dans le nuage et de Office
  
Clients de licence en volume peuvent avoir des stratégies stricts sur l’enregistrement de documents vers un stockage en nuage. La préférence par application peut être définie pour désactiver MSA/OrgID de connexion et l’accès à des compléments Office.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Si les utilisateurs tentent d’accéder à la fonction de connexion, ils verront une erreur qu’une connexion de réseau n’est pas présent. Étant donné que cette préférence bloque également l’activation du produit en ligne, il doit uniquement être utilisé pour les installations de licence en Volume. Plus précisément, à l’aide de cette préférence empêchera les applications Office à partir de l’accès aux points de terminaison suivants :
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Tous les points de terminaison répertoriés dans la section « Sign In » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Rechercher actives » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Activation de produit » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Applications Office (également appelées add-ins) » ci-dessus.
    
Pour rétablir toutes les fonctionnalités de l’utilisateur, soit définir l’option « 2 » ou la supprimer.
  
> [!NOTE]
> Cette préférence requiert Office pour générer Mac 15.25 [160726] ou version ultérieure. 
  
### <a name="telemetry"></a>Télémétrie
  
Office pour Mac envoie les informations de télémétrie à Microsoft à intervalles réguliers. Données sont téléchargées vers le point de terminaison « Connexion ». Les données de télémétrie permettent l’équipe d’ingénierie d’évaluer l’intégrité et les comportements inattendus de chaque application Office. Il existe deux catégories de télémétrie :
  
- **Pulsation** contient des informations de licence et de version. Ces données sont envoyées immédiatement après le lancement d’application. 
    
- **L’utilisation** contient des informations sur l’utilisation des applications et les erreurs récupérables. Ces données sont envoyées toutes les 60 minutes. 
    
Microsoft prend très au sérieux votre confidentialité. Vous pouvez en savoir plus sur stratégie de collecte de données de Microsoft sur [https://privacy.microsoft.com](https://privacy.microsoft.com). Pour empêcher les applications de l’envoi de télémétrie 'Utilisation', la préférence **SendAllTelemetryEnabled** peut être ajustée. La préférence est par application et peut être définie via Mac OS profils de Configuration, ou manuellement à partir de Terminal Server : 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

Télémétrie heartbeat est toujours envoyé et ne peut pas être désactivée.
  
### <a name="crash-reporting"></a>Bloquer la création de rapports
  
Lorsqu’une erreur irrécupérable se produit, l’application inattendue se terminer et télécharger un rapport d’incident au service « Watson ». Le rapport d’incident se compose d’une pile des appels, qui correspond à la liste des étapes de que l’application a été traitement menant à la défaillance. Ces étapes identifier l’équipe d’ingénierie la fonction exact qui a échoué et pourquoi.
  
Dans certains cas, le contenu d’un document entraîne l’application à bloquer. Si l’application s’identifie le document en tant que la cause, il demande à l’utilisateur si elle est OK d’envoyer le document ainsi que la pile des appels. Les utilisateurs peuvent faire un choix éclairé à cette question. Les administrateurs informatiques peuvent ont des exigences strictes sur la transmission de documents et prendre la décision de ne jamais envoyer des documents au nom de l’utilisateur. La préférence suivante peut être définie pour empêcher l’envoi de documents et pour supprimer l’invite à l’utilisateur :
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Si **SendAllTelemetryEnabled** est défini sur **FALSE**, tous les incident de création de rapports pour que le processus est désactivé. Pour activer le rapport d’incident sans envoyer de télémétrie d’utilisation, la préférence suivante peut être définie :```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Mises à jour
  
Microsoft publie Office pour les mises à jour Mac à intervalles réguliers (généralement une fois par mois). Nous conseillons vivement d’utilisateurs et les administrateurs informatiques à maintenir les ordinateurs à jour pour vérifier les derniers correctifs de sécurité sont installés. Dans les cas où les administrateurs informatiques à mieux contrôler et gérer les mises à jour de l’ordinateur, la préférence suivante peut être définie pour empêcher le processus de mise à jour automatique de détection et offrant des mises à jour automatiquement :
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Blocage des demandes avec un pare-feu/Proxy
  
Si les blocs de votre organisation demande aux URL via un pare-feu ou le serveur proxy veillez à configurer les URL répertoriées dans ce document en tant qu’autorisés ou bloquer accompagnée d’une réponse X 40 (403 ou 404). Une réponse X 40 permettra aux applications Office accepter normalement l’impossibilité d’accéder à la ressource et fournit une expérience utilisateur plus rapide, à faire glisser la connexion, qui à son tour entraîne le client de réessayer.
  
Si votre serveur proxy requiert une authentification, une réponse 407 est retournées au client. Pour optimiser les performances, assurez-vous que vous utilisez Office pour Mac s’appuie 15.27 ou version ultérieure, car ils incluent des correctifs spécifiques pour travailler avec des serveurs NTLM et Kerberos.
  
  
## <a name="see-also"></a>Voir aussi

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

