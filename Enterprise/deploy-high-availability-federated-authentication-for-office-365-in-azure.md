---
title: Déployer une authentification fédérée haute disponibilité pour Microsoft 365 dans Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 'Résumé : configurez l’authentification fédérée haute disponibilité pour votre abonnement Microsoft 365 dans Microsoft Azure.'
ms.openlocfilehash: 98b8bdff708d02f866a3e2f2d2521bec5b011bb7
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230050"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a>Déployer une authentification fédérée haute disponibilité pour Microsoft 365 dans Azure

Cet article contient des liens vers les instructions pas à pas pour le déploiement de l’authentification fédérée haute disponibilité pour Microsoft 365 dans les services d’infrastructure Azure avec ces machines virtuelles :
  
- Deux serveurs proxy d’application web
    
- Deux serveurs de services ADFS (Active Directory Federation Services)
    
- Deux contrôleurs de domaine répliqués
    
- Un serveur de synchronisation d’annuaire exécutant Azure AD Connect
    
Voici la configuration, avec les noms d’espace réservé pour chaque serveur.
  
**Une authentification fédérée haute disponibilité pour l’infrastructure Microsoft 365 dans Azure**

![La configuration finale de l’infrastructure d’authentification fédérée Microsoft 365 haute disponibilité dans Azure](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Toutes les machines virtuelles sont dans un réseau virtuel intersites unique Azure. 
  
> [!NOTE]
> L'authentification fédérée d'utilisateurs individuels n'utilise aucune ressource locale. Toutefois, si la connexion entre différents locaux devient indisponible, les contrôleurs de domaine du réseau virtuel ne reçoivent plus les mises à jour des comptes d'utilisateurs et des groupes apportées dans l'instance Active Directory Domain Services locale. Pour l’éviter, vous pouvez configurer une haute disponibilité pour votre connexion entre différents locaux. Pour plus d'informations, consultez [Configuration haute disponibilité pour la connectivité entre les réseaux locaux et la connectivité entre deux réseaux virtuels](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Chaque paire de machines virtuelles utilisée pour un rôle spécifique est dans son propre sous-réseau et son propre groupe à haute disponibilité.
  
> [!NOTE]
> Étant donné que ce réseau virtuel est connecté au réseau local, cette configuration n'inclut pas de machines virtuelles jumpbox ou de machines virtuelles de surveillance sur un sous-réseau de gestion. Pour plus d'informations, voir l'article relatif à l'[exécution de machines virtuelles Windows pour une architecture n-tiers](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm). 
  
Le résultat de cette configuration est que vous disposez d’une authentification fédérée pour tous vos utilisateurs de Microsoft 365, dans lesquels ils peuvent utiliser leurs informations d’identification AD DS pour se connecter à la place de leur compte Microsoft 365. L’infrastructure d’authentification fédérés utilise un ensemble redondant de serveurs qui sont plus faciles à déployer dans les services d’infrastructure Azure que dans votre réseau de périmètre en local.
  
## <a name="bill-of-materials"></a>Nomenclature

Cette configuration de base requiert l’ensemble de composants et services Azure suivant :
  
- Sept machines virtuelles
    
- Un réseau virtuel intersites avec quatre sous-réseaux.
    
- Quatre groupes de ressources
    
- Trois groupes à haute disponibilité
    
- Un abonnement Azure
    
Voici les machines virtuelles et leurs tailles par défaut pour cette configuration.
  
|**Élément**|**Description de la machine virtuelle**|**Image de la galerie Azure**|**Taille par défaut**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Premier contrôleur de domaine  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |Deuxième contrôleur de domaine  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |Serveur Azure AD Connect  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |Premier serveur AD FS  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |Deuxième serveur AD FS  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |Premier serveur proxy d’application web  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |Deuxième serveur proxy d’application web  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
Pour calculer les coûts estimés pour cette configuration, utilisez la [calculatrice de prix Azure](https://azure.microsoft.com/pricing/calculator/)
  
## <a name="phases-of-deployment"></a>Phases de déploiement

Vous déployez cette charge de travail au cours des phases suivantes :
  
- [Phase 1 : Configuration Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Créez des groupes de ressources, des comptes de stockage, des groupes à haute disponibilité et un réseau virtuel intersites.
    
- [Étape 2 : configurer les contrôleurs de domaine](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Créer et configurer les contrôleurs de domaine réplica Azure AD et le serveur de synchronisation d’annuaires.
    
- [Phase 3 : Configuration des serveurs AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Créez et configurez les deux serveurs AD FS.
    
- [Phase 4 : Configuration des proxys d’application web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Créez et configurez les deux serveurs proxy d’application web.
    
- [Phase 5 : configurer l’authentification fédérée pour Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configurez l’authentification fédérée pour votre abonnement Microsoft 365.
    
Ces articles fournissent un guide normatif, étape par étape, pour une architecture prédéfinie afin de créer une authentification fédérée fonctionnelle haute disponibilité pour Microsoft 365 dans les services d’infrastructure Azure. Gardez les points suivants à l’esprit :
  
- Si vous êtes un implémenteur d’AD FS expérimenté, n’hésitez pas à adapter les instructions des étapes 3 à 4 et à créer l’ensemble de serveurs qui correspond le mieux à vos besoins. 
    
- Si vous disposez déjà d’un déploiement de cloud hybride Azure avec un réseau virtuel entre différents locaux, n’hésitez pas à adapter ou à ignorer les instructions des phases 1 et 2 et placez les serveurs proxy AD FS et d’application web dans les sous-réseaux appropriés.
    
Pour créer un environnement de développement/test ou une preuve de concept de cette configuration, reportez-vous à [la rubrique identité fédérée pour votre environnement de développement/test Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment).
  
## <a name="next-step"></a>Étape suivante

Démarrer la configuration de la charge de travail avec [Phase 1 : configurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
  
