---
title: Planifier les certificats SSL tiers pour Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Résumé : Décrit les certificats SSL nécessaires pour Exchange sur site et hybride, l’authentification unique via AD FS, les services Exchange Online et les services web Exchange.'
ms.openlocfilehash: 82e37ebb058b8a6b4b618649bea31a4137897690
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975212"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Planifier les certificats SSL tiers pour Office 365

 **Résumé :** Décrit les certificats SSL nécessaires pour Exchange local et hybride, l’authentification unique avec ADFS, les services Exchange Online et les Services Web Exchange. 
  
Pour chiffrer les communications entre vos clients et theOffice 365Office 365 environnement, les certificats tiers Secure Sockets Layer (SSL) doivent être installés sur vos serveurs d’infrastructure.

||
|:-----|
| Cet article fait partie de la [planification de réseau et de réglage des performances pour Office 365](https://aka.ms/tune).|
   
Des certificats sont requis pour les composants Office 365 suivants :
  
- Exchange local
    
- Authentification unique (SSO) (pour les serveurs de fédération ADFS (Active Directory Federation Services) et les serveurs proxy de fédération ADFS)
    
- Services Exchange Online, tels que Autodiscover, Outlook Anywhere et Services Web Exchange
    
- Serveur Exchange hybride
    
## <a name="certificates-for-exchange-on-premises"></a>Certificats pour Exchange local

Pour une vue d’ensemble sur l’utilisation des certificats numériques pour sécuriser la communication entre l’organisation Exchange sur site et Exchange Online, consultez l’article TechNet [Présentation Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).
  
## <a name="certificates-for-single-sign-on"></a>Certificats pour l'authentification unique

Pour fournir aux utilisateurs une seule authentification simplifiée qui inclut une sécurité fiable, les certificats indiqués dans le tableau suivant sont nécessaires sur les serveurs de fédération ou les serveurs proxy de fédération. Le tableau ci-dessous se concentre sur Active Directory Federation Services (ADFS), nous avons également plus d’informations sur [l’utilisation de fournisseurs d’identité tiers](https://go.microsoft.com/fwlink/?LinkId=532869).
  
||||
|:-----|:-----|:-----|
|**Type de certificat** <br/> |**Description** <br/> |**Ce qu’il faut savoir avant de procéder au déploiement** <br/> |
|**Certificat SSL (également appelé certificat d'authentification serveur)** <br/> |Il s'agit d'un certificat SSL standard utilisé pour sécuriser les communications entre les serveurs de fédération, les clients et les serveurs proxy de fédération.  <br/> |AD FS requiert un certificat SSL. Par défaut, AD FS utilise le certificat SSL est configuré pour le site Web par défaut dans Internet Information Services (IIS).<br/> Le nom du sujet du certificat SSL est utilisé pour déterminer le nom du Service de fédération (FD) pour chaque instance d’AD FS que vous déployez. Pensez à choisir un nom de sujet pour toute nouvelle autorité de certification (CA)-émis les certificats que meilleur représente le nom de votre société ou organisation vers Office 365. Ce nom doit être routable Internet.<br/>**Mise en garde :** AD FS requiert que ce certificat SSL avoir aucun point (nom court) nom du sujet.          <br/> **Recommandation :** Étant donné que ce certificat doit être approuvé par les clients d’AD FS, nous vous recommandons d’utiliser un certificat SSL émis par une autorité de certification publique (tierce) ou par une autorité de certification qui est subordonnée à la racine de confiance publiquement ; par exemple, VeriSign ou Thawte.  <br/> |
|**Certificat de signature de jetons** <br/> |Il s’agit d’un certificat X.509 standard qui est utilisé pour signer en toute sécurité tous les jetons que le serveur de fédération émet et que Office 365 accepte et valide.  <br/> |Le certificat de signature de jetons doit contenir une clé privée qui est lié à la racine de confiance dans le système de fichiers. Par défaut, les services AD FS crée un certificat auto-signé. Toutefois, selon les besoins de votre organisation, vous pouvez modifier ce certificat à un certificat émis par une autorité de certification à l’aide du composant logiciel enfichable Gestion AD FS.<br/>**Mise en garde :** Le certificat de signature de jetons est essentiel pour la stabilité du système de fichiers. Si le certificat est modifié, Office 365 doit être informé de la modification. Si la notification n’est pas fournie, les utilisateurs ne peuvent pas se connecter à leurs offres de services Office 365.<br/>**Recommandation :** Nous recommandons d’utiliser le certificat de signature de jetons signé qui est généré par AD FS. En procédant ainsi, il gère ce certificat pour vous par défaut. Par exemple, lorsque ce certificat va expirer, AD FS génère un nouveau certificat auto-signé.<br/> |
   
Les serveurs proxy de fédération nécessitent le certificat décrit dans le tableau suivant.
  
||||
|:-----|:-----|:-----|
|**Type de certificat** <br/> |**Description** <br/> |**Ce qu’il faut savoir avant de procéder au déploiement** <br/> |
|Certificat SSL  <br/> |Il s'agit d'un certificat SSL standard utilisé pour sécuriser les communications entre un serveur de fédération, un serveur proxy de fédération et des ordinateurs clients Internet.  <br/> |Ce certificat SSL doit être lié au site Web par défaut dans IIS avant de pouvoir exécuter l’Assistant de Configuration de Proxy du serveur de fédération AD FS avec succès.  <br/> Ce certificat doit avoir le même nom de sujet que le certificat SSL configuré sur le serveur de fédération dans le réseau d'entreprise.  <br/> **Recommandation :** Nous vous recommandons d'utiliser le même certificat d'authentification serveur que celui configuré sur le serveur de fédération auquel ce serveur proxy de fédération se connecte.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certificats pour Autodiscover, Outlook Anywhere et la synchronisation Active Directory

Vos serveurs Exchange 2013, Exchange 2010, Exchange 2007 et accès Client Exchange 2003 externe (classes) nécessitent un certificat SSL de tiers pour les connexions sécurisées pour les services de synchronisation Autodiscover, Outlook Anywhere et Active Directory. Vous disposez peut-être déjà ce certificat installé dans votre environnement local.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certificat pour un serveur hybride Exchange

Votre serveur Exchange hybride externe ou les serveurs nécessitent un certificat SSL de tiers pour la connectivité sécurisée avec le service Exchange Online. Vous devez obtenir ce certificat à partir de votre fournisseur SSL de tiers.
  
## <a name="office-365-certificate-chains"></a>Chaînes de certificats d’Office 365

Cet article décrit les certificats, que vous devrez peut-être installer sur votre infrastructure. Pour plus d’informations sur les certificats installés sur nos serveurs Office 365, voir [Chaînes de certificats Office 365](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  

