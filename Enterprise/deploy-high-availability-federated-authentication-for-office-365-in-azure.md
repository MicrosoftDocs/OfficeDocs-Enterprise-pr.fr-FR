---
title: "Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/3/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- apr17entnews
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: "Résumé : Configurer l'authentification fédérée haute disponibilité pour votre abonnement Office 365 dans Microsoft Azure."
---

# Déployer une authentification fédérée haute disponibilité pour Office 365 dans Azure

 **Résumé :** Configurer l'authentification fédérée haute disponibilité pour votre abonnement Office 365 dans Microsoft Azure.
  
Cet article contient des liens vers les instructions détaillées de déploiement de l'authentification fédérée haute disponibilité pour Microsoft Office 365 dans les services d'infrastructure Azure avec ces machines virtuelles :
  
- Deux serveurs proxy d'application web
    
- Deux serveurs de services ADFS (Active Directory Federation Services)
    
- Deux contrôleurs de domaine répliqués
    
- Un serveur de synchronisation d'annuaire (DirSync) exécutant Azure AD Connect
    
Cette courte vidéo offre un aperçu rapide de l'infrastructure d'authentification fédérée et de la procédure de création de l'ensemble de serveurs Azure, et illustre le processus d'authentification.
  
![Icône Vidéo (bouton de lecture)](images/mod_icon_video_M.png)
  
Voici la configuration, avec les noms d'espace réservé pour chaque serveur.
  
**Une authentification fédérée haute disponibilité pour l'infrastructure Office 365 dans Azure**

![Configuration finale de l'infrastructure d'authentification fédérée haute disponibilité Office 365 dans Azure](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Toutes les machines virtuelles sont dans un réseau virtuel intersites unique Azure. 
  
> [!NOTE]
> L'authentification fédérée d'utilisateurs individuels n'utilise aucune ressource locale. Toutefois, si la connexion intersites devient indisponible, les contrôleurs de domaine du réseau virtuel ne reçoivent plus les mises à jour des comptes d'utilisateurs et des groupes apportées dans l'instance Active Directory Windows Server locale. Pour que cela n'arrive pas, vous pouvez configurer une haute disponibilité pour votre connexion intersites. Pour plus d'informations, reportez-vous à l'article [Configuration haute disponibilité pour la connectivité entre les réseaux locaux et la connectivité entre deux réseaux virtuels](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Chaque paire de machines virtuelles utilisée pour un rôle spécifique est dans son propre sous-réseau et son propre groupe à haute disponibilité.
  
> [!NOTE]
> Étant donné que ce réseau virtuel est connecté au réseau local, cette configuration n'inclut pas de machines virtuelles jumpbox ou de machines virtuelles de surveillance sur un sous-réseau de gestion. Pour plus d'informations, voir l'article relatif à l'[exécution de machines virtuelles Windows pour une architecture n-tiers](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm). 
  
Cette configuration met en place une authentification fédérée pour tous vos utilisateurs Office 365, qui peuvent ainsi utiliser leurs informations d'identification Active Directory Windows Server pour se connecter au lieu de leur compte Office 365. L'infrastructure d'authentification fédérés utilise un ensemble redondant de serveurs qui sont plus faciles à déployer dans les services d'infrastructure Azure que dans votre réseau de périmètre en local.
  
## Nomenclature

Cette configuration de base requiert l'ensemble de composants et services Azure suivant :
  
- Sept machines virtuelles
    
- Un réseau virtuel intersites avec quatre sous-réseaux.
    
- Sept comptes de stockage
    
- Quatre groupes de ressources
    
- Trois groupes à haute disponibilité
    
Voici les machines virtuelles et leurs tailles par défaut pour cette configuration.
  
|**Élément**|**Description de la machine virtuelle**|**Image de la galerie Azure**|**Taille par défaut**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Premier contrôleur de domaine  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |Deuxième contrôleur de domaine  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |Serveur Azure AD Connect  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |Premier serveur AD FS  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |Deuxième serveur AD FS  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |Premier serveur proxy d'application web  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |Deuxième serveur proxy d'application web  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
Pour calculer les coûts estimés pour cette configuration, utilisez la [calculatrice de prix Azure](https://azure.microsoft.com/pricing/calculator/)
  
## Phases de déploiement

Vous déployez cette charge de travail au cours des phases suivantes :
  
- [Authentification fédérée haute disponibilité, phase 1 : Configurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md) . Créez des groupes de ressources, des comptes de stockage, des groupes à haute disponibilité et un réseau virtuel intersites.
    
- [Authentification fédérée haute disponibilité, phase 2 : Configurer les contrôleurs de domaine](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) . Créez et configurez des contrôleurs de domaine répliqués Windows Server Active Directory (AD) et le serveur DirSync.
    
- [Authentification fédérée haute disponibilité, phase 3 : Configurer les serveurs AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) . Créez et configurez les deux serveurs AD FS.
    
- [Authentification fédérée haute disponibilité, phase 4 : Configurer les proxys d'application web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) . Créez et configurez les deux serveur proxy d'application web.
    
- [Authentification fédérée haute disponibilité, phase 5 : Configurer l'authentification fédérée pour Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) . Configurez l'authentification fédérée pour votre abonnement Office 365.
    
Ces articles fournissent un guide normatif phase par phase pour créer une authentification fédérée haute disponibilité fonctionnelle pour Office 365 dans les services d'infrastructure Azure à partir d'une architecture prédéfinie. Gardez les éléments suivants à l'esprit :
  
- Si vous êtes un implémenteur d'AD FS expérimenté, n'hésitez pas à adapter les instructions des étapes 3 à 4 et à créer l'ensemble de serveurs qui correspond le mieux à vos besoins. 
    
- Si vous disposez déjà d'un déploiement de cloud hybride Azure avec un réseau virtuel entre différents locaux, n'hésitez pas à adapter ou à ignorer les instructions des phases 1 et 2 et placez les serveurs proxy AD FS et d'application web dans les sous-réseaux appropriés.
    
Pour créer un environnement de développement/test ou une preuve de concept de cette configuration, voir [Identité fédérée pour votre environnement de développement/test Office 365](federated-identity-for-your-office-365-dev-test-environment.md).
  
## Étape suivante

Commencez la configuration de cette charge de travail avec [Authentification fédérée haute disponibilité, phase 1 : Configurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
  
> [!TIP]
> Pour qu'un jeu de fichiers déploie plus rapidement votre authentification fédérée haute disponibilité pour Office 365 dans Azure, voir le [Kit de déploiement de l'authentification fédérée pour Office 365 dans Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
  
## See Also

#### 

[Identité fédérée pour votre environnement de développement/test Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Adoption du cloud et solutions hybrides](cloud-adoption-and-hybrid-solutions.md)
#### 

[Identité fédérée pour Office 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)

