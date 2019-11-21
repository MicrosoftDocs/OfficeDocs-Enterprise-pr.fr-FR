---
title: Planifier les certificats SSL tiers pour Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Résumé : décrit les certificats SSL nécessaires pour Exchange sur site et hybride, l’authentification unique à l’aide d’AD FS, d’Exchange Online Services et des services Web Exchange.'
ms.openlocfilehash: 74540fb612bd515443912114ebec20cd8ed5e1aa
ms.sourcegitcommit: 6639b0f0171f7552111267a64d6b199755bf34fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "38756613"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Planifier les certificats SSL tiers pour Office 365

*Cet article s’applique à la fois à Office 365 entreprise et à Microsoft 365 entreprise.*

Pour chiffrer les communications entre vos clients et l’environnement Office 365, des certificats SSL (Secure Socket Layer) tiers doivent être installés sur vos serveurs d’infrastructure.

||
|:-----|
| Cet article fait partie de la [planification réseau et du réglage des performances pour Office 365](https://aka.ms/tune).|
   
Les certificats sont requis pour les composants Office 365 suivants :
  
- Exchange local
    
- Authentification unique (SSO) (pour les serveurs de fédération AD FS (Active Directory Federation Services) et les proxys de serveur de fédération AD FS)
    
- Services Exchange Online, tels que la découverte automatique, Outlook Anywhere et les services Web Exchange
    
- Serveur Exchange hybride
    
## <a name="certificates-for-exchange-on-premises"></a>Certificats pour Exchange local

Pour obtenir une vue d’ensemble de l’utilisation des certificats numériques pour établir la communication entre l’organisation Exchange locale et Exchange Online sécurisé, voir l’article TechNet [Understanding Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).
  
## <a name="certificates-for-single-sign-on"></a>Certificats pour l’authentification unique

Pour fournir à vos utilisateurs une expérience d’authentification unique simplifiée qui inclut une sécurité fiable, les certificats indiqués dans le tableau suivant sont requis sur les serveurs de Fédération ou sur les serveurs proxy de Fédération. Le tableau suivant se concentre sur les services ADFS (Active Directory Federation Services), d’autres informations sur [l’utilisation des fournisseurs d’identité tiers](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
||||
|:-----|:-----|:-----|
|**Type de certificat** <br/> |**Description** <br/> |**Ce que vous devez savoir avant de procéder au déploiement** <br/> |
|**Certificat SSL (également appelé certificat d’authentification de serveur)** <br/> |Il s’agit d’un certificat SSL standard utilisé pour sécuriser les communications entre les serveurs de Fédération, les clients et les serveurs proxy de Fédération.  <br/> |AD FS nécessite un certificat SSL. Par défaut, AD FS utilise le certificat SSL configuré pour le site Web par défaut dans Internet Information Services (IIS).  <br/> Le nom de sujet de ce certificat SSL est utilisé pour déterminer le nom du service FS (Federation Service) pour chaque instance des services ADFS (Active Directory Federation Services) que vous déployez. Vous pouvez choisir un nom de sujet pour les nouveaux certificats émis par une autorité de certification qui représente le mieux le nom de votre société ou organisation vers Office 365. Ce nom doit être routable par Internet.  <br/>**Attention :** AD FS nécessite que ce certificat SSL n’ait pas de nom d’objet sans point (nom abrégé).          <br/> **Recommandation :** Étant donné que ce certificat doit être approuvé par les clients AD FS, nous vous recommandons d’utiliser un certificat SSL émis par une autorité de certification publique (tierce) ou par une autorité de certification qui est subordonnée à une racine de confiance publique ; par exemple, VeriSign ou Thawte.  <br/> |
|**Certificat de signature de jetons** <br/> |Il s’agit d’un certificat X. 509 standard qui est utilisé pour signer de manière sécurisée tous les jetons que le serveur de Fédération émet et qu’Office 365 accepte et valide.  <br/> |Le certificat de signature de jetons doit contenir une clé privée qui est chaînée à une racine de confiance dans les FS. Par défaut, AD FS crée un certificat auto-signé. Toutefois, en fonction des besoins de votre organisation, vous pouvez modifier ce certificat en un certificat émis par l’autorité de certification à l’aide du composant logiciel enfichable Gestion AD FS.  <br/>**Attention :** Le certificat de signature de jetons est essentiel à la stabilité des FS. Si le certificat est modifié, Office 365 doit être informé de la modification. Si la notification n’est pas fournie, les utilisateurs ne peuvent pas se connecter à leurs offres de service Office 365.<br/>**Recommandation :** Nous vous recommandons d’utiliser le certificat de signature de jetons auto-signé qui est généré par les services ADFS (Active Directory Federation Services). En procédant ainsi, il gère ce certificat par défaut. Par exemple, lorsque ce certificat est sur le paragraphe expire, AD FS génère un nouveau certificat auto-signé.  <br/> |
   
Les proxies de serveur de Fédération nécessitent le certificat décrit dans le tableau suivant.
  
||||
|:-----|:-----|:-----|
|**Type de certificat** <br/> |**Description** <br/> |**Ce que vous devez savoir avant de procéder au déploiement** <br/> |
|certificat SSL  <br/> |Il s’agit d’un certificat SSL standard utilisé pour sécuriser les communications entre un serveur de Fédération, un serveur proxy de Fédération et des ordinateurs clients Internet.  <br/> |Ce certificat SSL doit être lié au site Web par défaut dans IIS avant de pouvoir exécuter l’Assistant Configuration du serveur proxy de fédération AD FS.  <br/> Ce certificat doit avoir le même nom de sujet que le certificat SSL configuré sur le serveur de Fédération dans le réseau d’entreprise.  <br/> **Recommandation :** Nous vous recommandons d’utiliser le même certificat d’authentification de serveur que celui configuré sur le serveur de Fédération auquel ce serveur proxy de Fédération se connecte.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certificats pour la synchronisation Autodiscover, Outlook Anywhere et Active Directory

Vos serveurs d’accès au client Exchange 2013, Exchange 2010, Exchange 2007 et Exchange 2003 (CASs) externes requièrent un certificat SSL tiers pour les connexions sécurisées pour la découverte automatique, Outlook Anywhere et les services de synchronisation Active Directory. Ce certificat est peut-être déjà installé dans votre environnement local.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certificat pour un serveur hybride Exchange

Votre ou vos serveurs Exchange hybrides externes nécessitent un certificat SSL tiers pour la connectivité sécurisée avec le service Exchange Online. Vous devez obtenir ce certificat auprès de votre fournisseur SSL tiers.
  
## <a name="office-365-certificate-chains"></a>Chaînes de certificats Office 365

Cet article décrit les certificats que vous devrez peut-être installer sur votre infrastructure. Pour plus d’informations sur les certificats installés sur nos serveurs Office 365, consultez la rubrique [chaînes de certificats office 365](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  
## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
